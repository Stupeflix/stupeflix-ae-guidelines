
Unsupported Features & Formats
==============================

As we continuously improve our rendering engine, we try to integrate more and more features. Sadly, the list below is still unsupported in our current engine:

Features
--------

- Effects (except those mentioned here)
- Masks
- Time Remapping
- Lights Layers
- Shape Layers
- Layer Styles
- Adjustement Layers
- 3D Material Options
- Photoshop Live Layers
- Photoshop 3D Layers
- Blending Modes
- Collapse Transformation
- Motion Blur
- Assets larger than 4096x4096
- Compositions larger than 4096x4096
- Layer In Point different than Layer Start Time
- Vertical Align for text Layers
- Frame blending
- Audio *

iOS Renderer
^^^^^^^^^^^^

If you design a Widget for our iOS Renderer you'll have to take those extra exceptions into consideration

- Assets larger than 2048x2048
- Compositions larger than 2048x2048

* We don't support audio files inside an After Effects Project, but audio files can be played inside the XML that will embbed your AE Widget. More info about this `here <https://stupeflix-ae-guidelines.readthedocs.org/en/latest/03-02_xml.html#audio>`_. 

Formats (Static Images)
-----------------------

We don't support these graphical assets inside AE projects (non exhaustive list):

- Photoshop Files
- Illustrator Files
- EPS Files
- Tiff Files

We recommand using jpegs for non alpha assets, and png otherwise.

Formats (Video files)
-----------------------

We don't support file formats other than h264 (in mp4 encapsulation) for non alpha videos, and On2VP6 (in flv encapsulation) for video with alpha.

For h264 we do recommand using the High Profile with 5.1 Level, 2 pass VBR with a 5-8Mb bitrate for SD videos, and a 10-15Mb bitrate for HD videos and up to 20Mb for Ultra HD videos.

For On2VP6 we do recommand a 10Mbit bitrate in VBR encoding, with target quality set to Optimal.

We are using Adobe Media Encoder in house to compress our assets, we do recommand it.
