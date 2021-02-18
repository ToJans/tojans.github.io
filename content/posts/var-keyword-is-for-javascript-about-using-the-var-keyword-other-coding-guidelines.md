---
layout: post
date: "2010-03-31"
slug: "var-keyword-is-for-javascript-about-using-the-var-keyword-other-coding-guidelines"
title: Var keyword is for JavaScript - about using the var keyword & other coding
  guidelines
---

<h3>Introduction<br /></h3>
<p>Today I was reading an <a href="http://www.codeproject.com/KB/library/simpleservicelocator.aspx" target="_blank">article on Codeproject</a>, and I was really astounded by the way some people rate articles and give comments...</p>
<p>It was an article about someone who had implemented a simple service locator which contained the following code sample :</p>
<p><div class="code">
<br /><span class="kwrd">using</span> System; <br /><span class="kwrd">using</span> CuttingEdge.ServiceLocation; <br /><span class="kwrd">using</span> Microsoft.Practices.ServiceLocation;  <br /><br /><span class="kwrd">public</span> <span class="kwrd">class</span> Global : System.Web.HttpApplication <br />{<br />&nbsp; <span class="kwrd">protected</span> <span class="kwrd">void</span> Application_Start(<span class="kwrd">object</span> sender, EventArgs e)     <br />&nbsp; {         <br />&nbsp;&nbsp;&nbsp;&nbsp; // 1. Create a <span class="kwrd">new</span> Simple Service Locator container         <br />&nbsp;&nbsp;&nbsp;&nbsp; var container = <span class="kwrd">new</span> SimpleServiceLocator();                  <br /><br />&nbsp;&nbsp;&nbsp;&nbsp; // 2. Configure the container                  <br /><br />&nbsp;&nbsp;&nbsp;&nbsp; // Register a <span class="kwrd">delegate</span> that will create a <span class="kwrd">new</span>         <br />&nbsp;&nbsp;&nbsp;&nbsp; // instance on each call to GetInstance.         <br />&nbsp;&nbsp;&nbsp;&nbsp; container.Register&lt;ISamurai(() =&gt;          <br />&nbsp;&nbsp;&nbsp;&nbsp; {             <br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; var weapon = ServiceLocator.Current                 .GetInstance();             <br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <span class="kwrd">return</span> <span class="kwrd">new</span> Samurai(weapon);         <br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; });              <br /><br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // Register a single <span class="kwrd">object</span> instance that always         <br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // be returned (must be thread-safe).         <br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; container.RegisterSingle(<span class="kwrd">new</span> Katana());              <br /><br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // 3. Register the container to the Common Locator         <br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ServiceLocator.SetLocatorProvider(() =&gt; container);     <br />&nbsp;&nbsp;&nbsp; } <br />}<br /></div></p>
<p>Which seems quite obvious to me. Since I noticed a <a href="http://www.codeproject.com/KB/library/simpleservicelocator.aspx?msg=3420815#xx3420815xx" target="_blank">comment titled 'my vote of 2'</a>, I was curious why this article would be voted such a low score (2 out of 5). I checked the comment and I was astounded:</p>
<p style="padding-left: 30px;"><em>Please note: the keyword "var" is supposed to be used with anonymous types. You should not use it for anything else. Otherweise please start <br />programming java script</em></p>
<p></p>
<h3>Who cares ?<br /></h3>
<p>Actually, I do.</p>
<p>Since I could not resist I posted the following comment:</p>
<p style="padding-left: 30px;"><em>Ahum... there have been numerous issues about this, but in general it should not pose a problem, because it is quite clear what it's intentions are at the beginning; i.e. :<br /><br /><div class="code">
var sl = <span class="kwrd">new</span> SimpleServiceLocator();</div><br /><br /><br />Is not really more obvious then :<br /><br /><div class="code">
SimpleServiceLocator sl = <span class="kwrd">new</span> SimpleServiceLocator();</div><br /><br /><br />In fact, the information in there is the same, but the second one is more verbose, so every person in his right mind would opt for the first alternative.<br />This might be different if you use a function which does not directly expose the return type in the function name; i.e. :<br /><br /><div class="code">
var x = SomeFunction(y,z); </div><br /><br /><br />This is considered bad practice by most.<br /><br />This one is not :<br /><br /><div class="code">
var myservice = sl.Resolve&lt;IMyService&gt;();</div><br /><br /><br />Because the initialization contains enough obvious info to give pointers to the var's type.<br /><br />So, if this is the only reason why you are giving a 2 (the author has obviously invested quite some time in this article), then you might need to start doing some JavaScript yourself </em></p>
<p style="padding-left: 30px;">&nbsp;</p>
<p>After tweeting about this, I had an interesting conversation with <a href="http://twitter.com/JacoPretorius" target="_blank">@JacoPretorious</a> about this, who says he uses var everywhere, but pays more attention to variable names.</p>
<p>While I understand what he means, IMHO variable names should not infer the type, only the meaning of the content if necessary.</p>
<p>I personally think there is nothing wrong with using single letters as variable names, as long as the intent is obvious. This is an example that is perfectly valid imho :</p>
<p><div class="code">
<br /><span class="kwrd">public</span> <span class="kwrd">bool</span> InvalidateCustomer(<span class="kwrd">int</span> CustomerId)<br />{<br />&nbsp; var c = sRepo.GetById&lt;Customer&gt;(CustomerId);<br />&nbsp; <span class="kwrd">if</span> ( c.Orders.Where(o=&gt;o.PaymentReceivedOn==<span class="kwrd">null</span>).Any()) <br />&nbsp;&nbsp;&nbsp; <span class="kwrd">return</span> <span class="kwrd">false</span>;<br />&nbsp; c.Valid=<span class="kwrd">false</span>;<br />&nbsp; sRepo.SaveOrUpdate(c);<br />&nbsp; sUOW.Commit();<br />&nbsp; <span class="kwrd">return</span> <span class="kwrd">true</span>;<br />}<br /></div></p>
<p>This one is not IMO :</p>
<p><div class="code">
<br /><span class="kwrd">public</span> <span class="kwrd">class</span> MyProcessQueue<br />{<br />&nbsp; <span class="kwrd">public</span> <span class="kwrd">void</span> ProcessQueue()<br />&nbsp; {</p>
<p>&nbsp; &nbsp; <span class="kwrd">for</span>(;;)<br />&nbsp; &nbsp; {<br />&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; var p = Queue.Next();<br />&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; <span class="kwrd">if</span> (p==<span class="kwrd">null</span>) <br />&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <span class="kwrd">break</span>;<br />&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; sProcessor.Process(p);<br />&nbsp; &nbsp; }<br />&nbsp; }<br />}<br /></div></p>
<p>Since you can not infer the type from <strong>Queue</strong>, you should make the type explicit :</p>
<p><div class="code">
<br /> <span class="kwrd">public</span> <span class="kwrd">class</span> MyProcessQueue<br /> {</p>
<p>&nbsp; <span class="kwrd">public</span> <span class="kwrd">void</span> ProcessQueue()<br /> &nbsp; {</p>
<p>&nbsp; &nbsp; <span class="kwrd">for</span>(;;)<br /> &nbsp; &nbsp; {<br /> &nbsp;&nbsp; &nbsp;&nbsp;&nbsp; Order o = Queue.Next();<br /> &nbsp;&nbsp; &nbsp;&nbsp;&nbsp; <span class="kwrd">if</span> (o==<span class="kwrd">null</span>) <br /> &nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <span class="kwrd">break</span>;<br /> &nbsp;&nbsp; &nbsp;&nbsp;&nbsp; sProcessor.Process(o);<br /> &nbsp; &nbsp; }<br /> &nbsp; }<br /> }<br /> </div></p>
<p><br />This would change if the <strong>MyProcessQueue</strong> would be a generic class :</p>
<p><div class="code">
<br /> <span class="kwrd">public</span> <span class="kwrd">class</span> MyProcessQueue&lt;T&gt; <span class="kwrd">where</span> T:ISomeInterface<br /> {<br /> &nbsp; <span class="kwrd">public</span> <span class="kwrd">void</span> ProcessQueue()<br /> &nbsp; {</p>
<p>&nbsp; &nbsp; <span class="kwrd">for</span>(;;)<br /> &nbsp; &nbsp; {<br /> &nbsp;&nbsp; &nbsp;&nbsp;&nbsp; var p = Queue.Next();<br /> &nbsp;&nbsp; &nbsp;&nbsp;&nbsp; <span class="kwrd">if</span> (p==<span class="kwrd">null</span>) <br /> &nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <span class="kwrd">break</span>;<br /> &nbsp;&nbsp; &nbsp;&nbsp;&nbsp; sService.Process(p);<br /> &nbsp; &nbsp; }<br /> &nbsp; }<br /> }<br /> </div><br /><br />In this case, I think you have enough information available to know that the type should be about the generic class. Using more explicit names for the variables does not add a lot info for me; I do not find the following (exagerated) example more abvious than the previous one; in fact, it takes more time to get the intent here, because your mind needs to process more information (also note the comments, which do not provide any extra info to me) :</p>
<p><div class="code">
<br /><span class="kwrd">public</span> <span class="kwrd">class</span> MyProcessQueue&lt;T&gt;<br /> &nbsp; <span class="kwrd">where</span> T:ISomeInterface<br />{&nbsp; <br />&nbsp; <span class="rem">// Process all jobs in the queue, until there is nothing left&nbsp;&nbsp; <br />&nbsp; public void ProcessAllISomeInterfacesInTheQueue()<br />&nbsp; { <br />&nbsp;&nbsp;&nbsp; // loop forever <br />&nbsp; &nbsp; for(;;)<br />&nbsp; &nbsp; {<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // get the next instance to process from the queue;&nbsp; <br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // if it returns null there are no more processes left on the queue&nbsp; <br />&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; ISomeInterface TheNextISomeInterfaceInstanceToProcess = Queue.Next();</p></span>
<p>&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; <span class="kwrd">if</span> (TheNextISomeInterfaceInstanceToProcess==<span class="kwrd">null</span>)<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; {<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; //exit the infinite loop&nbsp; <br /> &nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <span class="kwrd">break</span>;<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; }<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // process it&nbsp; <br /> &nbsp;&nbsp; &nbsp;&nbsp;&nbsp; sServiceThatProcessesSomeInterfaceInstance<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; .Process(TheNextISomeInterfaceInstanceToProcess);<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // go to the next one<br /> &nbsp; &nbsp; }<br />&nbsp;&nbsp; // <span class="kwrd">return</span>&nbsp; <br /> &nbsp; }<br /> }<br /> </div></p>
<p>There is way too much info here which can all be easily derived from the code, and if you change the code and forget the comments, this might actually do the opposite: cause confusion.</p>
<h3>In conclusion</h3>
<p>While this is all about preference and highly dependent on you point of view and background, I do think that the approach I am personnaly using is one of the better ones. They offer all the amount of information that you could need with the minimum amount of code.</p>
<p>If you do have another opinion, do not hesitate to let me know...</p>
<p>&nbsp;</p><div style="text-align:right"><a class="addthis_button" href="http://www.addthis.com/bookmark.php?v=250&amp;pub=xa-4aec37702e3161d4"><img src="http://s7.addthis.com/static/btn/v2/lg-share-en.gif" width="125" height="16" alt="Bookmark and Share" style="border:0"/></a><script type="text/javascript" src="http://s7.addthis.com/js/250/addthis_widget.js#pub=xa-4aec37702e3161d4"></script></div>