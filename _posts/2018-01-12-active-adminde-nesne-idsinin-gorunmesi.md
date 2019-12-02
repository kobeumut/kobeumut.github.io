---
title: Active Admin'de nesne id'sinin görünmesi
categories:
- ruby
- ruby on rails
date: '2018-01-12 00:06:00'
layout: post
---

Eğer migration işlemi yaptığınızda ve modelde referans olarak başka bir model adını yazdıysanız yani id ile ilişkilendirmek yerine referans olarak atadıysanız ("rails generate migration AddUserReferecesToCompanies user:references" gibi) active adminde bu user tablosunu direk eklediği için bunu nesnenin referansı olarak gösterebiliyor. Bu durumda yapılması gereken işlem basit. Form tagı açarak nesne içerisinden örneğin ben emaili getirmek istedim, o da şu şekilde.

``` ruby
ActiveAdmin.register Company do
  permit_params :user_id, :name ## Add this line


  form do |f|
    f.inputs "Admin Details" do
      f.input :user_id, as: :select, collection: User.all.map { |a| [a.email, a.id] }
      f.input :name

      f.actions
    end
  end
end
```