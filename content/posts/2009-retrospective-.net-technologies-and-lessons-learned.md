---
layout: post
date: "2010-01-02"
slug: "2009-retrospective-.net-technologies-and-lessons-learned"
title: '2009 retrospective: .Net technologies and lessons learned'
---

<p><img style="float: left; margin-left: 20px; margin-right: 20px; margin-top: 0px; margin-bottom: 0px;" src="http://www.corebvba.be/blog/image.axd?picture=2010%2f1%2fIMAG0006.jpg" alt="my pride &amp; joy" width="260" height="439" /></p>
<h3>Introduction</h3>
<p>&nbsp;</p>
<p>In December 2008 I was doing my job as a freelance technical analyst for <a href="http://www.gdfsuez.com/en/activities/our-businesses/energy-procurement-and-trading/energy-procurement-and-trading/" target="_blank">a big company</a>. While it was a very interesting job in several ways, I felt that a burn-out was coming up. I had no idea whether this was due to the job, or due to my personal merits ( a newborn and a one-year old son, lots of tasks and chores on my to-do list for our house, a busy social life, ...) Instead of waiting for the man with the hammer, I decided to be proactive about it, so I decided to quit the job and reinvent myself during 2009.</p>
<p>It has been both an interesting, very challenging and enriching year for me, with both high peaks and low valleys.<br /><br />I decided to write this blog post in order to evaluate myself, and I am hoping that other people might find some inspiration in this as well.</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p></p>
<h3>The initial plan</h3>
<p><br />I started the year with both a big and an average sized project which should at least have given me funds enough to get through my first year without any financial concessions. <br />Since the big project was a web application, I started to <a href="http://www.corebvba.be/blog/?tag=/w00t">build my own reference architecture</a> based on an <a href="http://en.wikipedia.org/wiki/ASP.NET_MVC_Framework" target="_blank">asp.net mvc</a> app. This has been a very enriching experience for me as I evaluated a lot of technologies and defined my current technology stack.</p>
<p>I will get into this in another part of this post.</p>
<h3>What happened</h3>
<p><br />Both of the projects were fixed price projects for the same company. As I had done a very special consultancy job for one of the division leaders for that company, I had a very solid professional relationship based on trust and integrity with that person. Since I was going to implement the average sized project for him, and they were looking for extra resources, he asked me if I was interested in doing a project for another division as well. <br />This is the part where I took the wrong decision:<br />For the average sized project, we did not have a contract at all. I know this might sound stupid, but this was simply because we both knew we could trust each other...<br />Based on my previous experiences with this company and a tight deadline, I decided to put up a preliminary contract for the big project, thinking we would be able to agree on the titbits later. However, the project's scope grew by the second, and after working day and night, reimplementing stuff over and over again, and only billing a fraction of the time I invested, we got to the point where we could not get to an agreement any more...<br />Luckily the trusted division leader was able to guard his own resources, so that I could at least finish his project and get it shipped/billed/paid.<br />In case you are wondering on the outcome of the big project, I will probably get the resulting verdict from my lawyer in February later on this year.</p>
<h3>Lessons learned</h3>
<p><br />Reflecting on this, it is strange that such obvious facts as the following did not appear to me during the project, so that is why I mention them explicit here:<br />- Always have a very detailed quote/contract that states everything in detail. Mention in the contract that every extra/change to the original quote/contract should be agreed upon in a contract appendix, no matter how small. The main reason for the scope creep was probably the fact that I had not been formal enough on their first (small) change requests which grew bigger and bigger each time.<br />- It is not because you can trust a single person in a company on it's word, that this is true for the entire company.</p>
<p>- Spread your resources... You should not be dependent on a single company/person/project...</p>
<h4>How to avoid making the same mistake again</h4>
<p><br />For every project I now create a rude application prototype, as well as a list of use cases/BDD stories. I do not implement all bdd feature story details, but I do implement those which might point to issues.<br />Using both these tools you have given the prospect an idea on what to expect on both the ui side and the behaviour, as well as an introduction to your approach on the project.<br />The biggest disadvantage of this approach is the amount of time you have to invest in a single quote, but if you do get the project, you can bill (part of) it back, since this is actual analysis.<br />Call me Captain Obvious, but it occurred to me that, in order to get a correct quote, you need to do your analysis upfront.<br />I posted a concrete example <a href="http://www.corebvba.be/blog/post/How-to-do-a-correct-estimate-for-a-project-using-BDD-and-a-HTML-prototypewireframe-built-with-jQuery-PolyPage.aspx">in this blog post.</a><br />Next to this I am careful with bigger projects, since they automatically imply a big risk when something goes wrong...</p>
<h4>Was it a completely negative experience ?</h4>
<p><br />Luckily for me it was not. At a certain moment I needed to get some office supplies. When I entered the shop, the shop owner (with whom I had done a few small projects in the past) told me that he might have some opportunities for me... Talk about a coincidence ! I started on some legacy code maintenance, and now I am slowly integrating more and more into his projects... So far so good. Also, while one part is ASP.Net MVC, another part is Windows Mobile, so this is now another experience I can add to my resume...<br />This brings me to my next part :</p>
<h3>Broaden my horizons on the development/technology side</h3>
<p><br />By building an Asp.net MVC framework, I did not only broaden my horizon on the .Net side, but also on a lot of alternative technologies. If you are planning on doing any serious development I would suggest you to at least study the following tools/technologies :</p>
<h4>Tools/Technologies</h4>
<p>- An ORM : building your own ORM component in today's world is rather ridiculous in my humble opinion; there should be enough alternatives available right now. My final choice was <a href="http://fluentnhibernate.org/" target="_blank">Fluent NHibernate</a> which allows me to define my classes based on a few conventions, and automatically wires the database for me.<br />- Dependency injection: While I had already used it quite some time,this year I fully grasped the advantages behind it. This helped my design skills a lot on the 'separation of concerns' and the testability part... I now favour composition over inheritance almost every time.<br />- Proper POCO domain objects: I violated my POCO objects' principles a few times in the past, but I now finally got to the point where they no longer contain anything other then the bare necessities.<br />- Using view models for building my pages: this made my code a lot more maintainable. I also implemented a command pattern for ASP.Net mvc; from that moment <a href="http://www.corebvba.be/blog/post/The-Quest-for-the-perfect-ASPNet-MVC-code-v03.aspx" target="_blank">all my links were wired in the controllers action</a> (i.e. Viewmodel.AL_SubmitEdit = c=&gt;c.AL("Save changes",c=&gt;c.Save(null,null)) in the controller view set-up). This implies more extensive testability and removes all implicit references from the controller to the view; the view rendering is only dependent on the view model.<br />- Using <a href="http://www.lostechies.com/blogs/jimmy_bogard/archive/2009/01/22/automapper-the-object-object-mapper.aspx" target="_blank">automapper </a>to convert between domain objects and view models: this cleaned up my code a lot, since now all the mapping is defined in a single location.<br />- <a href="http://sparkviewengine.com/" target="_blank">Spark view engine</a>: combining the use of view models with the spark view engine converted my aspx views from ugly ducklings into proper swans...<br />- Other technology stack items : generic <a href="http://martinfowler.com/eaaCatalog/repository.html" target="_blank">IRepository pattern</a>, <a href="http://jquery.com/" target="_blank">jQuery </a>+ <a href="http://plugins.jquery.com/" target="_blank">plugins</a>, <a href="http://logging.apache.org/log4net/" target="_blank">Log4Net</a>,<a href="http://www.postsharp.org/" target="_blank">PostSharp</a>,...</p>
<h4>Writing quotes using UI prototypes and BDD<br /></h4>
<p>Next to this I wanted to avoid mismatching future quotes for my clients, and after studying my options for a while i decided to go for <a href="http://www.corebvba.be/demos/prototype/index.html" target="_blank">UI prototypes</a> together with <a href="http://github.com/ToJans/Aubergine/blob/master/Be.Corebvba.Aubergine.Examples/Accounts/Stories/Transfer_money_between_accounts.txt" target="_blank">BDD stories</a>. The problem was I had never done anything BDD related at all. So I started studying/testing/implementing the whole lot.<br />I initially used <a href="http://codebetter.com/blogs/aaron.jensen/archive/2008/05/08/introducing-machine-specifications-or-mspec-for-short.aspx" target="_blank">Machine.Specifications</a> as a bdd engine, but after using it for a few days I started implementing <a href="http://wiki.github.com/ToJans/Aubergine" target="_blank">my own BDD engine</a>, in order to learn more about BDD and to be able to implement the stories I want to implement within my own constraints. This has been a very valuable experience for me, I learned a lot on BDD and it got me started in OSS.</p>
<h4>Get into open source/github<br /></h4>
<p>I like to learn from the web; by simply browsing and downloading stuff you can teach yourself a lot. As I had published <a href="http://www.codeproject.com/script/Articles/MemberArticles.aspx?amid=616289" target="_blank">a few articles on codeproject</a> as well as on my blog in the past, I decided to share my experiences with the rest of the world by <a href="http://github.com/ToJans" target="_blank">going open source</a> with my BDD engine and so I got started on github.</p>
<p>I never used github before, but in 2009 I had been<a href="http://www.corebvba.be/blog/post/To-git-or-not-to-git-Source-control-done-right-intro-and-quick-tutorial.aspx"> studying git </a>as well, and started using it with almost direct result as it made me do a lot more branching/checking in/checking out/experimenting in general without messing up anything at all. You could state that you could do this with any source control repository, but Git made it so easy and instantaneous that I used it a lot more.</p>
<h3>Me vs "the world"<sup>(tm)</sup><br /></h3>
<h4>Virtual coworkers / twitter</h4>
<p>Next to this I discovered <a href="http://twitter.com/tojans" target="_blank">twitter</a>. You could ask yourself why this is important from a technology point of view. Well, this is why: working from my home, I do not have any direct contact with fellow devs/architects/... Twitter allows me to get in touch and ask opinions on a certain matter; once you get a few followers, it gives you the ability to use it as a sort of "online instant FAQ/opinions database". If you have a certain question or just simply want to show of, you can post it to twitter, and based on your followers you will probably get some feedback as well as constructive criticism. Being part of this "huge brain" is also fun, since you can see ideas evolve quite a lot some times by giving your own input...</p>
<h4>Public visibility<br /></h4>
<p>I have also been posting some articles <a href="http://www.codeproject.com/script/Articles/MemberArticles.aspx?amid=616289" target="_blank">on codeproject</a> and <a href="http://www.corebvba.be/blog/?tag=/c">my blog</a> in order to get some opinions on a variety of subjects, some being more successful then others..</p>
<p><a style="float: left; margin-left: 5px; margin-right: 5px;display:block" title="this is my #pomodoro timer ;)" href="http://tweetphoto.com/5649602"> <img src="http://cdn.cloudfiles.mosso.com/c54112/x2_5634c2" alt="this is my #pomodoro timer ;)" width="79" height="79" /></a></p>
<h4>Productivity<br /></h4>
<p>And finally, the last I want to mention is the use of a <a href="http://www.gembapantarei.com/2009/06/agile_kanban_journal_day_8_do_we_need_a_done_colum.html" target="_blank">personal kanban </a>together with the <a href="http://www.pomodorotechnique.com/" target="_blank">pomodoro</a>. I tested it, and it worked great for a few days, but then I started lamenting...<br />In this year I will be using the kanban technique all the time, and probably the pomodoro as well.. This should give me the ability to properly focus on getting things out of the door on time...</p>
<p><a title="this is my #pomodoro timer ;)" href="http://tweetphoto.com/5649602"> </a></p>
<p>&nbsp;</p>
<h3>In conclusion</h3>
<p><br />While 2009 has been a very different year for me, I personally feel I learned a lot in this year; both direct and indirect. It enriched me both as a (business) person and as a developer on several aspects. If you feel a burn-out coming up, and you can somehow manage, try to take a year to do some things you feel the need for. Also note that most of the reasons for not doing this are not such a big issue after you name them, and look at the worst thing that could happen when it does come true...<br /><br />Best wishes for 2010 !!!<br /><br />Tom</p><div style="text-align:right"><a class="addthis_button" href="http://www.addthis.com/bookmark.php?v=250&amp;pub=xa-4aec37702e3161d4"><img src="http://s7.addthis.com/static/btn/v2/lg-share-en.gif" width="125" height="16" alt="Bookmark and Share" style="border:0"/></a><script type="text/javascript" src="http://s7.addthis.com/js/250/addthis_widget.js#pub=xa-4aec37702e3161d4"></script></div>