---
layout: post
title: Swift学习－UITableView & Navigation Controller
description: "Swfit Learning"
tags: [Swift]
---

今天学习的主要内容之一是UIKit中的UITableView。

UITableView包含两种delegate protocol，分别是UITableViewDelegate和UITableViewDataSource。

第一个的主要作用是对用户的操作做出反馈。例如 didSelectRowAtIndexPath()可以define在用户选择了某个行（indexPath）之后，delegate可做出的反馈。

第二个的主要作用是对数据的提取。例如cellForRowAtIndexPath()会返还给你在该行（indexPath）的cell，然后你可以对该cell做相关的处理，比如添加它textField的内容。再例如，numberOfRowInSection() 可以让你define该tableView总共有多少行——这一般取决于你的data model array的大小。

TableView的内容一般是由一个array来定义的。这个array可以array of struct，也可以是array of dictionaries。

记住，在Storyboard里建立新view controller，拖入table view后，需要将该table view的data source设定为当前view controller

————————————————————————

今天另一重点是Navigation Controller。其本质很简单，就是一个stack of view controllers，比如iOS自带的Settings。第一层是一个root view controller；点击一个新选项，这个新的view controllers就被push到stack上，然后被显示出来；点击返回后，这个view controller被pop，它下面的view controller就再次显示出来。

不同view controller之间的transition还是有三种方式：

1. code only - 从Storyboard中通过Identifier实例化新的view controller，然后downcast到这个view controller的type，定义完相关内容后，push到stack上
2. code & segue - 在Storyboard中建立新的segue (show)，from VC to VC，定义segue的identifier，然后在view controller 的file里定义prepareForSegue()。当然，还需要一个action来trigger这个segue——performSegueWithIdentifier()。
3. segue only - 通常是从一个button建立segue到一个新的view controller，然后在view controller 的file里定义prepareForSegue()。

~~~ swift
let resultVC = storyboard?.instantiateViewControllerWithIdentifier("ResultViewController") as! ResultViewController
navigationController?.pushViewController(resultVC, animated: true)
resultVC.property = 10
~~~
