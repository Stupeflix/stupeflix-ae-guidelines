
Preping your Project
====================

Non Linear Template
-------------------

If you're doing a non linear Template, you project must be spliced up into different Widgets. 

When designing a Template, it is important to keep in mind that it is the user who is storytelling his video, not you. Depending on what the user wants, and what the user wants to say, we will choose programmatically one widget or another. The most important aspect of your template is visual coherence. You don't know in what order, or in what combination your widgets will be used, so it's essential that they all have a consistent look & feel, and most importantly, that any widget can be used before or after any other widget.

Widget Recommanded Structure
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

After designing several templates, we found out that some amount of widget variation is necessary to avoid the feeling of videos looking the same, or looping on the same effects

For that we recommend to create at least the following set of widget and variations:

- A widget containing 1 picture (2 variations)
- An overlay Widget containing 1 text for caption (2 same variations)
- A widget containing 2 pictures (3 variations)
- An overlay Widget containing 2 texts for captions (3 same variations)
- A widget containing 3 pictures (3 variations)
- An overlay Widget containing 3 texts for captions (3 same variations)
- A widget containing 4 pictures (3 variations)
- An overlay Widget containing 4 texts for captions (3 same variations)
- A widget containing 1 short text (2 variations, for titles)
- A widget containing 1 long text (2 variations, for long texts)
- A widget containing 1 map (2 variations)
- An overlay Widget containing 1 text for captions (2 same variations)
- A custom transition widget (2 variations)

If you'd like to make your Template more unique, you can also add special widgets such as:

- Intro Widgets
- Outro Widgets
- Lower 3rd / Upper 3rd Widgets
- Customizable Widgets (Background, borders, vignettes, color scheme, fonts…)

Customizable Widgets
^^^^^^^^^^^^^^^^^^^^

If you want to, you can create what we call “Customizable Widgets”. In these Widgets, the placeholders are not only used for showing the user pictures, they are also used to receive decoration assets such as background, borders, custom graphic elements.

You can get a better idea of it by having a look at this After Effects Widget and this XML Editor project. See how you can completely customize the look and feel.

These Widgets are resource-hungry, so using them can have an impact on performance. You can choose to make an entirely customizable template (and specify default assets), but rendering time will be impacted, and depending on the complexity of your Widgets, render time can really be lengthened.

Sub-Styles
^^^^^^^^^^

You can also create sub-styles for your template. Sub-Styles are just a graphical variation of your template, to express a different mood or genre. For example, we could replace the cork background of the Scrapbook template with a concrete one, and white borders with spray paint to give a totally different feeling. Adding to that a faster camera animation and some hip-hop soundtrack and you'll get the idea.

Sub-styles are “pre-made” customizable Widgets. The only difference is that we don't allow the user to modify them on the fly like customizable Widgets, but just select one or more available style from a dropdown list, in order to get better and faster performance when rendering the video.

Technical Considerations
^^^^^^^^^^^^^^^^^^^^^^^^

We recommand a default to 5 seconds per item duration. An item can be a text, a picture or a map.

For example, a Widget with 3 pictures will have a 15 second duration. If in your widget you choose to display one picture at a time, these 15 seconds include the transitions between your pictures. So it's not 5 seconds of full display per item, it can be shorter or longer depending on how you organize your Widget. But in the end, it will have to be 15 seconds for 3 pictures. If you choose to add small captions on top of your pictures, they will still be shown for 15 seconds as items displayed simultaneously don't add-up their durations.


Linear Tempalte
---------------

When you are designing a video for an advertising campaign, unlike a non linear Template, you are doing the storytelling for the user, but you allow him/her to somehow interact with your story by customizing the video.

Usually, such projects are designed as a long video with special parts where user assets can be seen. One could even imagine different paths or scenes for the video depending on some user choices.

In such cases, there is not a predefined Widget structure, it really depends on how your video is conceived. From past projects and experience, it is safe to not slice your video into Widgets. Just keep on project for the whole video.

Technical Considerations
^^^^^^^^^^^^^^^^^^^^^^^^

On such custom projects, you are free to choose your most suitable framerate. But be sure to have all assets in your project, including compositions, set at the same framerate. It's a common source of error to have footage from different sources at different framerates not conformed with the destination framerate.

Technical Recommandations
-------------------------

Our render engine is much more efficient with standard 16/9 video ratio, such as 640×360, 960×540, 1280×720 or 1920×1080. Our online XML editor, used for previewing, can only preview correctly 16/9 projects. We of course support other resolutions and other aspect ratios, but we recommend you to work in 16/9 aspect ratio.

Working in native resolution is important. If you provide us a Full HD (1080p) project but only allow your users to create 360p videos, the render won't be as efficient as a lot of processing power will be lost dealing with high resolution assets to be scaled down. We highly recommend you to design and provide us a project that is matching your destination resolution.

For the framerate, we strongly recommand 24 fps as it's the default cinema one. You need to set your framerate according your assets. If you are using royalty free footage set a 29,97, your project framerate will need to be 29,97.

*Tip: for the same content, a 24 fps video will render faster than a 29,97 video. Just because we will render 5,97 frames less per second.*