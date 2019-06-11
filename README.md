# ZBCustomBackItem
**自定义全局返回按钮 保留侧滑返回手势**

下载后把文件拖入项目中即可

在.m的这个方法中修改你的全局自定义按钮:
```objc
- (void)cbi_viewDidLoad {
    
    //不在一级界面时添加自定义按钮
    if ([self.navigationController.viewControllers count] > 1) {
        //在这里自定义你需要的全局返回按钮
        UIBarButtonItem * leftItem = [[UIBarButtonItem alloc]
                                        initWithImage:[UIImage imageNamed:@"返回"] 
                                        style:UIBarButtonItemStylePlain 
                                        target:self 
                                        action:@selector(leftItemClick)];

        self.navigationItem.leftBarButtonItem = leftItem;
        
    }
    
    [self cbi_viewDidLoad];
}
```

如果想某个页面不用侧滑手势返回
就在该控制器的`viewDidAppear:`做如下操作关闭侧滑手势：
```objc
- (void)viewDidAppear:(BOOL)animated {
    [super viewDidAppear:animated];
    self.navigationController.interactivePopGestureRecognizer.enabled = NO;
}
```
如果要改变某个控制器的返回按钮，直接在`viewDidLoad`中自定义`leftBarButtonItem`就好了，会覆盖全局的。
