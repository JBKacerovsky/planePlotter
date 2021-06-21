# planePlotter
 
## PLANE PLOTTER - draws a plane defined by a point and normal vector
the plane will be drawn as a square of specified range centred around 'point'
!!!! Acknowledgement: !!!!!!!!!!!!
this is an implementation of a method [described](https://www.mathworks.com/matlabcentral/answers/291485-how-can-i-plot-a-3d-plane-knowing-its-center-point-coordinates-and-its-normal#answer_226405) by Roger Stafford on the MATLAB answers forum.

The actual method is taken straight from the forum, I simply added some input features etc. to make it universal and more convenient to use by organizing the input structure

### Syntax: 
```
p = planePlotter(point, normal)
p = planePlotter(point, normal, ...)
P = planePlotter(point, normal)
planePlotter(point, normal, ...)
```

### INPUTS: 
```
  point - xyz coordinates (1x3 or 3x1) of a point in the plane 
  normal - normal vector to the plane (1x3 or 3x1)
```
### OPTIONAL INPUTS:
optional inputs can be specified as Name-Value pairs to give additional
graphics choices
```
    'range': scalar; defines the range of the plane that will be graphed
    (size of the square); default=1 resulting in a 2x2 square
    'gridlines': scalar, defines how many grid-lines will be drawn on the plane; 
      default=1 -> no lines; 2 -> edges drawn; 3 -> edges plus 4 squares; etc
    'FaceColor': string, RGB triplet or hexidecimal string; default='green'
    'FaceAlpha': scalar; default=0.3
    'EdgeColor': string, RGB triplet or hexidecimal string; default='black'
    OUTPUT:
    for simple drawing, the output does not have to be defined
    defining the output p saves the graphics element to allow later editing
```
#### Example 1:
```
    % plane at 45º angle through origin
    % specifying only point and normal vector leaves optional inputs as
    % default resulting in a green plane with no lines:
    point=[0 0 0];
    vector=[1 1 1];
    planePlotter(point, vector);
    axis equal
    % we can add the point and vector to this as illustrations:
    hold on
    scatter3(point(1), point(2), point(3),  500, '+', 'LineWidth', 2);
    quiver3(point(1), point(2), point(3), vector(1), vector(2), vector(3), 'Color', 'r', 'MaxHeadSize', 1, 'LineWidth', 2);
    view(2);
```
#### Example 2:      
   ```
 % drawing the same plane with a range of 5 (resulting in a 10x10 square)
    % with gridlines drawing 1x1 grid squares (11 gridlines including 0 and 10)
    % with teal faces and magenta edges
    p=planePlotter([0 0 0], [1 1 1], 'range', 5, 'gridlines', 11, 'FaceColor', [0, 1, 1], 'EdgeColor', '#FF00FF');
    axis equal
    % specifying the graphics output (p) allows us to change individual graphics settings afterwards
    p.FaceAlpha=0.8;
    p.FaceColor='blue';
    p.EdgeColor='r';
    p.LineWidth=3;
    p.LineStyle=':';
```