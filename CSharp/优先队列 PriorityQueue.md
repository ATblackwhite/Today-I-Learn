微软终于在2021-2022期间发行的.net6中加入了优先队列PriorityQueue

[官方文档链接](PriorityQueue<TElement,TPriority> Class (System.Collections.Generic) | Microsoft Learn](https://learn.microsoft.com/en-us/dotnet/api/system.collections.generic.priorityqueue-2?view=net-8.0))
[简单介绍视频地址](【C#/.NET6新特性之 PriorityQueue 优先队列来啦！十年前我就在吐槽了！】 https://www.bilibili.com/video/BV1Qq4y1y7bb/?share_source=copy_web&vd_source=d9dc9426a85979e29b2d7aa0ecced0e9)

示例
```C#
using System.Collections.Generic;
using System;
namespace HelloCS
{
    internal class Program
    {
        static void Main(string[] args)
        {
            PriorityQueue<int, int> queue = new PriorityQueue<int, int>();
            queue.Enqueue(2, 2);
            queue.Enqueue(3, 3);
            queue.Enqueue(1, 1);
            while (queue.Count != 0)
                Console.WriteLine(queue.Dequeue());
        }
    }
}

```
结果为1 2 3