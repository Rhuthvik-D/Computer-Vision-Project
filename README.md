# Introduction
This project consists of 3 concepts, namely:
  - [Histogram Equalization](https://github.com/Rhuthvik-D/Computer-Vision-Project/new/main?filename=README.md#histogram-equalization)
  - [Otsu Image Thresholding](https://github.com/Rhuthvik-D/Computer-Vision-Project/new/main?filename=README.md#otsu-image-thresholding)
  - [Histogram Matching](https://github.com/Rhuthvik-D/Computer-Vision-Project/new/main?filename=README.md#histogram-matching)

## Histogram Equalization:
Using a technique called histogram equalization, one can improve an image’s contrast by 
dispersing the intensity values throughout the whole range. The fundamental concept behind 
histogram equalization is to adjust the pixel intensities so that the image’s histogram’s 
cumulative distribution function (also known as the CDF) is represented as a linear function. 
Through this technique, the intensity values are effectively spread out, resulting in a more 
uniformly distributed histogram for the image. 
  - Process:
      - **Compute Histogram**: As an image is given as an input, create a histogram of the input 
that gives the frequency of pixels at each pixel intensity.
      - **Compute Probability Density Function (PDF)**: Once histogram is computed, the frequencies are normalized, i.e., each 
frequency at a pixel intensity is divided by total count of pixels.
      - **Compute Cumulative Distribution Function (CDF)**:  With the PDF values, calculate the cumulative sum of counts of pixels. 
The range of this CDF is from 0 to total number of pixels. Then, calculate the normalized 
CDF values.
      - **Histogram Equalization Enhancement**:  Each pixel at a particular intensity will be 
denormalized again, i.e., the CDF of that intensity is multiplied by 255 and placed in the 
resulting equalized image.
> [!NOTE]
> The whole process is completely developed without using any libraries. For instance, even the histogram is being computed manually and not via using predefined methods.

## Otsu Image Thresholding:
A thresholding method that is used to divide a particular image into foreground and background. The concept includes a brute force approach to select a threshold amongst the pixel intensity values(0 - 255) which affects the inter-class variance. Since there are 256 pixel intensity 
values, this method checks for each intensity value and its corresponding inter-class variance. Upon finding the maximum inter-class variance, that pixel intensity is used as a threshold and transforms the given image into a bit image (0 and 255 as the pixel intensities). The resultant image gives
a bit image of the input image, that is, a black and white image. Transformation goes by the following set of rules:
  - If any pixel intensity is lesser than the selected threshold, then that pixel intensity is changed to "0".
  - If any pixel intensity is greater than the selected threshold, then that pixel intensity is changed to "255".

## Histogram Matching:
 This process is used to take a reference of a target image and change the input 
image’s contrast. The update of the input image’s contrast solely depends on the contrast level of the 
target image’s contrast levels. With the help of this process, we can either increase the contrast or 
decrease as well. The methodology is very practical. It creates a new histogram that tends to be similar 
to the target image’s histogram and generates the image from the derived histogram values.  

Delving deeper into the methodology, it calculates the difference between cumulative density function 
of the target image and that of the input image at the intensity level of the chosen pixel. Then chooses 
the minimum of the absolute differences computed earlier. Creating a new image, the resultant value is 
then assigned to the respective pixel of the new image that is to be formed. Mapping of the pixel 
intensity from the input image to the new image that better matches the target image’s histogram. 
Finally, a new image is generated that has the contrast and the histogram similar to the target image. 
