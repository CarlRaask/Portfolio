# Homebuilt neural network
## Calculus term 2 year 1s
### Summary
A flexible neural network built from the ground up using only NumPy and multivariate calculus.  
Teacher assistant said "Use MNIST if you are brave". So I decided to be brave.
Goal was to achieve 90%+ accuracy on MNIST digit classification, matching late 1990s pre-CNN neural network performance.  
**note from the future**  I had actually never heard of Neural Networks before calculus class.  
Some of my "lessons" are sortof correct but lacking.  
Im leaving them as is to reflect the knowledge of a first year undergraduate who went *slightly* overboard and went outside expected level of knowledge.  

### Final project of calculus class 
Built as part of a Mathematics for Machine Learning course to understand the basic mechanics behind neural networks.  
Instead of using prebuilt libraries such as TensorFlow or PyTorch, the class was tasked to build a NN from scratch using calculus and numpy as the main tools.   

### Key Features
*indicates going above and beyond task requirement  
Flexible Architecture: Configurable depth, width, and activation functions per layer   
Manual Backpropagation: Implemented gradient descent from scratch using derivatives and the chain rule   
*Automatic weight initialization based on activation function: He initialization for ReLU, Xavier for Softmax  
#### Training Optimizations:  
*Learning rate decay  
*Stochastic gradient descent with custom batch sizes  
*Gradient explosion/vanishing detection  
Both Regression & *Classification: Handles continuous function approximation and multi-class classification 

Activation Functions Supported  
ReLU (best for deep networks and overall shape)   
Sigmoid (good for smoothing and bounded outputs)   
Linear (output layer for regression)   
*Softmax (classification output)  

### Performance 
Function Approximation  
f(x) = exp(x) - Single hidden layer, 3000 iterations  
f(x) = sin(x)/x - 7-layer deep network capturing oscillations   
f(x,y) = sin(x) + cos(y) - 2D surface approximation with 96+ neurons  

*MNIST Digit Classification  
Test Accuracy: 90%+ (88-92% depending on run)   
Architecture: 784 → 128 → 64 → 32 → 10 (Softmax)  
Training: 5000 epochs, cross-entropy loss, batch size 64  
Comparable to research-level performance from the late 1990s  


### Key Learnings
Data scaling is critical: Gradient stability improved dramatically with StandardScaler/MinMaxScaler  
Dataset size matters: Increasing from 500 to 3000 samples made visualizations match reality even when loss was already low.  
This is a conventient sollution for synthetic data (as in this function approximation) but sadly not available to us in real life.  

Architecture choices have tradeoffs:  
*Deeper networks capture oscillations better but risk gradient issues   
*ReLU learns faster than sigmoid but can't produce negative values   
*Starting wide and narrowing helps capture overall patterns then details  

### Challenges & Solutions
*Gradient Explosion/Vanishing: Solved primarily through proper data scaling (StandardScaler → MinMaxScaler)  
'another note from the future* Since this was made during a basic calculus class we had not yet covered vanishing and exploding gradients.  
So I had to learn myself what it was. I am now fully aware that 0.25¹⁰ is a bad idea.  
Negative Value Prediction: ReLU and Sigmoid only output positive values.  
Solution: MinMaxScaler preprocessing or architectural choices (sigmoid at output)  
Memory Issues: Large meshgrids for 3D visualization required limiting dataset size strategically  
Limiting myself to the actual task:  
I probably spent more time tinkering with parameter tuning and subsequent tweaking of code to fix issues that popped up,  
than building the according to project specs.   


Built as part of MA4029 Mathematics for Machine Learning course project.  