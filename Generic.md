##Java 1.5之前并不直接支持泛型实现，而是使用继承来实现泛型方法和类

1. 使用Object表示泛型，只有引用类型能够与Object相容
2. 因此有了基本类型的包装类
3. 使用接口类型表示泛型，实现Comparable接口，传递Comparable数组，实现compareTo（）方法
4. 数组是协变类型的

##Java 1.5 泛型：

1. 一对尖括号<AnyType>，Comparable接口也是泛型的：Comparable<AnyType>
2. 自动装箱/拆箱：基本类型和他们的包装类
3. 泛型集合不是协变的，带有限制的通配符：<? extends AnyType>
4. 泛型static方法，在泛型方法中的类型参数位于返回类型之前
5. 类型限界：<AnyType extends Comparable<? super AnyType>>

##函数对象：实现Comparator<AnyType>方法
