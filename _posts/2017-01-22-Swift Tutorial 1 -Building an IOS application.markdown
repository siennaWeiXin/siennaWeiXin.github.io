---
title: Swift Tutorial Building an iOS application
layout: post
guid: urn:uuid:5b350d8d-f734-420c-8177-6a69534c95dc
tags:
  - translation
---

<p>翻译来自Jack Watson-Hamblin的文章</p> 
<br><a href= "https://www.airpair.com/swift/building-swift-app-tutorial/">Swift Tutorial: Building an iOS application</a>
 

<post no-compile><h2 id="1-introduction">1 Introduction</h2>
<p>在2014年WWDC大会上发布的Swift引爆了全世界的Apple开发者。随着Swift这种新兴语言的诞生，已经不存在真正的专家可言，对于设计模式的探索一刻也未曾停歇。</p>
<p>但所有的困难的都不会阻止我们做一些真正实用的东西出来，因为，作为程序员，不应该让新产生的事物成为创造道路上的阻碍。</p>
<h2 id="2-what-you-need">2 What You Need</h2>
<p>在这个系列中，我们会用Swift创建一个IOS app，在此之前，你需要准备三样东西：</p>
<ul>
<li>一个装载Mavericks或者Yosemite的MAC</li>
<li><a href="https://itunes.apple.com/au/app/xcode/id497799835?mt=12">Xcode 6</a></li>
<li>对Swift有个基本的认识，如果没有，你可以从这里获取<a href="http://www.airpair.com/swift/learning-swift-tutorial">Swift Reference Guide</a></li>
</ul>
<h2 id="3-getting-started">3 Getting Started</h2>
<p><img src="http://i.imgur.com/1DNlxoz.png" alt="Figure 1.3.1 - Choose Master Detail Application"></p>
<p>当你安装好Xcode后，启动Xcode并新建一个Project(Cmd+Shift+N),在template selector中，确保“iOS &rarr; Application”被选中, 并且选中“Master-Detail Application” 。</p>
<p>这个模版包含一个建立好的Storyboard，一个controller（主控制器和局部控制器）。</p>
<p>之所以要选用这个模版，是因为你即将做多个类似于“Hello World”页面的IOS 应用 －－ 任务清单应用。</p>
<p>当你选择“Master-Detail Application”后，点击“Next”进入建立项目的下一个步骤。</p>
<p><img src="http://i.imgur.com/ZfaPfM2.png" alt="Figure 1.3.2 - Project options"></p>
<p>在新建项目的下一个页面，需要做一些设置。</p>
<p>在“Product Name”填上给这个项目起的名字， 我把这个项目称为“TaskMe”, 你可以随便起个名字。</p>
<p>下一步确保你的“Organization Name” 填写正确, 然后在“Organization Identifier” 填写一个工作域名用于识别，比如我就用“com.airpair”.</p>
<p>“Organization Identifier” 可以帮助你创建一个标识符，用于给自己的APP一个唯一的名字。</p>
<p>在“Language” 的下拉菜单里面，选择“Swift”而不是“Objective-C”。这保证我们的程序是用swift语言的编译器来生成代码。</p>
<p>最后，在“Devices”的下拉菜单中选择“iPhone”，并且确保“Use Core Data” 没有被选择。Core Data很值得学习，但是目前我们只是对创建一个IOS应用的核心功能做一个大概的介绍。</p>
<h2 id="4-learning-by-example">4 Learning By Example</h2>
<p>在你正式着手编写代码的时候，先看一下你能从这个采用“Master-Detail Application” 模版创建的代码中学到些什么。</p>
<p>现在的项目已经是一个可以运行的应用，所以你可以编译运行(Cmd+R)一下程序看看已经能够做些什么了。</p>
<p><img src="http://i.imgur.com/iPchsZg.png" alt="Figure 1.4.1 - List screen in your new application"></p>
<p><img src="http://i.imgur.com/DjPnlLC.png" alt="Figure 1.4.2 - Detail screen in your new application"></p>
<p>当你开始运行这个项目时，你可以看到主界面上有一个“+” 和“Edit” 的按钮。点击“+” 会在列表中添加一个date/time行，单击新建的这一行，可以跳转到另外一个界面，这个界面是主界面那一行的详细信息，你可以看到日期信息放在中间。在列表界面上，你可以通过拖动已有的行直到出现“delete”的字样，然后点击删除，或者点击“edit”进入编辑模式，将其删除。</p>
<p>下面我们具体看看Xcode生成的代码。</p>
<h3 id="4-1-appdelegate-swift">4.1 AppDelegate.swift</h3>
<p>程序的入口是<code>AppDelegate.swift</code> 文件, 所以我们先从这个文件的代码开始探索。</p>
<p>忽略在文件顶部的标注，代码的第一行是<code>import UIKit</code>。这一行代码旨在让你可以访问<code>UIKit</code>文件中的所有内容。如果你在之前编写过Objective－C，就会这个很熟悉。和Objective－C为一个类或者框架导入一个头文件不同的是，Swift导入的是模块。导入是每个IOS应用文件里面都具有的，要么导入<code>UIKit</code>，或者一些简单的文件，比如<code>Foundation</code>。</p>
<p>下一行是<code>@UIApplicationMain</code>。与其他语言不同的是，Swift没有main文件，在应用程序中，需要在相应的Swift Class的文件中添加这一行已表示为程序入口。<a href="https://developer.apple.com/library/ios/documentation/Swift/Conceptual/Swift_Programming_Language/Attributes.html#//apple_ref/doc/uid/TP40014097-CH35-XID_515">attribute</a> 。你可能永远不需要变动Xcode对于程序入口的设置，但是最好是你能够知道这行代码是用来做什么的。</p>
<p>现在你已经拥有一个<code>AppDelegate</code>类的定义。 你可以看到这个类继承自<code>UIResponder</code>，和<code>UIApplicationDelegate</code> <a href="https://developer.apple.com/library/ios/documentation/Swift/Conceptual/Swift_Programming_Language/Protocols.html#//apple_ref/doc/uid/TP40014097-CH25-XID_390">协议。</a>从Objective-C过来，这个语法已经有了很大的改善。</p>
<!--code lang=swift linenums=true-->
<pre><code>class AppDelegate: UIResponder, UIApplicationDelegate {
</code></pre><p>看一下<code>AppDelegate</code> 类的实现，你可以发现并没有太多内容。首先你得到一个<code>window</code>变量，然后一大堆空的或者说几乎空着的方法。</p>
<p>唯一的一个有执行语句的方法是<code>application:didFinishingLaunchingWithOptions:</code> ，但是只是有一个简单的返回语句。</p>
<!--code lang=swift linenums=true-->
<pre><code>func application(application: UIApplication, didFinishLaunchingWithOptions launchOptions: [NSObject: AnyObject]?) -&gt; Bool {
  // Override point for customization after application launch.
  return true
}
</code></pre><p>发生了什么？为什么这个应用还可以运行？这是因为有一些机制作用在屏幕后方。在你的项目的设置中，Main.storyboard文件已经被设置为应用的运行起点，当程序被启动时，就会生成窗口和控制器。</p>
<p>这里唯一值得一提的是对于窗口变量的定义。</p>
<!--code lang=swift linenums=true-->
<pre><code>var window: UIWindow?
</code></pre><p>这是为了给T<code>AppDelegate</code> 类创建一个<a href="https://developer.apple.com/library/ios/documentation/Swift/Conceptual/Swift_Programming_Language/TheBasics.html#//apple_ref/doc/uid/TP40014097-CH5-XID_483">optional变量</a> <code>UIWindow</code> , 表示为<code>UIWindow?</code>, 即在类型名后面加上一个问话。</p>
<p>如果你没有学过optional，简单来说就是这个变量可以被赋予一定值，也可以就是一个<code>nil</code>, 但是我强烈建议你去了解一下optional，因为用Cocoa Touch框架会经常用到。 </p>
<p>对于optionals一个很重要的知识点是它们在参数类型中的应用，你在swift的代码中有的类型定义里会看到末尾有一个感叹号，这个叫做“implicitly unwrapped optional”。</p>
<!--code lang=swift linenums=true-->
<pre><code>@IBOutlet weak var detailDescriptionLabel: UILabel!
</code></pre><p>implicitly unwrapped optional 和optional之间的区别在于，如果你对一个没有值的变量采用implicitly unwrapped optional 会有运行错误，但是如果你用optional来表示就是正确的。所以当我们确信一些变量一定是会有值的时候才可以使用implicitly unwrapped optional，不然就会发生严重的错误。</p>
<p>你也许还会发现函数的第二个参数<code>application:didFinishLaunchingWithOptions:</code> 有两个名称，第一个<code>didFinishLaunchingWithOptions</code>表示的是外部在调用这个函数的时候的参数名称，第二个<code>launchOptions</code>则是该参数在函数体内部相对应的名称。</p>
<!--code lang=swift linenums=true-->
<pre><code>func application(application: UIApplication, didFinishLaunchingWithOptions launchOptions: [NSObject: AnyObject]?) -&gt; Bool {
</code></pre><h3 id="4-2-masterviewcontroller-swift">4.2 MasterViewController.swift</h3>
<p>打开<code>MasterViewController.swift</code> 文件，你会看到这里面包含了很多内容，首先看到导入<code>import</code> ，你还会发现 <code>MasterViewController</code> 类是继承 <code>UITableViewController</code>类。我不会逐行逐句地解释这些代码，但是我会呈现出一些有趣的swift相比与objective－C有进步的地方。 </p>
<p>对代码进行一个快速的浏览，首先最快看到的是T<code>override</code> 的应用。</p>
<!--code lang=swift linenums=true-->
<pre><code>override func awakeFromNib() {
override func viewDidLoad() {
override func didReceiveMemoryWarning() {
</code></pre><p>因为类中大部分的函数都在父类中定义，或者在某个遗传链中定义，如果你确定要在自己的子类里面重写或者拓展父类的方法，就要用override来标注，避免意外命名一个和父类函数相同名称的函数而造成的错误。</p>
<p><code>MasterViewController</code> 类的第一部分是一个对象变量的定义，用<code>NSMutableArray()</code>进行初始化.</p>
<!--code lang=swift linenums=true-->
<pre><code>var objects = NSMutableArray()</code></pre>
<p>当视图在控制器中被加载之后，方法<code>viewDidLoad</code> 被调用，这个方法通过调用父类的方法，这个方法创建了大多数我们现在看到的东西。</p>
<p>接下来设置左边和右边的按钮，有趣的是对于按钮<code>addButton</code>的定义是用常量, 这就表示这个按钮一旦定义之后就不再改变了，另外一部分就是<code>UIBarButtonItem</code>的初始化。</p>
<!--code lang=swift linenums=true-->
<pre><code>UIBarButtonItem(barButtonSystemItem: .Add, target: self, action: &quot;insertNewObject:&quot;)
</code></pre><p>不像是在Objective-C中所用的语句，设置按钮必须先调用<code>alloc</code> ，再调用<code>initWithWhatever:</code>, 现在这些函数都不需要了，只用在函数中配置一些参数。</p>
<p>再看函数<code>insertNewObject:</code>，我们会发现传入参数是<code>AnyObject</code>。</p>
<!--code lang=swift linenums=true-->
<pre><code>func insertNewObject(sender: AnyObject) {
</code></pre><p>在这个函数中，我们什么事情都不用做，所以再看下一个函数<code>tableView:cellForRowAtIndexPath:</code>。</p>
<!--code lang=swift linenums=true-->
<pre><code>override func tableView(tableView: UITableView, cellForRowAtIndexPath indexPath: NSIndexPath) -&gt; UITableViewCell {
  let cell = tableView.dequeueReusableCellWithIdentifier(&quot;Cell&quot;, forIndexPath: indexPath) as UITableViewCell

  let object = objects[indexPath.row] as NSDate
  cell.textLabel?.text = object.description
  return cell
}
</code></pre><p>在函数<code>tableView:cellForRowAtIndexPath:</code>的第一行，我们调用<code>dequeueReusableCellWithIdentifier:forIndexPath:</code> ，这个函数的返回值是<code>AnyObject</code>。</p>
<p>因为可以返回任意对象类型，可以用<code>as UITableViewCell</code>来限定类型，就像这一行最后所写。接下来可以用<code>TaskCell</code> 将返回类型定义为之后自己定义的类型。</p>
<h3 id="4-3-detailviewcontroller-swift">4.3 DetailViewController.swift</h3>
<p>接下来我们看看文件<code>DetailViewController</code>，这个文件比MasterViewController小很多,但是依旧有很多值得学习的案例。</p>
<p>首先我们把<code>@IBOutlet</code>属性附加在<code>detailDescriptionLabel</code> 变量上，就像Objective-C的头文件里，属性<code>@IBOutlet</code>让接口知道<code>DetailViewController</code>的特性。</p>
<!--code lang=swift linenums=true-->
<pre><code>@IBOutlet weak var detailDescriptionLabel: UILabel!
</code></pre><p>你还会注意到这个变量被定义为弱变量，因为我们并不想<code>DetailViewController</code>真正成为这个view 的所有者。</p>
<p>接下来你会看到变量属性定义的一个有趣的地方，这个属性附加了一些代码，这些代码定义了这个属性的行为。</p>
<!--code lang=swift linenums=true-->
<pre><code>var detailItem: AnyObject? {
  didSet {
    // Update the view.
    self.configureView()
  }
}
</code></pre><p>首先你有一个可选性变量<code>AnyObject?</code>, 这段代码中有趣的部分是<code>didSet</code>。</p>
<p><a href="https://developer.apple.com/library/ios/documentation/Swift/Conceptual/Swift_Programming_Language/Properties.html#//apple_ref/doc/uid/TP40014097-CH14-XID_368">Properties</a> 可以有一个代码块来执行并返回特定的事件。这里最惊喜的部分就是你可以不用专门定义一个setter函数，而是可以给出一个更详细的定义。</p>
<p>当<code>detailItem</code>被定义之后，视图中的有些地方改变了，所以<code>configureView</code> 要重新被调用。这些回调函数是IOS应用程序开发的一大进步。</p>
<p>可以提前告诉大家，多去看看<a href="https://developer.apple.com/library/ios/documentation/Swift/Conceptual/Swift_Programming_Language/TheBasics.html#//apple_ref/doc/uid/TP40014097-CH5-XID_483">optionals</a>相关的内容，因为它们经常在开发中用到，这里又是另外一个运用可变变量的场景。</p>
<!--code lang=swift linenums=true-->
<pre><code>func configureView() {
  // Update the user interface for the detail item.
  if let detail: AnyObject = self.detailItem {
    if let label = self.detailDescriptionLabel {
      label.text = detail.description
    }
  }
}
</code></pre><p>在这里optional用在if 语句中，这表示如果赋值符号右边的变量有值的话，就可以赋给赋值符号左边的变量，另一方面，如果右边的变量没有值，if 语句的执行语句就会被跳过，这里的做法和Objective－C中的<code>nil</code> 相似，但是更加安全。</p>
<h2 id="5-coming-up-next">5 Coming Up Next</h2>
<p>在这个部分你没有真正的开始写代码，但是你看到了一些更重要的东西，你看到了Swift是怎么对Cocoa Touch中的类以及API产生的影响，如果你不先了解这些，就不能很通畅的写代码。</p>
<p>现在学的这些东西是为了让程序开发的更加安全，而不用破坏语言的快捷性。</p>
