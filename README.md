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

```python
class GetAreaExample(Scene):
    
    def construct(self):
        axes = Axes( 
            axis_config={'include_numbers': True, 'numbers_to_exclude': [0]},
            x_range=[-8, 9, ], 
            y_range=[-6, 7, ], 
            x_length=8, 
            y_length=8,
            x_axis_config={'color': ORANGE}, 
            y_axis_config={'color': ORANGE}, 
        ) 
        axes_label = axes.get_axis_labels(x_label='x', y_label='f(x)')
        graph = axes.plot(lambda x: 5*np.e ** (-x**2/2), x_range=[-5, 5], color=YELLOW) 
        graph_label = axes.get_graph_label(graph, label='e^{-x^2}', color=YELLOW, x_val=1,dot=False) 
        # .get_area() takes the area covered by the curve or fuction from one point on x to another point of x 
        # these creates a mobject within the region which can have properties and animation based on the use 
        area = axes.get_area(
                        graph,
                        x_range=(-5, 5),
                        color=(YELLOW),
                        opacity=0.20,
                    )
        self.add(axes, graph, graph_label, axes_label, area)
```

### output
![GetAreaExample_ManimCE_v0 16 0 post0](https://user-images.githubusercontent.com/96633728/202234545-a2851a5b-c5e1-4647-a732-972eda9fe611.png)

```python
class My_scenes(Scene):
    
    def construct(self):
        axes = Axes( 
            
            axis_config={'include_numbers': True, 'numbers_to_exclude': [0]},

            x_range=[-8, 9, ], 
            y_range=[-6, 7, ], 
            x_length=8, 
            y_length=8,
            
            x_axis_config={'color': ORANGE}, 
            y_axis_config={'color': ORANGE}, 
        ) 
    
        axes_label = axes.get_axis_labels(x_label='x', y_label='f(x)')
        
        graph = axes.plot(lambda x: 5*np.e ** (-x**2/2), x_range=[-5, 5], color=YELLOW) 
        
        graph_label = axes.get_graph_label(graph, label='e^{-x^2}', color=YELLOW, x_val=1,dot=False) 
        # .coords_to_point() is method of axes Mobject which defines a point in axes plane.
        point = axes.coords_to_point(1, np.e**((-1)**2))
        # these methods does'nt output any mobject just stores cordinate 
        dot = Dot(point)
        # here we have created a Mobject Dot which takes two arrugments x and y
        # has 'point' stores the cordinates x and y hence we can use it to creat a vertical line 
        # because we can do it directly by 'Dot' but .get_vertical_line() does'nt accept Dot as arrugment it only 
        # takes coordinates of point in the graph or the Instance of graph is nesscarry 
        # which we have used in point varaible      
        line = axes.get_vertical_line(point)
        # makes a line from x axis to the given point
        # defaulty it creats a dotted line
        self.add(axes, graph, graph_label, axes_label, dot, line)
```

### output

![My_scenes_ManimCE_v0 16 0 post0](https://user-images.githubusercontent.com/96633728/202244463-4186a9c4-be90-4029-a5bd-06808d3c87cd.png)

