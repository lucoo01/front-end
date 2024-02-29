# 在vue3中setup是如何获得组件实例的？
在 Vue 3 中，setup 函数不再像 Vue 2 中那样提供 this 对象，因此无法直接通过 this 来获取组件实例。

要获取组件实例，可以使用以下两种方法：

**1. 使用 `getCurrentInstance` 函数**

`getCurrentInstance` 函数是 Vue 3 提供的一个 API，用于获取当前组件实例。

```js
import { getCurrentInstance } from 'vue'

export default {
  setup() {
    const instance = getCurrentInstance()
    // 现在可以访问组件实例的所有属性和方法
    console.log(instance.props)
    console.log(instance.emit)
  }
}
```

**2. 使用 `ref` 来获取组件实例**

使用 `ref` 来获取组件实例，需要将组件实例赋值给一个 `ref` 变量，然后可以通过 `ref.current` 来获取组件实例。

```js
export default {
  setup() {
    const instanceRef = ref()

    onMounted(() => {
      // 在组件挂载完成后，将组件实例赋值给 ref 变量
      instanceRef.current = this
    })

    // 现在可以访问组件实例的所有属性和方法
    console.log(instanceRef.current.props)
    console.log(instanceRef.current.emit)
  }
}
```

**注意:**

* 在 `setup` 函数中，`this` 指向的是当前组件的上下文对象，而不是组件实例本身。
* `getCurrentInstance` 函数只能在 `setup` 函数或其他 Composition API 函数中使用。
* 使用 `ref` 来获取组件实例，需要在组件挂载完成后才能获取到组件实例。

**总结:**

在 Vue 3 中，可以使用 `getCurrentInstance` 函数或 `ref` 来获取组件实例。