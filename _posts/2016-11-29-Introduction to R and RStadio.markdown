---
title: Introduction to R and RStudio
layout: post
guid: urn:uuid:7ce253a7-8f42-47a2-9dfd-60fc5653b838
tags:
  - translation
---
<p>翻译来自Bruno Skvorc的文章 <a href= "http://www.sitepoint.com/introduction-r-rstudio/">Intuoduction to R and RStadio</a>

<p>随着计算能力的增加，导致有大量的免费数据可访问。人们用数据来记录他们的运动量，卡路里消耗，健康程度和睡眠质量；政府出版数据研究报告；公司在用户测试的时候也需要数据分析。 </p>
<p><img src="http://dab1nmslvvntp.cloudfront.net/wp-content/uploads/2015/04/1428511658Fotolia_73597168_Subscription_Monthly_M-Resized.jpg" alt="Graphs and Analytics" title=""/></p>
<p>在这篇文章中，我们将介绍一些关于R语言编程的基础知识&#8211; 一种关门为统计计算而开发的语言.我不会用<a href="http://en.wikipedia.org/wiki/R_%28programming_language%29">维基百科</a>来进行介绍 &#8211; 而是深入到语言本身。在这篇文章涵盖了IDE和语言的安装，以及R的数据类型介绍。</p>
<h3 id="ide-areas">安装</h3>
<p>R是一种编程语言，同时也是一种软件环境，也就意味着这两个方面的安装都需要包含，所以安装步骤主要有两个：</p>
<ul>
<li>下载并安装最新的R: <a href="http://www.r-project.org/">http://www.r-project.org/</a></li>
<li>下载并安装RStudio: <a href="http://www.rstudio.com/">http://www.rstudio.com/</a></li>
</ul>
<p>这两个都是免费的并且开源的。R语言作为RStudio进行计算的底层引擎，同时RStudio能够提供简单的数据样例，命令行的自动填充，帮助文件，以及一个高效的交互界面能够帮助提高编程效率。你也可以如果其他编程语言一样在文本文件里面编写R，但是文本文件不会推荐相应的命令行，这样当你要完成复杂的计算时，会降低工作效率。</p>
<p>当你安装了R Studio之后，启动工具。</p>
<p><a href="http://dab1nmslvvntp.cloudfront.net/wp-content/uploads/2015/04/1428512117Screenshot-2015-04-08-18.53.44.png"><img src="http://dab1nmslvvntp.cloudfront.net/wp-content/uploads/2015/04/1428512117Screenshot-2015-04-08-18.53.44.png" alt="RStudio IDE" class="alignnone size-full wp-image-103000"/></a></p>
<h3 id="ide-areas">IDE界面</h3>
<p>简单介绍一下GUI。主要包括四个方面，首先我要解释一下Default Order，你可以在Settings/Preferences -&gt; Pane Layout里面改变设置。</p>
<h4 id="the-editor">编辑器</h4>
<p><a href="http://dab1nmslvvntp.cloudfront.net/wp-content/uploads/2015/04/1428512319Screenshot-2015-04-08-18.57.12.png"><img src="http://dab1nmslvvntp.cloudfront.net/wp-content/uploads/2015/04/1428512319Screenshot-2015-04-08-18.57.12.png" alt="The Editor" width="684" height="421" class="alignnone size-full wp-image-103004"/></a></p>
<p>顶部左边的版面是编辑器，这是你编写R语言的地方，在这里你可以编写函数，类，包等。这些基本工功能和其他语言的编辑器是类似的。除了一些不言自明的按钮，其他的按钮在一开始你没有必要关注。上方有一个Source on Save的单选框，勾选这个选项意味着每一次保存文件的时候，都要加载文件的内容到控制台。你应该将这个单选框一直勾选，来使得运行速度更快。</p>
<h4 id="the-console">控制台</h4>
<p><a href="http://dab1nmslvvntp.cloudfront.net/wp-content/uploads/2015/04/1428512314Screenshot-2015-04-08-18.57.25.png"><img src="http://dab1nmslvvntp.cloudfront.net/wp-content/uploads/2015/04/1428512314Screenshot-2015-04-08-18.57.25.png" alt="The Console" width="681" height="299" class="alignnone size-full wp-image-103003"/></a></p>
<p>左边偏下的面板是控制台，这是一个<a href="http://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop">REPL</a>，让R语言来测试你的想法，数据集，过滤器和函数。这个面板会消耗你开始使用R的大部分时间。&#8211; 在这里你可以先验证你的想法是否正确，之后再将内容输入编辑器。这里也是一个环境，在这个面板输入的R文件可以因为<em>sourced</em> on Save的选择而被保存，所以当你要在编辑器里面开始真正开发一个新函数的时候，会自动将控制台里面已经定义过的函数复用。所以在文章的剩余篇幅，我们会花大量时间在REPL中。</p>
<h4 id="history-environment">历史/环境</h4>
<p><a href="http://dab1nmslvvntp.cloudfront.net/wp-content/uploads/2015/04/1428512310Screenshot-2015-04-08-18.57.38.png"><img src="http://dab1nmslvvntp.cloudfront.net/wp-content/uploads/2015/04/1428512310Screenshot-2015-04-08-18.57.38.png" alt="History / Environment Pane" width="573" height="263" class="alignnone size-full wp-image-103002"/></a></p>
<p>顶部右边的面板有两个部分：运行环境和操作历史。</p>
<p><strong>环境</strong> 是指控制台的运行环境，它会罗列每一个你在控制台中定义的符号（无论是通过源文件输入还是直接定义）。如果你在REPL中定义了一个函数，这个函数也会出现在环境面板里面，变量和数据集也是一样。在这里你可以人工引入自定义的数据集，如果你不喜欢每次都要敲击命令让这些数据集可用，可以在环境面板中使它们在控制台中持续性可用。你还可以检查你安装并加载的其他包的环境。尽情在这个面板操作，你不会对其他地方造成任何影响。</p>
<p><strong>历史</strong> 这个面板会罗列从最新的项目开始时你在控制台中敲入的每一个命令。它存储在你项目文件中的一个<code>.Rhistory</code>的隐藏文件。如果你选择不保存当下环境，相应时期的操作历史也不会被保存。</p>
<h4 id="misc">Misc</h4>
<p><a href="http://dab1nmslvvntp.cloudfront.net/wp-content/uploads/2015/04/1428512305Screenshot-2015-04-08-18.57.49.png"><img src="http://dab1nmslvvntp.cloudfront.net/wp-content/uploads/2015/04/1428512305Screenshot-2015-04-08-18.57.49.png" alt="Misc pane" width="568" height="452" class="alignnone size-full wp-image-103001"/></a></p>
<p>右边下方的面板是一个misc面板，并且有5个独立的tab。第一个是<strong>Files</strong>, 这个功能不用介绍。<strong>Plots</strong> 会包括你用R生成的所有图像。在这里你可以对这些图像进行缩放，导出，设置规格，并检查相应的表单。<strong>Packages</strong> 可以让你导入安装另外的功能包。每一个可用的包下面都会有简单的介绍，不过这些介绍涵盖的内容并不完整。<strong>Help</strong> 让你可以搜索完整的帮助目录，如果你在控制台中输入帮助的命令，这个面板也会自动跳出。(帮助命令，是在本来的命令名后加上一个问号，就像这样：<code>?data.frame</code>)。最后, <strong>Viewer</strong> 版面是RStudio的<a href="https://support.rstudio.com/hc/en-us/articles/202133558-Extending-RStudio-with-the-Viewer-Pane">built-in browser</a>展示。这就意味着你可以用R开发网页端应用,并且完全通过它来进行发布。</p>
<h3 id="built-in-datasets">Built-in datasets</h3>
<p>在接下来的文章中，无论何时我提高要使用命令行，都假设我是在控制台中输入。因此当我说“让我们看看关于data frames的帮助文件”，你只需要在控制台输入<code>?data.frame</code>就可以了 :</p>
<p><a href="http://dab1nmslvvntp.cloudfront.net/wp-content/uploads/2015/04/1428512638dataframehelp.gif"><img src="http://dab1nmslvvntp.cloudfront.net/wp-content/uploads/2015/04/1428512638dataframehelp.gif" alt="Data Frame Help Call Gif" class="alignnone size-full wp-image-103007"/></a></p>
<p>RStudio自带了一些数据集给初级用户测试。为了使用built-in dataset，我们首先调用<code>data</code>函数加载数据集，然后添加相应的参数。为了查看所有可以直接使用的数据集，可以通过命令行<code>data()</code>, 不需要添加参数。</p>
<p><a href="http://dab1nmslvvntp.cloudfront.net/wp-content/uploads/2015/04/1428512742Screenshot-2015-04-08-19.05.19.png"><img src="http://dab1nmslvvntp.cloudfront.net/wp-content/uploads/2015/04/1428512742Screenshot-2015-04-08-19.05.19.png" alt="Data Sets in RStudio" width="403" height="715" class="alignnone size-full wp-image-103008"/></a></p>
<p>看看上面列出的这些可用的数据集，我们挑选一个数量级小的作为开始：</p>
<pre class="brush: r; title: ; notranslate" title="">
data(&quot;women&quot;)
</pre>
<p>可以看到数据集<code>women</code> 在环境面板中被列出，表示可用，但是在同时显示<code>&lt;Promise&gt;</code>。promise表示如果当你要使用这些数据时，这些数据可用。我们现在虽然告诉R要加载这个数据集，但是我们其实还没有真正使用它，所以R会觉得没有必要现在将整个数据集全部调入内存中。现在我们告诉R要正式使用数据集了。在控制台中，如果要打印整个数据集，只需要输入:</p>
<pre class="brush: r; title: ; notranslate" title="">
women
</pre>
<p>这个命令等同于:</p>
<pre class="brush: r; title: ; notranslate" title="">
print(women)
</pre>
<p><em>Note: 我们会使用前一条命令，因为输入更少。记住&#8211; 在R中，最后的结果不是由一个表达式打印出来的(就像赋值或者求和之类的)，而是自动打印在控制台中。</em></p>
<p>数据集中的数字会打印在控制台中，并且同时<code>women</code>的环境参数会发生变化。你可以看到现在环境面板中的数据的相应变化，你可以单击蓝色的扩展箭头去查看相应的变量名的内容。</p>
<p><a href="http://dab1nmslvvntp.cloudfront.net/wp-content/uploads/2015/04/1428512826Screenshot-2015-04-08-19.06.52.png"><img src="http://dab1nmslvvntp.cloudfront.net/wp-content/uploads/2015/04/1428512826Screenshot-2015-04-08-19.06.52.png" alt="Women dataset, expanded" class="alignnone size-full wp-image-103010"/></a></p>
<p>这个数据集只有15组，虽然没有提供太多的价值，但是用来适应R已经足够了。</p>
<p>为了更加深入的研究这个数据集，这里有几个函数你要记住。(下面列出这些函数，以及相应的介绍):</p>
<ul>
<li><code>nrow</code> / <code>ncol</code> 会列举出相应行/列的数量</li>
<li><code>summary</code> 会计算出数据集的数据总结。在<code>women</code>这个例子里面, 我们有两个数字列(即该列里面的数据都是数字，或者该列为一个数字向量&#8211; 向量的概念会在数据类型中介绍) ，当你要求对这些列进行数据分析时，R会检测出这些数字列，并且给出一些常规的数据分析结果：数据集中的最小值，1/4位数，平均值，3/4位数，最大值等。对于不同的向量类型(比如一个数据集的数据全是字符串而不是数字) 结果会不一样。</li>
<li><code>str</code> str是另一种形式的summary。实际上，<code>str</code> 代表“structure”，它会得出这个数据集的结构总结。在我们的例子中，R会告诉我们这个数据集是一个拥有15个obs（observations观察行或者行）和2个变量（或者列）的“data.frame” (一种特殊的数据类型，之后我们会讲解a)。然后它会列举中数据集中的所有列，并伴随有一些分析数据。</li>
<li><code>dim</code> 会给出数据集的维度。调用<code>dim(women)</code>在这个例子中，会返回给我们<code>15 2</code> 表示有15行，2列。 <code>length</code>用来计数，统计数据集中有多少个垂直元素。&#8211; 在向量中，返回有多少个数据；在数据集中，返回列数。</li>
</ul>
<pre class="brush: r; title: ; notranslate" title="">
&gt; nrow(women)
[1] 15
&gt; ncol(women)
[1] 2
&gt; summary(women)
     height         weight     
 Min.   :58.0   Min.   :115.0  
 1st Qu.:61.5   1st Qu.:124.5  
 Median :65.0   Median :135.0  
 Mean   :65.0   Mean   :136.7  
 3rd Qu.:68.5   3rd Qu.:148.0  
 Max.   :72.0   Max.   :164.0  
&gt; str(women)
'data.frame':	15 obs. of  2 variables:
 $ height: num  58 59 60 61 62 63 64 65 66 67 ...
 $ weight: num  115 117 120 123 126 129 132 135 139 142 ...
&gt; dim(women)
[1] 15  2
</pre>
<p>你会经常使用这些函数，所以我建议你要熟记它们。加载一些其他的数据集，并且用这些函数观察它们。不需要所有函数都要记住，&#8211; 这个文档以及帮助文件随时都在，你可以随时查阅，但是熟练应用还是会提高效率不少。</p>
<h2 id="data-types">数据类型</h2>
<p>R有一些原子类型的数据类型，你应该在其他语言中已经见到过，但是R还有一些专门用于数据分析的数据类型，我们简单的浏览一遍。在介绍这些结构的时候，我会讲到<em>assigning</em>。赋值在R中用一个左箭头完成 <code>&lt;-</code>, 如下例:</p>
<pre class="brush: r; title: ; notranslate" title="">
myString &lt;- &quot;Hello World&quot;
</pre>
<p>当然如果你不想总是使用箭头，R也可以允许在控制台中使用的<code>=</code> <a href="https://stat.ethz.ch/R-manual/R-patched/library/base/html/assignOps.html">赋值符号</a>。</p>
<pre class="brush: r; title: ; notranslate" title="">
myString = &quot;Hello World&quot;
</pre>
<p>但是我建议你习惯箭头符号，虽然你平时不怎么用。</p>
<p>为了检查一个变量（或者一个类）的类型，你可以使用函数<code>class</code>: <code>class(myString)</code>。</p>
<h3 id="atomics">原子变量</h3>
<p>原子变量是一些基本的数据类型。</p>
<h4 id="character">字符</h4>
<p>字符类是一个基本类，由一个或者多个字母组成。</p>
<pre class="brush: r; title: ; notranslate" title="">
&gt; myString &lt;- &quot;Hello World&quot;
&gt; class(myString)
[1] &quot;character&quot;
</pre>
<p> <code>[1]</code> 在向量的章节解释。</p>
<h4 id="numeric">数字</h4>
<p>与其他语言中的“float”相对应&#8211; R中也有像10, 15.6, -48792.5498982749879等数据。 </p>
<pre class="brush: r; title: ; notranslate" title="">
&gt; myNum &lt;- 5.983904798274987298
&gt; class(myNum)
[1] &quot;numeric&quot;

</pre>
<p>你可以将是数字的字符类型转换为数字类型，就像这样:</p>
<pre class="brush: r; title: ; notranslate" title="">
&gt; myString &lt;- &quot;5.60&quot;
&gt; class(myString)
[1] &quot;character&quot;
&gt; myNumber &lt;- as.numeric(myString)
&gt; myNumber
[1] 5.6
&gt; class(myNumber)
[1] &quot;numeric&quot;

</pre>
<p>这个也有一个特殊的数字<code>Inf</code> 表示无限。它可以被用于计算：</p>
<pre class="brush: r; title: ; notranslate" title="">
&gt; 1/0
[1] Inf
</pre>
<p>另一个数字是<code>NaN</code> 表示“Not a Number”。当你计算<code>0/0</code>就会出现。</p>
<h4 id="integer">整型数</h4>
<p>整型数全是数字，在被存入变量的时候，转换为数字（numeric）:</p>
<pre class="brush: r; title: ; notranslate" title="">
&gt; myInt &lt;- 209173987
&gt; class(myInt)
[1] &quot;numeric&quot;

</pre>
<p>为了将他们强制转化为整型数，需要调用函数<code>as.integer</code>:</p>
<pre class="brush: r; title: ; notranslate" title="">
&gt; myInt &lt;- as.integer(myInt)
&gt; class(myInt)
[1] &quot;integer&quot;

</pre>
<p>你也可以通过L suffix来防止自动转换:</p>
<pre class="brush: r; title: ; notranslate" title="">
&gt; myInt = 5L
&gt; class(myInt)
[1] &quot;integer&quot;

</pre>
<p>注意：如果你使用的数字超过容量，R会自动将其转换为实数，即使你在数据后面加上L:</p>
<pre class="brush: r; title: ; notranslate" title="">
&gt; myInt &lt;- 2479827498237498723498729384
&gt; class(myInt)
[1] &quot;numeric&quot;
&gt; myInt
[1] 2.479827e+27

</pre>
<p>但是如果你强行要转换为整型数，R会抛弃这个数字，因为R不能处理这么大的整型数。而你得到的会是一个 “NA”, 这是R中的一个特殊类型，表示“Not Available”, 同样可以当做一个缺失数据处理。</p>
<pre class="brush: r; title: ; notranslate" title="">
&gt; myIntCoerced &lt;- as.integer(myInt)
Warning message:
NAs introduced by coercion 
&gt; myIntCoerced
[1] NA
&gt; class(myIntCoerced)
[1] &quot;integer&quot;

</pre>
<p>NA是一种整型数，只是没有值。</p>
<p>注意，当把numeric类型转换为integer的时候，小数部分会被丢失，这种情况同样出现在将数字字符串转换为integer：</p>
<pre class="brush: r; title: ; notranslate" title="">
&gt; myString &lt;- &quot;5.60&quot;
&gt; myNumeric &lt;- 5.6
&gt; myInteger1 &lt;- as.integer(myString)
&gt; myInteger2 &lt;- as.integer(myNumeric)
&gt; myInteger1 == myInteger2
[1] TRUE
&gt; myInteger1
[1] 5

</pre>
<h4 id="complex">复数</h4>
<p>解释复数是一个超出本文范围的复杂的工程，尤其是当你在学校里没有接触过的时候。但是如果你好奇，你可以在这里找到更多。<a href="http://en.wikipedia.org/wiki/Complex_number">here</a> 复数的形式是<code>a + bi</code> ，在这里<code>a</code>和 <code>b</code> 是实数，<code>i</code> is 是虚的. 在R中，它们被<code>complex</code> 函数构建。</p>
<pre class="brush: r; title: ; notranslate" title="">
&gt; myComplex &lt;- complex(1, 3292, 8974892)
&gt; myComplex
[1] 3292+8974892i
&gt; class(myComplex)
[1] &quot;complex&quot;

</pre>
<p>一般来说，相较于其他数据类型，你不会用太多复数，但是如果你想了解更多关于<code>complex</code>，你可以调用帮助文件<code>?complex</code>来查看。</p>
<h4 id="logical">逻辑类型</h4>
<p>逻辑类型(布尔值) 和其他语言中的一样，有两种结果&#8211; 不是真就是假。True可以用<code>TRUE</code> 或者 <code>T</code>表示，同样false可以用<code>FALSE</code> or或者<code>F</code>表示.</p>
<pre class="brush: r; title: ; notranslate" title="">
&gt; TRUE == T
[1] TRUE
&gt; myBool &lt;- TRUE
&gt; myBool == T
[1] TRUE
&gt; myComparison &lt;- 5 &gt; 6
&gt; myComparison == FALSE
[1] TRUE
&gt; class(myComparison)
[1] &quot;logical&quot;
</pre>
<p>不管你使用什么表达式，最后的结果是“yes” 或者 “no” , 你都会得到TRUE 或者 FALSE &#8211; 就像这个例子中<code>5 &gt; 6</code>, 5 没有大于6, 所以表达式的结果为<code>FALSE</code>。</p>
<p>当逻辑符号应用在函数中时，逻辑符号自动转换为数字。这就意味着如果我写<code>1 + TRUE</code> 。控制台就会输出<code>2</code>, 输入 <code>1 + FALSE</code> 输出<code>1</code>。同样，我们可以把其他类型转换为逻辑类型。(<code>as.logical(myVariable)</code>). 任何数字类型或者整型数，值不是0 或者 NA 都会得到 <code>TRUE</code>。0 和 0L 会得到<code>FALSE</code>. 字符串如“True”, “TRUE”, “true” 和 “T” 会转换为TRUE, “False”, “FALSE”, “false” 和 “F”会转换为<code>FALSE</code>。其他字符串转换为逻辑上的NA。</p>
<h3 id="higher-types">高级类型</h3>
<p>高级类型由低级类型组成。</p>
<h4 id="vectors-and-lists">向量和列表</h4>
<p>在高级类型中，最重要的是向量（vector）,是相同类型的数据的组合。在之前的数据集例子中，<code>women</code> 数据集的一列数据就是一个<em>numeric vector</em>, 表示这是一个只由数字组成的集合。一个向量只能包含相同的数据类型。向量通过 <code>vector</code> 函数生成，但是通常通过<code>c</code>更加简短的生成:</p>
<pre class="brush: r; title: ; notranslate" title="">
&gt; myVector &lt;- c(&quot;Hello&quot;, &quot;World&quot;, &quot;Third Element&quot;)
&gt; class(myVector)
[1] &quot;character&quot;
&gt; myVector
[1] &quot;Hello&quot;         &quot;World&quot;         &quot;Third Element&quot;

</pre>
<p>在这里，向量的类型是“character”, 表示这个向量是包括了字符类型。如果我们只是通过调用向量名来打印，就会输出向量中的所有数据，并且伴随序数<code>[1]</code>。<code>[1]</code>表示遍历的序号。 你在<code>[]</code> 符号中看到的数字就是该数据在向量中的位置。例如:</p>
<pre class="brush: r; title: ; notranslate" title="">
&gt; myVector &lt;- c(&quot;One&quot;, &quot;Two&quot;, &quot;Three&quot;, &quot;Four&quot;, &quot;Five&quot;, &quot;Six&quot;, &quot;Seven&quot;, &quot;Eight&quot;, &quot;Nine&quot;, &quot;Ten&quot;, &quot;Eleven&quot;, &quot;Twelve&quot;, &quot;Thirteen&quot;, &quot;Fourteen&quot;, &quot;Fifteen&quot;)
&gt; myVector
 [1] &quot;One&quot;      &quot;Two&quot;      &quot;Three&quot;    &quot;Four&quot;     &quot;Five&quot;     &quot;Six&quot;      &quot;Seven&quot;   
 [8] &quot;Eight&quot;    &quot;Nine&quot;     &quot;Ten&quot;      &quot;Eleven&quot;   &quot;Twelve&quot;   &quot;Thirteen&quot; &quot;Fourteen&quot;
[15] &quot;Fifteen&quot; 

</pre>
<p>注意：向量是一维的，你不能把其他向量作为一个向量的数据，只能够进行合并:</p>
<pre class="brush: r; title: ; notranslate" title="">
&gt; v1 &lt;- c(&quot;a&quot;, &quot;b&quot;, &quot;c&quot;)
&gt; v2 &lt;- c(&quot;d&quot;, &quot;e&quot;, &quot;f&quot;)
&gt; v3 &lt;- c(v1, v2)
&gt; v3
[1] &quot;a&quot; &quot;b&quot; &quot;c&quot; &quot;d&quot; &quot;e&quot; &quot;f&quot;

</pre>
<p>你还可以通过range来生成整个向量：</p>
<pre class="brush: r; title: ; notranslate" title="">
&gt; myRange &lt;- c(1:10)
&gt; myRange
 [1]  1  2  3  4  5  6  7  8  9 10

</pre>
<p><strong><em>列表</em></strong> 和向量相似, 只是不再有必须是相同的数据类型的限制。可以通过<code>list</code> 函数或者<code>c</code> 函数（如果只有一种数据类型）来生成列表（list）:</p>
<pre class="brush: r; title: ; notranslate" title="">
&gt; myList &lt;- list(5, &quot;Hello&quot;, &quot;Worlds&quot;, TRUE)
&gt; class(myList)
[1] &quot;list&quot;
&gt; myList
[[1]]
[1] 5

[[2]]
[1] &quot;Hello&quot;

[[3]]
[1] &quot;Worlds&quot;

[[4]]
[1] TRUE

</pre>
<p>和向量一样，列表也是一维的，只能合并。</p>
<p><code>[[N]]</code> 可以用来输出list中每一个元素的数据类型：</p>
<pre class="brush: r; title: ; notranslate" title="">
&gt; class(myList[[1]])
[1] &quot;numeric&quot;
&gt; class(myList[[2]])
[1] &quot;character&quot;
&gt; class(myList[[3]])
[1] &quot;character&quot;
&gt; class(myList[[4]])
[1] &quot;logical&quot;

</pre>
<h4 id="dataframe">数据框</h4>
<p>数据框也是R中很重要的一个数据类型（Dataframes），是一个有行和列的数据类型。<code>women</code> 数据集就是一个数据框，我们可以单独访问数据框的每一列，用<code>$</code> 运算符在数据框变量名上，后面伴随该列名：</p>
<pre class="brush: r; title: ; notranslate" title="">
&gt; women$height
 [1] 58 59 60 61 62 63 64 65 66 67 68 69 70 71 72

</pre>
<p>输出的结果转变为一个数字向量，用<code>class(women$height)</code>来检验数据类型。</p>
<p>如果列名中间有空格，你可以用引号把列名括起来(<code>women$"Female Height"</code>), 或者可以通过该列的位置来访问：</p>
<pre class="brush: r; title: ; notranslate" title="">
&gt; head(women[1])
  height
1     58
2     59
3     60
4     61
5     62
6     63
&gt; head(women[[1]])
[1] 58 59 60 61 62 63

</pre>
<p> <code>head</code> 函数告诉R只需要返回前6个结果&#8211; 这样可以保持我们的控制台界面干净。(相对应的，输入<code>tail</code> 可以返回最后6个数据). </p>
<p>我们可以通过<code>[1]</code>查看相应列。如果数据集列数不多，那么我们可以通过<code>[[1]]</code>直接访问。用单方括号得到的数据保持原来的数据类型，用双方括号得到的数据转换为了数字类型。</p>
<p>我们通过 <code>data.frame</code> 函数创建数据框:</p>
<pre class="brush: r; title: ; notranslate" title="">
&gt; men &lt;- data.frame(height = c(50:65), weight = c(150:165))
&gt; head(men)
  height weight
1     50    150
2     51    151
3     52    152
4     53    153
5     54    154
6     55    155

</pre>
<p>这里我们创建了一个简单的数据框<code>men</code>。</p>
<p>如果我们只想获得列名，可以使用<code>names</code> 函数。我们可以新赋值一个变量，将这个变量变成新列名：</p>
<pre class="brush: r; title: ; notranslate" title="">
&gt; names(men)
[1] &quot;height&quot; &quot;weight&quot;
&gt; names(men) &lt;- c(&quot;Male Height&quot;, &quot;Male Weight&quot;)
&gt; head(men)
  Male Height Male Weight
1          50         150
2          51         151
3          52         152
4          53         153
5          54         154
6          55         155

</pre>
<h4 id="matrix">矩阵</h4>
<p>矩阵是多维的向量。和数据框有点相似，但是只能包含相同的数据类型。通过<code>matrix</code> 函数创建矩阵，并且需要输入列数和行数，以及矩阵中的数据：</p>
<pre class="brush: r; title: ; notranslate" title="">
&gt; m &lt;- matrix(nrow = 4, ncol = 5, 1:20)
&gt; m
     [,1] [,2] [,3] [,4] [,5]
[1,]    1    5    9   13   17
[2,]    2    6   10   14   18
[3,]    3    7   11   15   19
[4,]    4    8   12   16   20

</pre>
<p>如果输入的数据和矩阵的大小不匹配会怎么样？</p>
<pre class="brush: r; title: ; notranslate" title="">
&gt; m &lt;- matrix(nrow = 4, ncol = 5, 1:25)
Warning message:
In matrix(nrow = 4, ncol = 5, 1:25) :
  data length [25] is not a sub-multiple or multiple of the number of rows [4]
&gt; m
     [,1] [,2] [,3] [,4] [,5]
[1,]    1    5    9   13   17
[2,]    2    6   10   14   18
[3,]    3    7   11   15   19
[4,]    4    8   12   16   20

</pre>
<p>我们会得到一个警告，但是矩阵依旧会生成，只是有些数据会被舍弃。如果提供的数据少于矩阵的大小，会循环填充向量里面的数据，直到矩阵变满：</p>
<pre class="brush: r; title: ; notranslate" title="">
&gt; m &lt;- matrix(nrow = 4, ncol = 5, 1:16)
Warning message:
In matrix(nrow = 4, ncol = 5, 1:16) :
  data length [16] is not a sub-multiple or multiple of the number of columns [5]
&gt; m
     [,1] [,2] [,3] [,4] [,5]
[1,]    1    5    9   13    1
[2,]    2    6   10   14    2
[3,]    3    7   11   15    3
[4,]    4    8   12   16    4

</pre>
<p>和数据框一样，可以使用<code>names</code>函数，并且矩阵可以有<code>dim</code> (dimension) 函数。 改变维度这个变量，会使矩阵发生变化：</p>
<pre class="brush: r; title: ; notranslate" title="">
&gt; m &lt;- 1:15
&gt; m
 [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15
&gt; dim(m)
NULL
&gt; dim(m) &lt;- c(3,5)
&gt; m
     [,1] [,2] [,3] [,4] [,5]
[1,]    1    4    7   10   13
[2,]    2    5    8   11   14
[3,]    3    6    9   12   15
&gt; dim(m)
[1] 3 5
&gt; dim(m) &lt;- c(5,3)
&gt; m
     [,1] [,2] [,3]
[1,]    1    6   11
[2,]    2    7   12
[3,]    3    8   13
[4,]    4    9   14
[5,]    5   10   15
&gt; dim(m)
[1] 5 3
&gt; dim(m) &lt;- NULL
&gt; m
 [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15

</pre>
<p>这里我们创建了一个有15个连续数字的数字向量，<code>dim</code> 变量不存在，用<code>dim</code> 函数返回的是NULL。如果我们赋予一个向量<code>3, 5</code>给dim，里面的数据就会自动排列来适应这个新生成的矩阵。我们将这个向量变成了一个具有5行3列的矩阵<code>5, 3</code>。最后维度也和一开始的不一样了。</p>
<p>可以合并/扩展/改变向量，数据框和矩阵都可以使用<code>cbind</code> 和 <code>rbind</code>:</p>
<pre class="brush: r; title: ; notranslate" title="">
&gt; v &lt;- 1:5
&gt; x &lt;- 6:10
&gt; bound &lt;- cbind(v, x)
&gt; bound
     v  x
[1,] 1  6
[2,] 2  7
[3,] 3  8
[4,] 4  9
[5,] 5 10
&gt; bound &lt;- rbind(v, x)
&gt; bound
  [,1] [,2] [,3] [,4] [,5]
v    1    2    3    4    5
x    6    7    8    9   10

</pre>
<h4 id="factors">因子</h4>
<p>因子是有标签的向量。这个和字符向量或者数字向量都不一样，后者是R自己描述的向量，而因子是将向量中的数据加上一定的标签之后得到的结果。它们通过<code>factor</code> 函数来得到：
</p>
<pre class="brush: r; title: ; notranslate" title="">
&gt; f &lt;- factor(c(&quot;Hello&quot;, &quot;World&quot;, &quot;Hello&quot;, &quot;Annie&quot;, &quot;Hello&quot;, &quot;World&quot;))
&gt; f
[1] Hello World Hello Annie Hello World
Levels: Annie Hello World
&gt; table(f)
f
Annie Hello World 
    1     3     2 

</pre>
<p>等级是因子中的一个独一无二的元素，<code>table</code> 函数分析一个因子并建立一个表单来表述这个因子中不同的等级，以及每个等级出现的数量。</p>
<p>我在我的项目中还没有用到过因子。但是<a href="http://stackoverflow.com/questions/3445316/factors-in-r-more-than-an-annoyance">I’m learning about them</a>可以在这里看到更多。</p>
<h2 id="conclusion">结语</h2>
<p>在这篇文章中，涵盖了R中的数据类型和RStudio的一些基本用法，你可以有目的性的用一些操作来练习这些内容。记住我们讲解的函数在帮助文件中有更加详尽的解释。<br />
<code>?function</code> 其中“function” 是函数名。</p>
