需要 <algorithm>

sort(first,last,cmp)

#其中将[first,last)中的元素进行排序!

cmp函数是排序方法

如:

```c++
bool cmp(wty p, wty q)//wty is a struct
{
	return p.year<q.year;
}
//当p.year大于q.year时，让p.year排在q.year前边
//当xx真，让a排在b后边
```

关于<cstring>中

str.find('anyChar'/"anySubStr")!=npos//找得到时返回true