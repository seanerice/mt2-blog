# Music and Tech 2 Blog
My project updates will live here.

## Week of 2.3.2020
Let's get this bread.

## Week of 1.27.2020
No progress.

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

## Week of 1.20.2020

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


## Week of 1.13.2020
I want to pick up where I left off in MT1 -- build an interactive piece using pose tracking and classification. This will likely involve building a custom RNN along with creating lots of _good_ training data.

### Progress
- Create GitHub page @ [github page](seanerice.github.io/mt2-blog/)

### What's slowing me down
- Sickness :(

### Next steps
- Research ML packages suitable for LSTM
- Ask how to get lab time in MoCap lab
