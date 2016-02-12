---
published: true
title: spellbook
layout: post
summary: "Miałeś kiedyś do czynienia z długimi poleceniami? Lub rzadkimi na tyle, ze nie ma ich w .bash_history? Spellbook rozwiązuje te problemy."
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

Tak jak pisałem we wstępie, wspierany jest Python 2 i 3. Wspierane są systemy Windows, GNU/Linux, MacOS. Oczywiście kod jest paskudny i nie zalecam tam zaglądając. Wersja bez dropboxa składała się na ok 150 linii kodu. Dodanie dropboxa spowodowało napisanie kolejnych 170 linii. I rozwiązanie kilku ciekawych problemów. 

Założenia:

- najważniejszy jest mój UX :)
- szybkość działania,
- unikanie zależności,
- to co nie wspiera spellbook da się zrobić podstawowymi narzędziami (edytor tekstu, proste operacje na systemie plików),
- wszystko w jednym pliku,
- po co klasy.

## łączenie

Największym wyzwaniem okazało się wymyślenie logiki łączenia zmian w plikach 'ksiąg'. Przykładowe scenariusze:

- użytkownik nie ma lokalnego repozytorium 'ksiąg',
- użytkownik ma aktualnie repozytorium 'ksiąg',
- użytkownik nie ma aktualnego repozytorium 'ksiąg':
  - dodał coś do księgi AAAA,
  - usunął coś z księgi AAAA,
  - dodał nowa księgę ZZZZ,
  - usunął księgę BBBB.
  
Przemyślenie tego problemu zajeło trochę czasu, ostatecznie zdecydowałem się na:

- Jeśli nie ma pliku lokalnego, a jest zdalny to go pobieram.
- Jeśli jest plik lokalny w tej samej wersji co zdalny to go wrzucam do dropa - nie jest to zbyt optymalne rozwiazanie. Taki stan oznacza, że plik lokalny wywodzi się z tego samego miejsca co na dropie. Jeśli był zmieniony to zmiany zostaną zaakceptowane bez konfliktu. Jeśli nie ma zmian to dropbox nic nie zmieni. Więc kosztem transferu (kilka KB) i czasu (kilka sekund) rozwiązuję normalny przypadek użycia. 
- Jeśli plik lokalny jest w innej wersji niż zdalny to następuje połączenie obu plików. Zakładam, że to plik zdalny będzie bardziej akutalny, więc do pliku lokalnego dodaje brakujące linie. Kolejnym założeniem jest, że rzadko ktoś edytuje lub usuwa wpisy w spellbooku. Więc lepiej coś dodać za dużo i użytkownik będzie musiał usunąć znowu niż stracić nawet jedno zaklęcie.
- Jeśli 'księga' jest usunięta zdalnie to zostanie ona też usunięta lokalnie - jak odróżnić czy plik jest nowy czy usunięty zdalnie? Nowy plik nie ma wpisu w moim repozytorium, usunięty ma.

Żeby to wszystko zrealizować musiałem dokodować kilka funkcji. Zostałem zaskoczony przez złożoność problemu, dlatego trochę posypała mi się architektura. I teraz kod potrzebuje refactoringu :)

## Windows, GNU/Linux, MacOS i Python 2, Python 3

Napisanie przenośnego kodu jest też dość interesujce. Żeby uzyskać kompatybilność Pythona 2 w przód trzeba zastosować moduł future (pip install future). Do tego dwa importy i niby już. W praktyce i tak trzeba wszystko przetestować na obu środowiskach, bo inne moduły nie korzystają z funkcji z future. I np moduł json nie zwraca unicode i trzeba to dodatkowo konwertować. 

Wsparcie dla innych systemów niż GNU/Linux jest prawie teoretyczne :)
Mam info, że na Macu działa. Nie wiem co, ale działa. Jedynie co mogę zapewnić, że kod powinien być kompatybilny.

Obawiam się jak to się będzie ze wsparciem różnych kodowań. Nie sprawdzałem, obawiam się, że coś się posypie. 

Z mojej strony projekt wchodzi w stan utrzymania. Mam jeszcze ze dwa pomysły co by mi się przydało, ale dużych zmian się nie spodziewam.

Całość kodowana i testowana z:

- Kali Linux 2,
- PyCharm Pro 5,
- Python 3.4.2,
- dropbox api 4.0,
- future 0.15.2.

Serdecznie zapraszam do forkowania i udostępniania ficzurów!
