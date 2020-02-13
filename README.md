# Music and Tech 2 Blog
The purpose of this 'blog' is to track the progress of my PoseNet based gesture classifier and audio engine.

Checkout my project at https://github.com/seanerice/chuck-sta-pose

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
- Gather more training data
    - [ ] Create data annotation tools
        1. Load data point from file
        2. Render points on screen
        3. Label points with parameter data (i.e. r_arm: 0.3)
        - OpenCV and command line?
    - [ ] Record pose data
        - raise each arm
        - lower each arm
        - open arms
        - close arms
        - point to different areas off camera
    - [ ] Annotate pose data with gesture class label and parameters
        - Parameters:
            - `r_hand_ht`, `l_hand_ht`
            - `r_pointed_to`
            - `l_pointed_to`
        - Classes:
            - `b_arm_lower`, `r/l_arm_raise`, `r/l_arm_lower`
            - `arms_close`, `arms_open`
            - `point_l`, `point_r`, `point_both`
            
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
