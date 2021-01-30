#!/usr/bin/env python
# coding: utf-8

# # Covi-19  data analysis with small data set
# 
# ## Data used is till 29th April-2020

# In[1]:


import pandas as pd
import numpy as np 
import seaborn as sns
import matplotlib.pyplot as plt


# In[51]:


data=pd.read_csv(r"C:\Users\singjai\Downloads\Data science\covid_19_data.csv")


# In[6]:


data.head()


# In[7]:


data.count()


# In[8]:


data.isnull().sum()


# In[17]:


plt.show()
sns.heatmap(data.isnull(),xticklabels=True)


# ## 1.Show the number of confirmed and recovered cases in each region

# In[19]:


data.head(2)


# In[32]:


data.groupby('Region').sum().head(2)


# In[34]:


data.groupby('Region')['Confirmed'].sum().sort_values(ascending=False)


# In[38]:


data.groupby('Region')['Confirmed','Recovered'].sum()


# # 2.Remove all the records where confirmed cases is less than 10.

# In[52]:


data.Confirmed < 10


# In[55]:


data=data[~(data.Confirmed<10)] #to remove the records satisying particular condition


# In[56]:


data


# # 3.In which region , maximum number of confirmed cases were recorded?

# In[57]:


data.head(2)


# In[61]:


data.groupby('Region').Confirmed.sum().sort_values(ascending=False).head(10)


# # 4. In which region , minimum number of deaths cases were recorded?

# In[62]:


data.head(2)


# In[65]:


data.groupby('Region').Deaths.sum().sort_values(ascending=True)


# # 5. how many confirmed , death and recovered cases were reported from india till 29th Apr 2020?

# In[66]:


data.head(2)


# In[75]:


#using filtering
data[data.Region=='India']


# In[77]:


data[data.Region=='US'].head


# # 6.Sort the entire data w.r.t No.of ocnfirmed cases in ascending order

# In[78]:


data.sort_values(by=['Confirmed'], ascending=True)


# # 7.sort the entire data w.r.t to recovered cases in descending order

# In[80]:


data.sort_values(by=['Recovered'],ascending=True)

