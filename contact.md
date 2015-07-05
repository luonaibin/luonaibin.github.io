---
layout: default
title: Contact 新成
---

<div id="contact">
  <h1 class="pageTitle">Contact Me</h1>
  <div class="contactContent">
    <p class="intro">This is an example Contact page. If you want to make changes then do so in the <code>contact.html</code> file.</p>
    <p>The form is provided by <a href="http://formspree.io/">Formspree.</a> Follow the directions on their site to set up the form for use.</p>
    <p>If you have questions about the theme feel free to <a href="mailto:xujunfu@shu.edu.cn">email me</a> or create an issue on <a href="https://github.com/JunFuXu">GitHub</a>. Enjoy!</p>
  </div>
  <form action="https://formspree.io/xujunfu@shu.edu.cn" method="POST">
    <label for="name">姓名</label>    
    <input type="text" id="name" name="name" class="full-width"><br>
    <label for="email">Email</label>
    <input type="email" id="email" name="_replyto" class="full-width"><br>
    <label for="message">消息</label>
    <textarea name="message" id="message" cols="30" rows="10" class="full-width"></textarea><br>
    <input type="submit" value="发送" class="button">
  </form>
</div>