1. What are Channels and Kernels (according to EVA)?
   Information of a certain unique type collectively is called a channel, or more plainly, informatino with similar characteristics is from the same channel.
   For instance, the color channels most commonly used are Red, Green & Blue. The sound from the same musical instrument is from the same channel. The alphabets of english language are each individual channels (26 channels in this case).
   Basically, the fundamental building blocks of any piece of information, be it audio, image, etc, are channels. It is through the combinations of these channels, building blocks, that the end product is represented.

Kernels are unique characteristic or feature detectors. They are matrices with learned parameter values to detect features.

2. Why should we (nearly) always use 3x3 kernels?
   There is a 2 part answer to this, one explaining the choice of odd dimentional kernels for convolution, and another elaborating on preference of 3x3 kernels specifically.
   Odd kernels are favoured because it gives us symmetry along the central axis of the matrix (kernel). The advantage of this over a even kernels is that unlike its counterpart, the odd dimentional kernels can detect distinct changes in edges or topology. It gives us contrast of that edge, making it a better detector wrt sharpness or accuracy of detection.
   Does that mean any odd kernel can be used? Technically, Yes but computationally or practically, No.
   The preference of a 3x3 kernel over, let's say, 5x5 kernel is purely from a computational point of view. Higher the dimention of the convolutional kernel, higher the number of parameters to learn.
   For instance, an input of 8x8 image to reach 4x4 output requires 1 convolution by a 5x5 kernel (8-5+1 =4), but this is achieved by learning 5x5 = 25 parameters. The same operation/task can be done by 2 convolutions by a 3x3 kernel (8-3+1=6; 6-3+1=4) while only learning 3x3x2 = 18 parameters.

3) How many times to we need to perform 3x3 convolutions operations to reach close to 1x1 from 199x199 (type each layer output like 199x199 > 197x197...)
   shrink step size per convolution = org size - size after 1 conv = 199 - (199 - 3 + 1) = 2
   Let No. of convolutions required be 'n'.
   Thus, 199 - 2n = 1 (final output size req. is 1x1)
   solving for n, we get n = 99 iterations/convolutions.

4. How are kernels initialized?
   Kernels are initialized by drawing values randomly from gaussian distribution.
   Stochastic Gradient Descent (SGD) with random initialization can learn the convolutional filter in polynomial time and the convergence rate depends on the smoothness of the input distribution and the closeness of patches.
   (https://openreview.net/pdf?id=SkA-IE06W)

5) What happens during the training of a DNN?
   During training, a forward pass followed by a back propagation happens for each training sample.
   The forward pass comprises of linear combination of inputs with corresponding weights passed over an activation function.
   The backward propagation is used to update the weights of each node of the hidden layers.
   With each training sample, the error in the loss function keeps decreasing until convergence.
