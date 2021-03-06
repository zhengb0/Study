## 设计原则与思想 总结
![编写高质量代码](https://static001.geekbang.org/resource/image/f3/d3/f3262ef8152517d3b11bfc3f2d2b12d3.png "编写高质量代码")
### 代码质量评判标准
##### 如何评价代码质量的高低？
  代码质量的评价有很强的主观性，描述代码质量的词汇也有很多，比如可读性、可维护性、灵活、优雅、简洁。代码质量高低是一个综合各种因素得到的结论。我们并不能通过单一维度去评价一段代码的好坏。
##### 常用的评价标准
  可维护性、可读性、可扩展性、灵活性、简洁性、可复用性、可测试性。其中，可维护性、可读性、可扩展性又是提到最多的、最重要的三个评价标准。
##### 如何才能写出高质量的代码
  要掌握面向对象设计思想、设计原则、设计模式、编码规范、重构技巧。
  ![代码质量评判标准](https://static001.geekbang.org/resource/image/34/2b/34c51d1eb44ffc099d448ad10bcda82b.jpg "代码质量评判标准")
### 面向对象
##### 面向对象概述
  面向对象编程因为其具有丰富的特性（封装、抽象、继承、多态），可以实现很多复杂的设计思路，是很多设计原则、设计模式编码实现的基础。
##### 面向对象四大特性
  封装也叫作信息隐藏或者数据访问保护。类通过暴露有限的访问接口，授权外部仅能通过类提供的方法来访问内部信息或者数据。一方面是保护数据不被随意修改，提高代码的可维护性；另一方面是仅暴露有限的必要接口，提高类的易用性。
  如果说封装主要讲如何隐藏信息、保护数据，那抽象就是讲如何隐藏方法的具体实现，让使用者只需要关心方法提供了哪些功能，不需要知道这些功能是如何实现的。抽象存在的意义，一方面是修改实现不需要改变定义；另一方面，它也是处理复杂系统的有效手段，能有效地过滤掉不必要关注的信息。
  继承用来表示类之间的 is-a 关系，分为两种模式：单继承和多继承。单继承表示一个子类只继承一个父类，多继承表示一个子类可以继承多个父类。为了实现继承这个特性，编程语言需要提供特殊的语法机制来支持。继承主要是用来解决代码复用的问题。
  态是指子类可以替换父类，在实际的代码运行过程中，调用子类的方法实现。多态可以提高代码的扩展性和复用性，是很多设计模式、设计原则、编程技巧的代码实现基础。
##### 面向对象 VS 面向过程
  面向对象编程相比面向过程编程的优势主要有三个。
  - 对于大规模复杂程序的开发，程序的处理流程并非单一的一条主线，而是错综复杂的网状结构。面向对象编程比起面向过程编程，更能应对这种复杂类型的程序开发。
  - 面向对象编程相比面向过程编程，具有更加丰富的特性（封装、抽象、继承、多态）。利用这些特性编写出来的代码，更加易扩展、易复用、易维护。
  - 从编程语言跟机器打交道方式的演进规律中，我们可以总结出：面向对象编程语言比起面向过程编程语言，更加人性化、更加高级、更加智能。
不管使用面向过程还是面向对象哪种风格来写代码，我们最终的目的还是写出易维护、易读、易复用、易扩展的高质量代码。只要我们能避免面向过程编程风格的一些弊端，控制好它的副作用，在掌控范围内为我们所用，我们就大可不用避讳在面向对象编程中写面向过程风格的代码。
##### 面向对象分析、设计与编程
  面向对象分析（OOA）、面向对象设计（OOD）、面向对象编程（OOP），是面向对象开发的三个主要环节。简单点讲，面向对象分析就是要搞清楚做什么，面向对象设计就是要搞清楚怎么做，面向对象编程就是将分析和设计的的结果翻译成代码的过程。
  面向对象分析的产出是详细的需求描述。面向对象设计的产出是类。在面向对象设计这一环节中，我们将需求描述转化为具体的类的设计。这个环节的工作可以拆分为下面四个部分。
  - 划分职责进而识别出有哪些类
  - 定义类及其属性和方法
  - 定义类与类之间的交互关系
  - 将类组装起来并提供执行入口
##### 接口 VS 抽象类
   抽象类不允许被实例化，只能被继承。它可以包含属性和方法。方法既可以包含代码实现，也可以不包含代码实现。不包含代码实现的方法叫作抽象方法。子类继承抽象类，必须实现抽象类中的所有抽象方法。接口不能包含属性（Java 可以定义静态常量），只能声明方法，方法不能包含代码实现（Java8 以后可以有默认实现）。类实现接口的时候，必须实现接口中声明的所有方法。
  
  抽象类是对成员变量和方法的抽象，是一种 is-a 关系，是为了解决代码复用问题。接口仅仅是对方法的抽象，是一种 has-a 关系，表示具有某一组行为特性，是为了解决解耦问题，隔离接口和具体的实现，提高代码的扩展性。
  
  接口和抽象类的适用场景
  - 如果要表示一种is-a的关系，并且是为了解决代码复用问题，用抽象类
  - 如果要表示一种has-a的关系，并且是为了解决抽象而非代码复用问题，用接口
##### 基于接口而非实现编程
  应用这条原则，可以将接口和实现相分离，封装不稳定的实现，暴露稳定的接口。上游系统面向接口而非实现编程，不依赖不稳定的实现细节，这样当实现发生变化的时候，上游系统的代码基本上不需要做改动，以此来降低耦合性，提高扩展性。
  基于接口而非实现编程”这条原则的另一个表述方式是，“基于抽象而非实现编程”。
##### 多用组合少用继承
  继承是面向对象的四大特性之一，用来表示类之间的 is-a 关系，可以解决代码复用的问题。虽然继承有诸多作用，但继承层次过深、过复杂，也会影响到代码的可维护性。
###### 组合相比继承的优势
  继承主要有三个作用：表示 is-a 关系、支持多态特性、代码复用。而这三个作用都可以通过组合、接口、委托三个技术手段来达成。除此之外，利用组合还能解决层次过深、过复杂的继承关系影响代码可维护性的问题。
###### 如何判断用组合还是继承
  如果类之间的继承结构稳定，层次比较浅，关系不复杂，我们就可以大胆地使用继承。反之，我们就尽量使用组合来替代继承。
  
  ![面向对象](https://static001.geekbang.org/resource/image/f4/e7/f4ce06502a9782d200e8e10a90bf2ce7.jpg "面向对象")
### 设计原则
##### SOLID原则：SRP单一职责原则
  一个类只负责完成一个职责或者功能。单一职责原则通过避免设计大而全的类，避免将不相关的功能耦合在一起，来提高类的内聚性。同时，类职责单一，类依赖的和被依赖的其他类也会变少，减少了代码的耦合性，以此来实现代码的高内聚、松耦合。但是，如果拆分得过细，实际上会适得其反，反倒会降低内聚性，也会影响代码的可维护性。
  
  如果出现下面这些情况就有可能说明这类的设计不满足单一职责原则
  - 类中的代码行数、函数或者属性过多
  - 类依赖的其他类过多或者依赖类的其他类过多
  - 私有方法过多
  - 比较难给类起一个合适的名字
  - 类中大量的方法都是集中操作类中的某几个属性
##### SOLID原则：OCP开闭原则
###### 如何理解“对扩展开放，对修改关闭”？
  添加一个新的功能，应该是通过在已有代码基础上扩展代码（新增模块、类、方法、属性等），而非修改已有代码（修改模块、类、方法、属性等）的方式来完成。有两点要注意。第一点是，开闭原则并不是说完全杜绝修改，而是以最小的修改代码的代价来完成新功能的开发。第二点是，同样的代码改动，在粗代码粒度下，可能被认定为“修改”；在细代码粒度下，可能又被认定为“扩展”。
##### SOLID 原则：LSP 里式替换原则
  子类对象（object of subtype/derived class）能够替换程序（program）中父类对象（object of base/parent class）出现的任何地方，并且保证原来程序的逻辑行为（behavior）不变及正确性不被破坏。
  理解里式替换原则，最核心的就是理解“design by contract，按照协议来设计”这几个字。父类定义了函数的“约定”（或者叫协议），那子类可以改变函数的内部实现逻辑，但不能改变函数的原有“约定”。这里的“约定”包括：函数声明要实现的功能；对输入、输出、异常的约定；甚至包括注释中所罗列的任何特殊说明。
  理解这个原则，我们还要弄明白，里式替换原则跟多态的区别。虽然从定义描述和代码实现上来看，多态和里式替换有点类似，但它们关注的角度是不一样的。多态是面向对象编程的一大特性，也是面向对象编程语言的一种语法。它是一种代码实现的思路。而里式替换是一种设计原则，用来指导继承关系中子类该如何设计，子类的设计要保证在替换父类的时候，不改变原有程序的逻辑及不破坏原有程序的正确性。
##### SOLID 原则：ISP 接口隔离原则
  接口隔离原则的描述是：客户端不应该强迫依赖它不需要的接口。其中的“客户端”，可以理解为接口的调用者或者使用者。理解“接口隔离原则”的重点是理解其中的“接口”二字。这里有三种不同的理解。
  - 如果把“接口”理解为一组接口集合，可以是某个微服务的接口，也可以是某个类库的接口等。如果部分接口只被部分调用者使用，我们就需要将这部分接口隔离出来，单独给这部分调用者使用，而不强迫其他调用者也依赖这部分不会被用到的接口。
  - 如果把“接口”理解为单个 API 接口或函数，部分调用者只需要函数中的部分功能，那我们就需要把函数拆分成粒度更细的多个函数，让调用者只依赖它需要的那个细粒度函数。
  - 如果把“接口”理解为 OOP 中的接口，也可以理解为面向对象编程语言中的接口语法。那接口的设计要尽量单一，不要让接口的实现类和调用者，依赖不需要的接口函数。
  单一职责原则针对的是模块、类、接口的设计。接口隔离原则相对于单一职责原则，一方面更侧重于接口的设计，另一方面它的思考的角度也是不同的。接口隔离原则提供了一种判断接口的职责是否单一的标准：通过调用者如何使用接口来间接地判定。如果调用者只使用部分接口或接口的部分功能，那接口的设计就不够职责单一。
##### SOLID 原则：DIP 依赖倒置原则
  - 控制反转：实际上，控制反转是一个比较笼统的设计思想，并不是一种具体的实现方法，一般用来指导框架层面的设计。这里所说的“控制”指的是对程序执行流程的控制，而“反转”指的是在没有使用框架之前，程序员自己控制整个程序的执行。在使用框架之后，整个程序的执行流程通过框架来控制。流程的控制权从程序员“反转”给了框架。
  - 依赖注入：依赖注入和控制反转恰恰相反，它是一种具体的编码技巧。我们不通过 new 的方式在类内部创建依赖类的对象，而是将依赖的类对象在外部创建好之后，通过构造函数、函数参数等方式传递（或“注入”）给类来使用。
  - 依赖注入框架：我们通过依赖注入框架提供的扩展点，简单配置一下所有需要的类及其类与类之间的依赖关系，就可以实现由框架来自动创建对象、管理对象的生命周期、依赖注入等原本需要程序员来做的事情。
  - 依赖反转原则：依赖反转原则也叫作依赖倒置原则。这条原则跟控制反转有点类似，主要用来指导框架层面的设计。高层模块不依赖低层模块，它们共同依赖同一个抽象。抽象不需要依赖具体实现细节，具体实现细节依赖抽象。
##### KISS、YAGNI 原则
  KISS 原则的中文描述是：尽量保持简单。KISS 原则是保持代码可读和可维护的重要手段。
  "简单"： 并不是以代码行数来考量的，还要考虑逻辑复杂度、实现难度、代码的可读性...
  - 不要使用同事可能不懂的技术来实现代码
  - 不要重复造轮子，善于使用已经有的工具类库
  - 不要过度优化
  YAGNI 原则的英文全称是：You Ain’t Gonna Need It。直译就是：你不会需要它。这条原则的核心思想就是：不要做过度设计。
  YAGNI 原则跟 KISS 原则并非一回事儿。KISS 原则讲的是“如何做”的问题（尽量保持简单），而 YAGNI 原则说的是“要不要做”的问题（当前不需要的就不要做）。
  ##### DRY 原则 （Don't Repeat Yourself）
  - 实现逻辑重复
  - 功能语义重复
  - 代码执行重复
##### LOD原则（Law of Demeter）
  ###### 如何理解“高内聚、松耦合”？
  高内聚、松耦合”是一个非常重要的设计思想，能够有效提高代码的可读性和可维护性，缩小功能改动导致的代码改动范围。“高内聚”用来指导类本身的设计，“松耦合”用来指导类与类之间依赖关系的设计。所谓高内聚，就是指相近的功能应该放到同一个类中，不相近的功能不要放到同一类中。相近的功能往往会被同时修改，放到同一个类中，修改会比较集中。所谓“松耦合”指的是，在代码中，类与类之间的依赖关系简单清晰。即使两个类有依赖关系，一个类的代码改动也不会或者很少导致依赖类的代码改动。
  ###### 如何理解“迪米特法则”？
  又称最小知识原则。迪米特法则的描述为：不该有直接依赖关系的类之间，不要有依赖；有依赖关系的类之间，尽量只依赖必要的接口。迪米特法则是希望减少类之间的耦合，让类越独立越好。每个类都应该少了解系统的其他部分。一旦发生变化，需要了解这一变化的类就会比较少。
  ![设计原则](https://static001.geekbang.org/resource/image/fb/9f/fbf1ae0ce08d4ea890b80944c2b8309f.jpg "设计原则")
### 规范与重构
##### 重构的目的：为什么重构(why)?
  对于项目来言，重构可以保持代码质量持续处于一个可控状态，不至于腐化到无可救药的地步。对于个人而言，重构非常锻炼一个人的代码能力，并且是一件非常有成就感的事情。
##### 重构的对象：重构什么（what）？
  按照重构的规模，我们可以将重构大致分为大规模高层次的重构和小规模低层次的重构。大规模高层次重构包括对代码分层、模块化、解耦、梳理类之间的交互关系、抽象复用组件等等。这部分工作利用的更多的是比较抽象、比较顶层的设计思想、原则、模式。小规模低层次的重构包括规范命名、注释、修正函数参数过多、消除超大类、提取重复代码等编程细节问题，主要是针对类、函数级别的重构。小规模低层次的重构更多的是利用编码规范这一理论知识。
##### 重构的时机：什么时候重构（when）？
  我们一定要建立持续重构意识，把重构作为开发必不可少的部分融入到开发中，而不是等到代码出现很大问题的时候，再大刀阔斧地重构。
##### 重构的方法：如何重构（how）？
  大规模高层次的重构难度比较大，需要有组织、有计划地进行，分阶段地小步快跑，时刻保持代码处于一个可运行的状态。而小规模低层次的重构，因为影响范围小，改动耗时短，所以，只要你愿意并且有时间，随时随地都可以去做。
##### 单元测试
  单元测试是代码层面的测试，用于测试“自己”编写的代码的逻辑正确性。单元测试顾名思义是测试一个“单元”，这个“单元”一般是类或函数，而不是模块或者系统。
##### 为什么要写单元测试(why)?
  单元测试能有效地发现代码中的 Bug、代码设计上的问题。写单元测试的过程本身就是代码重构的过程。
##### 如何编写单元测试(how)?
  写单元测试就是针对代码设计覆盖各种输入、异常、边界条件的测试用例，并将其翻译成代码的过程。
  对于单元测试，我们需要建立以下正确的认知：
  - 编写单元测试尽管繁琐，但并不是太耗时
  - 我们可以稍微放低单元测试的质量要求
  - 覆盖率作为衡量单元测试好坏的唯一标准是不合理的
  - 写单元测试一般不需要了解代码的实现逻辑
  - 单元测试框架无法测试多半是代码的可测试性不好
##### 单元测试为何难落地执行？
  一方面，写单元测试本身比较繁琐，技术挑战不大，很多程序员不愿意去写。另一方面，国内研发比较偏向“快糙猛”，容易因为开发进度紧，导致单元测试的执行虎头蛇尾，最后，没有建立对单元测试的正确认识，觉得可有可无，单靠督促很难执行得很好。
##### 代码的可测试性
  粗略地讲，所谓代码的可测试性，就是针对代码编写单元测试的难易程度。
##### 编写可测试性代码的最有效手段
  依赖注入是编写可测试性代码的最有效手段。通过依赖注入，我们在编写单元测试代码的时候，可以通过 mock 的方法将不可控的依赖变得可控，这也是我们在编写单元测试的过程中最有技术挑战的地方。除了 mock 方式，我们还可以利用二次封装来解决某些代码行为不可控的情况。
  典型的、常见的测试不友好的代码有下面这 5 种：
  - 代码中包含未决行为逻辑
  - 滥用可变全局变量
  - 滥用静态方法
  - 使用复杂的继承关系
  - 高度耦合的代码
##### 大型重构：解耦
  过于复杂的代码往往在可读性、可维护性上都不友好。解耦，保证代码松耦合、高内聚，是控制代码复杂度的有效手段。如果代码高内聚、松耦合，也就是意味着，代码结构清晰、分层、模块化合理、依赖关系简单、模块或类之间的耦合小，那代码整体的质量就不会差。
  间接的衡量标准：改动一个模块或类的代码受影响的模块或类是否有很多、改动一个模块或者类的代码依赖的模块或者类是否需要改动、代码的可测试性是否好...
  直接的衡量标准：把模块与模块之间及其类与类之间的依赖关系画出来，根据依赖关系图的复杂性来判断是否需要解耦重构。
  解耦的方法：封装与抽象、中间层、模块化，以及一些其他的设计思想与原则，比如：单一职责原则、基于接口而非实现编程、依赖注入、多用组合少用继承、迪米特法则。当然，还有一些设计模式，比如观察者模式。
##### 小型重构：编码规范
###### 命名与注释
  - 命名的关键是能准确的达意。对于不同作用域的命名，我们可以适当的选择不同的长度，作用域小的命名，比如临时变量等，可以适当的选择短一些的命名方式。除此之外，命名中个也可以使用一些耳熟能详的缩写。
  - 我们借助类的信息来简化属性、函数的命名，利用函数的信息来简化函数参数的命名。命名要可读、可搜索。不要使用生僻的、不好读的英文单词来命名。除此之外，命名要符合项目的统一规范，也不要用些反直觉的命名。
  - 接口有两种命名方式。一种是在接口中带前缀"I"，另一种是在接口的实现类中带后缀“Impl”。两种命名方式都可以，关键是要在项目中统一。对于抽象类的命名，我们更倾向于带有前缀“Abstract”。
  - 注释的目的就是让代码更容易看懂，只要符合这个要求，你就可以写。总结一下的话，注释主要包含这样三个方面的内容：做什么、为什么、怎么做。对于一些复杂的类和接口，我们可能还需要写明“如何用”。
  - 注释本身有一定的维护成本，所以并非越多越好。类和函数一定要写注释，而且要写的尽可能全面详细些，而函数内部的注释会相对少一些，一般都是靠好的命名和提炼函数、解释性变量、总结性注释来做到代码易读。
##### 代码风格
  代码风格都没有对错和优劣之分，不同的编程语言风格都不太一样，只要能在团队、项目中统一即可，不过，最好能跟业内推荐的风格、开源项目的代码风格相一致。
##### 编程技巧
  - 将复杂的逻辑提炼拆分成函数和类
  - 通过拆分成多个函数的方式来处理参数过多的情况
  - 通过将参数封装为对象来处理参数过多的情况
  - 函数中不要使用参数来做代码执行逻辑的控制
  - 移除过深的嵌套层次，方法包括：去掉多余的 if 或 else 语句，使用 continue、break、return 关键字提前退出嵌套，调整执行顺序来减少嵌套，将部分嵌套逻辑抽象成函数
  - 用字面常量取代魔法数
  - 利用解释性变量来解释复杂表达式
##### 统一编码规范
  还有一条非常重要的，那就是，项目、团队，甚至公司，一定要制定统一的编码规范，并且通过 Code Review 督促执行，这对提高代码质量有立竿见影的效果。
  ![规范与重构](https://static001.geekbang.org/resource/image/fc/8a/fc56f7c2b348d324c93a09dd0dee538a.jpg "规范与重构")
