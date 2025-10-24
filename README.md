# Restaurant-Tips-Analysis

<img width="1000" height="563" alt="image" src="https://github.com/user-attachments/assets/82a46f04-e2a2-4733-a16c-93aa8da47d52" />

This project aims to use the restaurant tips dataset to practice creating composition plots and visualizations. We will examine the relationship between different variables and the tips given.

The dataset consists of information from 244 restaurant bills, collected in the US in 1987.

It includes details about the tips given to restaurant staff, such as the total bill, tip amount, gender of the person paying, smoking status, day of the week, time of day, and party size.
## The First Steps
### 📥 Data import
First, let's import the needed libraries: Pandas & Matplotlib.

```
import pandas as pd
import matplotlib.pyplot as plt
```

Then load data from the following link: https://raw.githubusercontent.com/RusAbk/sca_datasets/main/tips.csv

```
df =  pd.read_csv(' https://raw.githubusercontent.com/RusAbk/sca_datasets/main/tips.csv')
```
### 🔍 Data exploration
Let's take a look at the first 5 rows to be sure, that data is loaded properly:
```
df.head(5)
```
<img width="428" height="189" alt="image" src="https://github.com/user-attachments/assets/456fd1e7-d1f1-42ea-b746-eceb1b6d43ca" />
#### Column types checking
```
df.info()
```

We have string columns considered as objects.
<img width="346" height="260" alt="image" src="https://github.com/user-attachments/assets/a4ecdc34-588d-4b47-b6e7-c0c24d3937ae" />

Let's fix their types and make them string:
```
df = df.convert_dtypes()
```
Check again (output columns and their types):
```
df.info()
```
<img width="351" height="263" alt="image" src="https://github.com/user-attachments/assets/514e0294-2c3b-4516-a326-ce859bc21954" />

Nice! We finished this. Look like we are ready to explore some statistics on the given data.

#### Basic descriptive statistics
Show a descriptive statistics of the numeric columns:
```
df.describe()
```
<img width="392" height="288" alt="image" src="https://github.com/user-attachments/assets/1180eab3-baed-4c83-b339-9d2aa9cbba9d" />


Great! Now we know a little more about our data.

➡️ Let's move forward!

## 💸 Tip value influencers
### 🚬 Do people who smoke give more tips?
Let's figure out the difference between smokers and non-smokers in terms of their behavior and purchasing habits in public catering establishments.
#### Separate smokers and non-smokers
Create a new dataframe smokers_df containing only info about smokers.
```
# PUT YOUR CODE HERE
smokers_df = df[df['smoker'] =='Yes']
```
Check whether everything is okay. Output a test sample (5 random rows):
```
smokers_df.head()
```
<img width="423" height="195" alt="image" src="https://github.com/user-attachments/assets/b687b5ca-ff75-4c6b-ba41-9ccfb336793b" />

Also create another one dataframe non_smokers_df containing only non-smokers.
```
# PUT YOUR CODE HERE
non_smokers_df = df[df['smoker']=='No']
```
Check whether everything is okay. Output a test sample (5 random rows):
```
non_smokers_df.head()
```
<img width="446" height="188" alt="image" src="https://github.com/user-attachments/assets/0af1821a-e3fe-4073-84bd-9aeb3ceee848" />

#### Compare their measures of central tendency
As we know, measures of central tendency is one of the basic tools, that allow us to compare different datasets as it shows the most typical values.
##### 🌏 Whole dataset
Let's try to calculate measures of central tendency for the whole dataset first.

Calculate them for the 'tip' column through the whole dataset and save them into the following variables:

min => common_tip_min
max => common_tip_max
mean => common_tip_mean
median => common_tip_median
```
# YOUR CODE
common_tip_min = df['tip'].min()
common_tip_max = df['tip'].max()
common_tip_mean = df['tip'].mean()
common_tip_median = df['tip'].median() # df['tip'].quantile(0.5)
```
Let's show the resulting values for whole dataset (we already have the code written for you 😉)
```
# Make a list of values
common_values = [common_tip_min, common_tip_max, common_tip_mean, common_tip_median]
# Round all the values to 4 decimal places
common_values = map(lambda x: round(x, 4), common_values)

# Make a dataframe from the list
common_mct = pd.DataFrame(common_values, index=['min', 'max', 'mean', 'median'])
# Output the dataframe
common_mct
```
<img width="123" height="157" alt="image" src="https://github.com/user-attachments/assets/3444250d-e3af-4c2c-9e0e-53f3e95caa94" />

##### 🚬 Smokers
Do the same taking into account only smokers. Use the following variables:

min => smokers_tip_min
max => smokers_tip_max
mean => smokers_tip_mean
median => smokers_tip_median
```
# YOUR CODE
smokers_tip_min = smokers_df['tip'].min()
smokers_tip_max = smokers_df['tip'].max()
smokers_tip_mean = smokers_df['tip'].mean()
smokers_tip_median = smokers_df['tip'].median()
```
Let's output the results in the same format.

Make the same dataframe containing the measures of central tendency for smokers as we did for whole dataset. Then output it.
```
# YOUR CODE
# Make a list of values
smokers_tip_value = [smokers_tip_min, smokers_tip_max, smokers_tip_mean, smokers_tip_median]
# Round all the values to 4 decimal places
smokers_tip_value = map(lambda x: round(x, 4), smokers_tip_value)

# Make a dataframe from the list
smokers_tip_value = pd.DataFrame(smokers_tip_value, index=['min', 'max', 'mean', 'median'])
# Output the dataframe
smokers_tip_value
```
<img width="142" height="152" alt="image" src="https://github.com/user-attachments/assets/9f7041c1-62d6-4acc-81c2-9e7ea452c6fd" />


##### 🚭 Non-smokers
Now repeat it for non-smokers. Use the following variables:

min => non_smokers_tip_min
max => non_smokers_tip_max
mean => non_smokers_tip_mean
median => non_smokers_tip_median
```
# YOUR CODE
non_smokers_tip_min = non_smokers_df['tip'].min()
non_smokers_tip_max = non_smokers_df['tip'].max()
non_smokers_tip_mean = non_smokers_df['tip'].mean()
non_smokers_tip_median = non_smokers_df['tip'].median()
```
Make the same dataframe containing the measures of central tendency for non-smokers as we did for whole dataset. Then output it.

```
# YOUR CODE
# Make a list of values
non_smokers_tip_value = [non_smokers_tip_min, non_smokers_tip_max, non_smokers_tip_mean, non_smokers_tip_median]
# Round all the values to 4 decimal places
non_smokers_tip_value = map(lambda x: round(x, 4), non_smokers_tip_value)

# Make a dataframe from the list
non_smokers_tip_value = pd.DataFrame(non_smokers_tip_value, index=['min', 'max', 'mean', 'median'])
# Output the dataframe
non_smokers_tip_value
```
<img width="134" height="161" alt="image" src="https://github.com/user-attachments/assets/714367e0-9a2e-4e06-a437-a458c80321db" />


##### 📝 Conclusion
Let's show the retrieved results together (we already have the code written for you 😉):
```
all_vals_dict = {
    'Common': {'min': common_tip_min, 'max': common_tip_max, 'mean': common_tip_mean, 'median': common_tip_median},
    'Smokers': {'min': smokers_tip_min, 'max': smokers_tip_max, 'mean': smokers_tip_mean, 'median': smokers_tip_median},
    'Non-smokers': {'min': non_smokers_tip_min, 'max': non_smokers_tip_max, 'mean': non_smokers_tip_mean, 'median': non_smokers_tip_median}
}

# Make a dataframe
all_mct = pd.DataFrame(all_vals_dict)
# Output the dataframe
all_mct
```
<img width="321" height="170" alt="image" src="https://github.com/user-attachments/assets/8418635b-1a63-4b5d-a482-136466dc06a6" />

**Insights based on measures of central tendency comparison:**
Overall, both smokers and non-smokers tend to give similar amounts of tips,  as reflected by their close mean and median values. However, smokers show     slightly higher averages (mean = 3.01, median = 3.00) compared to non-smokers (mean = 2.99, median = 2.74). This suggests that, on average, smokers tend to leave marginally higher tips than non-smokers, though the difference is relatively small.

#### Look at histograms
As we already discussed on the last lecture, there are a lot of cases, when comparing the measures of central tendency is not enough.

This is because they only show the most typical values. However, the way data is distributed is equally important. There are situations where measures of central tendency are exactly the same, but due to different distributions, it is incorrect to say that the datasets are similar.

##### 🌏 Whole dataset tips histogram
Plot the histogram for the whole dataset tips distribution.

Use the following settings:

Size: 15 x 5
Color: #74b9ff
X-axis label: Tip value
Y-axis label: Frequency
Chart title: Whole dataset tip values
Gridlines: show
```
# YOUR CODE
plt.figure(figsize=(15, 5))
plt.hist(df["tip"], color = '#74b9ff')
plt.title("Whole dataset tip values")
plt.ylabel("Frequency")
plt.xlabel("Tip value")
plt.grid(True)
```
<img width="1282" height="475" alt="image" src="https://github.com/user-attachments/assets/21780d07-892c-4a16-beaa-832dd00a55bf" />

##### 🚬 Smokers' tips histogram
Plot the histogram for smokers tips distribution.

Use the following settings:

Size: 15 x 5
Color: #ff7675
X-axis label: Tip value
Y-axis label: Frequency
Chart title: Smokers tip values
Gridlines: show
```
# YOUR CODE
plt.figure(figsize=(15, 5))
plt.hist(smokers_df["tip"], color = '#ff7675')
plt.title("Smokers tip values")
plt.ylabel("Frequency")
plt.xlabel("Tip value")
plt.grid(True)
```
<img width="1226" height="448" alt="image" src="https://github.com/user-attachments/assets/24119e0b-ef4e-4e92-a812-0f117f15dc52" />

##### 🚭 Non-smokers tips histogram
Plot the histogram for non-smokers tips distribution.

Use the following settings:

Size: 15 x 5
Color: #55efc4
X-axis label: Tip value
Y-axis label: Frequency
Chart title: Non-smokers tip values
Gridlines: show
```
# YOUR CODE
plt.figure(figsize=(15, 5))
plt.hist(non_smokers_df["tip"], color = '#ff7675')
plt.title("Non Smokers tip values")
plt.ylabel("Frequency")
plt.xlabel("Tip value")
plt.grid(True)
```
<img width="1237" height="459" alt="image" src="https://github.com/user-attachments/assets/61af6786-06be-4860-ab58-fadf49457d1f" />

##### ⭐ Extra-task with a higher difficulty
Plot all 3 charts in a row in the same cell:
```
# YOUR CODE
figure, axis = plt.subplots(1, 3, figsize=(20, 5))

axis[0].hist(df.tip, bins=5, color="#74b9ff")
axis[0].set_title('Whole dataset tip values')

axis[1].hist(smokers_df.tip, bins=5, color="#ff7675")
axis[1].set_title('Smokers tip values')

axis[2].hist(non_smokers_df.tip, bins=5, color="#55efc4")
axis[2].set_title('Non-smokers tip values')

plt.tight_layout()
plt.show
```
<img width="1608" height="536" alt="image" src="https://github.com/user-attachments/assets/d5a17d32-9039-496e-a68e-413e6de21c86" />

##### 📝 Conclusion
**Insights based on distribution comparison:**
The tip amount distribution for both smokers and non-smokers is right-skewed, showing that small tips are more common. While the difference is subtle, smokers appear to give slightly higher tips more frequently than non-smokers, aligning with the mean and median comparison results.
