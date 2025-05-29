# USEME: Script Commands for MIME

## Overview

The GRIME (Graphical Image Manipulations and Editing) Application supports two main modes of
utilization: A GUI and Script commands. To use the program with the GUI, run it without args. To use
in the terminal use the -text arg. To run a script use the -file arg.  

This file will go over the basic usage of the program and catalogue all functions.

## GUI Controls
![prgram screenshot](res/screenshot.png)

### Layout
The program has a pane to the left containing the image you are currently working on. Only one image
can be worked on at a time in graphical mode (if you wish to work on more, use textual mode). To the
right of this is the preview mode toggle and split percentage spinner. Underneath that is the
current color histogram (a representation of the colors in the image). In the menu bar there are two
tabs: FIle and Operation.

### File Tab
This dropdown contains two options:
#### Open
Open an image file. The supported file formats are JPEG, PNG and PPM.
#### Save
Save the current file to the given name. Supported formats are JPEG, PNG, and PPM.

### Operation Tab
THis dropdown contains all the transformations that can be applied to an image. Operations are
sorted in alphabetical order.
#### Blue Component
Set each pixel's RGB values to its blue value.
#### Blur
Blurs the image.
#### Color Correct
Adjust the RGB values in the image so the peaks of the histogram align (ignoring values <10 or >245)
#### Compress
Lossy compression. Returns image of same dimensions. Program will prompt you to enter a compression
percentage between 0 and 100. (Just enter the numeral, no percent sign or words.)
#### Downscale
Resize the image to a smaller dimension. Program will prompt you to enter a new height and width.
Only enter whole numbers less than or equal to original dimensions.
#### Green Component
Set each pixel's RGB values to its green value.
#### Greyscale
Grayscale an image using the luma or the image.
#### Horizontal Flip
Flips the image horizontally.
#### Level Adjust
Input a new black, mid, and white point for the image. Shifts these points horizontally only.
Only put numbers when prompted by the program.
#### Red Component
Set each pixel's RGB values to its red value.
#### Sepia
Apply a sepia filter to the image.
#### Sharpen
Sharpen the image.
#### Vertical Flip
Flip the image vertically.

### Image Pane
The image pane will have scroll bars if it is larger than the default max size of 640 wide by 360
tall. This pane is empty when the program is initially opened.

### Histogram Pane
Displays the histogram of RGB values in the image as a line chart to give an idea of the values in
the image. When the lines intersect, the colors mix (for example, if the red and green lines cross,
a yellow pixel is shown).

### Preview Controls
#### Preview Toggle
This checkbox designates when the program is in preview mode. When in preview mode, any operation
will only temporarily be applied to the current image. When Preview is disables the image will
revert to the state before preview was turned on. In preview mode, one can see a split version of
the image, where the operation is only applied to the left part of the image. Not all commands
support this. To learn more, see the section on "Splittable Commands" in the Script Commands
section.
#### Split Percentage Spinner
This spinner determines the split percentage. Values range from 0 to 100. Adjusting the value will
change the image preview and histogram in real time. The histogram shows the RGB values of the image
in the split state while in preview mode.

## Script Commands

### 1. Load Image
**Description:** Loads an image from the specified file path and stores it under the given image
name.

**Command:** load 'file-path' 'image-name'

**Example:** load res/test.jpg test.

**Condition:** This command should be executed before any transformation or operation on the image.

### 2. Save Image
**Description:** Saves the specified image to the given file path.

**Command:** save 'file-path' 'image-name'

**Example:** save output/test-blur.jpg testblur

**Condition:** The image must have been loaded or created previously in the script.

### 3. Brighten/Darken Image
**Description:** Adjusts the brightness of the image by the specified amount. A negative value
darkens the image.

**Command:** brighten 'amount' 'source-image' 'destination-image'

**Example:** brighten 50 test testbright

**Condition:** The source image must be loaded before applying this command.

### 4. Red Component
**Description:** Set each pixel's RGB values to its red value.

**Command:** red-component 'source-image' 'destination-image'

**Example:** red-component test testred

### 5. Green Component
**Description:** Set each pixel's RGB values to its green value.

**Command:** green-component 'source-image' 'destination-image'

**Example:** green-component test testgreen

### 6. Blue Component
**Description:** Set each pixel's RGB values to its blue value.

**Command:** blue-component 'source-image' 'destination-image'

**Example:** blue-component test testblue

### 7. Blur Image
**Description:** Applies a blur transformation to the source image and stores the result.

**Command:** blur 'source-image' 'destination-image'

**Example:** blur test testblur

### 8. Sharpen Image
**Description:** Sharpens the image to enhance edges and details.

**Command:** sharpen 'source-image' 'destination-image'

**Example:** sharpen test testsharp

### 9. Sepia Transformation
**Description:** Applies a sepia filter to give the image a warm, brownish tone.

**Command:** sepia 'source-image' 'destination-image'

**Example:** sepia test testsepia

### 10. Flip Image Horizontally
**Description:** Flips the image horizontally.

**Command:** horizontal-flip 'source-image' 'destination-image'

**Example:** horizontal-flip test testhori

### 11. Flip Image Vertically
**Description:** Flips the image vertically.

**Command:** vertical-flip 'source-image' 'destination-image'

**Example:** vertical-flip test testvert

### 12. RGB Split
**Description:** Splits the image into red, green, and blue components and stores them as separate
images.

**Command:** rgb-split 'source-image' 'red-dest' 'green-dest' 'blue-dest'

**Example:** rgb-split test testred testgreen testblue

### 13. RGB Combine
**Description:** Combines separate red, green, and blue component images into a single image.

**Command:** rgb-combine <destination-image> <red-image> <green-image> <blue-image>

**Example:** rgb-combine test-rgbcomb testred testgreen testblue

**Condition:** The component images must be created using rgb-split or equivalent.

### 14. Luma Component
**Description:** Extracts the luma component (brightness) from the image and stores it.

**Command:** luma-component 'source-image' 'destination-image'

**Example:** luma-component test testluma

### 15. Intensity Component
**Description:** Extracts the intensity component, representing average brightness.

**Command:** intensity-component 'source-image' 'destination-image'

**Example:** intensity-component test testint

### 16. Value Component
**Description:** Extracts the value component, which represents the maximum color intensity.

**Command:** value-component 'source-image' 'destination-image'

**Example:** value-component test testvalue

### 17. Histogram Generation
**Description:** Generates a histogram representation of the image, depicting the distribution of
RGB values.

**Command:** histogram 'source-image' 'destination-image'

**Example:** histogram test testhistogram

**Condition:** This command should be used to visually analyze the color distribution of an image.

### 18. Compression
**Description:** Compresses the image using the specified percentage, reducing its data size.

**Command:** compress 'source-image' 'destination-image' 'percentage'

**Example:** compress test testcompressed 50

**Condition:** The percentage should be between 0 and 100.

### 19. Color Correction
**Description:** Adjusts the colors of the image to align the peaks of the RGB histogram.

**Command:** color-correct 'source-image' 'destination-image'

**Example:** color-correct test testcorrected

### 20. Levels Adjustment
**Description:** Adjusts the levels of black, mid-tones, and whites to enhance image contrast.

**Command:** levels-adjust 'source-image' 'destination-image' 'black' 'mid-tone' 'white'

**Example:** levels-adjust test testlevels 20 128 240

**Condition:** The values must be in the range 0-255, and must satisfy black < mid-tone < white.

### 21. Downscale
**Description:** Downscale an image to a new resolution.

**Command:** downscale 'new-height' 'new-width' 'source-image' 'dest-image'

**Example:** downscale 100 100 test testscaled

**Condition:** The values must be less than or equal to the original height/width respectively.

### 22. Splitting commands
**Description:** This is an additional parameter that can be added to another command to only apply
the transformation to the left part of an image. A percentage is supplied to designate where in the
image the split lies. Does not work in conjunction with masking. 
These are the commands that support this feature:  
- blur
- sharpen
- red-component
- green-component
- blue-component
- luma-component
- intensity-component
- value-component
- compress
- color-correct
- sepia
- levels-adjust

**Command:** <insert splittable command args here> split 'percentage'

**Example:** sepia source dest split 30

**Condition:** Command must be splittable and source image must exist.

### 23. Masking commands
**Description:** This is an additional parameter that can be added to another command to only apply
the transformation to part of an image. To use this, have an image loaded with black pixels in the
area where you want the transformation to apply.
These are the commands that support this feature:
- blur
- sharpen
- red-component
- green-component
- blue-component
- luma-component
- value-component
- intensity-component
- sepia

**Command** <insert maskable command args here> mask 'mask-image'

**Example:** sepia source dest mask mask_image

### 24. Quit
**Description:** Exits the application.

**Command:** quit or q

**Example:** quit

### 25. Run
**Description:** Run a script file.

**Command:** run 'filename'

**Example:** run script.txt

## Notes

Before applying any transformations ensure images are loaded

To save images produced by transformations, use the save command.
