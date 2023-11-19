# GEE_Cloud-computing
Ggoogle earth engine combined with cloud computing

Rearch Background:
Since the successful launch of the first US weather satellite in 1960, Remote Sensing(RS) technology has developed rapidly, and the Earth orbit is full of a variety of Earth observation satellites on a global scale. 
Mankind has accumulated historical remote sensing data for nearly half a century. Meanwhile, with the rapid development of human civilization, the global ecosystem has been greatly damaged due to human activities such as deforestation, industrial emissions, and the overutilization of water resources.
These have resulted in various environmental variations including temperature, vegetation, snow cover, and atmosphere. All of them have been recorded as data products by the National Aeronautics and Space Administration(NASA) through RS technology and are available on some cloud platforms such as Google Earth Engine(GEE). 
Therefore, the users can use these data products to detect any change related to the ecosystem all around the world. Considering the ever-increasing concern about the variation tendency of vegetation cover all over the world, the objective of this research is to avail the RS data product “ MOD13A2.061” provided by GEE to investigate the dominating variation inclination of vegetation cover in the primary region in Oceania. 
I chose the Normalized Difference Vegetation Index(NDVI) in the data product as my research object. It contains information on vegetation greenness, coverage, and health conditions. I also use some algorithms to generate results such as line charts so it can give an intuitionistic impression of the main change of NDVI in the region I choose.

The following steps cover the components of my notebook and how to use it:
In step one, users should initialize the environment first and import every module or lib may be used in subsequent steps:
I imported the ee module for interacting with Google Earth Engine and gained access and initialization. 
Next, I imported the Google Drive module of Google Colaboratory(Colab) to connect to the Google Cloud drive so that all my experimental data could be stored in Google Cloud. 
Lastly, in order to gain the data of NDVI in different regions appropriately, I imported the Geemap library for interactive map visualization and geospatial data analysis on Colab, which enables users to get point data by clicking on the map with a mouse. 

In step two, users should make a creative map in order get data from it:
I first created an interactive Map object and imported the data product MOD13A2.061, setting observation time from 2015 to 2022 and selecting the NDVI indices.  
Next, I added layers to the map to display the MODIS NDVI time series and its visualization results. 
Lastly, I set plotting options for adding marker clusters and markers to the map so that I could gain my experimental data easily.

In step three, users can learn how to output experimental data and how to make the curve of the line chart smoother:
Because Geemap can record all the points clicked by the user, I set the path in order to output the CSV files and extract numerical data from maps to CSV files. 
However owing to the visualized NDVI variation line chart having big fluctuation during certain time series, the major tendency of NDVI change is less than intuitionistic which can have a negative influence on research results. 
I found a mathematical method called the Whittaker Smoother Method on the blog (http://t.csdn.cn/ZMCWE). It can smooth the set of time series images and return a new set of time series images. In this function, the data is treated as constituent data and preprocessed. 
Then compute the difference matrix of a given order and perform matrix operations, generate a smoothing coefficient image and solve the linear system between the smoothing coefficient image and the original array image, and finally reassemble the smoothing image set. 
After using this, I can easily observe the main change of NDVI in different areas, which is greatly beneficial to my research.

In the last step, to present a better visual effect, I cited a method online (http://t.csdn.cn/YD1i7) to draw line charts that have 2 lines. The one represents the raw NDVI. Another one is on behalf of the smoothed NDVI. 
The original method I found online cannot detect a value that is below zero. When NDVI is less than 0, it usually indicates that the selected point may be non-vegetation areas such as water bodies and urban buildings. 
This is because of the factors of human activities such as urban development. Areas with NDVI less than 0 are generally not suitable for applications requiring healthy vegetation such as agriculture, forestry, or ecosystem restoration. 
Therefore, the data points are less than 0 which is nonsignificant for my research. I improved this method so that it can detect abnormal data. Next, I replaced the smoothed NDVI line with red dots. They indicate the location of the outlier so I can know I cannot use this point data to generate my final result.

