# Animal-10 CNN Project

In this model, 5 different data augmentation method were used.
 - Shear
 - Zoom
 - Horizontal Flip
 - Rotation
 - Brightness

Image size set to 224x224. Because I need more information from the pixels and also to make dataset size equal.

Dataset was split to training and validation with 0.2 ratio.

In the model, 
- 6 Convolutional layer (activation is relu),
- 3 Max Pooling layer ( Feature map with max values of pixels),
- 6 Batch Normalization layer (to make model process more safe and fast with less loss),
- Global Average Pooling 2D was preffered instead of Flatten. (to reduce parameters and overfitting),
- 2 Dense layer (1024 neuron),
- 2 Dropout layer with 0.2 ratio (to avoid overfitting),
- Softmax layer (to take value between [0,1] with probability)
were used.

Optimizer was set to adam with its own default learning rate.
Early Stopping function were added as callback function.




