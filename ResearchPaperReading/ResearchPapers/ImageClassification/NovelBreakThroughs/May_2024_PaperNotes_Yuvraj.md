## VGG(Visual Geometry Group) Research Paper
![[VGG16_Architecture.png]]
- Short overview of the research Paper:

| Questions                                                                    | Answers                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| ---------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Is it clear what the paper is about, if yes then what?                       | Yes, the paper talks about variation of depths in CNN's by using very small convolution filters. <br>The representation of their network is able to generalise well to other datasets achieving state of the art results.                                                                                                                                                                                                                                                                                                                                                                           |
| In a very brief glance, what do the figures and tables convey?               | The tables describe the cnn architectures at varying depths, comparison of performance among the networks.<br>The authors also perform fusion of networks, and testing their performance. <br>Also the authors compare their network to other SOTA networks from 2012.                                                                                                                                                                                                                                                                                                                              |
| What methods do authors use in their paper?                                  | The authors utilize simple architecture configurations, variating in depths from 11 to 19 convolutional layers.<br><br>The layers are arranged in stacks of 5 convolutional layers. (2,2,3,3,3) for VGG 16. Each conv stack is followed by maxpooling.<br><br>The config for convolutional layers and max-pooling layers is pretty simple as mentioned below.                                                                                                                                                                                                                                       |
| How do these methods compare to other research in the domain?                | The VGG net configs utilize the benefit of using small receptive fields because a stack of 2 3x3 conv layers (without spatial pooling in between) has an effective receptive field of 5x5, likewise 3 3x3 conv layers stack has an effective receptive field  of 7x7.<br><br>By doing this the net incorporate 3 non-linear rectification layers instead of a single one, which makes the decision function more discriminative.<br><br>Secondly the authors decrease the number of parameters : [[02_VGG_ResearchPaper_2014.pdf#page=3&selection=279,0,347,47\|02_VGG_ResearchPaper_2014, page 3]] |
| What is better about their method?                                           | The number of weights in the VGG configs is not greater than the number of weights in a more shallow net with more larger conv. layer widths and receptive fields.<br><br>The nets require less epochs to converge due to implicit regularization imposed by greater depth and smaller conv. filter sizes and pre-initialization of certain layers.<br><br>The way they work on the test set is also quite different as compared to other domain research and shows some computation benefits.                                                                                                      |
| What is the summary of paper?                                                | Representation depth is beneficial for the classification accuracy, and sota performance on the ImageNet challenge dataset can be achieved using a conventional ConvNet architecture with substantially increased depth, and training at variation input scales.                                                                                                                                                                                                                                                                                                                                    |
| What of the research paper can be implemented in the real world application? | The depth configurations of VGG 16 and 19 can be beneficial to implement when you have large amount of data.<br>Another bit is about training at variated scales and testing also at variated scales can be implemented in real world.<br>Lastly combining dense and multi-crop evaluation techniques can also yield some benefits on the test data as showcased in the paper.                                                                                                                                                                                                                      |
| Any implementations of your own, you would like to experiment with?          | Not yet, however, if possible, it will be good to experiment with the variated scale training and testing of the model.                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
- Bits I like in the Paper:
	- Easy walkthrough in the paper like in section 2.
	- The research paper doesn't have their a full section of literature review, but they give a brief comparison to other research in the field in each of their section like section 2.3
	- Simple experimentation strategy where the authors start with basic architecture and increase complexity bit by bit.
- General Architecture of VGG:
	- Input: 224x224x3 RGB Image
	- Preprocessing: Subtracting the mean RGB value, computed on the training set, from each pixel
	- 5 Stacks Convolutional Layers each having (2,2,3,3,3 for VGG16) their own amount of conv layers depending on a VGG config
		- Each layer of CNN has a 3x3 filter applied over input by stride of 1 pixel, padding config of 1 pixel (so that input w n h) doesn't change after convolving. Also in C configuration one CNN layer at few layers (3,4,5) are having 1x1 filter applied with stride of 1 over the input, with padding config of 1 pixel
	- After the ending CNN layer in each convolution layer stack, there is a max pooling layer having a stride of 2 and a pixel window of 2x2. This directly halves the input given to max pooling layer, before sending it to next convolutional stack
	- Lastly there are 3 FC layers the first 2 having 4096 channels and third performs 1000-way ILSVRC classification and thus contains 1000 channels (one for each class). The final layer sitting on top of last layer is soft-max layer. FC layers configuration is same through all the networks
## Alex Net Research Paper
![[AlexNetArchitecture.png]]
- Working of Convolutional Neural Networks From the basics [^1] 
	- Simple explanation of working of a convolution block moving L->R and T -> B
	- Very intuitive explanation of 3 features of CNN:
		- Sparse interaction: Kernel size being smaller as compared to image
		- Parameter Sharing: Kernel taking strides, in a manner that the pixels overlap for creating a feature map
		- Invariant Translation: A single filter moving across the whole image, so we update only a single filter based on an input and not have weights for every single pixel in an image
		- Very basic code implementation
- Simple CNN implementation [^4]
	- Here the explanation is in bit more depth of the above mentioned 3 features of CNN
	- Simple code of a CNN block 
	- Formula for calculating the W & H after passing from a convolution are as follows:
		- General Formula: $\left\lfloor \frac{{\text{Input size} - \text{Kernel size} + 2 \times \text{Padding}}}{{\text{Stride}}} \right\rfloor + 1$ 
		- Output Height = $\left\lfloor \frac{{H_{\text{in}} - K_{\text{h}} + 2 \times P_{\text{h}}}}{{S}} \right\rfloor + 1$
		- Output Width =$\left\lfloor \frac{{W_{\text{in}} - K_{\text{w}} + 2 \times P_{\text{w}}}}{{S}} \right\rfloor + 1$
		- Where:
			- H_in: Height of the input image.
			- W_in: Width of the input image.
			- K_h: Height of the convolutional kernel/filter.
			- K_w: Width of the convolutional kernel/filter.
			- P_h: Padding added to the height dimension of the input image.
			- P_w: Padding added to the width dimension of the input image.
			- S: Stride of the convolution operation.
- How do the Convolution Filters work with multiple channels [^2] 
	- Is a bit more mathematical Implementation of how Convolutions work with multiple input channels
- YouTube Explanation of AlexNet by Krish Naik[^5]
	- Simple explanation of AlexNet
- Implementation of AlexNet from Scratch in Python [^3]
	- A good from scratch implementation of AlexNet in Pytorch 

## Annotations
| Symbol | Meaning |
| ------ | ------- |
| W      | Width   |
| H      | Height  |

# FootNotes
[^1]: [How Do Convolutional Layers Work in Deep Learning Neural Networks? - MachineLearningMastery.com](https://machinelearningmastery.com/convolutional-layers-for-deep-learning-neural-networks/) 
[^2]: [7.4. Multiple Input and Multiple Output Channels — Dive into Deep Learning 1.0.3 documentation (d2l.ai)](https://d2l.ai/chapter_convolutional-neural-networks/channels.html) 
[^3]: [AlexNet from scratch in PyTorch Lightning](https://lightning.ai/jed/studios/alexnet-from-scratch-in-pytorch-lightning)
[^4]: [Convolutional Neural Networks, Explained | by Mayank Mishra | Towards Data Science](https://towardsdatascience.com/convolutional-neural-networks-explained-9cc5188c4939)
[^5]: [Alexnet Architecture In-depth-Discussion Along With Code-Deep Learning Advanced CNN (youtube.com)](https://www.youtube.com/watch?v=7LQSdPjWjdA&t=178s&ab_channel=KrishNaik)