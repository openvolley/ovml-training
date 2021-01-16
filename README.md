# ovml-training

Use [Yolo_mark](https://github.com/AlexeyAB/Yolo_mark) to mark bounding boxes for training [ovml](https://openvolley.org/ovml) networks.

Credit: this repo is a clone of [Yolo_mark](https://github.com/AlexeyAB/Yolo_mark), modified/preconfigured for `ovml` training.

## Usage

1. Compile the executable (see below)

1. Assemble your collection of images, which are usually frame grabs from video files. You can use e.g. `ovideo::ov_video_frame` for this if you have video files locally, or https://www.youtubescreenshot.com/ to extract frames from YouTube videos

1.  Put your `.jpg` images into the `data/img` directory

1. Run `./mark_ovml.sh` (Linux) or `mark_ovml.cmd` (Windows). You might find it useful to make the bounding box lines thinner (cycle through line widths by pressing `w`) and hide the object names (`k`)

1. Send us the contents of the `data/img` directory (the image files and their bounding box `.txt` annotation files)

### Notes on images

- Images should generally have all or most of the court in view. For ball detections, the minimum image size (video resolution) should be 1280 x 720

- Try and collect images with varying ball colouration, lighting, court surrounds, and backgrounds

- Mark *all* target objects in an image. If we are marking balls, don't just mark the ball in play. All other balls in view must also be marked. You might want to avoid images with ball trolleys full of balls, or balls all over the court during warmup for this reason

- Avoid images with blurry balls (mild blurring is OK), or balls that are more than about 20% occluded by other objects (player bodies, net posts, etc)


## Compilation

* To compile on **Windows** open `yolo_mark.sln` in MSVS2013/2015, compile it **x64 & Release**. Change paths in `yolo_mark.sln` to the OpenCV 2.x/3.x installed on your computer:

    * (right click on project) -> properties -> C/C++ -> General -> Additional Include Directories: `C:\opencv_3.0\opencv\build\include;`

    * (right click on project) -> properties -> Linker -> General -> Additional Library Directories: `C:\opencv_3.0\opencv\build\x64\vc14\lib;`

* To compile on **Linux**:
    ```
    cmake .
    make
    ```

----

### Instruction manual

#### Mouse control

Button | Description | 
--- | --- |
Left | Draw box
Right | Move box

#### Keyboard Shortcuts

Shortcut | Description | 
--- | --- |
<kbd>→</kbd> | Next image |
<kbd>←</kbd> | Previous image |
<kbd>r</kbd> | Delete selected box (mouse hovered) |
<kbd>c</kbd> | Clear all marks on the current image |
<kbd>p</kbd> | Copy previous mark |
<kbd>o</kbd> | Track objects |
<kbd>ESC</kbd> | Close application |
<kbd>n</kbd> | One object per image |
<kbd>0-9</kbd> | Object id |
<kbd>m</kbd> | Show coords |
<kbd>w</kbd> | Line width |
<kbd>k</kbd> | Hide object name |
<kbd>h</kbd> | Help |

