
### 原性能

time ./drltrace  -- locate aaaaa

```
real    3m7.544s
user    1m0.658s
sys     2m6.795s
```

filter：只打印 strlen , 1205 次
```
real    1m19.786s
user    0m59.208s
sys     0m20.433s
```

### 优化1在module加载时过滤而不是在func trace时  

```
real    2m50.408s
user    0m46.580s
sys     2m3.589s
```

filter：只打印 strlen , 1205 次

``` 
real    0m1.242s
user    0m1.096s
sys     0m0.021s
```

filter：只打印 memmove, 2110240 次


```
real    0m50.376s
user    0m15.290s
sys     0m34.968s
```

### 优化2在module加载时过滤，并且相关变量也从运行时搜索改为参数传递的固定地址访问


跟1 没区别

```
real    2m48.934s
user    0m44.542s
sys     2m4.125s
```

filter：只打印 strlen, 1205 次

real    0m1.234s
user    0m1.087s
sys     0m0.021s

filter：只打印 memmove, 2110240 次

```
real    0m50.412s
user    0m14.736s
sys     0m35.548s
```

### no dr_fprintf and no print args

time ./drltrace  -- locate aaaaa

```txt
real    1m36.693s
user    0m41.539s
sys     0m55.079s
```



### no dr_fprintf and no print  args and no print unknown call args


```
real    0m14.808s
user    0m14.778s
sys     0m0.030s
```


###


```txt
real    1m31.959s
user    0m22.370s
sys     1m9.420s
```