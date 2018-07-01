#### Semantic Segmentation Project (Advanced Deep Learning)

##### 1. Introduction
The objective of this project is to perform semantic segmentation on a car image for drivable road area by constructing a fully convolutional neural network based on the VGG-16 image classifier architecutre. The network was trained and tested on the KITTI data set.

[//]: # (Image References)
[image1]: ./test result 00.png "test result image 0"
[image2]: ./test result 01.png "test result image 1"
[image3]: ./test result 02.png "test result image 2"
[image4]: ./test result 03.png "test result image 3"

##### 2. Approach
###### Network Architecture
FCN-8 architecture developed at Berkeley was implemented in this project. The encoder is the VGG-16 model pretrained on ImageNet for classification. To convert it into a fully convolutional network, the fully-connected layers are replaced by 1x1 convolutions. To build decoder portion of FCN-8, I upsampled the input (output from encoder) to the original image size. For improving segmentation accuracy, skip connections have been implemented. To be specific, the pooling layer3, and pooling layer4 in the encoder were directly feeded into corresponding decoder upsamping layers by using element-wise addition before the final output were upsampled back into the original image size.

###### Optimizer
An Adam optimizer is used.The loss function for the network is cross-entropy.

###### Training
The hyperparameters used for training are:
keep_prob: 0.5
learning_rate: 0.001
epochs: 11
batch_size: 5
Results

Loss tends to decrease in general over epoches:
EPOCH 1 ...
Loss: = 0.194
EPOCH 2 ...
Loss: = 0.246
EPOCH 3 ...
Loss: = 0.179
EPOCH 4 ...
Loss: = 0.105
EPOCH 5 ...
Loss: = 0.146
EPOCH 6 ...
Loss: = 0.181
EPOCH 7 ...
Loss: = 0.102
EPOCH 8 ...
Loss: = 0.183
EPOCH 9 ...
Loss: = 0.128
EPOCH 10 ...
Loss: = 0.131
EPOCH 11 ...
Loss: = 0.092

###### Test Results
Below are some test result images output from the implemented fully convolutional network with the segmentation class overlaid upon the original image in green.
![Test Result][image1]
![Test Result][image2]
![Test Result][image3]
![Test Result][image4]


