Further Optimizations
=====================

This section highlight some of the optimizations that are automaticaly suggested by our validation script based on your project analysis.

Merging Mattes
--------------

The script detected that you have several stacked mattes. This is going to severly impact the rendering time on our servers.
One way to limit the overhead, is to create a video with an alpha channel on top of your assets, merging your background asset and your alpha mattes. That way the resulting alpha channel of the video will act as your cut out for your assets.

Nested Scale
------------

We detected that some of your nested compositions are way bigger than their parent composition (ex: having a full HD comp nested in an SD comp). If you used nesting as a way of scaling the pre composition down, this won't make the rendering faster as we'll still need to process the full resolution. You should really try to lower the nested composition resolution as much as you can to improve rendering performance.

Duration Trim
-------------

We detected that some of your video assets are longer than the main composition. This affects performance because the bigger the file assets are, the longer they take to process.

File Size
---------

We detected that your project is somehow heavy weigthed for its duration. You might want to reduce the file count or the assets bitrate. Bigger the file size are, the longer it takes our servers to process or to import. Big files can take some times even when they are streamed from one AMZ bucket to our. If render speed performance is key to your workflow, you might want to investigate this issue. 

Video Stacks
------------

We detected that you have 3 or more video stacked at some point in your widget. Decompressing and playing back several video streams at the same time can heavily slow down the rendering. You might want to merge them to lower the stream count. Remember that you can also render videos with an alpha channel using the On2VP codec in an FLV container.
