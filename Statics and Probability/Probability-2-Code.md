# Poisson DIstribution

q_size=np.random.poisson(3.6,1000)
# Here generating 1000 numbers belongs to poisson distribution with mean =3.6

# SO, here we are using simulation

sns.countplot(x=q_size)
plt.show()

# Now we will use the theoritical formula of poisson

from scipy.stats import poisson
#poisson.cdf(k,mu) #cumulative distribution function- for less than or equal to
#poisson.pmf(k,mu) #probability mass function- for exact value
# poisson.sf(k,mu) # Survival function- (1-cdf)
 

#poisson.pmf(k,mu) where k = how many people we want to check in the queue and mu is the mean 
poisson.pmf(7,3.6) # probability of getting 7 people in the queue when the mean is 3.6

poisson.cdf(7,3.6) # probability of getting <=7 people in the queue

poisson.sf(7,3.6) # probability of getting more than 7 people in the queue 
# cdf and sf sum up to 1

poisson.mean(3.6) # mean of poisson distribution, kind of silly doing that but as we want to check 
#var and mean are same or not, let's check it




poisson.var(3.6)

# Coding Question for you
* A company receives on average 4.6 calls per hour. What is the probability of getting exactly 8 calls in an hour? Assume that the call volume follows the Poisson Distribution.

* A company receives on average 4.6 calls per hour. What is the probability of getting more than 6 calls in an hour? Consider the call volume follows the Poisson Distribution.

p8=poisson.pmf(8,4.6)
p_gt_6=poisson.sf(6,4.6)

# Normal Distribution

import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

np.random.normal(100,2) #mean=100 and sd=2 sample =1

np.random.normal(100,2,10) #drawing 10 samples from a normal dist with mean 100 and std=2

np.round(np.random.normal(100,2,10),2)

a=np.random.normal(100,2,1000)
sns.histplot(x=a)
plt.show()

a=np.random.normal(100,2,1000000)
sns.histplot(x=a, kde=True) #kernel density estimation
plt.show()

sum(a>98) #84% data is on the right of -1sigma 

# Trying to find out the area b/w -1 sigma to 1sigma

sum((a>98) & (a<102))

# Trying to find out the area b/w -2 sigma to 2sigma

sum((a>96) & (a<104))

# Trying to find out the area b/w -3 sigma to 3 sigma

sum((a>94) & (a<106))

# Now will use theoritical formula

## Questions: Perfume bottles are filled with an average volume of 150cc and a standard deviation of 2cc. 
What percent of bottles will have a volume of more than 153 CC?


import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from scipy.stats import norm

norm.sf(153,150,2) # x=153, u=150, sd=2 prob og getting >153 cc

# Perfume bottles are filled with an average volume of 150cc and a standard deviation of 2cc. 
What percent of models will have the volume between 148 and 152 CC?

norm.sf(148,150,2) - norm.sf(152,150,2)# Area to the right



#norm.cdf(x,n,p) #cumulative distribution function- for less than or equal to 2
#norm.pdf(x,n,p) #probability density function- for exact values
#norm.sf(0,20,0.12) # Survival function- more than 2 
#binom.mean(20,0.12)
# binom.var(20,0.12)
#binom.std(20,0.12)

x_ax=np.linspace(144,156,13) # creating 13 items b/w 144 to 156
x_ax

from scipy.stats import norm
norm.pdf(153,150,2)  #This gives you the z table value (area on the right). 
#Look at the Z table in the slide given, you'll get the same value


norm.sf(153,150,2)

y_ax=norm.pdf(x_ax,150,2)  #This maps the point of a random variable with its probable density by taking a delta area.
y_ax

y_ax=norm.sf(x_ax,150,2)  #This gives you the z table value (area on the right)
y_ax

sns.lineplot(x=x_ax,y=y_ax)
plt.show()

x_ax=np.linspace(144,156,1300) # creating 1300 items b/w 144 to 156
y_ax=norm.pdf(x_ax,150,2)
sns.lineplot(x=x_ax,y=y_ax)
plt.axvline(152,color='red')
plt.show()

