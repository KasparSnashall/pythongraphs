
# coding: utf-8

# In[1]:


import pandas as pd
from pandas import DataFrame
import numpy as np


# In[2]:

matplotlib inline


# In[7]:

#making some random data for our graphs


# In[3]:

data = DataFrame(np.random.randn(20, 4), columns=list('ABCD'))


# In[4]:

print(data)


# In[5]:

#this is great data so we are going to make it more manageable
data = 100*data**2
print(data)


# In[7]:

import mpl_toolkits.axisartist.floating_axes as floating_axes
from matplotlib.projections import PolarAxes
from mpl_toolkits.axisartist.grid_finder import FixedLocator,      MaxNLocator, DictFormatter
import numpy as np
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd
from pandas import DataFrame
import math
import sys
import pylab

#this is an example of a nice from of polar plot with colour bar using a dataframe which can be made from reptty much anydata
#its useful for representing data with direction and change
    
maxi = 500    
section=data.index

N = len(data)

theta = np.linspace(0.0, 2 * np.pi, N, endpoint=False)
width = [2*np.pi/N]
colours = np.random.uniform(0,1,len(data)) 
thetaticks = np.linspace(-360/(2*N), 360 -360/(2*N), num=N+1, endpoint=True)
#labeling
height = data.A.get_values()


titles = []


for i in range(0,len(section)):
    y= section[i]
    titles.append(str(y))
    i+=1


# initialize figure:
fig = plt.figure()

# set up polar axis
tr = PolarAxes.PolarTransform()

 # define angle ticks around the circumference:
for i in range(len(thetaticks)):
    if thetaticks[i]<0:
        thetaticks[i]=360+thetaticks[i]
        angle_ticks = []
    for i in range(N):
      angle_ticks.append((math.radians(thetaticks[i]),titles[i]))


# set up ticks and spacing around the circle
grid_locator1 = FixedLocator([v for v, s in angle_ticks])
tick_formatter1 = DictFormatter(dict(angle_ticks))

    # set up grid spacing along the 'radius'
radiustick=np.linspace(0,maxi-100,5)
radius_ticks=[]
for i in range(len(radiustick)):
    radius_ticks.append((radiustick[i],str(int(radiustick[i]))))

grid_locator2 = FixedLocator([v for v, s in radius_ticks])
tick_formatter2 = DictFormatter(dict(radius_ticks))

# set up axis:
# tr: the polar axis setup
# extremes: theta max, theta min, r max, r min
# the grid for the theta axis
# the grid for the r axis
# the tick formatting for the theta axis
# the tick formatting for the r axis
grid_helper = floating_axes.GridHelperCurveLinear(tr,
                                                      extremes=(2*np.pi, 0, 200, 20),
                                                      grid_locator1=grid_locator1,
                                                      grid_locator2 = grid_locator2,
                                                      tick_formatter2 = tick_formatter2,
                                                      tick_formatter1=tick_formatter1
                                                      )

ax1 = floating_axes.FloatingSubplot(fig, 111, grid_helper=grid_helper)
ax1.axis["bottom"].set_axis_direction("right")
ax1.axis["top"].set_visible(False)
ax1.grid(True,zorder=0.9)
ax1.grid(axis='both',linestyle = "-",color = 'lightgrey')

fig.add_subplot(ax1)

# create a parasite axes whose transData in RA, cz
aux_ax = ax1.get_aux_axes(tr)

aux_ax.patch = ax1.patch # for aux_ax to have a clip path as in ax
ax1.patch.zorder=0.9 # but this has a side effect that the patch is
                         # drawn twice, and possibly over some other
                         # artists. So, we decrease the zorder a bit to
                         # prevent this.

# plot your data:
    
bars = aux_ax.bar(theta,height,width=width,bottom=20)
norm = plt.Normalize(colours.min(), colours.max())




cax = aux_ax.imshow((height,theta), cmap=plt.cm.jet, interpolation='nearest',)
cbar = plt.colorbar(cax, ticks=(data.A.min(),(data.A.max()-data.A.min())/2,data.A.max()),shrink=0.6,pad=0.3,aspect=20)
cbar.ax.set_yticklabels(['Decrease', 'normal', 'Increase'],fontsize=15)# horizontal colorbar

for thisfrac, thispatch in zip(colours, bars):
    color = plt.cm.jet(norm(thisfrac))
    thispatch.set_facecolor(color)
    thispatch.set_edgecolor(color)

plt.show()
  


# In[6]:




# In[ ]:




# In[ ]:



