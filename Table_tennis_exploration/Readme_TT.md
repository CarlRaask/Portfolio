# An exploratory analysis of results from physical tests of youth female table tennis players.  
#### The theme is "field expedience"


### Background
I come from a sports science background and have been doing some work with athletes of differing levels.  
Somehow I ended up doing a fair bit of either targeted "weak spot" with individuals work or group consulting for physical training  
for table tennis players.  
The data here is from one of the group projects.  
We did physical tests with female players of the youth national team of that country  
Their ranking points were extracted from the national ranking database the same month as the tests were done.  

Observant readers will note the small sample size. This is simply due to the fact that there doesn't exist enough players of  
that level to get a statistically rigorous sample. We do what we can with what we have.  

### The goals of the project were: 
Give the players a push to take physical training seriously by providing them with performance numbers  
See if we could build some kind of predictive model or at least tease out if our test battery was relevant.  
The models also have to prioritize interpretability over precision.  
We wanted actionable recommendations both on an aggregate and individual level.  
The ultimate outcome would be being able to create sentences like "All of you players would benefit from building leg strength,  
but you three need more arm work and you four need more rotational core work"  

### Data and variables
*isometrics using strap and crane scale*  
triceps	- 5s max contraction with arm in "I just hit a heavy forehand position", writing down highest observed value  
biceps	- 5s max contraction with arm in "I just hit a heavy forehand position", writing down highest observed value  
rot_r	- 5s max contraction with arms holding strap in front of belly button. Rotating TOWARDS right hand side, writing down highest  observed value  
rot_l	- 5s max contraction with arms holding strap in front of belly button. Rotating TOWARDS left hand side, writing down highest  observed value  

dl_5	- 5 rep max deadlift, straps allowed. Stopping at technical failure rather than muscular failure for safety.  
s_j_r	- Static start sideways jump. Jumping with right foot forward. Tape measure for distance, measuring left foot landing position. No  leg crossing allowed.  
s_j_l	- Static start sideways jump. Jumping with left foot forward. Tape measure for distance, measuring right foot landing position. No  leg crossing allowed.  
sq_hold	- Sit in a deep squat with femur at a 90 degree angle towards the floor. Cell phone with level app strapped on thigh to ensure position.     

### **samples**   
As noted in the actual file. There is only 25 samples.  

25 datapoints in sports science = "How did you get that many samples! Amazing!!"  
25 datapoints in statistics = "We want at least 30 samples to approximate normal distribution"  
25 datapoints in data science = "That's not even a sample of a sample"  
This is indeed a convenience sample.  
But its also a sample that covers a large part of the population of national youth players in country X.  
It is hard to do inference when your actual population is smaller than the sample size needed for statistical certainty.  

Take the results for what they are. A pilot/exploration.  


### Data science lessons  
We have talked about Conway's  venn diagram during class.  
It was very rewarding and fun to be able to add the "Substantive expertise" circle to the process and be in close communication with stakeholders.  
Much better than a toy dataset with flower petals or american election results!

### Technical Setup

**Python version:** 3.10.12

**Required packages:**
```bash
pip install pandas numpy scikit-learn scipy matplotlib seaborn
```

**Libraries used:**
- `pandas` - Data manipulation
- `numpy` - Numerical operations
- `scikit-learn` - Machine learning models (LinearRegression, DecisionTreeRegressor, StandardScaler)
- `scipy` - Statistical testing
- `matplotlib` - Plotting
- `seaborn` - Statistical visualizations


### What was found
We could get some nice modelling! Both with linear regression and decision trees.  
Feature engineering trial and error based on general knowledge of the training space made predictions better as well.  
Arguably regression models were too good. R² = 0.4125 for the best one.   

Best model in the context of keeping as few variables as possible contained the following: 
All variables square rooted to make data more linear than log shaped:  
triceps  
rot_l  
dl_5  
sq_hold	 
rot_asym  

Where rot_asym consisted of taking the absolute difference between rot_l and rot_r  

### Bootstrapping on regression
I also did some bootstrapping to try and add some statistical rigour to the results.  
In short. Model as a whole seemed to produce fairly consistent R² results across bootstraps.  
But individual slopes were all over the place and should not be trusted.  

And if you put your sports scientist or table tennis hat on you realize that defensive players might benefit  
more from leg endurance and offensive players probably benefit more from rotational and tricep strength.  


## Decision Tree
I did a max_depth=2 decision tree as well.  
First split on tricep strength was in line with regression model and showed both a statistically significant  
and meaningful difference in ranking. We might be looking at a threshold level of strength needed for fast forehands here.  
The second splitting the False branch with rotational asymmetry was also both statistically significant  
and showed a meaningful difference in  ranking.  
Possibly a threshold thing here too.   

Second split in True branch on deadlift strength had too few samples to show any significance and the splitting showed weaker players performing better.  
I think that effect was due to chance rather than something real.  
I'm fully onboard with the idea that Table Tennis players should not become specialized powerlifters, but I think there is room for strength improvement.   
After a couple of rounds of testing we might find some threshold values. I don't know.  


## **For sports scientists and trainers** 
Before starting the project (spring 2023) I did a brief literature search on variations of "physical testing table tennis players" with the goal of finding field expedient tests that also would appear relevant to the players.  
And, as many times before, I more or less came out empty handed.  
I found one study comparing athletes of different sports and table tennis players stood out by having a greater side jump ability.  
Which makes more biomechanical sense than the classics such as counter movement jump or standing long jump.  
Things might have changed by now.  

All players were beginners as far as physical training is concerned.  
Meaning we tried to bring the skill level down as low as possible, while still maintaining biomechanical and physiologic relevancy.

We also had some budget constraints. It is only adults that get large funds for these things.  
In practice this meant we came up with tests from scratch.  

Tests consisted of:
Isometric rotation using a strap and a crane scale 5s looking for the max value  
Isometric tricep and bicep testing at "when you hit your forehand" point
Sideway jump using tape measure for length  
The three above tests were done both right and left side  
Squat hold at femur parallel depth. Strapping a phone to the thigh with a level app on to make sure there was no cheating.    
Deadlift 5rm using straps overseen by me, stopping early of technique started to look bad.

Observant sport nerds will note the lack of cardiovascular tests.   
We considered classics such as coopers or jojo style tests but really didn't like the fact that those are sagittal movement tests.  
First run we tried a multi ball style heart rate test. And it was very fun watching the athletes get tortured but the results were terribly inconsistent and more often than not ended up being a test of "can you play with crappy technique when tired". One player even switched hands because of tiredness in the dominant arm!  
We will have to sit down at the drawing board for something better. I'm open to suggestions!