eBPF（Extended Berkeley Packet Filter）是一种强大的技术，它允许在Linux内核中运行沙盒化的程序，而无需修改内核源代码或加载内核模块。以下是一个eBPF快速入门指南，将帮助你开始使用eBPF进行开发。

## 准备开发环境

1. **安装Linux内核**：你需要一个较新版本的Linux内核（至少4.8版本，推荐5.15+或6.2+），以支持eBPF功能。如果可能，安装新版本的Ubuntu（例如23.10）会更好[2]。

2. **安装LLVM和Clang**：这些是编译eBPF程序所必需的工具。使用`clang --version`来检查你安装的LLVM版本[6]。

3. **安装必要的开发包**：对于Debian/Ubuntu系统，通常需要安装`libbpf-dev`。对于Fedora系统，需要`libbpf-devel`[6]。

4. **安装内核头文件**：对于AMD64 Debian/Ubuntu，安装`linux-headers-amd64`。对于Fedora，安装`kernel-devel`[6]。

## 开始编写eBPF程序

1. **创建eBPF C程序**：编写一个简单的eBPF C程序，例如一个用于计数的程序。你可以在一个空目录中创建一个名为`counter.c`的文件，并在其中编写eBPF程序[3][6]。

2. **编译eBPF程序**：使用`bpf2go`工具来编译你的eBPF C程序，并生成一些框架代码，这些代码将用于将eBPF程序加载到内核并与之交互。创建一个包含`//go:generate`语句的`gen.go`文件，这将在运行`go generate`时调用`bpf2go`[3][6]。

3. **设置Go模块**：使用`go mod init`命令来声明一个Go模块，并使用`go mod tidy`来添加模块需求和总结。你还需要手动添加对`bpf2go`的依赖，因为它不是由.go源文件显式导入的[3][6]。

## 加载和使用eBPF程序

1. **编写Go应用程序**：创建一个`main.go`文件，并在其中编写Go应用程序代码，以加载eBPF程序到内核，并定期显示其输出[3][6]。

2. **运行你的应用程序**：使用`go build`来构建你的应用程序，然后使用`sudo ./你的应用程序名`来运行它。如果一切顺利，你的eBPF程序将被加载到内核，并开始执行[3][6]。

## 学习资源

- **阅读书籍**：Liz Rice的《What is eBPF?》和《Learning eBPF》以及Brendan Gregg的《BPF Performance Tools》是入门的好资源[4]。
- **查看在线资源**：访问eBPF相关的网站和GitHub仓库，例如ebpf.io和cilium/ebpf，以获取更多的教程和示例代码[1][3][7]。
- **观看视频教程**：例如，Liz Rice在Isovalent的YouTube频道上的eBPF入门教程[8]。

通过上述步骤，你可以开始探索eBPF的世界，并逐步学习如何开发和使用eBPF程序。记住，eBPF是一个复杂的技术，需要时间和实践来掌握。

Citations:
[1] https://github.com/lizrice/ebpf-beginners
[2] https://eunomia.dev/tutorials/1-helloworld/
[3] https://github.com/cilium/ebpf/blob/main/docs/ebpf/guides/getting-started.md
[4] https://ebpf.io/get-started/
[5] https://eunomia.dev/tutorials/0-introduce/
[6] https://ebpf-go.dev/guides/getting-started/
[7] https://ebpf.io
[8] https://www.youtube.com/watch?v=TJgxjVTZtfw&t=0
