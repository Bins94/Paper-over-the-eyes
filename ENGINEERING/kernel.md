# Book of linux kernel

## Understanding Linux kernel
http://www.johnchukwuma.com/training/UnderstandingTheLinuxKernel3rdEdition.pdf

## Linux kernel development
https://github.com/yuanhui-yang/Linux-Kernel-Development/blob/master/Linux%20Kernel%20Development%20-%203rd%20Edition.pdf

## Professional Linux Architecture 
http://cse.yeditepe.edu.tr/~kserdaroglu/spring2014/cse331/termproject/BOOKS/ProfessionalLinuxKernelArchitecture-WolfgangMauerer.pdf

 
# Network

## Kernel ipv6
http://www.tldp.org/HOWTO/Linux+IPv6-HOWTO/

## tun device
http://www.cis.syr.edu/~wedu/seed/Labs/VPN/files/simpletun.c

## socket repair queue
https://lwn.net/Articles/495304/

# Kernel hook

## Ptrace tutorial
http://www.linuxjournal.com/article/6100

## Tracepoint set
https://lwn.net/Articles/346470/

## Using the TRACE_EVENT() macro
https://lwn.net/Articles/379903/

## eBPF introduction
https://lwn.net/Articles/740157/
http://www.brendangregg.com/ebpf.html

## kprobe & jprobe
https://opensourceforu.com/2011/04/kernel-debugging-using-kprobe-and-jprobe/

## bpf guide
https://github.com/iovisor/bcc/blob/master/docs/reference_guide.md#2-bpf_hash
https://lwn.net/Articles/747640/

https://lwn.net/Articles/driver-porting/

# ELF
## Introduction to ELF
http://people.redhat.com/mpolacek/src/devconf2012.pdf


# Memory
## Understanding the linux virtual memory manager
https://pdos.csail.mit.edu/~sbw/links/gorman_book.pdf

## Linux memory manerger 
http://www.stillhq.com/pdfdb/000446/data.pdf

## Process address space
https://www.utdallas.edu/~zxl111930/spring2012/public/lec11-handout.pdf
* 图文并茂

## Page fault error code
https://lkml.org/lkml/2015/2/28/243

## VMA -> page -> pfn
http://duartes.org/gustavo/blog/post/how-the-kernel-manages-your-memory/

# Kernel vm base  
```  
arch/x86/include/asm/page_32_types.h:#define __START_KERNEL_map __PAGE_OFFSET
arch/x86/include/asm/page_64_types.h:#define __START_KERNEL_map _AC(0xffffffff80000000, UL)
```  