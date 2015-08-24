---
layout: post
title: Setting mail account for Subscription of scheduled Jobs in JasperServer.
date: 2015-02-11 11:54:00.000000000 +05:30
categories:
- Jasper Reports
tags:
- email settings
- Jasper Server
- jaspersoft
- scheduler
- tutorial
- walkthrough
status: publish
type: post
published: true
meta:
  blogger_bid: '2279754227642197645'
  blogger_blog: ankurthetechie.blogspot.com
  blogger_id: '6390887846119543671'
  blogger_author: g116451164261752827176
  blogger_comments: '0'
  blogger_permalink: /2015/02/setting-mail-account-for-subscription.html
  _edit_last: '1'
  imax_hidetitle: '0'
  imax_show_slider: '0'
  imax_hide_breadcrumb: '0'
author:
  login: admin@reportlingo
  email: ankur.gupta.aug@gmail.com
  display_name: admin@reportlingo
  first_name: Ankur
  last_name: Gupta
---
<div dir="ltr" style="text-align: left;">
I wanted to document the process from a long time but due to crunch of time I could not, but now I will like to explain the process in simple easy to follow steps.First of all I would like to give an idea to problem addressed in the blog, basically when a report runs as a daily status or daily count one need not run it manually it could be scheduled, but when the report is scheduled the export in desired form is exported on jasper server.</p>
<p>But wait a minute do we really login and see what the results came as in the PDF, Excel etc. export, no we need not the problem is handled by mail subscription attached to the scheduler, which will automatically send the Exports to the subscribers on their email accounts and send a confirmation to the administrator.</p>
<p>So lets cut the explanation and lets jump directly into how to do.</p>
<p>Prerequisites -</p>
<p>1. You should have working copy of JasperServer community/pro<br />
2. You should have uploaded a report to the server<br />
3. Choose you favourite text editor  (Windows(default) - Notepad/MacOS(default) - TextEdit)<br />
4. Shut down the jasper server so that no sort of errors come in case of Editing/Saving documents.</p>
<p>after following the above prerequisites now we head on to edit two files as follows.<br />
Both these files will be found at the location<br />
&lt;directory of Jasperserver on Disk&gt;/apache-tomcat/webapps/jasperserver/WEB-INF/</p>
<p>1. <b>js.quartz.properties</b><br />
- Edit the file with the Text Editor</p>
<blockquote class="tr_bq"><p>Change the portion of the document as (Please select your own server details I have used a gmail account )</p></blockquote>
<p>&nbsp;</p>
<blockquote class="tr_bq"><p>report.scheduler.mail.sender.host=smtp.gmail.com<br />
report.scheduler.mail.sender.username=testpanda@gmail.com<br />
report.scheduler.mail.sender.password=password<br />
report.scheduler.mail.sender.from= testpand@gmail.com<br />
report.scheduler.mail.sender.protocol= smtp<br />
report.scheduler.mail.sender.port= 587</p></blockquote>
<p>- Make the changes and save the file.</p>
<p>2.   <b>applicationContext-report-scheduling.xml</b></p>
<p>-  Locate the bean reportSchedulerMailSender<br />
-  Locate the property javaMailProperties<br />
-  Do the changes as below - This will enable java to interact the smtp/startls authentication.</p>
<p>&lt;props&gt;<br />
&lt;prop key="mail.smtp.auth"&gt;true&lt;/prop&gt;<br />
&lt;prop key="mail.smtp.starttls.enable"&gt;true&lt;/prop&gt;<br />
&lt;/props&gt;</p>
<div>  - Now save the document.</div>
<div></div>
<div>Now the report subscription is ready for run, just start the Jasper Server and you are good to go.</div>
<div></div>
<div>Cheers!!</div>
</div>
