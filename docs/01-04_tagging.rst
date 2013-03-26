
Placeholder and Tagging
=======================

As After Effects was not designed to have dynamic content generated from an external source, we need to specify in the project where the user content will be. We have 2 types of content, graphical content such as maps, pictures and videos, and text content. Both are tagged the same way, but are handled slightly differently.

Graphical Placeholders
----------------------

If you want to add a placeholder for a Google Map, a video or a picture, you just need to create a precomposition with the correct dimensions and aspect ratio. Then, nest it into your main comp and tag it. What is important to understand is that this tagged precomposition, aka Placeholder, will act as a “window” to the user data. Any modification you do on it such as rotation, zoom, track mattes, transparency and so on will be applied to the user data. Also be aware that any layers or data inside the precomposition will be completly replaced by the user asset.

The size of the placeholder composition depends on the use you plan to have. Depending of the kind of data you expect to fill it with, you can optimize it:

- Google Maps are usually square, with a max size of 640×640
- Portrait Pictures usually have a 10/15 ratio
- Landscape Pictures usually have a 15/10 ratio
- Videos usually have a 16/9 ratio, but can also be 4/3 ratio

For picture size, I usually use the main composition width as the width of the placeholder. Like this you can always fit the screen without scaling it. For example, if your Widget is in Full HD resolution (1920×1080) I will use 1920 as the default width for the picture placeholders. As general advice, make sure your placeholder is neither too small, nor too big. Scaling up assets can result in a visible loss of quality (above 200% scale, results can really look terrible). Keeping assets scaled down results to a loss of performance in render time. So it's up to you to find the perfect balance between quality, performance and placeholder size.

If you are doing a personalized video campaign and you control where the user pics come from, you can even get perfectly sized placeholders.

If in your UI or in our Studio, users select a bigger or smaller picture, our engine will automatically make it fit in your placeholder. We'll see how to do this, and how to customize this behavior in our Applying XML effects and behaviors page.

Text Placeholders
-----------------

If you want to add a text placeholder, simply add a text layer and tag it.

*When creating the text layer be sure to use the simple text tool and not the box text tool. To create a simple text layer, just clic on the composition viewer with the text tool selected, instead of drawing a box with it. If your texts are inside text boxes, they will be slightly moved around depending on the anchor point position.*

Also make sure the font size of your text is big enough to be readable, especially in high definition videos where texts are usually designed to be small. Then become unreadable if the video is not viewed at full resolution. A small sized text at 1080p won't be readable at all at 360p. The smaller the characters, the more the compression will harm them.

Texts are the most difficult layers to export from After Effects as we don't have access to a lot of parameters. This is a list of what we *can't* do with text layers:

Character Panel
^^^^^^^^^^^^^^^

- Multiple Fonts or different font parameters on a single layer
- Kerning
- Leading
- Horizontally scale / Vertically scale
- Baseline shift
- Tsume
- Faux Bold and Faux italic
- All Caps
- Small Caps
- Sub/Superscript

Paragraph Panel
^^^^^^^^^^^^^^^

- Justify (all variations)
- Indent (all variations)
- Add space (all variations)

To sum it up, on a text layer we only support one font, one font style (color included), and the paragraph alignment (left, right or centered). All layer transformations such as rotation, opacity, position, scale, track mattes & so on are still available.

Also note that we don't do Vertical Align yet, so if you define a 3 line text input, we'll always fill it from top to bottom.

**As for any other layer, Layer Styles are not supported either!**

After Effects doesn't allow us to get the exact bounding box of your text layer, so we have to calculate it. In order to do that, you'll need to fill your text layer until you max it out with characters. To calculate it, our engine simply takes the text layer, reads it, renders it to an image file and then we get the width and height of the text zone.

We recommend using Capital W. Spacing and kerning might be slightly different between After Effects and our render engine, so using W allows us to reduce this shift (by reducing the number of characters) when calculating the bounding box on our side.

Capital W makes the font size looks bigger than it actually is (unless you plan to only use capitalized letter in your text). Before filling your text with W for export, make sure to test it with random text (or Lorem Ipsum) to avoid any readability issues.

In our Applying XML effects and behaviors we will see how to change the text color and, to some extent, the font face.

Tagging Details
---------------

So, how do we tell our engine that this nested composition or this text layer is to be replaced with the user input? We simply tag it. To tag it, you just have to add a marker on the layer. To do that, simply select the layer and press the * key on the numeric keypad (or go to Layer > Add Marker).

Now that you have your layer marked, we need to edit the marker to give it all the data we need.

We are using 2 important text zones in the marker settings:

- Comment: the text here won't do anything apart from being displayed in the timeline. This is recommended for easy referencing inside your project. Not mandatory.
- Flash Cue Point Name: This is where we define the type of placeholder, and its index. This information is mandatory. If not properly filled, your placeholder won't be recognized.

As you can write whatever you want in the comment section, let's focus on the Flash Cue Point Name and see what information needs to be there. We actually support 2 indexed tags:

- TEXT_XX
- IMAGE_XX

TEXT_XX, where XX is an index ranging from 01 to 99, is used to tag a text placeholder.
IMAGE_XX, where XX is also an index ranging from 01 to 99, is used to tag a picture, map or video placeholder.

If you want to display several times the same user input, may it be a text or a graphical asset, you can tag different elements with the same index. For this to work, you just need to take care of renaming all the layers sharing the same tag with the same index with the same name.

For example, if you have 3 different text layers displaying the same user input, even if they are in different compositions with different properties, they will need to have the same layer name.

Tagging a project comes in the very last steps of it creation. In order to properly index your placeholder, you must have already sliced your project into widgets, or know how it will be sliced. For each Widget, tags must start at 01 and then go on without skipping any number.

Example with a Widget accepting 2 user texts, and 2 user pictures:

This is correct:

- TEXT_01
- TEXT_02
- IMAGE_01
- IMAGE_02

TEXT and IMAGE tags are correctly indexed.

This is incorrect:

- TEXT_02
- TEXT_03
- IMAGE_01
- IMAGE_02

The TEXT tags doesn't start at 01.

This is incorrect too:

- TEXT_01
- TEXT_03
- IMAGE_01
- IMAGE_02

The TEXT tag TEXT_02 is missing

This is also incorrect:

- TEXT_01
- TEXT_02
- IMAGE_03
- IMAGE_04

Indexes are tag independent. Here IMAGE tags cannot take the index continuity of the TEXT tags indexes.

Tags are usually the first place to look when a user text or picture is missing in the stupeflixed video.