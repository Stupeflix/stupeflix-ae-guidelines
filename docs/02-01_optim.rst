
Optimizing your Project
=======================

Naming Convention
-----------------

We need your layers to avoid special characters in their name to be properly used within an XML context (changing layer color, hiding a layer….).

Please, only use [a-z][A-Z][0-9] along with “_” in your layer names.

Pre-Rendering
-------------

Proxies and pre-rendering are really usefull when you have a bunch of layers with motion blur and effects that are not supported by our engine. They can also be used to reduce the amount of layers and effects to be processed by our engine, resulting in faster rendering times.

You can render your proxies and/or pre-renders in any file format we support. You can find a summary on our Supported File page.

Don't forget that you can also render semi-transparent animated footage, very usefull to add, for exemple, a layer of dust and scratches to simulate old film footage !

You can also use pre-rendered video in black and white to be used as a Luma or Luma Inverted track matte, especially if your track matte is a crowded composition with a lot of animations and effects such as blurs.

Pre-rendering a single image is quite straight forward: JPEG if it has no transparency, PNG otherwise.

Pre-rendering an animation is slightly more complicated as you have to keep the filesize low, and the compression low too, to keep a top quality level to avoid to much artifacting when it will be reencoded for the final user.

Start/End - In/Out Points
-------------------------

In After Effects, each layer have 2 starting points and 2 ending points. By default, they are the same, but sometimes you might need to change them, and they'll become out of sync. If that's not a problem for the ending / out point, our engine will struggle if the Starting / In point are different. But what are those points ?

Starting and Ending points are where the layer starts and end. 
In and Out points are where the layer is active.

The difference is subtle, here is an exemple: let's say you have a 5 seconds precomposition but want it to be trimed down to 3 seconds in your main comp. Either you'll shorten the precompo to 3 seconds by opening it and changing it's duration in the composition setting panel, or you'll just trim it down in the main composition view by dragging the end of the layer with your mouse or your Wacom pen. In that case, the Ending point will still be at 5 second, but the Out point will be at 3 second.

It is mendatory that both Start and In point remains in sync. So if you need a layer to start at the 2 second mark in your timeline, don't trim it's head, move the whole layer to it. Same if you need your layer to start a bit before it's actual position, don't expend it from it's head, move it entirely. Be sure to move your keyframes accordingly.

Assets Size
-----------

As you may have read in our Unsupported Features page, we don't allow graphical assets larger than 4096 pixel in width and/or 4096 pixel in height. That is also true for your composition sizes.

This limatation is due to graphic card memory and Open GL drivers to ensure best performances.

Still, 4096×4096 assets requires a lot of ressources and we recommand you, to keep your project as fast as possible, to limit your assets size to 2048×2048.

Also, the smaller the assets file size, the faster it's processed, thus the faster the video is rendered. If you need transparency in your file, use PNG, if not use JPEG.

Output that Matters
-------------------

We are now all used to work in native HD, may it be 720p or 1080p, and output at several range of resolutions, from SD for mobile devices and DVD to HD for broadcast and BluRay.

When creating a project for Stupeflix, you have to keep in mind that we are not rendering it once, we are rendering it everytime a customer calls it. So using oversized assets will slow down render time every time your assets is called.

The best practice is to create the AE project at the correct resolution to avoid as much as possible realtime downsizing during rendering.

For a client, we managed to divide by a factor of 2 the render time of their widget simply by reducing assets size, because they designed their project and rendered their assets in 1080p while they delivered to their customer through Stupeflix only 360p videos at best. This rendertime gain was only by reducing file sizes through assets resolution reduction.

To put it simple, if you are targetting to deliver 360p or 540p files to your customers through Stupeflix, the best practice is to deliver us AE projects in 360p or 540p.

If you plan to deliver multiple resolutions, you can either provide us a project at the highest resolution, or several projects to cover several resolutions.

Please note that just nesting your high resolution comp into a small definition comp inside AE is not the way to go because you don't scale down your original assets, and you are indeed adding 1 level of depth thus slowing down the whole rendering process.

Depth and Matte
---------------

The most render time intensive elements in an After Effects project are depth of the composition nesting, and the trackmattes. And the more you nest both, the bigger the render hit.

Matting a precomp is something sometimes you can't avoid, but matting a precomp which already have matting inside will be killing the render time. If on top of that your precomps are exceeding the recommanded max size of 2048×2048 it will get ugly.

So beware of nested matting and try to avoid depth bigger than 3.

