# Convert_from_images_to_animations_in_C
## Pixelate Images and Convert to C Animation Structs

This tool converts a sequence of PNG JPG or JPEG images into C structs, which can be used for animations in embedded systems and other C-based projects. The script pixelates the images to a fixed grid, extracts brightness data, and generates the corresponding C code for animation frames.

### Features

- **Pixelate images** to a fixed grid (default: 18x11).
- **Batch process** a directory of PNGs into a C array of animation frames.
- **Single image** conversion supported.
- **Outputs C structs** ready for use in microcontroller or embedded projects.

---

## Usage

### 1. Converting Images
To convert multiple images to an array of frames in one struct, thus making an animaton, it is important to **put all input images in one folder and name them in an alphabetich/numeric order.** 

**In the terminal:**
- Run the command `python3 pixelate_and_convert.py <folder_containing_input_pictures>` in terminal
- Then you will be asked to enter the name for your C struct and file, do so

After doing this will one C file in the `frames_as_c_code` folder appear, and multiple images of the pixelated grayscale input images appear in the `output_images` folder

### 2. Testing 

**View generated frames as pixelated grayscale images**

The generated images will appear in the òutput_images` file

**View generated C code**

To view the generated C-code in the terminal, a 

Compile: `gcc -o test_animation -I. test_c_struct.c frames_as_c_code/*.c -DTEST_ANIMATIONS_MAIN`
Run: `./test_animation <struct_name> <num_frames>`

## Script Details
**Image processing**

`filter_dark_pixels` is an image processing function that filters out dark noise and makes a smoother gradient between the darkest level (led turned off) and the remaining darkerst active pixels. The function gets active when .num_pixels is above a certain level. 

`enhance_contrast_if_many_active` adjusts the constrast and is default on. Good for videoes taken on phone camera. Adjust how strong you want the contrast with _k_ (value ranges from 0 to 1) whereas a higher value gives a steeper sigmoid function, thus higher contrast. 

![A descriptive caption for the image](./README_images/default_image_prosessing.png)
*Comparison of prosessed and unprocessed images. The plot displays the default settings*


XOX Andrea

