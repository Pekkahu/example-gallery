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

```python
from manim import *

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
        # .get_vertical_lines_to_graph(function, x_range=[start, end point], num_lines=how many lines in between them, color)
        vertical_lines = axes.get_vertical_lines_to_graph(
            graph, x_range=[-1, 1], num_lines=10, color=BLUE
        )
        self.add(axes, graph, graph_label, axes_label, vertical_lines)
        
```
### output
![My_scenes_ManimCE_v0 16 0 post0](https://user-images.githubusercontent.com/96633728/202268598-ce06444a-ed6b-40dc-a056-d89962cf9864.png)

```python
from manim import *

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
        # riemann rectangle approximation or integration
        #.get_riemann_rectangles()takes few arguments
        # first the graph which is ploted
        # second start and end point
        # width of the rectangle
        # color of rectangle 
        rectangles = axes.get_riemann_rectangles(
            graph, x_range=[-9, 9], dx=0.15, color=RED
        )
        self.add(axes, graph, graph_label, axes_label, rectangles)
```
### output

![My_scenes_ManimCE_v0 16 0 post0](https://user-images.githubusercontent.com/96633728/202288635-8dc1c779-8c03-479c-86c4-d0b9ad3d606a.png)

```python
from manim import *

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
        rectangles = axes.get_riemann_rectangles(
            graph, x_range=[-9, 9], dx=0.60, color=RED
        )
        self.add(axes, graph, graph_label, axes_label, rectangles)
```

### output

![My_scenes_ManimCE_v0 16 0 post0](https://user-images.githubusercontent.com/96633728/202288951-2a7c2cc6-3355-4276-ae97-d88445d87ca5.png)


```python
class LabelForDomain&Range(Scene):

    def construct(self):
        axes = Axes(
            axis_config={'include_numbers': True, 'numbers_to_exclude': [0]},
            x_range=[0, 11, ], 
            y_range=[0, 11, ], 
            x_length=7, 
            y_length=7,
            x_axis_config={'color': WHITE}, 
            y_axis_config={'color': WHITE}, 
        ) 
        axes_label_for_x = axes.get_x_axis_label('time')
        # adds a labels for Domain
        axes_label_for_y = axes.get_y_axis_label('distance')
        # adds a labels for Range
        self.add(axes, axes_label_for_x, axes_label_for_y)
```

### output

![My_Second_Scene_ManimCE_v0 16 0 post0](https://user-images.githubusercontent.com/96633728/202272197-f29215dd-e1fb-4251-9f8f-b2a7d0748dc6.png)

> by default they are aligned at the tip of the graph we can align them by adding few more arrugments into the function

```python
class My_Second_Scene(Scene):

    def construct(self):
        axes = Axes(
            axis_config={'include_numbers': True, 'numbers_to_exclude': [0]},
            x_range=[0, 11, ], 
            y_range=[0, 11, ], 
            x_length=8, 
            y_length=5.5,
            x_axis_config={'color': WHITE}, 
            y_axis_config={'color': WHITE}, 
        ) 
        # use these as template don't go deep in these it will work everywhere you want
        axes_label_for_x = axes.get_x_axis_label('time', edge = DOWN, direction= DOWN, buff = 0.7)
        axes_label_for_y = axes.get_y_axis_label('distance', edge = LEFT, direction = LEFT, buff = 0.01).rotate(90 * DEGREES)
        self.add(axes, axes_label_for_x, axes_label_for_y)
```

### output

![My_Second_Scene_ManimCE_v0 16 0 post0](https://user-images.githubusercontent.com/96633728/202275944-b707488b-1b03-44ee-bf8d-5437f084e37c.png)

```python
class My_Second_Scene(Scene):

    def construct(self):
        axes = Axes(
            axis_config={'include_numbers': True, 'numbers_to_exclude': [0]},
            x_range=[0, 11, ], 
            y_range=[0, 11, ], 
            x_length=8, 
            y_length=5.5,
            x_axis_config={'color': WHITE}, 
            y_axis_config={'color': WHITE}, 
        ) 
        graph = axes.plot(lambda x: x/2, x_range=[0, 9], color=BLUE)
        # same way as before it does'nt gives an Mobject but only the cordinates
        # but it is easier then previous methode for specially for graphs because the y value is calculated by the program.
        at_8point = axes.input_to_graph_point(8, graph)
        # created a Mobject to display the position
        dot = Dot(at_8point)
        self.add(axes, graph, dot)
```

### output

![My_Second_Scene_ManimCE_v0 16 0 post0](https://user-images.githubusercontent.com/96633728/202278723-5c7428e2-7c33-4801-b439-359fcde7284a.png)

```python
class My_Second_Scene(Scene):

    def construct(self):
        axes = Axes(
            axis_config={'include_numbers': True, 'numbers_to_exclude': [0]},
            x_range=[-10, 11, ], 
            y_range=[-4, 5], 
            x_length=13, 
            y_length=7,
            x_axis_config={'color': WHITE}, 
            y_axis_config={'color': WHITE}, 
        ) 
        graph = axes.plot(lambda x : np.sin(x), x_range = [-9, 9], color=YELLOW)
        # graphs derivative of a function
        graph2 = axes.plot_derivative_graph(graph, color=RED)
        self.add(axes, graph, graph2)
```

### output

![My_Second_Scene_ManimCE_v0 16 0 post0](https://user-images.githubusercontent.com/96633728/202281475-59bcb4f9-6f61-41ea-b861-74041e43f978.png)

```python
class My_Second_Scene(Scene):

    def construct(self):
        axes = Axes(
            axis_config={'include_numbers': True, 'numbers_to_exclude': [0]},
            x_range=[-10, 11, ], 
            y_range=[-4, 5], 
            x_length=13, 
            y_length=7,
            x_axis_config={'color': WHITE}, 
            y_axis_config={'color': WHITE}, 
        ) 
        graph = axes.plot(lambda x : np.sin(x), x_range = [-9, 9], color=YELLOW)
        # graphs integral of a function it does'nt draws the area under curve
        graph2 = axes.plot_antiderivative_graph(graph, color=RED)
        self.add(axes, graph, graph2)
```

### output

![My_Second_Scene_ManimCE_v0 16 0 post0](https://user-images.githubusercontent.com/96633728/202282270-7c56e1aa-6d71-47fd-8f75-bb7ec6a21a2f.png)

```python
class Example(Scene):
        def construct(self):
            # NumberPlane() 
            axes1 = NumberPlane(
                # these first number in list says where to start
                # second number in list says where it should'nt reach 
                # and third number in list says by what value it should step(default value is one)
                x_range=[-10, 11], 
                y_range=[-4, 5], 
                # decides what lenght or space it takes in scene
                x_length=13, 
                y_length=7,
                # colors the main axis of the graph or domain and range line.
                x_axis_config={'color': WHITE}, 
                y_axis_config={'color': WHITE}, 
                background_line_style ={
                    # grid line color
                    "stroke_color": BLUE_D,
                    # width of the grid 
                    "stroke_width": 1,
                    # opacity of grid from 0 to 1 (floating value)
                    "stroke_opacity": 1
                }
            )
            axes = Axes(
            axis_config={'include_numbers': True, 'numbers_to_exclude': [0]},
            x_range=[-10, 11], 
            y_range=[-4, 5], 
            x_length=13, 
            y_length=7,
            x_axis_config={'color': WHITE}, 
            y_axis_config={'color': WHITE}, 
            ) 
            graph = axes.plot(lambda x : np.sin(x), x_range = [-9, 9], color=YELLOW)
            # graphs integral of a function it does'nt draws the area under curve
            graph2 = axes.plot_antiderivative_graph(graph, color=RED)
            self.add(axes, graph, graph2, axes1)
```

### output

![Example_ManimCE_v0 16 0 post0](https://user-images.githubusercontent.com/96633728/202518366-3bf588cb-7c18-423c-bcf1-5311630d77b4.png)

```python
class Example(Scene):
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

        self.add(axes, graph, axes_label, dot, line)
        self.play(ApplyWave(graph_label))
        self.wait()
        self.play(ApplyWave(axes_label))
```
### output 

![Example (2)](https://user-images.githubusercontent.com/96633728/202887362-e258b402-9e88-46bd-9c68-477f2f068bc9.gif)


```python
class Example(Scene):
    def construct(self):
        hi = Tex("deafult").scale(6)
        self.play(ApplyWave(hi))
```

### output

![Example](https://user-images.githubusercontent.com/96633728/202886987-4a137d78-99b1-45e0-8cc0-159669a6d418.gif)


```python
class Example(Scene):
    def construct(self):
        hi = Tex("deafult").scale(6)
        # Circumscribe function does'nt add text or Mobject by default it should be added manually before self.play...
        self.add(hi)
        # Circumscribe() adds a animating square around an mobject 
        # first parameter name of the varaible Mobject which is been animated by default manim will be create a rectangle around the Mobject if the shape is not mentioned
        # second shape can either Rectangle(default) or Circle.
        #  buff decides how much space will be there from the border of the Mobject to the Animation.
        self.play(Circumscribe(hi, buff = 1))
```
> if we can add more parameters we can have more funcationality from these <br>
> color – The color of the surrounding shape. <br>
> run_time – The duration of the entire animation. <br>
> fade_in – Whether to make the surrounding shape to fade in. It will be drawn otherwise. <br>
> fade_out – Whether to make the surrounding shape to fade out. It will be undrawn otherwise.

### output

![Example](https://user-images.githubusercontent.com/96633728/203888406-77d2a113-5d22-4070-8c10-726821e69c2a.gif)


```python
class Example(Scene):
    def construct(self):
        hi = Tex("deafult").scale(6)
        a = NumberPlane()
        # NumberPlane is added to properly give height and width for flash animation 
        rectangle = Rectangle(height = 4.05, width = 10.69)
        self.add(hi)
        self.add(rectangle, a )
        self.play(Circumscribe(hi, buff = 1, run_time=2))
```

### output

![Example (1)](https://user-images.githubusercontent.com/96633728/203891168-1f2bdd48-cb12-496e-8ecf-65eff0369d16.gif)

```python
class Example(Scene):
    def construct(self):
        hi = Tex("deafult").scale(4)
        radius = 3
        d = Circle(radius = 3)
        self.add(hi)
        self.play(Circumscribe(hi, Circle, buff = 0.01, run_time=2))
        self.play(Flash(d, 
            #lenght of the flash line 
            line_length=1,
            # number of flashes
            num_lines=30, 
            color=RED,
            # flash_radius – The distance from point at which the flash lines start.
            # factor + buff 
            flash_radius=radius+SMALL_BUFF,
            time_width=0.3, run_time=2,
            # increase the aniation speed but not the run time
            rate_func = rush_from
            ))
```
### output

![Example (2)](https://user-images.githubusercontent.com/96633728/203910885-e716282d-a20a-4e9d-9515-e54f214e9ccf.gif)

> flash() function only works on points soo even giving a rectangle will not give a flash from sides it will be from center of rectangle therefore avoid rectangles and only use Circle for flash animation

```python
class Example(Scene):
    def construct(self):
        c = Dot()
        self.add(c)
        self.play(FocusOn(c))
```
> focus only takes a point and if a Mobject is based it takes its center to focus and wave is by deafault a circle and cannot be changed

### output

![Example (3)](https://user-images.githubusercontent.com/96633728/203912438-12ee65f7-37b0-4727-be15-515d2c18f35a.gif)


<a>https://docs.manim.community/en/stable/reference/manim.mobject.graphing.coordinate_systems.CoordinateSystem.html#manim.mobject.graphing.coordinate_systems.CoordinateSystem.add_coordinates</a>

> for logic read these 
<a>https://docs.manim.community/en/stable/tutorials/building_blocks.html</a>


