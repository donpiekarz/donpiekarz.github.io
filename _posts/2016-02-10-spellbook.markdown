---
published: false
title: spellbook
layout: post
summary: Miales kiedys do czynienia z dlugimi poleceniami? Lub rzadkimi na tyle, ze nie ma ich w .bash_history? Spellbook rozwiazuje te problemy.
tags: 
 - spellbook
 - linux
 - projekt
---

Pomysl walal sie po mojej glowie juz prawie rok. W koncu udalo sie do niego usiasc i po prostu napisac. Glowna motywacja bylo to, ze po prostu potrzebuje go do zrealizowania kolejnego projektu. 

Projekt jest zrealizowany w Pythonie. Dla mnie interesujace tutaj bylo sprawdzenie jak sie pisze kod dzialajacy tak samo w Python 2 jak i Python 3. Wiecej szczegolow technicznych jest w czesci zatytulowanej (realizacja)[#realizacja]. 

# problem

Najlepiej problem opisuje komiks z portalu [xkcd.com](http://imgs.xkcd.com/)

!(tar)[http://imgs.xkcd.com/comics/tar.png]

Moja praca i przyzwyczajenia powoduja, ze sporo czasu spedzam w konsolach tekstowych typu Bash. Do tego bardzo rzadko pracowalem na tej samej maszynie. W efekcie typowe CTRL + R nie znajdywalo tego co szukalem. Czesto tez nie wiedzialem jak tego szukac. 

# spellbook

bbbb

# realizacja

Caly kod jest dostepny na githubie: [Spellbook](https://github.com/donpiekarz/spellbook). 

Tak jak pisalem we wstepie, wspierany jest Python 2 i 3. Oczywiscie kod jest paskudny i nie zalecam tam zagladac. Wersja bez dropboxa skaladala sie na ok 150 lini kodu. Dodanie dropboxa spowodowalo napisanie kolejnych 170 linii. I rozwiazanie kilku ciekawych problemow. Najwiekszym wyzwaniem okazalo sie wymyslenie logiki laczenia zmian w plikach 'ksiag'. Przykladowe scenariusze:
- uzytkownik nie ma lokalnego repozytorium 'ksiag' - sciagamy wszystko z dropa
- uzytkownik ma akutalne repozytorium 'ksiag' - nie robimy nic, ale jak sprawdzic czy jest aktualne ??
- uzytkownik nie ma aktualnego repozytorium 'ksiag':
  - dodal cos do ksiegi AAAA
  - usunol cos z ksiegi AAAA
  - dodal nowa ksiege ZZZZ
  - usunol ksiege BBBB
  - 
