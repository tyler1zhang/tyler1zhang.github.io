# tyler1zhang.github.io

## [李骏编程课](https://www.bilibili.com/video/BV1ME411W7dE)学习笔记.
>（以下笔记来源与2019年末的李骏“进入编程世界的第一课”的内容和我的感想。版权归李骏老师）李骏，[沪江英语](https://www.hjenglish.com/)CTO. 现任华东师大教授，教授《数据思维与实践》。 

### 1. 注释：(程序的基本结构（二）：操作符与函数)
 >有不少编程语言还提供配套的工具，可以自动分析源代码里的注释来生成程序文档，比如 Python 的 [pydoc](https://docs.python.org/2/library/pydoc.html)。

>注释并非越多越好，注释一定是“光看源代码难以知晓的重要信息”，我个人的风格是程序尽量写得不需要注释，然后再写少量必须注释的内容。比如写了一个经典算法的实现，参考的算法说明可以作为一个链接附上，方便不了解这个算法原理的人参考；再比如某处代码用到了一个临时假定，是未来有可能变化的，也很适合记录下来，并且标记一个 TODO 之类的标签，这样以后你只要全文检索 TODO 就能找出所有这类假定，检查是不是情况已经变化或者有了更好的解决方案，而做出相应修改。


### 2. 循环

> 1. python中的循环语句主要有两种： *for* 和 *while*.
> 2. break 和 continue 可以改变循环体的执行流程。 

### 3. 异常处理

Python 提供的异常处理机制可以用下面的模板来说明：

```python
try:
    # 把有可能出现异常的代码放在 try 后面
    # 当出现异常时解释器会捕获异常
    # 并根据异常的类型执行后面的对应代码块
    do_something_nasty()
except ValueError:
    # 如果发生 ValueError 类型的异常则执行这个代码块
    pass
except (TypeError, ZeroDivisionError):
    # 可以一次指定几个不同类型的异常在一起处理exceptions
    # 如果出现 TypeError 或者 ZeroDivisionError 则执行这个代码块
    pass
except:
    # 所有上面没有专门处理的类型的异常会在这里处理
    pass
else:
    # 当且仅当 try 代码块里无异常发生时这个代码块会被执行
    pass
finally:
    # 无论发生了什么这个代码块都会被执行
    # 通常这里是清理性的代码，比如我们在 try 里面打开一个文件进行处理
    # 无论过程中有没有异常出现最后都应该关闭文件释放资源
    # 这样的操作就适合在这里执行
```

上面出现的关键字 `pass` 的意思是“什么也不做”，Python 语法需要有点什么，但是我们暂时什么都不想做的时候放上一个 `pass` 就可以了。

在这里异常处理确保用户输入可以转换为整数且赋值给 x，否则就不会继续执行下去，经过这样的处理，在这段代码之后我们可以相当有把握的说：x 里面有个合法的、用户输入的整数值；同时用户不管怎么乱输入也不会对程序构成致命影响，我们预期到可能出现的问题，并做了合理处理。这就是异常处理的意义所在。

```python
def this_fails():
    x = 1/0

try:
    this_fails()
except ZeroDivisionError as err:
    print('Handling run-time error:', err)
```

Handling run-time error: division by zero

这个例子展示了用 except ZeroDivisionError as err 这样的语法来取得一个 err 对象，这个对象是系统定义的 Exception 类型或者子类，里面存放着发生异常时的具体上下文信息，可以打印出来也可以做别的处理。

我们还可以从 Exception 派生出我们自己的异常类型，并使用 raise 关键字来在出现某种情况时抛出我们定义的异常，并在文档中做出清晰的说明。这样使用我们代码的其他程序员就知道什么情况是我们程序处理不了的，会抛出什么样的异常，并在调用端用捕获异常进行处理。

建议学习 [关于 Python 异常处理的官方教程](https://docs.python.org/3/tutorial/errors.html) 来了解更多。





### 4. Other books or courses:

1.  [How To Ask Questions The Smart Way](http://www.catb.org/~esr/faqs/smart-questions.html)

怎样提问才能得到快速而正确的帮助？这是所有的初次迈进计算机世界的所有人需要掌握的一项**基本技能**. 因为操作系统，环境，编程语言的不同，导致同一个问题的解法可能是完全不一样的，甚至在某种特定的情况下无解（不做硬性重启，重装系统）。 所以这将是每个初学者的必修的**支线课程**，而这支线课程很多老师并不教，就像不是所有的学校都教你如何做人。 2001年，有个大牛Eric S. Raymond在BBS上发表了一篇文章(点击此节标题）， 这篇文章经过多次修改后，经过了时间的考验，几乎成为经典。

2. ["Story"](https://www.amazon.com/Story-Structure-Substance-Principles-Screenwriting-ebook/dp/B0042FZVOY). --Robert Mckee

3. ["Computer Systems, A Programmer's Perspective"](http://csapp.cs.cmu.edu/) --Randal E. Bryant and David R. O'Hallaron, Carnegie Mellon University

4. 学习命令行的[推荐教材](http://cglab.ca/~morin/teaching/1405/clcc/book/cli-crash-courseli3.html#x4-40000.1).

5. [PEP 8 -- Style Guide for Python Code](https://www.python.org/dev/peps/pep-0008/). 

6. String 的各种内置的[方法](https://docs.python.org/3/library/stdtypes.html#string-methods). 比如
```python
str.ljust(), str.join(), str.count(), str.find(), str.lower(), str.upper(), str.isalnum(), str.isdigit(), etc. 
```

<div>
  <a href='https://www.counter12.com'><img src='https://www.counter12.com/img-b0zD7x0BDdD7315B-2.gif' border='0' alt='counter'>
  </a>
  <script type='text/javascript' src='https://www.counter12.com/ad.js?id=b0zD7x0BDdD7315B'>
  </script>
</div>
