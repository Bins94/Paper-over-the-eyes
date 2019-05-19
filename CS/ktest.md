# systemtap path
https://www.systutorials.com/docs/linux/man/7-stappaths/
# S2E
https://dslab.epfl.ch/pubs/s2e-tocs.pdf
# A survey of symbol execution techniques
https://arxiv.org/pdf/1610.00502.pdf

# SemFuzz: Semantics-based Automatic Generation of Proof-of-Concept Exploits
https://www.informatics.indiana.edu/xw7/papers/p2139-you.pdf
基于patch和漏洞描述确认syscall以及相应的一些分析加权,重现漏洞,直接用涉及的内核函数所对应的corpus进行fuzz会不会更有效

# AFL 优化
https://lifeasageek.github.io/class/cs52700-fall16/pages/prog-assignment-1.html
拆分分支条件, 渐进式协助命中目标, 用到 QEMU 的 TCG

# ThreadSanitizer
https://clang.llvm.org/docs/ThreadSanitizer.html
tutorial
https://github.com/google/sanitizers/wiki/ThreadSanitizerAlgorithm
在访问内存周围插入指令调处理函数+运行时调用处理函数, 维护针对变量的shadow state, 报错由状态机检测产生

# Fuzz summery
https://www.mwrinfosecurity.com/our-thinking/15-minute-guide-to-fuzzing/

# T-fuzz
https://nebelwelt.net/publications/files/18Oakland.pdf
除了常规的fuzz, 针对性的越过部分检查做局部fuzz, 再判断bug存在的条件, NCC/CC 检查

# symdriver
http://pages.cs.wisc.edu/~swift/papers/symdrive_osdi2012.pdf
framework:路径优先级，数据注入，I/O符号化模拟
Execution tracing:版本对比
instrument:代码级别修改？
checker:内核驱动模块状态跟踪通过实现自己的库

# Linux driver verification
https://pdfs.semanticscholar.org/773e/780f13727ecf4205072c14562872a07df903.pdf
指针分析和动态数据分析
符号化验证
状态验证
终止状态验证
并发
