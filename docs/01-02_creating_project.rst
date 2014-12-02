
Creating a Stupeflix Compatible AE Project
==========================================

So here comes the tricky part: creating a project that is compatible with our render engine. Creating projects for Stupeflix calls for a slight change of design paradigm. I'll try to explain this on this page, along with general technical stuff. You'll find on separate pages more information on selected (and important) topics.

But first things first, we need to talk about what we call widgets, so…

Let's talk about Widgets
------------------------

From now I will make a distinction between an After Effects Project and an After Effects Widget.

At Stupeflix, we build videos like `Lego <http://www.lego.com/>`_ objects. For each video theme (aka “template”) in the `Stupeflix Studio <http://studio.stupeflix.com/>`_, we have basic bricks for each kind of data the user can input, and then plug them together to create a unique video every time. We can add bricks next to each other, on top of another, regroup them together in a long sequence, and so on. Like Legos, the possibilities are endless. You can try and experience that with our `Scrapbook template <http://studio.stupeflix.com/>`_. Play with the template, add a map, a picture and a text, change their orders, put several pictures one after another, with or without captions. Preview you video between each action you make, you'll see that we are using a limited amount of basic bricks and build your video on the fly with them.

When we design a template for the studio, we create all the basic variations of scenes and transitions, or bricks to go on with the Lego analogy, inside the same After Effects project, to share the graphical assets and to ensure that all our variations share the same look and feel. Then we export each brick separately using this brilliant `After Effects Script <http://aescripts.com/save-comp-as-project/>`_ (created by yours truly) into their own projects.

Even if you're not designing a Studio Template, but a personalized video ad campaign, there are numerous advantages to slice your project into smaller widgets. But we'll see that later.

Because grown-ups don't like being reminded that they cannot play Legos anymore, we are calling these bricks Widgets. That was the end of the Lego analogy.

Designing Your Widget
---------------------

Now let's talk about what you can and cannot do in After Effects, and how it interacts with our render engine and XML video description language.

Widgets can contain 2 sorts of elements:

Design elements (like the cork texture of the Scrapbook template)
Placeholder elements (like the precomps that receive the user picture)

The only difference between a design element and a placeholder is tagging. In order to “convert” a composition or a text layer into user customizable elements, you have to add a tag. We'll come back later on `that subject <https://stupeflix-ae-guidelines.readthedocs.org/en/latest/01-04_tagging.html>`_.

So, what's the big picture when designing an After Effects Widget to be used by Stupeflix ? Well, the short answer is: you see that pretty “Effects” menu in After Effects? Well forget about it. Slightly longer answer: you see that pretty “Effects” menu ? Well, pretty much forget about it for placeholders (not for design elements).

Joke aside, since projects are rendered by our engine, not After Effects, we had to develop our own feature set. The most import feature is animation, so we decided to add effects on a case by case basis. We already support some of them as you can see on our Supported Effects page. When I say support, I mean, available on our engine for real time rendering. You can use any effects (including 3rd parties effects) on design elements as long as you `Pre render or Proxy <https://stupeflix-ae-guidelines.readthedocs.org/en/latest/02-01_optim.html#pre-rendering>`_ them.

You can find a detailed list of all the features we do not support yet on our `Unsupported Features <https://stupeflix-ae-guidelines.readthedocs.org/en/latest/01-07_unsupported.html>`_ page.

Now, on the bright side, we support almost all of the other features you can find in After Effects: Trackmattes, Expressions and Bézier curves, parenting, and all layer transformation properties such as Position, Rotation, Anchor Point, Scale, Opacity and so on. As disabled layers are not exported (except for trackmattes), be sure to parent layers to enabled layers only.

For text layers there is extra complication. We support the same transformations and effects as any other layer, but we don't support any character animations. And because After Effects doesn't allow the export of leading, kerning and most of the font options (including the layer size, or bounding box) we don't support anything else than paragraph alignment, Font face (one per layer), Font size (one per layer) and Font color (one per layer). Also, don't change the anchor point position on a text layer. Last but not least, as we have to recalculate the layer size on our side, it is not recommended to use a text layer as a parent. You can still use it as a child without problem.

You can find more informations about text layers in the `Placeholder and Tagging <https://stupeflix-ae-guidelines.readthedocs.org/en/latest/01-04_tagging.html>`_ page.

Paradigm shift
--------------

So what about this Paradigm shift I talked about earlier? The big difference between a normal After Effects project and a Stupeflix After Effects project is rendering.

When you design an AE project to make a video, you usually make the final render once, so you don't really care about rendering time or rendering optimization (I don't know anyone converting expressions into keyframes to reduce rendering time).

In the case of a Stupeflix AE project, once your Widgets are in our system, they will be rendered every time a user uses them. The most important thing for us is speed. We target a faster than realtime rendering in SD, and realtime for HD videos. If you create heavy, complicated Widgets, we won't be able to deliver that speed, and it will impact the user experience.

We have a full help section dedicated to `Widget optimization <https://stupeflix-ae-guidelines.readthedocs.org/en/latest/02-01_optim.html>`_. You'll find examples on how you can drastically reduce render times.

Camera and 3D layers
--------------------

We completely support 3D layers and cameras. You have to make sure that any composition featuring 3D layers has a single camera. If you have no camera, or more than one camera in your composition, our AE `SxC Validation Script <https://stupeflix-ae-guidelines.readthedocs.org/en/latest/01-09_script.html>`_ will warn you, and log an error.

When building your 3D world, make sure that your 3D layers are in the correct depth order, front layer on top of the layer stack, back layer at the bottom of the stack. Having two 3D layers separated by less than 2 pixels in depth can produce Z-Fight. Z-Fight is an inelegent side effect where our 3D engine don't know which pixel of the 2 layers is in front because the rounded calculation results are equal. This usually happens when rotating in z-space the layers.

You can of course use 2D layers along with your 3D layers.

We don't support the depth of field of the camera. The trick involving `Adjustment Layers <https://stupeflix-ae-guidelines.readthedocs.org/en/latest/01-07_unsupported.html>`_ to break the 3D world doesn't work with Stupeflix. `Collapsing Transformation <https://stupeflix-ae-guidelines.readthedocs.org/en/latest/01-07_unsupported.html>`_ to propagate a precomposed 3D world into another 3D world doesn't work either.

Nesting and Precomposing
------------------------

Nesting and Precomposing is a great feature we totally support (except for `Collapsed Transformations <https://stupeflix-ae-guidelines.readthedocs.org/en/latest/01-07_unsupported.html>`_). We also use precomposing for `graphical placeholders <https://stupeflix-ae-guidelines.readthedocs.org/en/latest/01-04_tagging.html#graphical-placeholders>`_.

But you should be light on your nesting depth, as nesting is heavy on our render engine. We think that you shouldn't go deeper than 3 levels of nesting:

	main comp (lvl 1)
		precomp (lvl 2)
			precomp (lvl 3)

Of course, precompositions used as `placeholders for graphical elements <https://stupeflix-ae-guidelines.readthedocs.org/en/latest/01-04_tagging.html#graphical-placeholders>`_ won't be considered as precomps in our system, they will be replaced by the user assets, so they don't slow down rendering.

Also you have to make sure any precomp or nested comp is using the same framerate as it's parent comp. We only allow 1 framerate per project.

Some Limitations
----------------

As our render engine don't use the same algorithms as After Effects, you might notice some aliasing around the edges of your layers. Activating anti-aliasing on our side would drastically reduce the render performance. We have found a very subtle, but yet significant, workaround to get anti aliasing for free.

We have aliasing issues on the edges of layers, not on the content of the layer itself. If your layer, may it be a footage or a composition, have transparent edges it will be ok.

For that I recommand you to make your precomposition a bit wider to leave some empty space around the edges, and to prepare your graphical assets accordingly using the same trick.

If you have Photoshop, you can import your PNG files in it and just make them 4-6 pixel wider by simply adjusting it's canvas size in the Image menu.

Having slightly larger assets works around another limitation: blur. Of the few effects we support, Blur is the most usefull one. But we are facing a big limitation: we cannot blur outside the boundaries of a layer. So if you have a 50×50 pixels asset and apply a blur of 100 on it, only the small 50×50 pixel asset will be blured, showing it's clear cut edges, thus giving a bad result. If you want your layer to have a larger blur than it's boundaries, either precomp it (but it can produce slowdowns as you can see in the `Nesting and Precomposing <https://stupeflix-ae-guidelines.readthedocs.org/en/latest/01-02_creating_project.html#nesting-and-precomposing>`_ section above) in a larger comp or enlarge it's canvas size in Photoshop.

We don't support masks. You will have to use track mattes instead.

Hold keyframes are not supported either, be sure to be carefull about this.

Blending modes are not supported.

For every layer, may they be placeholders or design elements, make sure that their `In Point and Starting Point <https://stupeflix-ae-guidelines.readthedocs.org/en/latest/02-01_optim.html#start-end-in-out-points>`_ are exactly the same. If they are not, this will confuse our engine and might give an unexpected result.

Click here for a full list of `Unsupported Features <https://stupeflix-ae-guidelines.readthedocs.org/en/latest/01-07_unsupported.html>`_.

Sneak Preview of the XML Power
------------------------------

Your After Effects Widget will be interacting with our `XML language <https://stupeflix-api.readthedocs.org/en/latest/tutorials/02_stupeflix_xml_langage.html>`_. XML is mainly used as a cement between Widgets: It allows stacking and grouping Widgets amongst other things.

XML is also used to directly modify the behavior of a Widget:

To fill the placeholders with user's data
To define the behavior of user's data inside a graphical placeholder (ken burs, stretch, etc…)
To hide a layer
To change a Solid color / transparency

If you want to know how does it works, we have a whole section about `Mixing After Effects with XML <https://stupeflix-ae-guidelines.readthedocs.org/en/latest/03-02_xml.html>`_.

Exporting
---------

In order for us to convert your After Effects Widget into a Stupeflix Widget, we need you to send us your project. In order to do that efficiently, we need you to follow these easy steps:

- Check that your project is Optimized, properly tagged & keyframed, and fully compatible using our `AE SxC Validation Script <https://stupeflix-ae-guidelines.readthedocs.org/en/latest/01-09_script.html>`_.
- Make sure your main comp is named 'main' and is in the root folder of the project (if not, you'll have a warning, and the script will take care of it during the export process)
- Select your main composition and go to File > Reduce Project.
- Now go to File > Collect Files, select a folder and choose to export all files.
- If you use custom Fonts, include them in the directory created by the Collect Files command.
- Zip the directory.
- Send it to us.

Demo Project
------------

We have made a sample projects for you to see how everything is working out on a simili real-world project:

If you have After Effects CS5 or above, please download this full featured project: `Demo CS5 <http://assets.stupeflix.com.s3.amazonaws.com/help/projects/Demo_CS5.zip>`_

You can preview the result in our XML Editor `here <http://xeditor.stupeflix.com/video/7R8w3QvDYK/>`_ (remix a copy to see the XML code).

In this project, you can customize the front logo, the front text (the left text is linked to the front text), the movie poster on the right and the color of the front pane. For that you will find 2 graphical placeholders and 1 text placeholder. 

The project is a mix of 2D/3D layers spread in several precompositions masked by trackmattes.
