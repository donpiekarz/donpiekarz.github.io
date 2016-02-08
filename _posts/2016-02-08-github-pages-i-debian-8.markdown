---
published: true
title: Github pages i Debian 8
layout: post
---
Jak każdy pewnie się spodziewa, [instrukcja odpalenia](https://help.github.com/articles/using-jekyll-with-pages) github pages na Debianie osiem nie działa.

W skrócie, trzeba zrobić tak:

1. Zainstalować Ruby w wersji conajmniej 2.0.0
2. Zainstalować bundlera
3. W katalogu bloga trzeba stworzyć plik Gemfile a w nim zawartość:
{% highlight ruby %}
source 'https://rubygems.org'
gem 'github-pages'
gem 'pygments.rb'
{% endhighlight %}
4. Potem zrobić bundle install
5. I można już uruchamiać jekylla poleceniem:
{% highlight bash %}
bundle exec jekyll serve
{% endhiglight %}
