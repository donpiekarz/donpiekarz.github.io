---
published: false
title: spellbook
layout: post
summary: Miałeś kiedyś do czynienia z długimi poleceniami? Lub rzadkimi na tyle, ze nie ma ich w .bash_history? Spellbook rozwiązuje te problemy.
tags:
 - spellbook
 - linux
 - projekt
---

Pomysł walał się po mojej głowie już prawie rok. W końcu udało się do niego usiąść i po prostu napisać. Główną motywacja było to, ze po prostu potrzebuje go do zrealizowania kolejnego projektu.

Projekt jest zrealizowany w Pythonie. Dla mnie interesujące tutaj było sprawdzenie jak się pisze kod działający tak samo w Python 2 jak i Python 3. Więcej szczegółów technicznych jest w części zatytułowanej [realizacja](#realizacja).

# problem

Najlepiej problem opisuje komiks z portalu [xkcd.com](http://imgs.xkcd.com/)

![tar](http://imgs.xkcd.com/comics/tar.png)

Moja praca i przyzwyczajenia powodują, że sporo czasu spędzam w konsolach tekstowych typu Bash. Do tego bardzo rzadko pracowałem na tej samej maszynie. W efekcie typowe CTRL + R nie znajdywało tego co szukałem. Często też nie wiedziałem jak tego szukać.

# spellbook

Teraz słów kilka jak tego używać. Jest to przetłumaczona dokumentacja ze [strony projeku](https://pypi.python.org/pypi/spellbook).

Zaczynamy od instalacji (dropbox jest opcjonalny):
{% highlight bash %}
# pip install spellbook[with_dropbox]
Lub
# pip install spellbook dropbox
{% endhighlight %}

Na początku musimy utworzyć pierwszą 'księgę':
{% highlight bash %}
$ spellbook rozne create
{% endhighlight %}

Jak chcemy coś dodać do 'księgi':
{% highlight bash %}
$ spellbook rozne add "tar -xvzf file.tar.gz" "extract tar.gz archive"
{% endhighlight %}

Żeby wyszukać należy zrobić tak:
{% highlight bash %}
$ spellbook rozne search tar
tar -xvzf file.tar.gz
{% endhighlight %}

Ficzerów jest więcej, zainteresowanych zapraszam do pytania lub readme/helpa.

Ja swoje 'księgi' powoli buduję, w przyszłości się nimi podzielę :)

# realizacja

Cały kod jest dostępny na githubie: [Spellbook](https://github.com/donpiekarz/spellbook).

Tak jak pisałem we wstępie, wspierany jest Python 2 i 3. Oczywiście kod jest paskudny i nie zalecam tam zaglądając. Wersja bez dropboxa składała się na ok 150 linii kodu. Dodanie dropboxa spowodowało napisanie kolejnych 170 linii. I rozwiązanie kilku ciekawych problemów. Największym wyzwaniem okazało się wymyślenie logiki łączenia zmian w plikach 'ksiąg'.

Przykładowe scenariusze:
- użytkownik nie ma lokalnego repozytorium 'ksiąg' - ściągamy wszystko z dropa,
- użytkownik ma aktualnie repozytorium 'ksiąg' - nie robimy nic, ale jak sprawdzić czy jest aktualne ??
- użytkownik nie ma aktualnego repozytorium 'ksiąg':
  - dodał coś do księgi AAAA
  - usunl coś z księgi AAAA
  - dodał nowa księge ZZZZ
  - usunął księgę BBBB
