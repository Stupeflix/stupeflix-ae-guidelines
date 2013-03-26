
Creating a Transition Widgets
=============================

A transition widget is created like any other After Effects project, but the way it's used in our engine requires some extra carefullness and involves some extra work.

Transition Widgets have 2 graphical placeholders:

- One for the input video
- One for the output video

Transitions are always inserted between two Widgets elements, and when our render engine stumble upon one, this is what he does:

- It renders the Widget before the transition
- It renders the Widget after the transition
- It then fill the transition with the rendered Widgets videos

What does this means , it first means that your placeholder will get a rendered version of the in and out Widgets, so transition can't change anything in them. it also means that in order to be seamless, the In placeholder must start fullscreen, and the Out placeholder must finish fullscreen.

It's not easy to explain the behavior with words (and then, not easy to have a clear mind about it when reading this), but if you try the good, the bad, and the ugly transition projects, you'll see in context what it does. You can download the CS5.5 After Effects projects to check how these were done.

