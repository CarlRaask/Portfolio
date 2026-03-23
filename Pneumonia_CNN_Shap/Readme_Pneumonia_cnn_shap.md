# School project Pneumonia CNN Shap
## Summary
A deep learning project classifying pneumonia from chest X-rays using ResNet18, with model interpretability via shap package
Done with barely any knowledge of CNNs, transfer learning or pytorch
Train acc: 0.996
Test acc: 0.875
RoC: 0.958

### Model Architecture
- **Base Model**: ResNet18 (pretrained on ImageNet)
- **Transfer Learning**: Fine-tuned final layers for binary pneumonia classification
- **Framework**: PyTorch

### SHAP Explainability
Implemented multiple explainability methods to interpret predictions:
- **Partition Explainer**: Feature attribution through hierarchical partitioning
- **Deep Explainer**: DeepLIFT-based explanations for neural networks
- **Analysis**: Examined both correct and incorrect predictions across classes



## Project goals (copied from handouts)
<details>
<summary>Click to expand original assignment specifications</summary>

Use Convolutional Neural Network (CNN) architectures to classify medical images, specifically using the PneumoniaMNIST dataset. Document your process and findings in a detailed report.

**Specific Requirements:**

* **Dataset**: Use the PneumoniaMNIST dataset.
* **Preprocessing**: There is no need for additional preprocessing as the dataset is already processed.
* **Code and Resources**: All required code for loading, training, and evaluating the model is available on the MedMNIST GitHub Repository. Refer to the following resources:
  * [Getting Started Notebook](https://colab.research.google.com/github/MedMNIST/MedMNIST/blob/main/examples/getting_started.ipynb) for a toy example.
  * [Experiments Repository](https://github.com/MedMNIST/experiments) for full-fledged training of ResNet18 and ResNet50. Use ResNet18 for this project.

1. **Data Preparation**:
Use the **PneumoniaMNIST** dataset, which requires no additional preprocessing.
2. **Model Training**:
Implement and train a ResNet18 model using the provided resources and examples.
3. **Model Evaluation**
Evaluate the model's performance using the test set.
Generate and analyze a confusion matrix and ROC curve.
4. **Explainability with SHAP**
* Apply SHAP for global and local explanations of the model.
* Analyze at least two test cases with correct and incorrect predictions, from different classes.
* Experiment with different explainers for image classifications, namely Partition Explainer, Deep explainer. You can find examples on how to apply them in the [official shap repo](https://github.com/shap/shap/tree/master/notebooks/image_examples)
5. **Report Writing**
* Document each step, from data preparation to explainability.
* Include figures for model evaluation and SHAP analysis, and discuss their significance.
* Address any challenges and insights.
Deliverables:
# Code implementation in Google Colab.
* Trained ResNet18 model.
* Evaluation and explanation plots.
* Comprehensive final report.
</details>

## Challenges (wall of text incoming)
-Roughly 2 weeks study time, technically ~40 hours but significantly more time had to be dedicated to this.  
  -Along with preparing a report and presentation (see files in same repo)  
-Only had introductory lecture to CNNs  
-Only one short lecture on pytorch in another course ~2hours experience with pytorch  
-No knowledge of popular CNN architectures such as resnet or what they actually do other than "finding rough features early and putting them together in later layers"  
-No prior knowledge of what either transfer learning or freezing layers entails   
-“getting_started” helper file was more or less uncommented and ran a too big resnet model, making colab time out and therefore more or less useless  
-No comments in "getting_started" helper file indicates teachers thought we knew torch syntax  
-Shap documentation pytorch examples broken  
-No lectures on what actually happens with each image shap method under the hood 
  -Documentation on above methods is quite arcane
-Found several .torch-shap bugs that were of masters student/senior programmer level to solve  
-Me being stubborn actually solving some of those issues by diving into shap issues forums and feeding the info to a llm to vibecode a solution  
    -I figured a bit of "cheating" was ok since this problem was way above my paygrade  
-Me being stubborn wanting to run this on VSC locally to actually use my own GPU despite having to tweak google colab code to work locally
-Me not accepting "monkey see, monkey do" code. I followed a "code resnet(50) from scratch and commented almost every single line of code to understand somewhat what happens in a resnet.

## Post course extra work 
Me still not accepting "monkey see, monkey do" code after the project was done. I jumped a 25hr coding with pytorch course on my own after the fact.  
Now I actually understand what happens both math- and syntax levels reasonably well!  


## References

- MedMNIST Dataset: [Paper](https://medmnist.com/) | [GitHub](https://github.com/MedMNIST/MedMNIST)
- SHAP Documentation: [GitHub](https://github.com/shap/shap)
- ResNet Architecture: [Deep Residual Learning for Image Recognition](https://arxiv.org/abs/1512.03385)




