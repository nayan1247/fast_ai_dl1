#Fast AI - Lesson 1

###Introduction to Jupyter Notebook and Dogs vs. Cats 

- You can run a cell by selecting it and hitting shift+enter , or you can click on Run button at the top. A cell can contain code, text, picture, video, etc.
- Fast.ai requires Python 3
- `!` tells the interpretor to use shell instead of python

### Data 

- Every image is a 3 dimensional array (rank 3 tensor). The three dimensions are x, y and channels.
- `img = plt.imread(f'{PATH}valid/cats/{files[0]}')` reads a image as an array
- `img.shape` shows the dimensions of the image, in this case pixels in x, pixels in y , # of channels

### Neural Network Basics
- An epoch is a single pass through the entire training set which consists of multiple iterations of SGD.
- a batch or mini-batch is a subset of training samples used in one iteration of Stochastic Gradient Descent (SGD)
-  `# `of microbatches is # of training samples/# of iterations
-  data augmentation is a technique to use the same data in a slight different way - horizontal flip, vertical flip, zoom, rotating etc to get additional information from the same image
-  augmentation can be done on both training and test data sets , and also is named training time augmentation and test time augmentation
-  activation means A NUMBER
-  activation function (sigmoid, ReLU - rectified linear unit) take the activation and convert that into a output
-  learning rate annealing is a technique to use differential learning rates for different microbatches. This is to take advantage of the gradient descent method to allow larger LR in the start and as we near the optima gradually reduce the LR. A common accepted method is cosine rate annealing where half of the cosine curve is used to generate the LR
-  stochastic gradient descent with restarts  - Use half cosine wave form to have a cyclic pattern of LR. This helps to jump the local hills and try to move from local minima to global minima. We want to encourage our model to find parts of the weight space that are both accurate and stable. Therefore, from time to time we increase the learning rate (this is the 'restarts' in 'SGDR'), which will force the model to jump to a different part of the weight space if the current area is "spikey"
-  cycle length =1 by default which means 1 cycle of cosine wave for 1 epoch
-  fully connected layer - 

### Learning Rate Finder
- Fast AI has a functionality to find optimal learning rate called LR_FIND
- While plotting loss vs LR , the point where the gradient for the loss is maximum is ideal learning rate. (and not the bottom of the chart) . Learning rate needs to be a a larger number than the bottom to be able to traverse effectively to the global minima, while at the bottom the LR is a very small number and hence not optimal



### Fast AI specific features
- The layers are classified into 3 groups. By default all the layers are frozen except the last layer when a new learner is create.
- Unfreezing by default it unfreezes all the layers
- Typically (1/100,1/10,1) are the learning rates for the 3 groups of layers when the objective is similar to what is used in the architecture. In case it is very difference (1/10,1/3,1) are used to allow earlier networks also to be optimized
-  `learn.fit(lr, 3, cycle_len=1, cycle_mult=2)` 
	- 3 is the # of cycles
	- cycle length is the length of each cycle wrt epocs
	- cycle mult gives a multiplier to the cycle length once every cycle is complete
	-So in the `learn.fit(lr, 3, cycle_len=1, cycle_mult=2)` there are 3 cycles and 7 epocs with each cycle having of 1,2,4 epocs respectively
	- 

 


