# 类属性(property)
- 应用场景: 对变量除了普通的三种操作，还想增加一些附加的操作，那么可以通过property完成
    
        class A():
            def __init__(self):
                self.name = "niuwa"
                self.age = "18"
                
            # 此功能，是对类变量进行读取操作的时候应该执行的函数功能
            def fget(self):
                print("我被读取了")
                return self.name
                
            # 模拟的是对变量进行写操作的时候执行的功能
            def fset(self, name):
                print("我被写入了，但是还可以做一些其他的事情")
                self.name = "图灵学院: " + name
                
            # fdel  模拟的是删除变量的时候进行的操作
            def fdel(self):
                pass
                
            # property 的四个参数顺序是固定的
            # 第一个参数代表读取的时候需要调用的函数
            # 第二个参数代表写入的时候需要调用的函数
            # 第三个参数代表删除的时候需要调用的函数
            # 第四个参数是对它的一个解释说明
            name2 = property(fset, fget, fdel, "这是一个property的例子")
            
        a = A()
        print(a.name)   # 这里只是对name 做读取操作，跟property 无关
        print(a.name2)  # 这里是对类属性的读取操作的应用，也就是property 的实际应用，它将会调用fget() 函数
    
