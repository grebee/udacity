# Finding Lane Lines on the Road

### **Finding Lane Lines on the Road**
>The goals / steps of this project are the following:
>
>* Make a pipeline that finds lane lines on the road
>* Reflect on your work in a written report

## **Reflection**

1. **Describe your pipeline. As part of the description, explain how you modified the    draw_lines() function.**

    My pipeline consisted of 5 steps. 
    * I converted the images to grayscale.
    * Then I apply Canny edge detection.
    * Next, I create region of interest by creating a masked edge with four sided polygon.
    * In order to draw a single line on the left and right lanes, I modified the **draw_lines()** function by:
        * Loop through the lines, and file its slope. Slopes with less then 20 degrees will be ignore. If slope is > 0.23 radian, meaning it's the right line, I saved it to right line list. If slope is < -0.23 radian, meaining it's the left line, I saved it to left line list.
        * Then, I calculate average slope for each line.
        * From average slope, I can calculate intercept points (for left and right lines) from this equation:
         _y = **m**x + **b**_ where m is average slope, and b is intercept point. x and y values are point on each line.
        * After that, I identify 4 points (2 for each line) with upper bound with y = 320 and lower bound with y = 540 or **imshape[0]**.
    * Finally I draw these lines to original image.

2. **Identify potential shortcomings with your current pipeline**

    * One potential shortcoming would be what would happen when the lines are not visible, or it's not bright enough
    * Another shortcoming could be driving along the sharp curve.

3. **Suggest possible improvements to your pipeline**

    * A possible improvement would be to improve draw_lines() function to handle curve lane. 
    * Another potential improvement could be to ...