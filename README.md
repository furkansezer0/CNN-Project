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


## Update-1

Model properties changed with 5 different way in order to see the contribution of some features.

### Comparisons

1. Two Dense Layers vs One Dense Layer
2. Two Dropout Layers vs One Dropout Layer
3. Dataset ratio 0.2 vs 0.3
4. GlobalAveragePooling2D Layer vs Flatten Layer
5. Input Size 224px vs 64px

#### 1. Two Dense Layers(Original Model) vs One Dense Layer 

##### ACCURACY

![main-acc](https://user-images.githubusercontent.com/91841885/178354140-a8ed28cf-c6ce-438e-becb-97e7ea247bf1.png)
![one-dense-acc](https://user-images.githubusercontent.com/91841885/178354418-4220e3b7-ce1e-4e7e-80f1-1fd677436df0.png)

<pre>    
Two Dense Layers train_acc = 0.9408               One Dense Layer train_acc = 0.9523

Two Dense Layers val_acc = 0.8624                 One Dense Layer val_acc = 0.8052
</pre>

##### LOSS

![main-loss](https://user-images.githubusercontent.com/91841885/178361475-113e966f-29c3-4960-893a-106005d74688.png)
![one-dense-loss](https://user-images.githubusercontent.com/91841885/178361512-1acb152e-3eb3-4168-b03b-f4dd557ebc69.png)

<pre>
Two Dense Layers train_loss = 0.1820              One Dense Layer train_loss = 0.1392

Two Dense Layers val_loss = 0.5580                One Dense Layer val_loss = 0.8125
</pre>


#### 2. Two Dropout Layers(Original Model) vs One Dropout Layer 

<pre>
! Dropout Layer reduces overfitting so model accuracy decreases a bit when dropout layer is used. But it also make training and validation accuracy more close each other.
</pre>

##### ACCURACY

![main-acc](https://user-images.githubusercontent.com/91841885/178354140-a8ed28cf-c6ce-438e-becb-97e7ea247bf1.png)
![one-dropout-acc](https://user-images.githubusercontent.com/91841885/178363497-9eb054af-3240-419a-aacd-79259ebe4d1d.png)

<pre>
Two Dropout Layers train_acc = 0.9408              One Dropout Layer train_acc = 0.9474

Two Dropout Layer val_acc = 0.8624                 One Dropout Layer val_acc = 0.8243
</pre>

##### LOSS

![main-loss](https://user-images.githubusercontent.com/91841885/178361475-113e966f-29c3-4960-893a-106005d74688.png)
![one-dropout-loss](https://user-images.githubusercontent.com/91841885/178364421-f6e69136-1bde-440a-ac0f-321dc471868c.png)

<pre>
Two Dropout Layers train_loss = 0.1820             One Dropout Layer train_loss = 0.1544

Two Dropout Layer val_loss = 0.5580                One Dropout Layer val_loss = 0.6891
</pre>

#### 3. Dataset ratio 0.2(Original Model) vs Dataset ratio 0.3
<pre>
! If dataset ratio increases, training set size decreases. so model accuracy decreases a bit when dataset ratio is increased.
</pre>

##### ACCURACY

![main-acc](https://user-images.githubusercontent.com/91841885/178354140-a8ed28cf-c6ce-438e-becb-97e7ea247bf1.png)
![ratio-3-acc](https://user-images.githubusercontent.com/91841885/178365287-dc67698a-57be-4d80-9cf1-dfecf6a57af2.png)

<pre>
Dataset ratio 0.2 train_acc = 0.9408               Dataset ratio 0.3 train_acc = 0.9360

Dataset ratio 0.2 val_acc = 0.8624                 Dataset ratio 0.3 val_acc = 0.8318
</pre>

##### LOSS

![main-loss](https://user-images.githubusercontent.com/91841885/178361475-113e966f-29c3-4960-893a-106005d74688.png)
![ratio-3-loss](https://user-images.githubusercontent.com/91841885/178365581-80932b17-4e9a-4b9d-a3d0-851481eb5eed.png)

<pre>
Dataset ratio 0.2 train_loss = 0.1820              Dataset ratio 0.3 train_loss = 0.1842

Dataset ratio 0.2 val_loss = 0.5580                Dataset ratio 0.3 val_loss = 0.7423
</pre>

#### 4. Global Average Pooling 2D Layer(Original Model) vs Flatten Layer

<pre>
! GlobalAveragePooling2D Layer is just an option for CNN models. It has less parameters than Flatten Layer. So it can reduce overfitting.
</pre>

##### ACCURACY

![main-acc](https://user-images.githubusercontent.com/91841885/178354140-a8ed28cf-c6ce-438e-becb-97e7ea247bf1.png)
![flatten-acc](https://user-images.githubusercontent.com/91841885/178365873-6ac88da6-995d-496c-88e8-f8beaaa2003b.png)

<pre>
GlobalAveragePooling2D Layer train_acc = 0.9408    Flatten train_acc = 0.9201

GlobalAveragePooling2D Layer val_acc = 0.8624      Flatten val_acc = 0.7867
</pre>

##### LOSS

![main-loss](https://user-images.githubusercontent.com/91841885/178361475-113e966f-29c3-4960-893a-106005d74688.png)
![flatten-loss](https://user-images.githubusercontent.com/91841885/178365894-b642b931-a362-409a-855e-f9cb6f78a18f.png)

<pre>
GlobalAveragePooling2D Layer train_loss = 0.1820   Flatten train_loss = 0.2690

GlobalAveragePooling2D Layer val_loss = 0.5580     Flatten val_loss = 0.8638
</pre>

#### 5. Input Size 224px(Original Model) vs Input Size 64px

<pre>
! Input size is very important parameter for CNN models. It directly affects train and validation accuracy. If model layer architecture is complicate for input size, model cannot learn sufficiently and also higher input size provide more information for layers.
</pre>

##### ACCURACY

![main-acc](https://user-images.githubusercontent.com/91841885/178354140-a8ed28cf-c6ce-438e-becb-97e7ea247bf1.png)
![input-64-acc](https://user-images.githubusercontent.com/91841885/178366876-cec6cfcd-1778-4082-b9b5-cbebc82c7951.png)

<pre>
Input Size 224px train_acc = 0.9408                 Input Size 64px train_acc = 0.8707

Input Size 224px val_acc = 0.8624                   Input Size 64px val_acc = 0.7152
</pre>

##### LOSS

![main-loss](https://user-images.githubusercontent.com/91841885/178361475-113e966f-29c3-4960-893a-106005d74688.png)
![input-64-loss](https://user-images.githubusercontent.com/91841885/178366903-f5810641-4d03-4474-b53f-b62c5420f2ba.png)

<pre>
Input Size 224px train_loss = 0.1820                Input Size 64px train_loss = 0.3907

Input Size 224px val_loss = 0.5580                  Input Size 64px val_loss = 1.0093
</pre>

