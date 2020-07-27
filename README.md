# goos
GPM 多线程协程调度器 for PHP Extension

## config & install
```asciidoc
> cd /path/to/goos
> php7.3.5-ize
> ./configure --with-php-config=php7.3.5-config
> make install
> echo 'extension=go.so' >> phpetcpath/php.ini 


```

## demo
```php
<?php
Runtime::GOMAXPROCS(10);
for($i = 0;$i <100; $i++)
{
    go(function()use($i){
       go(function(){
            echo "go yield  \n";
            goyield();
            echo "go end \n";
       });
    });
}

Runtime::wait();
```

## @G-M 多线程调度
- [x] 实现任意协程G创建后，自动绑定到线程M上去执行
- [x] 实现多线程协程G调度让出与恢复
- [ ] 优化php函数的拷贝与释放，更好的隔离内存申请与安全释放
- [ ] ... 

## @G-P-M 任务窃取调度

## @G-P-M 信号抢占调度

