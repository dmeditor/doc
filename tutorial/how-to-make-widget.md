How to make a widget
======

A widget can be simple like a button, or complex like intractive form. 

Basically a widget can be treated as a React component with customize settings. We provide some setting component(eg. color) so the developer only need some configuration and the setting will be there.

A typical widget need below information

1. A definition file, which defines widget's name, type, icons, etc
2. An entity, which define data model of this widget
3. A main render which is a react component rendering the widget's data
4. Settings configuration and/or setting component which render in setting panel and make intraction with the main render.

Then you need to register your widget into dmeditor.

Register widget folder
----
