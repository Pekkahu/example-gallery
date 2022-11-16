# example-gallery
```python
from manim import *

class My_scenes(Scene):
    
    def construct(self):
        # A instance of mobject is created
        axes = Axes( 
            # by default manim does'nt gives numbers on axis 
            # if axis_config is not included manim will still make divisions for X and Y range 
            axis_config={'include_numbers': True, 'numbers_to_exclude': [0]},
            # these first number in list says where to start
            # second number in list says where it should'nt reach 
            # and third number in list says by what value it should step(default value is one)
            x_range=[-8, 9, ], 
            y_range=[-6, 7, ], 
            # decides what lenght or space it takes in scene
            x_length=8, 
            y_length=8,
            # colors for axis
            x_axis_config={'color': ORANGE}, 
            y_axis_config={'color': ORANGE}, 
        ) 
        # .get_axis_labels(), is a method which gives name to range and domain of the graph 
        axes_label = axes.get_axis_labels(x_label='x', y_label='f(x)')
        # plots the function f(x), x , from where to which point, and color of the curve 
        # piecevise function can not be ploted by .plot()methode instead use .plot_implicit_curve() for ploting such functions.
        # plot is only used for curvy function
        graph = axes.plot(lambda x: 5*np.e ** (-x**2/2), x_range=[-5, 5], color=YELLOW) 
        # .get_graph_label() 
        # Creates a properly positioned label for the passed graph, with an optional dot.
        """Parameters
        ----------
        graph
            The curve.
        label
            The label for the function's curve. Defaults to :class:`~.MathTex` for ``str`` and ``float`` inputs.
        x_val
            The x_value along the curve that positions the label.
        direction
            The cartesian position, relative to the curve that the label will be at --> ``LEFT``, ``RIGHT``.
        buff
            The distance between the curve and the label.
        color
            The color of the label. Defaults to the color of the curve.
        dot
            Whether to add a dot at the point on the graph.
        dot_config
            Additional parameters to be passed to :class:`~.Dot`."""
        graph_label = axes.get_graph_label(graph, label='e^{-x^2}', color=YELLOW, x_val=1,dot=False) 
        # adds mobject in the scene
        self.add(axes, graph, graph_label, axes_label) 
```

> output

![My_scenes_ManimCE_v0 16 0 post0](https://user-images.githubusercontent.com/96633728/202218955-36dc5f48-bc9e-4f39-ab4b-7c6aca2be678.png)

