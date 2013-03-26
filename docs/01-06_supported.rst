
Supported AE Features & Formats
===============================

Supported Effects
-----------------

We currently support this list of effects:

- Fast Blur
- Exposure
- Directional Blur
- Tint
- Tritone
- Threshold
- Hue/Saturation
- Ramp

Support Details
---------------

Fast Blur
^^^^^^^^^

- Bluriness: supported and keyframable
- Blur Dimensions: supported but not keyframable
- Repeat Edge Pixels: ignored

Directional Blur
^^^^^^^^^^^^^^^^

- Direction: supported and keyframable
- Blur Length: supported and keyframable

Bilateral Blur
^^^^^^^^^^^^^^

- Radius: supported and keyframable
- Threshold: supported but not keyframable
- Colorize: ignored

Exposure
^^^^^^^^

- Channels: Master only, not keyframable
- Master > Exposure: supported and keyframable
- Master > Offset: unsupported
- Master > Gamma Correction: supported and keyframable

Tint
^^^^

- Map Black To: supported but not keyframable
- Map White To: supported but not keyframable
- Amount to Tint: supported and keyframable

Tritone
^^^^^^^

- Highlights: supported but not keyframable
- Midtones: supported but not keyframable
- Shadows: supported but not keyframable
- Blend With Original: supported and keyframable

Threshold
^^^^^^^^^

- Level: supported and keyframable

Hue/Saturation
^^^^^^^^^^^^^^

- Channel Control: Master, Reds, Greens & Blues supported
- Channel Range: ignored
- Master Hue: supported
- Master Saturation: supported
- Master Lightness: supported
- Colorize: supported
- Colorize Hue: supported but not keyframable
- Colorize Saturation: supported but not keyframable
- Colorize Lightness: supported but not keyframable

Ramp
^^^^

- Start / End of Ramp: supported but not keyframable
- Start / End Color: supported but not keyframable
- Ramp Shape: supported but not keyframable
- Ramp Scatter: ignored
- Blend With Original: supported but not keyframable

Supported File Types
--------------------

Graphical Assets
^^^^^^^^^^^^^^^^

- Png files
- Jpeg files

Video Assets
^^^^^^^^^^^^

- h264 files in *.mp4, *.flv, *.f4v or *.mov container
- QT Animation files
- on2 VP6 files, including Alpha channel, in *.flv container

Font files
^^^^^^^^^^

If you use a special font file in your project, and if you have the correct licences, we need to install them separatly on our servers. We support *.otf or *.ttf files as long as they don't have any special character in their filename, or in their font name.
