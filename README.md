PagesSum Module For ProcessWire
===============================

This is a (very) slightly rewritten version of ESRCH's original PagesSum module for Processwire CMS/CMF. You can find
the orignal article that introduced it [here](https://processwire.com/talk/topic/8524-creating-a-fast-pages-sum-function/#comment-82519). The only change introduced is that I've used a closure for the hook
function.


## Credit

This is ESRCH's work. I've just put it on github to make it a little more accessible (it's buried deep in the
Processwire forums.)


##Method Of Operation

The module uses ProcessWire's ability to extend its classes by adding new hook functions to them. It adds one method
_sum_ to the Pages class. Thus, anywhere you get access to the $pages class, you can get a sum worked out from any
subset of pages. The subset is defined using PWs [selectors](http://processwire.com/api/selectors/).

The summation is fast as it uses MySQL to sum the underlying data rather than having to iterate over every page in the
selected set and pull out a value.


##Installation

In the Processwire modules page, click the "New" tab and either enter PagesSum into the box or choose the option to
install from a zip file. The zip file to use is the master branch zip from the gihub repository, [here](https://github.com/netcarver/PW-PagesSum/archive/master.zip).


##Example Use In Template File

If you wanted to sum a field called 'costs' across all pages using the 'job' template, you'd simply do this...

```
<p>Job costs £<?php echo $pages->sum('template=jobs', 'costs'); ?></p>
```

And if you wanted things a little more formatted, just run that through number_format first...

```
<p>Job costs £<?php echo number_format($pages->sum('template=jobs', 'costs'), 2); ?></p>
```
