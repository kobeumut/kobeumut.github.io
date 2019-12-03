---
title: Link_to yerine data-method kullanma
layout: post
date: '2018-01-12 00:00:00'
categories: ruby on rails
---

Ruby on rails'de bilindiği üzere belli standartlar var ve html içerisinde link_to kullanıyoruz aslında kullanmanız şart değil uygulama path yani yolunu vererekte kullanabilirsiniz. Ancak bir method kullanıldıysa bunun için href tag'ı içerisine data-method'unu da eklemeniz gerekiyor. 
Örneği inceleyince daha iyi anlayabiliriz.

```ruby
<a data-method="delete" href="<%= destroy_user_session_path %>">
  <i class="fa fa-sign-out" aria-hidden="true"></i>
  <span class="hidden-xs hidden-sm">Exit</span>
</a>

<!--
  this is user signout with devise sample. That's equivalent to:
	<%= link_to('Exit', destroy_user_session_path, method: :delete) %>
-->
```