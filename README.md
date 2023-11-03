# CNNs-and-Vision-Transformers

### Multi-Scale Feature Representations:

In convolutional architectures, we generally try to increase the number of channels through the encoder blocks in order to learn and model more complex representations in feature maps. At this point, we also downscale the resolution of these feature maps by using max-pooling or striped convolution for compensation in computational complexity. In fact, this approach provides us with multi-scale, also called as hierarchical, feature maps through the network. 

One disadvantage of utilizing vision transformers as a feature extractor backbone is that they are unable to work in multi-scale feature hierarchy unlike CNNs. For example, if input image is split into $16 \times 16$ patches to be fed into ViTs, feature representations through the entire transformer module remain as $\frac{H}{16} \times \frac{W}{16}$. On the contrary, we can resize them with the help of max-pooling, strider convolution, or up-conv in convolutional architectures. Working with mono-scale feature maps, actually, limits maximum potential that ViTs can reach in dense prediction tasks like segmentation. Besides, the detection of varying-sized objects in image context can be more difficult with fixed resolution in feature maps. 

To solve this problem, the patches flowing through the transformer try to resized by patch-merging and patch expanding modules. The following papers provide some insights about this:

- SegFormer: Simple and Efficient Design for Semantic Segmentation with Transformers

- A Robust Volumetric Transformer for Accurate 3D Tumor Segmentation

- Learning to Merge Tokens in Vision Transformers

### Embedding Size and Number of Layers:

Hyper-parameter tuning is another important point to be discussed in vision transformers. How many number of encoder layers they have and their embedding size can have directly impact model performance. It is commonly observed that using only 6 encoder layers in a ViT architecture is not enough, yet so many different convolutional architectures like U-Net, V-Net are able to converge in a very quick way and show promising results. 9 to 12 number of layers can regarded as a threshold for a simple vision transformer. In addition to this, ViTs are also sensitive to embedding size; it is commonly set to 768, which seems to be quite large for a just 16x16 patch. However, if it is decreased to 192, their performance can be restricted especially depending on the task. These show that vision transformers are not satisfied with few number of layers and inclined to work with larger embedding size, which make them non parameter-efficient models. 

### Information Retrieval and Kernel-based Learning:

Multiplication of input embeddings by weight matrices to generate query, key and value matrices for attention layer is a more global-scale methodology used in transformers to cover and evaluate contextual information in different parts of the image. Compared with this attention mechanism, convolution operates on images with restricted and local $3 \times 3$ or $5 \times 5$ kernels by cross correlation calculation. So, the former one goes through entire image and look at it in a more global scope, the latter tries to enlarge its local scope with more number of consecutive convolution layers in deeper architectures to gain more global point of view. 

Since weight kernels are in the similar shape of images, CNNs gain more inductive bias. This helps them to converge faster with a limited amount of dataset. On the other hand, ViTs actually try to reformulate images and convert them into sequence embeddings. This approach and also information retrieval system depending on key-value-query generation are not so assumption based; namely they are not specifically designed for the shape and spatial domain of image. ViTs are lacking inductive bias, which decreases the speed of convergence, requires the usage of small learning rate and makes themselves greedy to the larger datasets. To solve this problem, adding some convolution layers inside or using with vision transformers starts to be common practice. 

- Early Convolutions Help Transformers See Better
  
- Conformer: Local Features Coupling Global Representations for Visual Recognition
