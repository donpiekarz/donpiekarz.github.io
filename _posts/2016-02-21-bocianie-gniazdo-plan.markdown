---
published: true
layout: post
title: Bocianie Gniazdo - plan
summary: przedstawienie planu rozwoju projektu pt. Bocianie Gniazdo
tags:
- bocianiegniazdo
- dajsiepoznac
- plan

---

W [poprzednim poscie]({% post_url 2016-02-17-bocianie-gniazdo-cel %}) opowiedziałem o czym ma być projekt. Natomiast w tym chciałbym przedstawić jakie dalsze kroki identyfikuję teraz. 

Plan działań:

1. zestawienie środowiska:
 - Kali Linux 2,
 - Python 3,
 - PyCharm 5,
 - Scapy X,
 - future (dla wstecznej kompatybilności z Pythonem 2);
1. pierwsze przechwycone pakiety,
1. od filtrowanie pakietów SSL/TLS,
1. połączenie pakietów w sesję (o ile to będzie potrzebne),
1. pobieranie danych z sesji (lub bezpośrednio z pakietów),
 - lewy adres ip (klient),
 - prawy adres ip (serwer),
 - nazwa domenowa lewego hosta,
 - nazwa domenowa prawego hosta,
 - dostępne algorytmy wraz z długościami kluczy,
 - wybrany algorytm,
 - główny CA,
 - wynik lokalnej weryfikacji CA;
1. produkowanie wyjścia z programu:
 - w formie tekstowej, 
 - w formacie syslog i przesłanie dalej;
1. zbieranie danych
1. analiza danych i odpowiedzi na pytania z [postu o planie]({% post_url 2016-02-17-bocianie-gniazdo-cel %})
1. koniec :)

Aktualnie jestem na kroku pierwszym i prawie drugim. Mianowicie trochę poczytałem dokumentacji o [Scapy](http://www.secdev.org/projects/scapy/). I mniej więcej wiem jak punkt drugi może wyglądać. Ciekawe jest też to, że wszystkie pozostałe kroki (poza ostatnim) są dla mnie prawie niewidoczne. I nie jestem wstanie przewidzieć czy to w ogóle da się zrobić.

