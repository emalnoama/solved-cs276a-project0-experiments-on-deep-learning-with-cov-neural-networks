Download Link: https://assignmentchef.com/product/solved-cs276a-project0-experiments-on-deep-learning-with-cov-neural-networks
<br>
In the past 3 years, deep learning has become popular and been used widely for pattern classification tasks when large training data become available. This project is designed to provide you with first hand experience on training and testing a typical convolutional neural network (CNN) structure in a task of classifying 10 object classes.

Don’t panic! We have not taught this yet, and you don’t have to really understand the algorithm and learning method before you play with it. Standard code and data are provided to you. All you need to do is to follow the steps and run some experiments, then report results.

Figure 1: A ConvNet consists of multiple layers of filtering and sub-sampling operations for bottom-up feature extraction, resulting in multiple layers of feature maps and their sub-sampled versions. The top layer features are used for classification via multi-nomial logistic regression

<h1>2           ConvNet</h1>

The convolutional neural network (ConvNet) is a specific artificial neural network structure inspired by biological visual cortex and tailored for computer vision tasks. The ConvNet is a discriminative classifier, defined as a conditional (posterior) probability.

(1)

where <em>c </em>∈ {1<em>,</em>2<em>,…,C </em>= 10} is the class label of an input image <em>I</em>, and <em>f<sub>c</sub></em>(<em>I</em>;<em>w</em>) is the scoring function for each category, and computed by a series of operations in the CNN structure. Figure 1 displays an structure (architecture) of the CNN.

<ol>

 <li><strong>Convolution</strong>. The convolution is the core building block of a ConvNet and consists of a set of learnable filters. Every filter is a small receptive field. For example, a typical filter on the first layer of a ConvNet might have size 5x5x3 (i.e. 5 pixels width and height, and 3 color channels). Figure 2 illustrates the filter convolution.</li>

</ol>

Figure 2: Filter convolution. Each node denotes a 3-channel filter at specific position. Each filter spatially convolves the image.

<ol start="2">

 <li><strong>Pooling</strong>. Pooling is a form of non-linear down-sampling. Max-pooling is the most common. It partitions the input image into a set of non-overlapping rectangles and, for each such sub-region, outputs the maximum.</li>

 <li><strong>Relu</strong>. Relu is non-linear activation function <em>f</em>(<em>x</em>) = <em>max</em>(0<em>,x</em>). It increases the nonlinear properties of the decision function and of the overall network without affecting the receptive fields of the convolution layer.</li>

</ol>

LeNet shown in Table 2 is a typical structure design taylored for the CIFAR-10 dataset. The Block1 has 32 filters and the filter size is 5x5x3. The Block5 is a logistic regression layer, in which the number of filters is the number of classes and the filter size should be the same as the output from Block4. The CIFAR-10 dataset consists of 60<em>,</em>000 32 × 32 color images in 10 classes, with 6<em>,</em>000 images per class. There are 50<em>,</em>000 training images and 10<em>,</em>000 testing images. Figure 3 shows example images from 10 categories. The objective of classification is to predict the category of each image.

Figure 3: CIFAR-10 Dataset. CIFAR-10 contains 60,000 images in 10 classes.

<table width="551">

 <tbody>

  <tr>

   <td width="105">Block1</td>

   <td width="112">Block2</td>

   <td width="112">Block3</td>

   <td width="112">Block4</td>

   <td width="112">Block5</td>

  </tr>

  <tr>

   <td width="105">Conv 5x5x3x32</td>

   <td width="112">Conv 5x5x32x32</td>

   <td width="112">Conv 5x5x32x64</td>

   <td width="112">Conv 4x4x64x64</td>

   <td width="112">Conv 1x1x64x10</td>

  </tr>

  <tr>

   <td width="105">Pooling 3×3</td>

   <td width="112">Relu</td>

   <td width="112">Relu</td>

   <td width="112">Relu</td>

   <td width="112">Softmax</td>

  </tr>

  <tr>

   <td width="105">Relu</td>

   <td width="112">Pooling 3×3</td>

   <td width="112">Pooling 3×3</td>

   <td width="112"> </td>

   <td width="112"> </td>

  </tr>

 </tbody>

</table>

<h1>3           What to do</h1>

There are 3 steps for you to do in this project. We will also ask you to run this code again in later projects for comparison.

We will host a Tutorial Session on Tuesday evening.

<ol>

 <li>Download CIFAR-10, and learn a LeNet as described in Table 2 on it. Plot thetraining error and testing error against the training iteration.</li>

 <li>Keep the Block5, learn a ConvNet only with : a) Block1; b) Block1 and Block2;c) Block1, Block2 and Block3 respectively. Compare the final training errors and testing errors with LeNet in a table. (<strong>Hint</strong>: You need to change the filter size in Block5 to match the output from previous block.)</li>

 <li>Filter response visualization. Figure 4 displays the visualization of filter responsescomputed by 32 filters in the first layer. The first color image is the input image, and the rest of 32 heat images are the corresponding filter response maps. The directory of ./code/examples/images/ contains 10 images from each category. For each image, visualize the filter response maps of 32 filters in the first layer. (<strong>Hint</strong>: For each image, you need to preprocess it by subtracting the mean image of CIFAR-10. The mean image is saved in averageImage. You can use res = vl_simplenn(net, image)</li>

</ol>

to compute filter responses, and all filter responses computed by the first layer filters are saved in res(2).x)

Figure 4: Filter response visualization

<h1>4           Code</h1>

The code locates at ./code/examples/, and the code will donwload CIFAR-10 automatacally.

<ol>

 <li>m is the function to compile the code. You need run setup.m first.</li>

 <li>m is the main entry function, which gives an example of learning a LeNet.</li>

 <li>m is the training function to train a ConvNet. <strong>Modification: </strong>You design the draw_figure function in the line of 82 and 85 to plot the training and testing error. The error is computed by error_multiclass function and save in info.train.error and info.val.error.</li>

 <li>m defines the structure of ConvNet. <strong>Modification: </strong>You change the structure of ConvNet as required in step 2.</li>

</ol>