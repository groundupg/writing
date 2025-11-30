# A Theory of Shapes

1. A Point is an X, Y coordinate.
2. A Shape is an ordered collection of Points.
2.1. A Line is an ordered collection of 2 points.
2.2. A Triangle is an ordered collection of 3 points.
2.3. A Quadrilateral is an ordered collection of 4 points.
2.4. A Pentagon is an ordered collection of 5 points.
.....

3. A Shape can be *drawn* through drawing a straight line from each point to the next, starting
at the first item and ending with the last item drawning a line to the first item.

```go
type Point [2]Number
type Line [2]Point
type Triangle [3]Point
type Quad [4]Point
type Shape []Point
```

## Constructing Shapes

```go
// The order matters, imagine a graph where you are drawing a square from one point to the next.
func ConstructQuad(x0, y0, x1, y1 Number) Quad {
  return [[x0, y0], [x1, y0], [x1, y1], [x0, y1]]
}

func ConstructTriangle(x0, y0, x1, y1 Number) Triangle {
  return [[x0, y0], [x1, y1], [x0, y1]]
}
```

A Circle, too, can be represented as a collection of points.
A circle may be constructed through a procedure which takes a `Line` as it's input, where
the line represents the circle's radius -- l[0] as the center and l[0] as an outer point.

```go
// Length of the radius of a given circle given a center & outer point
func Radius(c, x Point) Number {
  return Sqrt((x[0]-c[0])^2 + (x[1]-c[1])^2)
}
func ConstructCircle(l Line) Shape {
  c, x := l[0], l[1]
  r := Radius(c, x)
}
```

### 30.11.25

The points of a circle can be represented as the set of all (x, y) where r^2 = (x-h)^2 + (y-k)^2,
where h, k represent the coordinates of the center of the circle.

The question still stands however -- How can we produce all of the coordinates of a circle given
A line which represents the radius of the circle.
We can:
  1. Determine r
  2. Determine h, k (the point of (h, k) can be called c)

How do we build an algorithm which will produce a collection of (x, y) which satisfy the formula
presented above.

If one were to take a sheet of paper and place a center point, one can then draw a square around
the point, where the point is the center of the square. Continue this, Shifting the position of
the square each time, until the points of the square satify the appearance of a circle.

Is it possible that we, given an x or y, may check if the equation referenced above is valid,
and that on each iteration we may increment or decrement the given x or y.

```go
func Radius(c, x Point) Number {
  return Sqrt((x[0]-c[0])^2 + (x[1]-c[1])^2)
}

func Point(c, r, x) Point | None {
  
    
}
``` 
