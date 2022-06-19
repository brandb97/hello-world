一个内存分配算法的讨论：
```C
struct vma *vmainit(unsigned long start, unsigned long end);
unsigned long vmaalloc(struct vma *vmap, unsigned long len);
unsigned long vmadealloc(struct vma *vmap, unsigned long addr, unsigned long len);

```

定义一个数据结构`struct vma`，来实现上面的三个函数。

`vmainit`：用空闲地址的开始地址和结束地址初始化一个`struct vma`对象，并返回指向这个对象的指针。

`vmaalloc`：分配一块长度为`len`的内存，并返回内存的首地址。出现错误则返回NULL。

`vmadealloc`：释放一块从`addr`开始，长度为`len`的内存。返回实际释放的长度，出现错误则返回0。

如果增加一个限制：
```C
#define NVMA 16
struct vma {
	unsigned long start;
	unsigned long end;
	
	struct {
		unsigned long vma_start;
		unsigned long vma_end;
	} vma_recorders[NVMA];
}
```
你又要怎么样作实现？

feel free to contribute any code.
