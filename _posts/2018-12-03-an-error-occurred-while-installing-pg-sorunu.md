---
title: An error occurred while installing pg sorunu
categories:
- Sorunlar ve Çözümleri
- Ruby on Rails
date: '2018-12-03 23:00:00'
layout: post
---

# Rails Postgres adaptörünün pg gem'ine bağlanamama sorunu
Postgres eklentisinin 1.0.0 sürümü çıktı ancak henüz rails ile uyumlu değil dolayısıyla gemfile içerisinde bazı değişiklikler yapmanız gerekiyor.

Eğer Rails 5 sürümü üzeri ise

`gem 'pg','~> 0.18'`

yada Rails 5 sürümünden küçükse

`gem 'pg', '~> 0.11'`

olarak Gemfile dosyanıza ekleyip 

`bundle update pg`

yazmanız yeterli olacaktır.

Hala "An error occurred while installing pg (0.21.0), and Bundler cannot continue." şeklinde hata alıyorsanız postgresql'in devel yani geliştirme (development) dosyaları yüklü değil demektir. Eğer sunucunuza postgresql yüklemeyip sadece bağlantı yapacaksanız yapmanız gereken,

Centos;

`sudo yum install postgresql-devel`

Ubuntu;

`sudo apt-get install libpq-dev`

Mac;

`brew install postgresql`

Eğer postgresql yükleyecekseniz;

Ubuntu;

`sudo apt-get install postgresql postgresql-contrib libpq-dev`

Centos;

`sudo yum install postgresql-server postgresql-contrib postgresql-devel`

Macde zaten yukarıdaki işlem ile direk yüklenmektedir.