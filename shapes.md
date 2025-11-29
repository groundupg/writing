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
func Radius(c, x) Number {
  return Sqrt((x[0]-c[0])^2 + (x[1]-c[1])^2)
}


func ConstructCircle(l Line) Shape {
  c, x := l[0], l[1]
  r := Radius(c, x)
  
}
```
