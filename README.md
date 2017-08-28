# js 内存管理
[内存管理](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Memory_Management)

### 自动回收
`
    找出不再使用的变量，然后释放掉其占用的内存,
    消耗性能大，定期回收
`

###
- 引用
- 全局变量
```
只有在浏览器会话结才会释放，
```
- 局部变量
```
只在函数执行过种中存在，（堆和栈）
```

- 标记清除
- 引用计数
