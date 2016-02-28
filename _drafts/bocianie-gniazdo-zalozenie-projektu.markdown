---
layout: post
title: Bocianie Gniazdo - założenie projektu
summary: kilka słów o napotkanych przeszkodach i pierwszym streamie 
tags: 
- bocianiegniazdo
- dajsiepoznac
- stream

---

![bocianie gniazdo](/images/posts/640px-BN_caboose,_Eola_Yard,_1993.jpg)

W [ostatnim streamie](https://www.livecoding.tv/donpiekarz/videos/a9gnQ-plen-bocianie-gniazdo-2) pokazywałem jak stworzyć nowy projekt w PyCharmie, bazując na, poprzednim projekcie, [spellbooku](https://github.com/donpiekarz/spellbook). Jednym z głównych powodów powstania spellbooka, było przetarcie szlaków w procesie wypuszczania oprogramowania przez [pypi](https://pypi.python.org/pypi). 

Oczywiście nie obyło się bez zaskoczeń. Pierwszym i najtrudniejszym była oczywiście nazwa paczki pythonowej. Było wiele pomysłów: 

- crow's nest
- foretop
- stork's nest

Jeszcze nie zdecydowałem się na jakąkolwiek. Która wam się podoba?

Spodziewałem się, że Bocianie Gniazdo też będzie wspierało Pythona 2 i 3, a tak niestety nie będzie. Okazało się, że [scapy](http://www.secdev.org/projects/scapy/) wspiera tylko Pythona 2. Musiałem z tego powodu odkręcać połowę ustawień projektu - stąd tak długi stream :)

