# DS_Demo

When we take images of stars over a large range of wavelengths or colors, we need to know what part of the image corresponds to what color, for example the pixels on the left side of the image correspond to blue and pixels on the right side corresponds to red. We need to know this to an accuracy of 1 in 10^-10 meters in order to accurately measure color dependent properties of the star. We can do this by taking an image of a reference object that has features with known colors. In this demo, create a machine learning model to relate pixel to color using the reference object. Then we can apply this model to the image of the star which is ultimately what we want to study.
![image](https://user-images.githubusercontent.com/80592123/167475029-6579570c-41fa-47f9-a97d-0091851561ae.png)


In this code, I automated the measuring the pixel positions of the known features in the reference object and plotted them against their corresponding expected colors. This revealed a seemingly linear relationship between measured and expected values, so I performed a linear regression with scikit-learn. However, when I examined the residuals, I noticed that there was some structure indicating that a higher order polynomial was required to best fit the data. When I performed the polynomial regression and examined the residuals, I then found that there were some outliers that were over 2 standard deviations away from the mean. Upon examination, I determined these outliers were due to misidentifications, meaning that the measured value was not matched with the correct expected value. (This can happen if two features are very close to each other.) Therefore I removed the outliers and recalculated the model.  

![image](https://user-images.githubusercontent.com/80592123/167475170-0ee315b5-0e23-4e6b-9b58-a53b81e8241b.png)

![image](https://user-images.githubusercontent.com/80592123/167475185-c5aa0b9e-c7b5-4434-8fce-e6fe00ceb090.png)



I was able to achieve a root mean squared error of 0.1, which corresponds to 10^-11 meters, and surpasses the required accuracy. This allowed me to precisely measure color dependent properties of the star and compare them to measurements taken at different times.

![image](https://user-images.githubusercontent.com/80592123/167475219-d78e6503-6322-4230-8c1f-ac5a5cbdcb39.png)
