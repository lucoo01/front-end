##  在TypeScript支持静态类吗？

是的，TypeScript支持静态类。

在TypeScript中，可以使用`static`关键字来定义静态属性和静态方法。静态属性和静态方法属于类本身，而不属于类的实例。这意味着静态属性和静态方法可以通过类名直接访问，而不需要创建类的实例。

静态类在TypeScript中有很多用途，例如：

* 定义工具类：工具类通常包含一些通用的方法，这些方法不需要创建类的实例就可以使用。例如，可以使用静态类来定义一个数学工具类，该工具类包含一些数学运算方法。
* 定义单例模式：单例模式是一种设计模式，它确保只有一个类的实例存在。可以使用静态类来定义单例模式，因为静态类只能创建一个实例。
* 定义命名空间：命名空间可以用来组织代码。可以使用静态类来定义命名空间，因为静态类可以包含多个属性和方法。

以下是使用静态类的一个示例：

```typescript
class MathUtils {

  static add(a: number, b: number): number {
    return a + b;
  }

  static subtract(a: number, b: number): number {
    return a - b;
  }

}

const sum = MathUtils.add(1, 2); // 3
const difference = MathUtils.subtract(4, 2); // 2
```

在这个示例中，`MathUtils`是一个静态类。它包含两个静态方法：`add()`和`subtract()`。这两个方法可以直接通过类名来调用，而不需要创建`MathUtils`类的实例。

TypeScript支持静态类的原因如下：

* 静态类可以提高代码的简洁性。
* 静态类可以提高代码的性能。
* 静态类可以提高代码的可维护性。

因此，在TypeScript中可以使用静态类来提高代码的开发效率和质量。