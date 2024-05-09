##
## VGG Net Research Paper
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