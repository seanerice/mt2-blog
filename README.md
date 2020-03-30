# Music and Tech 2 Blog
The purpose of this 'blog' is to track the progress of my PoseNet based gesture classifier and audio engine.

Checkout my project at https://github.com/seanerice/chuck-sta-pose

# Week of 3.30.2020

### What's going on?

I made a little progress; after hours of trial and error, I finally found the right implementation to get initial results. Currently the model has an _okay_ test accuracy with some pet data, now I need to tweek the model to work well with the stream data.

### To-do this week

Optimize for pose-data:
- Find optimal parameters
- Consider convolution before LSTM for positional invariance

Take a short video of classification.

### For the future

Train a model:
- More data!
- Save it!!!

Hook into ChucK:
- OSC sender

Test it (oh lord let it be good)

Design a short piece to showcase gesture control.

# Week of 3.23.2020

### What's going on?

Spring break is over and I rested and relaxed as much as I could which means I have no progress to report. Currently my LSTM won't train, which is a bit disconcerting, however I'm confident it is fixable.

### To-do this week

Figure out why my LSTM isn't training. :(

# Week of 3.2.2020

### What's going on?
Over the last two weeks I have worked towards getting a trained model working, but I've had a few difficulties getting the LSTM model to train on my pet train set. This may be due to a lack of understanding on my part as far as feeding the data to the model.

### To-do for the coming weeks

- [ ] Train and test LSTM on small dataset
- [ ] Integrate LSTM with ChucK scripts and test audio control

# Week of 2.24.2020

### Progess

Created annotation tool according to last weeks specs.

# Week of 2.17.2020

### What's going on?
Last week I remebered I had no way of labeling training data. Neural networks are really good at learning an output from a given input. In unsupervised learning, an ML model gradually learns what features produce what output after showing it numerous (input, output) pairs. In my case I have a lot of input and no output, so I can't train my network!!! Through the process of __data annotation__, however, I can create output data which represents the outputs I want the network to learn. 

### Creating training data
I have a thousands of training data which needs to be labeled. The hardest method (and most fine-grain) involves going through each point one-by-one and creating annotations. I can speed up class annotation when I label ranges of data as one class. For example, if my right arm is moving up over a period of time, I can label that region of data with r_arm_raise. Similarly, with parameter data, my arm may start at a height of 0.3 and stop at height 0.8; it's just a matter of interpoating between those points. Using this annotation model I can significantly speed up data annotation. Now I just have to build it.

### Data annotation tool
I want to use Unity3D to quickly build an annotation tool. I believe this is feasible within a one-week timeframe. Here's the deliverables:
- Load data from file, store in a buffer
- Interactive 'read-head' which displays one point in time
    - Slider moves time forwards and backwards
    - Arrow keys or on-screen keys for frame-by-frame precision
- Parameter annotation
    ```
    {
        name: string with no spaces or special characters
        start: integer >= 0
        end: integer < number of data points
        low: float in [0.0-1.0]
        high: float in [0.0-1.0]
        method: optional, string, default 'linear' 
    }
    ```
- Class annotation
    ```
    {
        name: string with no spaces or special characters
        start: integer >= 0
        end: integer < number of data points
    }
    ```
- Place start and stop points to annotate a range of data
- Can add more than one annotation at a time
- Export annotations to file

### Ideas
The annotation tool could become a spring-board for a visualizer which does interesting things with the data. Maybe I could extrude the 2d point data into the time dimension for a cool slithery stickman-snake. Maybe I can plot one dimension of data against time and annotate that way.

- Add 'hold-out' variable to each point; whether or not to ignore the data point.

### To-Do This Week
- [ ] Create data annotation tools
    1. Load data point from file
    2. Render points on screen
    3. Label points with parameter data (i.e. r_arm: 0.3)
    - ~OpenCV and command line?~
    - Unity3D
- [ ] Record pose data
    - raise each arm
    - lower each arm
    - open arms
    - close arms
    - point to different areas off camera
- [ ] Annotate pose data with gesture class label and parameters
    - [ ] Parameters:
        - `r_hand_ht`, `l_hand_ht`
        - `r_pointed_to`
        - `l_pointed_to`
    - [ ] Classes:
        - `b_arm_lower`, `r/l_arm_raise`, `r/l_arm_lower`
        - `arms_close`, `arms_open`
        - `point_l`, `point_r`, `point_both`

# Week of 2.10.2020

### To-Do This Week
- Gather training data
    - [x] Set up webcam with [PoseNetOSC](https://github.com/tommymitch/posenetosc)
    - [x] Create data writer for posenetosc
    - [ ] Record raw pose data (output 17x2 dimensional vector)
    - [ ] ~~Annotate each point with class label data.~~
    
### Ideas
- Consider preprocessing pose data
    - replace -1 values with last known position
    - (x, y) coordinates in range 0.0 - 1.0
    - Convert (x, y) coordinates from screen space to local space.
        - Point position is relative to 'root' bone
- Two neural nets
    - NN for parameters
    - LSTM for gesture classification

### To-Do Next Week
- Create data annotation tools
- Record pose data
- Annotate pose data with gesture class label and parameters
            
### Thoughts
I'm worried about the feasibility of annotating data, however well annotated data is useful for training.

# Week of 2.3.2020
    
### Progress
- Implemented LSTM classifier
    - Input: sequence of 17-dimension vectors (N x 17)
    - Output: Class probabilities (C dim vector)
- Created toy data for LSTM to test implementation

# Week of 1.27.2020

### Planning
- Leverage Pytorch ML library
    - Dynamic models are easy to put together (as opposed to static graph workflow in Tensor Flow).
    - LSTM model for classifying sequence data.
- Gather training data
    - Record pose data (output) from Google's DeepPose net
    - Webcam and subject should be in optimal lighting positions
    - Dozen or so examples for each classification
- "Normalize" training data
    - Minimum/maximum sequence length
- Parameterize voices in piece
    - Important to abstract audio logic for "simple" gesture control
    - I have a vision of a choral voice which can be controlled through dramatic gesturing. It will probably have parameters like pitch, volume, and layers (which changes the number of voices). 

# Week of 1.20.2020

### Planning
- Parameterize voices in piece
    - Important to abstract audio logic for "simple" gesture control
    - I have a vision of a choral voice which can be controlled through dramatic gesturing. It will probably have parameters like pitch, volume, and layers (which changes the number of voices). 

### Progress
- Papers!
    - [Paper](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=903641) describes pose classification using RBF (radial basis function) neural networks to classify hand gestures
    - [Paper](https://static.googleusercontent.com/media/research.google.com/en//pubs/archive/42237.pdf) describes Google's pose tracking method using Tensorflow's DNN (deep neural network) classifiers.
    
### What's slowing me down
- Lingering cough

### Next steps
- Research ML packages suitable for LSTM
- Ask how to get lab time in MoCap lab


# Week of 1.13.2020
I want to pick up where I left off in MT1 -- build an interactive piece using pose tracking and classification. This will likely involve building a custom RNN along with creating lots of _good_ training data.

### Progress
- Create GitHub page @ [github page](seanerice.github.io/mt2-blog/)

### What's slowing me down
- Sickness :(

### Next steps
- Research ML packages suitable for LSTM
- Ask how to get lab time in MoCap lab
