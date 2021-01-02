###### 2020 阅读清单总结

[TOC]

# 编译器设计

| ==名称==                                                     | ==Reference==                                                | ==简要说明==                                                 | ==个人注解==                                                 |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| make programming languages(interpreter)                      | http://craftinginterpreters.com/contents.html                | 包含了实现全功能、高效脚本语言所需的一切。你将学习到关于解析和语义的高级概念，以及诸如字节码表示和垃圾回收等具体细节 | 学习编译器(严格意义事解释器)的最优秀读本之一，入门级参考文献 |
| The Secret Sauce in Efficient and Precise Static Analysis    | https://bodden.de/pubs/bodden18secret.pdf                    | 程序逻辑分析方法论(静态分析方案)                             | static-analysis一点都不稀奇，文章描述的方案一般性不强，仅供参考 |
| Feral-(C++14写的编程语言解释器)                              | https://www.reddit.com/r/cpp/comments/fvkb66/a_programming_language_interpreter_in_c/ | Compiler ?? VM ??                                            | 只是稍微扫了下设计模式，有兴趣的可以自己看看                 |
| libclang的使用与分析                                         | 1.https://www.youtube.com/watch?v=E6i8jmiy8MY<br>2.https://github.com/peter-can-talk/cppnow-2017 | RT                                                           | 需要构建特定的编译组件分析特定模式                           |
| Challenging LR Parsing                                       | https://rust-analyzer.github.io/blog/2020/09/16/challeging-LR-parsing.html |                                                              | 不做过多解释，工作相关                                       |
| A small C compiler                                           | https://github.com/rui314/chibicc                            |                                                              | 说实话，这个作者不知道是不是有点偏执，他还写了8cc,9cc等C编译器，看看设计逻辑倒是不错，不必要深究 |
| PEG Parsing Series Overview(Python之父的解析器分析)          | https://medium.com/@gvanrossum_83706/peg-parsing-series-de5d41b2ed60 |                                                              | 不做过多解释，编译器Parser                                   |
| Simple but Powerful Pratt Parsing                            | 1. https://matklad.github.io/2020/04/13/simple-but-powerful-pratt-parsing.html<br>2. https://www.reddit.com/r/ProgrammingLanguages/comments/j8f9i3/what_are_some_great_resources_for_building_your/ |                                                              | 不做过多解释，编译器Parser                                   |
| On Symbolic Execution of Decompiled Programs                 | 1. https://qrs20.techconf.org/QRS2020_FULL/pdfs/QRS2020-4LGdOos7NAbR8M2s6S6ezE/891300a265/891300a265.pdf<br>2. https://divine.fi.muni.cz/2020/decompile/ |                                                              | 符号执行是趋势，既方便应用程序测试，也方便反编译程序分析，动态调试也能从中获取相关有用的信息 |
| A self-hosting and educational C compiler                    | https://github.com/jserv/shecc                               |                                                              | 我也不知道为啥看了这么多C的编译器，不过就是觉得好玩，而且每个作者的思路都是不一样的，不错。。。 |
| C++ parser combinator library                                | https://github.com/foonathan/lexy                            |                                                              | 相较于flex与bison，或者boost 的Spirit框架，我更喜欢这个作者的思路,DSL |
| A Complete Guide to LLVM for Programming Language Creators   | https://mukulrathi.co.uk/create-your-own-programming-language/llvm-ir-cpp-api-tutorial/ |                                                              | 相较于官方的LLVM组件例子，这个例子稍微深一点，还是蛮不错的教程 |
| **TCC & QuickJS**                                            | 1. https://bellard.org/quickjs/<br>2. https://bellard.org/tcc/ |                                                              | ***阅读分析了很多小型Toy编译器，但是给我影响最深的莫属这两个了，作者的testsuites做的很好，逻辑设计也是极棒的*** |
| A Compiler Writing Journey                                   | 1. https://github.com/DoctorWkt/acwj<br>2. https://news.ycombinator.com/item?id=21968420 |                                                              | C Compiler From Scratch,C 语言编译器分析                     |
| CirCle Language Compiler                                     | https://github.com/seanbaxter/circle                         |                                                              | 自己备用看的设计逻辑                                         |
| Janet: a lightweight, expressive and modern Lisp             | 1. https://news.ycombinator.com/item?id=23164614<br>2. https://janet-lang.org/ |                                                              | Lisp 方言最佳实践方案之一，优秀                              |
| Pratt Parsers: Expression Parsing Made Easy                  | http://journal.stuffwithstuff.com/2011/03/19/pratt-parsers-expression-parsing-made-easy/ |                                                              |                                                              |
| Parsing Expression Grammar Template Library                  | https://github.com/taocpp/PEGTL                              |                                                              | Parsing Expression Generator                                 |
| Using LLVM to Prevent Objective-C Swizzling Through Devirtualization | https://tech.guardsquare.com/posts/objc-methodcall-lowering/ |                                                              | Objective-C Swizzling                                        |
| Adding PoisonValue for representing poison value explicitly in IR | https://github.com/llvm/llvm-project/commit/75f50e15bf8fff6fba1d4678adedd33ef6a945e5 |                                                              | LLVM 组件的IR PoisonValue设计(注意无关编译)                  |

## 编译器岗位面试(个人认为这些能很好地评估编译器相干知识掌握情况)

> - For frontend: could you explain parsing techniques like  LR/LALR/LL/PEG/RD/Pratt/precedence algorithms? How about the design of  good error messages and error recovery? UX/HCI methods in general?
> - For architecture: are you familiar with the differences between traditional linear compiler pipeline architecture, and the newer  incremental/interactive/query-driven architectures?
> - For static & dynamic semantics: could you write a Simply Typed Lambda  Calculus interpreter with lexically scoped variables and  capture-avoiding substitution? Could you discuss the tradeoffs of names  vs. De Bruijn indices vs. De Bruijn levels vs. locally nameless  representations?
> - For type systems: could you discuss Hindley–Milner type inference with  constraint solving (Algorithm W) vs. bidirectional type checking  algorithms? Are you aware of advances in dependent types, refinement  types, subtyping…? Can you use natural deduction notation?
> - For analysis: are you familiar with various IRs like SSA, CPS, and ANF and  their tradeoffs? Do you know how to implement things like liveness and  escape analyses? Fixpoint/lattice/abstract-interpretation techniques in  general?
> - For optimisation: could you sketch the implementation of various common  compiler optimisations like dead code elimination, inlining, common  subexpression elimination? Are you familiar with program transformation  techniques like the polyhedral model and automatic vectorisation  methods?
> - For codegen: could you explain how register allocation works with a greedy  or heuristic graph-colouring approach? Could you talk about instruction  selection and calling conventions?

# C++&C 优秀代码分析

| ==代码简介==                                                 | ==链接==                                                     | ==个人见解==                                                 |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 使用C语言的预处理器构建解释器                                | https://github.com/Ferdi265/preprocessor_brainfuck           | 思想蛮新颖的，不过不建议玩，毕竟预处理器指令不好玩，😄        |
| Evaluating user defined logical Expressions                  | https://github.com/m-peko/booleval                           | C++17/库比较小巧，逻辑表达式的代码判定比较有用               |
| C++17 vs C++20                                               | http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2020/p2131r0.html | C++20最大的优势就是引入了Concept概念，给Templates增添了更多的神秘色彩 |
| ModernCppStarter                                             | https://github.com/TheLartians/ModernCppStarter              | 基于CMAKE的C++ project 模板工程，不用说，很好用就行了，因为长期使用Emacs做安全研究与代码开发 |
| Performance benefits of likely/unlikely and such             | 1. https://www.reddit.com/r/cpp/comments/ap12od/performance_benefits_of_likelyunlikely_and_such/<br>2. https://stackoverflow.com/questions/1851299/is-it-possible-to-tell-the-branch-predictor-how-likely-it-is-to-follow-the-branc/1851445#1851445<br>3.  https://www.realworldtech.com/forum/?threadid=189711&curpostid=189723 | 说实话，写C的预处理指令时，也不知道为啥Linux 老手都喜欢这个东西，反正跟风呗，自己也尝试用了下 |
| Higher level programming in C                                | 1. https://github.com/orangeduck/Cello<br>2. http://libcello.org/learn/a-fat-pointer-library | 暂时还没用，贴出来等待查验                                   |
| Fast sorted collections for Swift using in-memory B-trees    | https://github.com/attaswift/BTree                           | 为数不多的swift的优秀库，虽然swift研究的不多，但是语言设计绝壁足够优秀 |
| C++17 & C++ 20 error-handling and utility extensions         | https://github.com/lamarrr/STX                               | Error-Handling and Utility Extensions                        |
| A collection of improved binary search algorithms.           | 1. https://github.com/scandum/binary_search<br>2. https://news.ycombinator.com/item?id=23893366 | Binary Search的性能提升比较                                  |
| C++ Memory Allocator设计                                     | http://dmitrysoshnikov.com/compilers/writing-a-memory-allocator/ |                                                              |
| Writing a custom iterator in modern C++                      | https://internalpointers.com/post/writing-custom-iterators-modern-cpp | Iterator 设计(C++ Version)                                   |
| Pointers Are Complicated, or: What's in a Byte?              | https://www.ralfj.de/blog/2018/07/24/pointers-and-bytes.html | Pointers(Rust vs C 语言)                                     |
| A library implementing different string similarity and distance measures using Python | https://github.com/luozhouyang/python-string-similarity#python-string-similarity | string 相似度计算(python版)，C++对应版本更新                 |
| Nameof operator for modern C++, simply obtain the name of a variable, type, function, macro, and enum | https://github.com/Neargye/nameof                            | C++ Macros使用                                               |
| Generating random numbers                                    | https://codingnest.com/generating-random-numbers-using-c-standard-library-the-problems/ | C++ PCG 使用，可与openssl库对比                              |
| Lock-Free Queue                                              | https://www.codeproject.com/articles/43510/lock-free-single-producer-single-consumer-circular | C++实例，简单扫一下即可                                      |
| An introduction to C++'s SFINAE concept: compile-time introspection of a class member | http://jguegant.github.io/blogs/tech/sfinae-introduction.html | C++ SFINAE 最佳指南                                          |
| A quick primer on type traits in modern C++                  | https://www.internalpointers.com/post/quick-primer-type-traits-modern-cpp | Type Trait                                                   |
| Allocators and an Inclusive STL                              | https://thephd.github.io/freestanding-noexcept-allocators-vector-memory-hole | STL Compatible Malloctor                                     |

# Sec 安全好文

| ==简介==                                                     | ==链接&文章==                                                |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| 10 Years of  Linux Security                                  | https://grsecurity.net/10_years_of_linux_security.pdf        |
| **An iOS zero-click radio proximity exploit odyssey**        | https://googleprojectzero.blogspot.com/2020/12/an-ios-zero-click-radio-proximity.html |
| Yurichev博客内容                                             | https://yurichev.com/news/                                   |
| a discretization attack(离散化攻击模式，密码学相关)          | https://cr.yp.to/papers/categories-20200918.pdf              |
| Jailed Just-in-Time Compilation on iOS(JIT相关)              | https://saagarjha.com/blog/2020/02/23/jailed-just-in-time-compilation-on-ios/ |
| Ransomware groups continue to target healthcare, critical services; here’s how to reduce risk | https://www.microsoft.com/security/blog/2020/04/28/ransomware-groups-continue-to-target-healthcare-critical-services-heres-how-to-reduce-risk/ |
| How Does a TCP Reset Attack Work ?                           | 1. https://robertheaton.com/2020/04/27/how-does-a-tcp-reset-attack-work/<br>2. https://news.ycombinator.com/item?id=22995046 |
| Psychic Paper: iOS Sandbox Escape                            | 1. https://siguza.github.io/psychicpaper/<br>2. https://news.ycombinator.com/item?id=23045042 |
| SAT solver on top of regex matcher                           | 1. https://yurichev.com/news/20200621_regex_SAT/<br>2. https://news.ycombinator.com/item?id=23543131 |
| ARM StackOverflow and MacOSX&IOS Exploit CVE Analysis        | https://www.fortinet.com/blog/search?author=Kai+Lu           |
| **CVE-2020-1350**--POC                                       | https://github.com/maxpl0it/CVE-2020-1350-DoS                |
| WasmBoxC: Simple, Easy, and Fast VM-less Sandboxing          | https://kripken.github.io/blog/wasm/2020/07/27/wasmboxc.html |
| Anti-Debug Tricks                                            | https://anti-debug.checkpoint.com/                           |
| CORS, XSS and CSRF 对比分析                                  | 1. https://dev.to/maleta/cors-xss-and-csrf-with-examples-in-10-minutes-35k3<br>2. https://security.stackexchange.com/questions/108835/how-does-cors-prevent-xss |
| Exploiting Android Messengers with WebRTC(**GoogleZero**)    | 1. https://googleprojectzero.blogspot.com/2020/08/exploiting-android-messengers-part-1.html<br>2. https://googleprojectzero.blogspot.com/2020/08/exploiting-android-messengers-part-2.html<br>3. https://googleprojectzero.blogspot.com/2020/08/exploiting-android-messengers-part-3.html |
| XSLeaks Google 分享资料整合                                  | https://xsleaks.dev/                                         |
| RCE via Server-Side Template Injection                       | https://cyc10n3.medium.com/rce-via-server-side-template-injection-ad46f8e0c2ae |
| Introduction to Whiteboxes and Collision-Based Attacks With QBDI(QBDI的使用) | https://blog.quarkslab.com/introduction-to-whiteboxes-and-collision-based-attacks-with-qbdi.html |
| Security Infographics                                        | https://medium.com/malware-buddy/security-infographics-9c4d3bd891ef |
| Apple Notes(MacOSX vs IOS)                                   | https://ciofecaforensics.com/categories/#Apple%20Notes       |
| ProcessInjection Techniques                                  | https://github.com/3xpl01tc0d3r/ProcessInjection             |
| A Tale of Static Devirtualization(VTIL，较为有优势的反序列化方案) | https://0xnobody.github.io/devirtualization-intro/           |

2. 

​		**备注**

​		说实话，今年年初到现在，安全界最好的文章writeups 在我看来，应该归属于 google 安全员Ian beer的这篇文章(https://googleprojectzero.blogspot.com/2020/12/an-ios-zero-click-radio-proximity.html)，全文大概13500字左右，文章从协议，安全隐患，触发条件介绍的如此细腻，很值得国内的安全员学习下，不过国内的安全员貌似很多不愿分享，。。。。。😔

​		同时今年也开始接触部分CVE的了，主要是IOS＆Mac OSX这块，希望明年能够有一半时间用来搞CVE相关的安全事件吧，今年大部分时间献给了编译器了



## 安全类的开源软件框架

| ==简介==                                                     | ==链接==                                  |
| ------------------------------------------------------------ | ----------------------------------------- |
| Dynamic Infrastructure(nmap,ffuf,masscan,nuclei,etc)         | https://github.com/pry0cc/axiom           |
| TEE resources for learning how to reverse-engineer(基本以学术论文为主) | https://github.com/enovella/TEE-reversing |



# Hacker CTF

* HACKvent 2019 Write Up

  https://sigterm.ch/2019/12/22/hackvent-2019-write-up/

* DefCon Archive

  https://archive.ooo/

* HIT Con 2020

  https://ctf2020.hitcon.org/dashboard/

* Google CTF 2020

  https://capturetheflag.withgoogle.com/

***备注***

​	 看看人家的writeups,希望明年有机会参加吧。。。。

#  优秀杂文分享

## 计算机杂文

| ==文献说明==                                                 | ==链接==                                                     | ==个人注解==                                                 |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 学习过去的计算机架构                                         | https://fabiensanglard.net/another_world_polygons/index.html | 最原始的色彩分析，图形学分析，好奇心驱使                     |
| 用Go构建一个新型的Bittorrent软件                             | https://blog.jse.li/posts/torrent/                           | 相比复杂的逻辑与算法设计，简单的思路貌似更有效               |
| 路径搜索算法的分析软文(😄)                                    | https://www.redblobgames.com/pathfinding/a-star/introduction.html | 结合数独游戏，这个东西应该很好理解的                         |
| 从头开始实现STL=兼容的hashmap                                | https://jguegant.github.io//jguegant.github.io/blogs/tech/dense-hash-map.html | 说实话，链接提及的博主另一篇SFNINE也是不错的文章             |
| SAT Solvers                                                  | 1. https://codingnest.com/modern-sat-solvers-fast-neat-underused-part-1-of-n/ <br>2. https://www.reddit.com/r/programming/comments/gd3eiy/modern_sat_solvers_fast_neat_and_underused_part_1/ | 安全分析与编译器研究过程中经常会用到SAT理论                  |
| gcc 是如何实现stdc++ vector container                        | https://www.reddit.com/r/cpp/comments/gi2m0i/how_does_gcc_implement_vector_containers_in_c_a/ | 虽然文章提起的实现方案不错，但我更加偏向与LLVM 关于vector container的实现机制 |
| C++ 中的Lambda使用                                           | https://brevzin.github.io/c++/2020/06/18/lambda-lambda-lambda/ | lambda分析，无需赘述                                         |
| Google Interview Questions Deconstructed: The Knight’s Dialer | https://alexgolec.dev/google-interview-questions-deconstructed-the-knights-dialer/ | 说实话，这个文章看着真压抑，在技术面试官面前，你考虑的往往欠充分(足够优秀的当我没说) |
| Learn Rust the Dangerous Way                                 | http://cliffle.com/p/dangerust/                              | Rust这门语言的设计逻辑可以参考下                             |
| Finding unique items - hash vs sort?                         | 1. https://douglasorr.github.io/2019-09-hash-vs-sort/article.html <br>2. https://news.ycombinator.com/item?id=21985246 | hash vs sort 方案对比                                        |
| Measuring Mutexes, Spinlocks and how Bad the Linux Scheduler Really is | 1. https://probablydance.com/2019/12/30/measuring-mutexes-spinlocks-and-how-bad-the-linux-scheduler-really-is/<br>2. https://news.ycombinator.com/item?id=21919988 | Linux Scheduler 调度器关于锁机制的分析                       |
| BMW Connected Apps Protocol                                  | 1. https://hufman.github.io/stories/bmwconnectedapps<br>2. https://news.ycombinator.com/item?id=22096600 | BMW APP 通信协议分析                                         |
| Full Proof that C++ Grammar is Undecidable                   | https://medium.com/@mujjingun_23509/full-proof-that-c-grammar-is-undecidable-34e22dd8b664 | C++较为有深度的研究Context的课题                             |
| Make LLVM fast again                                         | 1. https://nikic.github.io/2020/05/10/Make-LLVM-fast-again.html<br>2. https://news.ycombinator.com/item?id=23137345 | LLVM 组件足够臃肿，有必要好好分析的                          |
| PythonWheels解释                                             | https://pythonwheels.com/                                    |                                                              |
| SFINAE 解释(C++11以上)                                       | https://www.bfilipek.com/2016/02/notes-on-c-sfinae.html      | SFINAE解释分析                                               |
| All About Linux Signals Design and logic                     | https://www.linuxprogrammingblog.com/all-about-linux-signals |                                                              |
| Ultimate Guide to Python Debugging                           | https://martinheinz.dev/blog/24                              | Python Logging  终极指南                                     |
| Dynamic linking                                              | 1. https://drewdevault.com/dynlib.html <br>2. https://news.ycombinator.com/item?id=23654353 | 动态链接性能评估                                             |
| Removing the Linux /dev/random blocking pool                 | https://lwn.net/Articles/808575/                             | /dev/random testing                                          |
| 涉及部分有趣的编程思想设计以及部分教程(regex片段就不错)      | https://blog.robertelder.org/                                |                                                              |
| Comments on optimizations around string concatenation        | https://gist.github.com/llllllllll/7ad5905275233f1fb3868f4a67793616 | CPython String Concatenation的优化分析(3.8.5)                |
| Lockless algorithms for mere mortals                         | https://lwn.net/Articles/827180/                             | Lockless 设计算法分析                                        |
| WebRTC For The Curious                                       | 1.https://webrtcforthecurious.com/#webrtc-for-the-curious<br>2, https://news.ycombinator.com/item?id=24323589 | WebRTC 学习的最佳实践                                        |
| Exploring mullender.c - A deep dive into the first IOCCC winner | https://lainsystems.com/posts/exploring-mullender-dot-c/     | IOCCC tricky Code鉴赏                                        |

## 其他杂文

| ==标题==                                                 | ==链接==                                                     |
| -------------------------------------------------------- | ------------------------------------------------------------ |
| Mathematics for the adventurous self-learner(数学的魅力) | 1. https://www.neilwithdata.com/mathematics-self-learner<br>2. https://news.ycombinator.com/item?id=22400375 |
| Apple, ARM, and Intel                                    | 1. https://stratechery.com/2020/apple-arm-and-intel/?href=<br>2. https://news.ycombinator.com/item?id=23538894 |
| MegaEase的远程工作文化                                   | https://coolshell.cn/articles/20765.html                     |
| an engineer's guide to stock options                     | https://blog.alexmaccaw.com/an-engineers-guide-to-stock-options# |
| Nintendo DS Architecture                                 | https://www.copetti.org/writings/consoles/nintendo-ds/       |
| GCD and the magic of subtraction                         | https://plumsempy.com/2020/08/24/gcd-and-the-magic-of-subtraction/ |
| How To Write In Plain English                            | http://www.plainenglish.co.uk/how-to-write-in-plain-english.html |



# 优秀视频资源分享

| ==视频简介==                                               | ==链接==                                                     | ==个人注解==                                                 |
| ---------------------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| database indexing(数据库索引学习)                          | https://www.youtube.com/watch?v=HubezKbFL7E                  | 虽然身为一名安全人员，但是这个视频关于indexing的介绍还是对于coding以及代码审计有些许帮助的 |
| Faculty of Khan(物理学与数学资料)                          | https://www.youtube.com/channel/UCGDanWUzNMbIV11lcNi-yBg/videos | 对3Blue1Brown 的补充，基础学科学习的不二选择                 |
| Code Bullet                                                | https://www.youtube.com/channel/UC0e3QhIYukixgh5VVpKHH9Q     | 计算机AI相关的趣文视频                                       |
| Sudoku solver(使用Backtracking算法)                        | https://www.youtube.com/watch?v=rctRBFE7wmg                  | 个人认为较通俗易懂的解释方案                                 |
| GOD MODE UNLOCKED - Hardware Backdoors in x86 CPUs         | https://www.youtube.com/watch?v=_eSAF_qT_FY&list=PLH15HpR5qRsVAXGmSVfjWrGtGLJjIJuGe&index=10&t=0s | 不做过多解释，工作相关                                       |
| C++ Weekly                                                 | https://www.youtube.com/playlist?list=PLs3KjaCtOwSZ2tbuV1hx8Xz-rFZTan2J1 | C++ Tricks和新特性尝试的不二选择                             |
| Controlling Elegoo Robot Smart Car with ASIO and C++       | https://www.youtube.com/watch?v=nkCP95zLvSQ                  | 智能车的控制逻辑基于C++ ASIO款框架，说实话，玩硬件的感觉总是那么热血 |
| Exploring How Computers Work                               | 1. https://www.youtube.com/watch?v=QZwneRb-zqA<br>2. https://www.youtube.com/watch?v=I0-izyq6q5s | 从逻辑门开始探索计算机工作原理，这个作者的其他视频也是很不错的，至少让我弥补了大学的数电遗憾 |
| A Complete Guide to LLVM for Programming Language Creators | https://mukulrathi.co.uk/create-your-own-programming-language/llvm-ir-cpp-api-tutorial/c |                                                              |

# 不想做过多解释的Emacs(自2014年工作至今，最喜欢的Editor没有之一)

## 来自不同开发者的思考

> **State of C++ editing With Emacs**
>
> ​								***Redditor Author: /u/m_ninepoint***
>
> I'm posting to see if my experience mirrors that of others, and perhaps to  get ideas. As it is emacs has been my primary editor on Linux for years, and it's completely unusable.
>
> I've tried:
>
> - eglot/clangd
> - lsp/ccls
> - rtags
>
> All of them work to varying degrees on a clean project with minimal code. I test a clean blank-slate emacs config each time to ensure none of my  other configuration is interfering.
>
> However, the moment I try to use them on non-trivial projects (hundreds of  thousands of lines of code, more complicated code, etc), that's when  everything quite literally blows up. Clangd is utterly hopeless and  can't even find headers that plainly exist in the compile_commands file. On the flip side, clang crashes when trying to index certain files for  CCLS for reasons that elude me. Rtags has deficiencies which was what  brought about the LSP in the first place (hanging the editor seems to be the problem I run into the most).
>
> Is Emacs + C++ just an unmitigated disaster? Are these projects actually  used by people successfully for large codebases? I'd love to keep using  Emacs (I've been a user since 1997!), but I've lost too many hours at  this point.

## Emacs Themes

* https://github.com/hlissner/emacs-doom-themes



# 优秀的软件

| ==软件简介==            | ==链接==                                  | ==个人见解==                                                 |
| ----------------------- | ----------------------------------------- | ------------------------------------------------------------ |
| ZSTD(zstandard)压缩算法 | https://github.com/facebook/zstd          | 库的开发作者Yann Collet(Cyan4973)，@Facebook,主要从事数据压缩方向的，该作者还开发了很多其他压缩算法，值得学习 |
| Kiwi Browser            | https://github.com/kiwibrowser/src        | 如果有兴趣从事浏览器开发，可以参考下这个源码设计             |
| Briar                   | https://code.briarproject.org/briar/briar | 这个软件不多做解释，懂的人自然懂，基于WiFi or BlueTooth，软件的协议实现可以参考下，很不错的。 |
| Matrix                  | https://matrix.org/                       | 分布式的安全通信框架                                         |
| Detect It Easy          | https://github.com/horsicq/Detect-It-Easy | 虽然称不上足够优秀，但是可以作为私有HexEditor的参考库        |
| mimalloc                | https://github.com/microsoft/mimalloc     | 内存释放的巧妙设计                                           |
| Python For Browser      | https://github.com/brython-dev/brython    | 没啥可以聊的，直接参考Readme即可                             |
| KIRC                    | https://github.com/mcpcpc/kirc            | A tiny IRC client written in POSIX C99.                      |



# 尝试着读过的几篇PhD文章(虽然自己没有拿到，甚至Master都没拿到，😄)

| ==PhD Thesis==                                               | ==Reference==                                                |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| On the practical security of white-box cryptography          | https://tel.archives-ouvertes.fr/tel-02953586/document       |
| Greybox Automatic Exploit Generation for Heap Overflows in Language Interpreters | 1. https://seanhn.files.wordpress.com/2020/11/heelan_phd_thesis.pdf<br>2. https://sean.heelan.io/2020/11/18/phd-thesis-greybox-automatic-exploit-generation-for-heap-overflows-in-language-interpreters/ |

# 杂文

## 关于美国众议院的反垄断案的调查报告(雪球好文)(英文原版500多页，中文翻译版10万字左右，但是个人觉得真的是很不错的互联网调查报告)

1. [对美国众议院反垄断调查报告《数字市场竞争的调查》的翻译和思考（1）——Introduction](https://xueqiu.com/5995780717/161508243)
2. [对美国众议院反垄断调查报告《数字市场竞争的调查》的翻译和思考（2）——Background](https://xueqiu.com/5995780717/162209926)
3. [对美国众议院反垄断调查报告《数字市场竞争的调查》的翻译和思考（3）——Markets Investigated（1/2）](https://xueqiu.com/5995780717/163324103)
4. [对美国众议院反垄断调查报告《数字市场竞争的调查》的翻译和思考（4）——Markets Investigated（2/2）](https://xueqiu.com/5995780717/163323506)
5. [对美国众议院反垄断调查报告《数字市场竞争的调查》的翻译和思考（5）——Facebook（1/2）](https://xueqiu.com/5995780717/164463796)
6. [对美国众议院反垄断调查报告《数字市场竞争的调查》的翻译和思考（6）——Facebook（2/2）](https://xueqiu.com/5995780717/164464478)
7. [对美国众议院反垄断调查报告《数字市场竞争的调查》的翻译和思考（7）——Google（1/3）](https://xueqiu.com/5995780717/165841526)
8. [对美国众议院反垄断调查报告《数字市场竞争的调查》的翻译和思考（8）——Google（2/3）](https://xueqiu.com/5995780717/165842478)
9. [对美国众议院反垄断调查报告《数字市场竞争的调查》的翻译和思考（9）——Google（3/3）](https://xueqiu.com/5995780717/165843419)

## 段永平投资问答录(虽然只是个程序员，但是还是有勇气看这类文章的，哈哈)

[段永平投资问答录（商业逻辑篇）](https://xqdoc.imedao.com/174beedc1fc13d3fe1f6bc4d.pdf)

## 美国反对美国

**[AmericaOpposeAmerica](https://github.com/zealotCE/AmericaOpposeAmerica)**

书比较老了，不过依旧不影响理解和思考当年的美国地位

# Hacker News 好文

| ==标题==                                                     |
| ------------------------------------------------------------ |
| [Ask HN: What are you learning?](https://news.ycombinator.com/item?id=22786287) |
| [Ask HN: What is your blog and why should I read it?](https://news.ycombinator.com/item?id=22800136) |
| [Ask HN: What are your favorite low-coding apps / tools as a developer?](https://news.ycombinator.com/item?id=22786853) |

