# CS5010-Programming Design Paradigm-Project
## GRIME: Graphical Image Manipulation and Enhancement

## Overview
This project implements a simple image processing application that supports loading, saving, and
applying various image filters. The design follows a Model View Controller (MVC) architecture. It
also uses a Command design pattern for the controller commands and and operations on the model. It
also uses Java SWing for an interactive GUI.
- **Model** represents the data and logic.
- **View** represents the user interface (Terminal-Based or Graphical Interface).
- **Controller** represents and manages the interaction between the model and view.

## How to Run
Use the `main(String[] args)` method in the [`Main`](src/Main.java) class with the appropriate
argument(s).  
If using the JAR file, type `java -jar GRIME.jar` with a Java runtime that is Java 11 or newer.  
The project can be run in two modes:
1. **Graphical Mode** : Don't provide args to interact with the program in the terminal.
2. **Terminal mode** : Use the argument `-text` to use text commands in the terminal.
3. **Script Mode** : Use the argument `-file` followed by the file path of the script file.
(Example: `-script script.txt`) 
                      

---

## Implementation

### 1. Main
The [Main](src/Main.java) class is the entry point of the application. It processes command-line
arguments to determine whether to run the application. Depending on the argument, the appropriate
controller is initiated to handle user input.

### 2. Model
The model handles the main logic of the image manipulation. It consists of the following components:

- **[ImageModel](src/model/ImageModel.java) Interface**: Defines the operations supported by the
image model, including loading/saving images and applying transformations.
  
- **[ImageManagerModel](src/model/ImageManagerModel.java) Class**: Implements the `ImageModel`
interface and manages a collection of images and their operations. All the file-related operations
such as image type are given to appropriate file managers.
  
- **[Image](src/model/Image.java) Interface**: Represents a simple image. It provides methods to
retrieve pixel data and apply transformations to the image.
  
- **[PixelImage](src/model/PixelImage.java) Class**: Implements the `Image` interface and uses the
`Pixel` objects to represent the pixels of the image. It defines methods to get individual pixels,
transformations and handles operations.
  
- **[Pixel](src/model/Pixel.java) Interface**: Represents a single pixel in the image with methods
to access RGBA values.
  
- **[RGBAPixel](src/model/RGBAPixel.java) Class**: Implements the `Pixel` interface and stores pixel
data. It also provides basic getter methods for red, green, blue, and alpha components.

### 4. Transformations
Transformations modifies the image by altering their pixel data in some way. Some transformations
can be split. This means that they can be applied to the first X% of an image where X is the given
parameter. Blur, sharpen, color-correct, compress, and levels-adjust, and all color transformations
are splittable.

- **[ImageTransformation](src/model/transformations/ImageTransformation.java) Interface**: Defines 
the transformations that can be applied to images.
  
- **[ColorTransformation](src/model/transformations/ColorTransformation.java) Enum Class**:
Defines transformations that multiply each pixel with a matrix.   
Examples:
  - BlueComponentTransformation.
  - SepiaTransformation.
  - LumaTransformation.

- **[KernelTransformation](src/model/transformations/KernelTransformation.java) Abstract Class**:
Defines transformations that use kernels to determine pixel value from surrounding pixels.  
Examples:
  - [BlurTransformation](src/model/transformations/BlurTransformation.java).
  - [SharpenTransformation](src/model/transformations/SharpenTransformation.java).

- **[CompressionTransformation](src/model/transformations/CompressionTransformation.java) Class**:
Compresses images using a Haar wavelet transformation to reduce data size while retaining image
quality.

- **[ColorCorrectionTransformation](src/model/transformations/ColorCorrectionTransformation.java) 
Class**: 
Aligns the peaks of the RGB histogram to improve image balance.

- **[LevelsAdjustmentTransformation](src/model/transformations/LevelsAdjustmentTransformation.java)
:** Adjusts the black, mid-tone, and white levels to enhance contrast.

- **[HistogramGenerator](src/model/transformations/HistogramGenerator.java)**: Generates a histogram
representation of an image by calculating the distribution of RGB values. The resulting image
contains the Red, Green, and Blue histograms overlaid over each other. Overlapping colors are mixed.
For example, an area where the Red and Green histograms overlap is yellow. We thought this histogram
style would be pleasing.
- **[DownscaleTransformation](src/model/transformations/DownscaleTransformation.java)**: Downscales
an image to a given height and width. Dimensions can be of any ratio but must be less than or equal
to the original.

### 5. Multi-Image Operations
This operation require multiple images as input (e.g., RGB Combine).

- **[MultiImageOperation](src/model/transformations/multiimage/MultiImageOperation.java)
Interface**: Defines operations that combine multiple images.
  
- **[RGBCombineOperation](src/model/transformations/multiimage/RGBCombineOperation.java) Class**:
Implements `MultiImageOperation` by combining three images such as the red, green, and blue channels
of the final image.

### 6. Controller
The controller manages user input and interacts with the model to perform operations.

- **[ImageEditorController](src/controller/ImageEditorController.java) Interface**: Defines the 
methods for controlling the image editor application.
  
- **[SimpleController](src/controller/SimpleController.java) Class**: Implements the 
`ImageEditorController` interface and handles the user's textual input.

- **[SwingController](src/controller/SwingController.java) Class**: Extends `SimpleController` and
adds support for an `ImageEditorSwingView`. The controller will construct a default view object if
one is not passed as an argument. This controller listens for `ActionEvent` and `ChangeEvent` to
update itself accordingly. It supports the preview functionality of `ImageEditorJFrame`. This class
translates GUI inputs into a series of textual commands which are run using its parent class's 
`run()` method.
  
- **[ControllerCommand](src/controller/commands/ControllerCommand.java) Interface**: Commands to be 
executed by the controller on the model. Each one processes the user's args and performs 
accordingly. If a command is splittable, these classes will look for a "split" arg and act
accordingly.
Examples:
  - [LoadCommand](src/controller/commands/LoadCommand.java).
  - [RGBSplitCommand](src/controller/commands/RGBCombineCommand.java).
  - [BrightenCommand](src/controller/commands/BrightenCommand.java).
  - **[ColorCommands](src/controller/commands/ColorCommands.java)** 
  (Commands that do color transformations)
  - **[CompressionCommand](src/controller/commands/CompressionCommand.java)**.
  - **[ColorCorrectionCommand](src/controller/commands/ColorCorrectCommand.java)**.
  - **[LevelsAdjustmentCommand](src/controller/commands/LevelsAdjustCommand.java)**.
  - **[HistogramCommand](src/controller/commands/HistogramCommand.java)**.
  - **[DonwscaleCommand](src/controller/commands/DownscaleCommand.java)**.

### 7. View
The view is required for displaying information to the user.

- **[ImageEditorView](src/view/ImageEditorView.java) Interface**: Defines the methods for
displaying messages and images to the user.
  
- **[TerminalView](src/view/TerminalView.java) Class**: Implements the `ImageEditorView` and 
provides a terminal-based interface. It displays text-based messages such as errors, image info, and
operation success messages.
- **[ImageEditorSwingView](src/view/ImageEditorSwingView.java) Interface**: Defines the methods for
a Swing based GUI for the program.
- **[ImageEditorJFrame](src/view/ImageEditorJFrame.java) Class**: Extends `javax.swing.JFrame` and
implements `ImageEditorSwingView`. This View offers a scrollable window for a currently loaded
image with a color histogram displayed to the right as a line chart. operations are found in
drop-down menus at the top of the screen. There is a preview toggle that will let you preview an
operation and see a split view that you can change via the Spinner component. It sends 
`ActionEvent`s and `ChangeEvent`s to the a listener (the controller) based off data given during 
construction when buttons are clicked. It can show `JOptionPane` input and message boxes when
prompted by the controller.

## Image Credits
[test.jpg](res/test.jpg) is a public domain image. We sourced this image from the Wikimedia Commons.
You may find the file [here](https://commons.wikimedia.org/wiki/File:Samoyed-and-teddy-bear.jpg).

[tinytest.png](res/tinytest.png) was created by Supergreennina to Wikimedia Commons.
It is licensed under a Creative Commons Attribution-Share Alike 4.0 International license.
You may find the image [here](https://commons.m.wikimedia.org/wiki/File:Red_Square_(2x2_Pixel).png).

---
