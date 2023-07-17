# ImageSteganography
In the context of image steganography, the goal is to hide a
secret message within an image. For this purpose, we have used Convolutional Neural
Network (CNN). Convolutional Neural Networks (CNNs) are a type of neural network
commonly used in image recognition and computer vision tasks. While CNN are not
traditionally used for steganography, it is possible to use them for this purpose.

Development of models consists of two section:
I. Embedding image in image
II. Revealing secret image from stego image

I.Embedding image in image
For embedding secret image in cover image, two network model were developed. They
are as follows:
1. Preparation Network: Preparation Network transforms the RGB-pixels of the se-
crete into features that can be used by the Hiding-Network. These features are not
a prior specified; they are learned. An analysis of the transformations done by the
preparation network revealed ones that are commonly useful for hiding images,
such as edges and orthogonal components.The preparation network received the
secret image as input and applies a series of convolutional layers with different
kernel sizes, which are 3x3 with 50 filters, 4x4 with 10 filters, 5x5 with 5 fil-
ters.The activation function used is relu activation function. The outputs of these
layers are concatenated together and passed to a series of other convolutional
layers with the same kernel sizes.
2. Hiding Network: The actual embedding of the hidden image into the host im-
age/cover image is done by the Hiding-Network. The Hiding-Network receives
the output of the Preparation-Network and the host image as input. The input is
formatted as an N×N pixel field (for our studies, N=64), with depth concatenated
RGB channels of the host image and the transformed channels of the hidden
image The output of this network is the Container image (N×N, RGB pixels).
The container image should appear as similar to the host as possible, while also
containing enough information to recreate the hidden image.The hiding network
received the concatenation of the output of the preparation network and the cover
image as input and applies several series of convolutional layers with different
kernel sizes, which are 3x3 with 50 filters, 4x4 with 10 filters, 5x5 with 5 filters.
The activation function used is relu activation function.. The outputs of these
layers are concatenated together.

II.Revealing secrete image from stego-image
The second component, the Reveal-Network for extracting the hidden image from the
container. Though this network is used only by the receiver, all components are trained
as a single network in the form of autoencoder model.  The network applies a series of convolutional layers with
different kernel sizes, which are 3x3, 4x4, 5x5. The outputs of these layers are concate-
nated together and passed to more convolutional layers with the same kernel sizes. The
final output of the network is the decoded image and it is obtained by applying a final
3x3 convolutional layer on the concatenated features.


![image](https://github.com/ArpitRb/ImageSteganography/assets/121932552/ba9f1d5c-2045-4e41-9a60-bc692bdb5fd9)
Figure 3: Hiding signature, pixel error between cover and encoded cover found to be
11.623072 per pixel and pixel error between secret and decoded secret images found to
be 7.7668705 per pixel
