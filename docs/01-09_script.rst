
Using the SxC Validation Script
===============================

In order to help you make sure that your project is compatible with our engine, we've built an After Effects Script that will scan your project and report any error it encounters. it's name is: SxC Validator; SxC stands for *S*tupefli*X* *C*reative*.

Script Basics
-------------

Current version is 2.2 (Released April 16th 2013).

You can download it here for CS5 and above: `Sxc Validation Script <http://assets.stupeflix.com.s3.amazonaws.com/help/projects/SxC_Validator_v2.2.zip>`_

To check if your project is good to go, open it in After Effects and then:

- File > Script > Run Script File (swith the dropdown from *.jsx to *.jsxbin)
- Select the script
- Select, in the Project panel, your widget main composition
- Clic on “Project Analysis”.

The script now reports several key project information right inside it's UI: The number of compositions (plus the number of time they are used) and same goes for your layers and your placeholders. It also gives you your project depth, the highest layer stack and the number of errors/warnings it found.

If the script finds anything that is not complient with our workflow, or anything that could impact visualy the final look once it's in our system, it will generate a text log, with links to this documentation for each problem it found.

On top of these details, the script will give you an estimation of the Render Speed of the project on our render engine.

I highly recommand you to run it regularly while you are developing your widget to make sure you take the appropriate steps. Discovering at the end that you went the wrong way is always depressing and irritating.

WARNING
^^^^^^^

The script is just a tool built to help you investigate, find and correct the issues your project might have. Because of some scripting limitations, it cannot scan everything and thus, report everything. If your project scan is successfull, it means that there is a very high probability that it will be compatible with our system without further modification.

When receiving your AE projects, we will review them and will report you back asap if we find anything problematic that was not raised by the script.

Please note that the script covers around 95% of what we support, and whenever I find a situation that can be added to it, I'll update it. Be sure to come back regularly for new updated versions.

Scoring System
--------------

Starting with the version 2.0 of the script, we introduced a “scoring” system built to help you estimate how fast and how light your project will be when turned into a Stupeflix Widget.

In the text log header, you'll see a “Score” line looking like this:

::

	Score: 0.59 (average per layer)

It's a score based on the comps & layers, the depth, the effects and everything you put in your project. We assigned a default score to every items, depending on how they perform or impact our rendering engine. We also take into consideration the complexity of your project for any given frame, and weight the score on it too.

The score found in the header as described above is your project total score, frame by frame divided by the total length of your Widget giving you an estimate of how time consuming it is. Here are the performences you can expect depending on your score.

As your project complexity can vary during time, we added a temporal complexity table, looking like this:

::

	Time Stamp: 		| 0		| 10	| 20	| 30	| 40	| 50	| 60	| 70	| 80	| 90	| 
	Layer Stack: 		| 12	| 12	| 12	| 12	| 12	| 12	| 12	| 12	| 12	| 12	| 
	Project Score: 		| 1		| 1		| 1		| 1		| 1		| 1		| 1		| 1		| 1		| 1		| 
	Death Combo: 		| No 	| No 	| No 	| No 	| No 	| No 	| No 	| No 	| No 	| No 	| 

The first line, **Time Stamp** is the frame number. We display show 10 frames, every 1/10 length of your project.
The second line, **Layer Stack** is the height of the layer stack at that Time Stamp.
The third line, **Project Score** is the complexity score of the project at this Time Stamp. The lower, the better.
The last line, **Death Combo** is if what we call a *Death Combo* have been found at that Time Stamp.

Death Combo
^^^^^^^^^^^

Some things are time consuming in our engine, and when combined with other things, it can become really ugly.

We have identified 3 Death Combo, and here they are:

- Stack Death Combo: Staking more than 15 layers reduce rendering performance
- Placeholder Death Combo: showing too many user assets at the same time reduce rendering performance too
- trackmatte Death Combo: Nesting trakmattes, or having simultaneous trackmattes crush rendering performance. You really wanna avoid that.


Estimated Render Time
---------------------

To give you an idea of how fast your project will render, we have captioned the score into 11 stages. And this time, you don't want to go up to 11.

- **ERS: Fastest**: Your project will be rendered faster than realtime. This is the best.
- **ERS: Very Fast**: Your project will be render slightly faster than realtime.
- **ERS: Fast**: Your project will be rendering more or less at realtime. That's the usual target.
- **ERS: Not so Fast**: Your project will be rendering in less than two time the realtime. Usually preview (half framerate) will be realtime.
- **ERS: Mediocre**: Your project is quite heavy and will take more than two times the realtime to render.
- **ERS: Sluggish**": Your project is heavy and will take around three times the realtime to render.
- **ERS: Slow**: Your project is really heavy and will take around four times the realtime to render.
- **ERS: Very Slow**: Your project is too complicated and will take around five times the realtime to render.
- **ERS: Ultra Slow**: Your project will take too long to render for our engine. We won't accept it.
- **ERS: Killing Slow**: Your project will take too long to render for our engine. We won't accept it.
- **ERS: Deadly Slow**: Your project won't be able to render on our engine. We won't accept it.


A grain of Salt
^^^^^^^^^^^^^^^

This scoring system is far from being bullet-proof, and your project might be faster or slower to render than what we actually expect. But from the test we've had in house with a large variety of projects, we are confident enough to make it available for you.

Also, for each composition in the text log generated by the script, you'll have a score line looking like this:

::

	SCORE : 3.1 (total comp layer score)

This is the total score of your comp, which is just a sum of all it's layer scores. With this info you can see what compositions are render intensive and try to optimize them for better performance.
