NUI - Natural UI
================
**NUI for mobile devices.** NOTE: Just a rapid proof-of-concept so far.

####DEMO: http://codepen.io/mikkokam/pen/Geotz

####USAGE: Check the src/www/index.html - or the Codepen demo.
Load the required js (**Ionic**, then `velocity.js`, `velocity.ui.js` and `Box2dWeb.js`).
After them, load NUI: `nui.ionic.js` and `nui.ionic.box2d.js`.
Add an attribute (`nui-tiltable`, `nui-touchable` or `nui-body`) to some element in your html. That's it.

Documentation coming later.

---------------

####Goals:
* Enable the user to directly manipulate, drag, and throw any UI element,
* using touch and multi-touch with inertia, plus tilting/orienting the device.
* Let elements automatically interact with each others, using natural and intuitive phenomena from physics.
* Make this very easy for anyone to implement in code. No canvas, just plain DOM elements. Declarative, i.e. an element is declared to be tiltable by an HTML attribute > it automatically starts reacting to the device orientation.


---------------

We are testing these principles using [Ionic framework](http://ionicframework.com/). This enables rapid building of web apps and iOS and Android apps.

NUI includes **Angular/Ionic modules** to enable declaring any DOM element to respond to drag and multi-touch, accelerometer input or calculations from a 2D physics engine: gravity, collisions, inertia, friction and several others.

##Natural UI
From CLI to GUI, and now to NUI

CLI is based on remembering the commands.
GUI is symbolic, turns-based.
The user is presented with all the options in a symbolic form, such as a button representing a tool to scale something. The interaction is request - response; a conversation between the user and the device (indirect).
The interface is abstract, the user might be moving a mouse on a table to move a pointer elsewhere to click an icon representing a zoom tool.

So, what about NUI?

Eight Principles of Natural User Interfaces by [Rachel Hinman](http://designprinciplesftw.com/collections/eight-principles-of-natural-user-interfaces):

1. **Performance Aesthetics** - The joy of doing: the pleasure comes from the *flow of the interaction*, not the accomplishment of each task like in traditional GUI.
2. **Direct Manipulation** - Physically touching and manipulating information with fingertips or other direct means, without an aid such as a mouse. 
3. **Scaffolding** - Scaffolding is a strong cue or guide that sets users’ expectations by giving them an indication of how the interaction will unfold.
4. **Contextual Environments** - Responsive to the context, suggesting what the next interaction could be.
5. **The Super Real** - The UI elements not only feel real, but we also perceive them to be *super real* as their character can change in a way that is almost magical.
6. **Social Interaction** - UI should be streamlined, enabling more opportunities for users to engage and interact with other users instead of the system’s interface.
7. **Spatial Relationships** - Represent information as such, as objects - not symbols of the information.
8. **Seamlessness** - Sensors, and the use of gestural UI's enable interactions to feel seamless. There are fewer barriers between the user and information.


###Multi-touch and other inputs

**Abstraction for UI design:**

Input:  one or more touches, x and y (Hammer.js used by Ionic can track many touches simultaneously - take a look at  'touches' under the event when doing a pinch or rotate with many fingers). Accelerometer data. Effect from other elements via collisions, and links such as hinges and springs.

Output: transform a DOM element by any combo of 'translateX', 'translateY', 'translateZ', 'rotateX','rotateY','rotateZ','scale', 'scaleX','scaleY'. Apply multipliers (magnitude and reversing effects) and functions.

Ideally triggers events to chain actions.

###Physics
To make elements behave in a natural way, plain CSS animations and transitions are not enough. A physics engine is needed.

A physics engine calculates the interactions using real properties. Many projects link this with an external renderer to draw the results on a HTML5 canvas element. In this project, we intend to test linking the engine with plain DOM elements, to better utilize frameworks like Angular and Ionic.

####Engine
Testing the old Box2 ([Box2dWeb](https://code.google.com/p/box2dweb/wiki/BasicUsage)) currently, but might be wise to switch to [LiquidFun](http://google.github.io/liquidfun/) or something completely different (native js or even 3d).

LiquidFun enables particles, liquids and elastic bodies while maintaining compatibility with Box2D. To replace Box2dWeb with LiquidFun will not be a big task.
