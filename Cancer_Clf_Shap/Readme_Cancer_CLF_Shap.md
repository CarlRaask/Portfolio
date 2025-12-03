# Cancer classifier. EDA. Scaler Exploration. Model selection and validation. Shap exploration and validation.

## Smart Healthcare with Applications year 2 term 1 of Applied AI for machine learning university program

### Overveiw
As a part of Smart Healthcare with Applications course we were tasked with working with **Glioma Grading Clinical and Mutation Features dataset**
https://archive.ics.uci.edu/dataset/759/glioma+grading+clinical+and+mutation+features+dataset
Part of the assignment was making sure my thought process was well documented.  
For example:  
I thought Sensitivity/Recall would be a better performance metric than pure accuracy as I figure that if your doctor are at a gene testing stage, then the doctor probably has a reason for it and we want to detect all possible cases.
I also made some decent predictions on feature importance based on EDA output such as age at diagnosis being predictive and idh1 being protective.
I also assumed Gaussian Naive Bayes would fail on predominantly binary/categorical features due to its continuous distribution assumptions. It turned out to be the best-performing model for Sensitivity/Recall!  
But not to a statistically significant degree than other top performing models.  
This taught me not to dismiss models based on theoretical mismatches - empirical testing matters.  
Because of the lack of statistical difference between top models I selected a simple decision tree with max_depth=5 as the best model. An extremely important factor in healthcare applications.

For the second assignment we were tasked with learning Shapley values. We had a tutorial lecture in school.  
But upon investigation I realized it was out of date and syntax was incorrect.  
I also felt the explanation for Shapley values during class was lacking and a bit hand wavey
    ""A partnership among group of players cooperates and obtains a certain overall gain from the
    cooperation... ""
So i made sure to learn the actual math on a base case level for both basic shap regression and variations on the theme such as classification and tree based models.
I also worked though several of the earlier created models and got a very good insight in "model assumptions" a phrase often used in classes but with limited meaning until I saw how different shap output on the same observation using different models was.  
This stuff should be mandatory for Datascience! Not just part of a self selected course.  
During shap learning a thought hit me. "This is kinda lika regression slopes. I know I can do bootstrap on slopes for CI. I wonder if I can do the same on this".  
And I actually found a paper seeming to confirm my idea! So I tried out that idea with decent success.  
Finally I decided to learn shap clustering and it's implications for future model building and optimization.


### Challenges & Solutions
I gave myself several personal challenges for the project:
    -Making sure i got sklearns grid search syntax down
    -Learned several new classification models. Including math, not just "lets see what happens if I run this model"
We had recently done a stats course. But it was 99% pen and paper and no code. So I added the following in order to bridge that gap. 
    -Added statistical rigour to model selection. 
    -Learning chi² for classifiers
Part 2 Shap:        
    -Understanding shap math and process for different models
    -Adding a tiny bit of statistical rigour to shap too by bootstrapping confidence intervals
    -Learning more about the library than required such as clustering and more plots than asked by the task
Most of these have detailed markdown notes at the latter half of the notebook. 

Another, less voluntary, challenge was that the code for Shap class was outdated and I had to spend a lot of time working out the syntax.   
But given the fact that even the official documentation guides were slighly off I can partially forgive my teachers for that extra work.


### Environment
This project was developed with:

Python 3.10.12

Key packages:
scikit-learn: 1.6.1
pandas: 2.3.2
numpy: 2.2.6
shap: 0.49.1 *most likely an important dependency as the library was not syncronized with current api guides*
matplotlib: 3.10.6
seaborn: 0.13.2
scipy: 1.15.3
ucimlrepo: 0.0.7