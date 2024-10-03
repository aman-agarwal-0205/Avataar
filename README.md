# Image Generation Using ControlNet and StableDiffusers

## Introduction
This project emphasizes on the use of ***ControlNet*** and ***StableDiffusers*** from ***Hugging Face*** for image generation. Here we have used:

- [Depth Maps](depthmaps) and [Prompts](prompts) to pass into the model and generate images. We also calculate the ***Generation Latency*** which shows us the time taken for each image to be generated and total time taken by all images.

- Creating a function which helps us in changing the [Aspect Ratio](aspect_Ratio) of a given depthmap image and running it for the aspect ratios: ***1:1*** and ***16:9***.

## Thought Process
While creating a GenAI project, I used pre-trained models which were available on [Hugging Face](https://huggingface.co/). 
By using these models, we will generate image from the prompts and depthmaps of the images. 
The prompts that we use are used to label the images that are generated. 

Each image will be generated differently everytime we generate it and this is because of the ***Randomness*** in the diffusion model and ***flexibility in image interpretation***. There may be multiple reasons for this behavior 

## Concepts
**Depthmap**: A depth map is a grayscale image used to represent the distance of surfaces in a scene from a specific viewpoint, typically a camera. Each pixel's brightness in the depth map indicates the distance of that pixel from the camera; brighter pixels represent closer objects, while darker pixels indicate objects that are farther away.

**Prompt**: A prompt is a textual input that describes what the user wants the model to generate. It serves as a directive for the model, guiding it in producing images, text, or other content based on the description provided.

**Aspect Ratio**: Aspect ratio refers to the proportional relationship between the width and height of an image or screen. It is usually expressed as two numbers separated by a colon (e.g., 16:9 or 4:3), where the first number represents the width, and the second number represents the height.

## Features
**StableDiffusers**: Stable Diffusion is a deep learning-based generative model primarily used to generate high-quality images from textual descriptions. It leverages ***latent diffusion models (LDMs)*** to convert text prompts into images by iteratively denoising a latent space. 

**ControlNet**: ControlNet is a technique designed to give additional control over diffusion models (like Stable Diffusion) by incorporating structural information into the generation process. It allows the model to follow specific guidelines or structures, such as human poses, edges, depth maps, or segmentation masks, while generating images.

**Aspect Ratio Adjustment**: One of the features of the code is to ***adjust the aspect ratio*** of an input image to a desired one. User can define the desired aspect ratio when we call the funtion and pass the value.

**Image Resizing**: The code performs image resizing by calculating new dimensions based on the target aspect ratio while preserving as much of the original image as possible.
It uses ***OpenCV's*** `cv2.resize()` function to resize the image, ensuring that the content does not get overly distorted in the process.

**Saving Generated Images**: The generated output images are stored in the output directory of ***Kaggle*** `/kaggle/working/output/` which I created using the following code: 
``` 
output_folder = '/kaggle/working/output/'
if not os.path.exists(output_folder):
    os.makedirs(output_folder)
```
**Error Handling**: The code has basic error handling for common issues, such as unsupported file formats or incorrect paths. If OpenCV encounters an error while saving the image, the issue is reported, helping users understand what went wrong.


## Output
The generated images can viewed in [Output](<generated image>).

The generational latency is as follows:

![Generational Latency](https://github.com/aman-agarwal-0205/Avataar/raw/main/generational%20latency.png)

The depthmap generated after modifying the aspect ratio can be viewed in [Modifyed Aspect Ratio](aspect_Ratio).

## Observations
The obersvations are listed in the attached [report](<Project Report of Image Generation Using ControlNet and StableDiffusers.pdf>).
