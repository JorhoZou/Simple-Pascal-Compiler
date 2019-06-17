### A simple compiler for SPL

本项目实现了一个基于SPL(simple pascal language)语法的编译器，支持整型、浮点运算，类型声明，函数调用，全局、局部变量，引用传值，所有种类的statement（如assign_stmt, if_stmt等）等。
编译器的编写使用c++，采用flex + bison + llvm的模式。

实验环境
Linux 4.4.0-43-Microsoft(wsl)
gcc version 5.4.0 (GCC)
bison (GNU Bison) 3.0.4
flex 2.6.4
llvm version 6.0.0
clang

code/ 文件夹中
buildGraph.c用来生成语法树的可视化效果
Lex_Analysis.c是用flex解析Lex_Analysis.l得到的文件
parse.c parse.h是用bison解析parse.y得到的文件
AST.c AST.h定义了抽象语法树的节点
codegen.cpp codegen.h用于语义分析和代码生成
main.c 用来生成编译器(我们放了一个我们编译得到的main)

test/ 文件夹中
test2.spl test4.spl test6.spl为一些简单的测试样例
test.spl为控制流语句的测试样例

run.sh 脚本使用方法如下：
生成编译器：
./run.sh -g

使用生成的编译器编译test.spl程序(可得到test.ll文件)并运行(需要安装clang)
./run.sh -c test.spl
(注：如果没装clang，可以在它提示错误之后执行
lli test.ll
使用llvm提供的lli运行test.ll

gen.sh使用方法如下：
获得test.spl程序的可视化语法树:
./gen.sh test.spl
