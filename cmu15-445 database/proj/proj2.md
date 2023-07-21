# Extendible Hash Index

> [Extendible Hashing - Data Structures](https://www.youtube.com/watch?v=cmneVtDrhAA)

## 思路

### LRU

只要能够实现弹出最后使用的frame即可。

### BufferPoolManagerInstance

只需要理解到一个page和存放这个page的frame只可能三种状态：

+ 被锁定Pinned：此时，该frame被锁定，它保存的page正在被上层使用，即：该page的`pin_count_`大于等于1；
+ 空闲Ready：此时，该frame被`free_list_`管理。逻辑上，它未保存任何有效page；物理上，它保存的页元数据全为0；
+ 待释放Wait：此时，该frame被`replacer_`管理，它保存的page未被上层使用，即：该page的`pin_count_`等于0。

### ParallelBufferPoolManager

理解映射关系就行了。

## 踩的坑

+ 提交格式一定按要求，且要使用check-format、check-clang-tidy和check-lint检查代码格式。

``` bash
.
├── buffer
│   ├── buffer_pool_manager_instance.cpp
│   ├── lru_replacer.cpp
│   └── parallel_buffer_pool_manager.cpp
└── include
    └── buffer
        ├── buffer_pool_manager_instance.h
        ├── lru_replacer.h
        └── parallel_buffer_pool_manager.h
```

+ 在BufferPoolManagerInstance的UnpinPgImp函数里，注意只有参数`is_dirty`为真时，才能修改，否则，可能出现原本元数据已经为真，反而被修改成假了。

``` c++
if (is_dirty) {
    pages_[frame_id].is_dirty_ = is_dirty;
}
```

+ 在BufferPoolManagerInstance的DeletePgImp函数里，记得要把脏页写入磁盘。

``` c++
if (pages_[frame_id].IsDirty()) {
    disk_manager_->WritePage(page_id, pages_[frame_id].GetData());
  }
```

+ 在ParallelBufferPoolManager的成员函数中，仅NewPgImp需要使用锁。此外，其余函数不要使用assert等判断，否则会超时。
