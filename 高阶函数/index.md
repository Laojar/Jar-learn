# 关于函数

- 与数学上函数的却别，数学上的函数没有副作用。
  - 数学： 参数 → 函数值

  - 程序：(参数，外部变量) → (函数值，副作用)

- JS中的函数
  1. JS 中，一等公民，可以赋值给其他变量，也可以作为参数，传入另一个函数，或者作为别的函数的返回值。
  2. 只用"表达式"，不用"语句"。"表达式"（expression）是一个单纯的运算过程，总是有<b>返回值</b>；"语句"（statement）是执行某种操作，没有返回值。原因是函数式编程的开发动机，<b>一开始就是为了处理运算</b>（computation），不考虑系统的读写（I/O）。"语句"属于对系统的读写操作，所以就被排斥在外。
- 柯里化函数的特点：
  1. 没有“副作用”。函数内部与外部互动，产生运算以外的结果。这就意味着函数要保持独立，所有功能返回一个新的值。
  2. 不修改状态。在其他类型的语言中，变量往往用来保存"状态"（state）。而在 JS 中函数不修改变量，不改变下一次函数执行的结果。函数式编程使用参数保存状态。
  3. 引用透明。指的是函数的运行不依赖于外部变量或"状态"，只依赖于输入的参数，任何时候只要参数相同，引用函数所得到的返回值总是相同的。

-   特点
    -   结构清晰，便于理解，代码管理。
    -   易于“并发编程”。函数式编程不需要考虑"死锁"（deadlock），因为它不修改变量，所以根本不存在"锁"线程的问题。不必担心一个线程的数据，被另一个线程修改，所以可以很放心地把工作分摊到多个线程。
    -   代码的热升级。函数式编程没有副作用，只要保证接口不变，内部实现是外部无关的。所以，可以在运行状态下直接升级代码，不需要重启，也不需要停机。（参数不变，函数体不变，返回的结果不变）

-   叫法
    -   偏函数。返回一个包含预处理参数的新函数。闭包。
    -   预置函数。当达到某种条件时才执行回调函数。(装饰者模式)

# 高阶函数

-   定义：输入一个函数或多个函数为输入，输出一个函数。
-   应用
    -   柯里化（curry）。又称部分求值。1. 柯里化函数会接收一些参数，然后不会立即求值，而是继续返回一个新函数，将传入的参数通过闭包的形式保存。2. 等到被真正求值的时候，再一次性把所有传入的参数进行求值。（bind）
    - 反柯里化（uncurry）。非我之物，为我所用。如果说柯里化的过程是将函数拆分成功能更具体化的函数，那反柯里化的作用则在于扩大函数的适用性，使本来作为特定对象所拥有的功能函数可以被任意对象所使用。
    - 节流。规定在一个单位时间内，只能触发一次函数。如果这个单位时间内触发多次函数，只有一次生效。（ps. 防抖是在事件被触发n秒后再执行回调，如果在这n秒内又被触发，则重新计时。）
    - 分时。主要是来解决主动调用函数时，频繁触发会导致一些客观的问题。（例如：短时间插入过多的DOM）。
    - ...

    - [更多的高阶函数](https://github.com/mqyqingfeng/Blog)