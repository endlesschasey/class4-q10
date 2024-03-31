# 第四课作业

## Question 10: 

实现一个打印图形面积的函数，它接收一个可以计算面积的类型作为参数，比如圆形，三角形，正方形，需要用到泛型和泛型约束

```rust
use std::f64::consts::PI;

// 定义一个 trait 表示可以计算面积
trait Area {
    fn area(&self) -> f64;
}

// 为圆形实现 Area trait
struct Circle {
    radius: f64,
}

impl Area for Circle {
    fn area(&self) -> f64 {
        PI * self.radius * self.radius
    }
}

// 为三角形实现 Area trait
struct Triangle {
    base: f64,
    height: f64,
}

impl Area for Triangle {
    fn area(&self) -> f64 {
        0.5 * self.base * self.height
    }
}

// 为正方形实现 Area trait
struct Square {
    side: f64,
}

impl Area for Square {
    fn area(&self) -> f64 {
        self.side * self.side
    }
}

// 打印图形面积的函数，使用泛型和泛型约束
fn print_area<T: Area>(shape: &T) {
    println!("Area: {}", shape.area());
}

fn main() {
    let circle = Circle { radius: 5.0 };
    let triangle = Triangle {
        base: 3.0,
        height: 4.0,
    };
    let square = Square { side: 2.0 };

    print_area(&circle);
    print_area(&triangle);
    print_area(&square);
}
```


```output
Area: 78.53981633974483
Area: 6
Area: 4
```