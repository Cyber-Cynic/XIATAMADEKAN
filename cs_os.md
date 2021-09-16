### 虚拟内存
内存管理就在程序和物理内存之间引入了虚拟内存的概念，对进程地址和物理地址进行隔离

物理地址空间是有限的，虚拟地址空间可以是任意大小。程序可以通过操作虚拟地址，把虚拟地址空间映射到物理地址空间。
通过```缺页中断```和```swap机制```，实现虚拟地址映射。

### 连续分配内存 vs 碎片
连续分配内存的时候，RAM会固定大小（或者动态大小）为进程分配空间，进程使用完成后，这些空间就无法再次分配了（因为要连续分配）。  
碎片分为两种：
1. 内部碎片 Internal Fragmentation
2. 外部碎片 External Fragmentation  

https://afteracademy.com/blog/what-is-fragmentation-and-what-are-its-types

### 内部碎片
比如，RAM中都是固定大小的内存块，分配的内存大于进程所需的，就造成内部碎片。  
比如下图进程P1是3M  
![internal](https://s3.ap-south-1.amazonaws.com/afteracademy-server-uploads/what-is-fragmentation-and-what-are-its-types-internal-fragmentation-83dfb09baf456d21.jpg)   

那如何不让存在内部碎片呢？我们动态分配内存就好了。  

### 外部碎片
接上图，我们又分配了三个进程，我们发现有多个内部碎片，加起来有4M。假如又有一个4M的进程来，我们也无法将这空闲的4M给其分配。  
这就叫外部碎片。  
![external](https://s3.ap-south-1.amazonaws.com/afteracademy-server-uploads/what-is-fragmentation-and-what-are-its-types-external-fragmentation-846daa95c07f025f.jpg)  

那如何解决外部碎片呢，我们通过不连续的内存分配技术。

### 不连续的内存分配技术
1. 分页（Paging）
2. 分段（Segmentation）

https://afteracademy.com/blog/what-are-paging-and-segmentation

### 分页
辅助存储器中叫页，主存储器中叫帧，划分为```等大```的区域。  

逻辑地址 to 物理地址  
Logical Address = Page Number + Page Offset  
Physical Address = Frame Number + Page Offset  
![page](https://s3.ap-south-1.amazonaws.com/afteracademy-server-uploads/what-are-paging-and-segmentation-paging-diagram-83049c7d4fcd94d0.jpg)

问题：
1. 由于帧是固定大小的，所以还可能出现内部碎片
2. 中间增加了一层转换，速度慢了
3. 每个进程都要维护一个pagetable，开销大

### 分段
将进程划分为多个大小不一的模块或者片段。

逻辑地址 to 物理地址
Logical Address = Segment Number + Segment Offset  
![segment](https://s3.ap-south-1.amazonaws.com/afteracademy-server-uploads/what-are-paging-and-segmentation-segmentation-diagram-ccb18429e8be5934.jpg)

