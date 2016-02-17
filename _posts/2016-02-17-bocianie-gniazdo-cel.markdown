---
published: true
layout: post
title: Bocianie Gniazdo – cel
summary: dlaczego chcę zrealizować pomysł Bocianie Gniazdo
date: 2016-02-17 18:00:01
tags:
- dajsiepoznac
- python
- pomysl
- bezpieczenstwo
- siem
- bocianiegniazdo

---

Tak jak wspomniałem w poscie z [pomysłami]({% post_url 2016-02-09-pomysly %}) o pomyśle wtedy nazwanym [Bez nazwy 1]({% post_url 2016-02-09-pomysly %}#bez-nazwy-1). Teraz chciałbym go przedstawić już dumnie nazwanego 'Bocianie Gniazdo'. Nazwa z czapki, lepszej nie miałem :)

Chciałbym zrobić badania odpowiadające na poniższe pytania:

1. Ile jest nawiązanych połączeń z niezaufanym lub odwołanym CA[^1] (w tym self-signed)?
1. Jakie są statystyki wykorzystania różnych CA?
1. Jakie algorytmy są dostępne podczas negocjowania połączeń SSL/TLS?
1. Jakie algorytmy są wybierane do połączeń SSL/TLS?
1. Jakie domeny przedstawiają się nieprawidłowym certyfikatem?

Żeby odpowiedzieć na powyższe pytania potrzebuję stworzyć odpowiednie narzędzie. Tym narzędziem ma być właśnie 'Bocianie Gniazdo'. 

W dłuższej perspektywie chcę skutecznie wykrywać [ataki Man in the Middle](https://en.wikipedia.org/wiki/Man-in-the-middle_attack). Planuję wykorzystać jeden z dostępnych systemów [SIEM](https://en.wikipedia.org/wiki/Security_information_and_event_management) do tego zadania. Dlatego potrzebuję aplikacji, która będzie produkowała w czasie rzeczywistym wyniki inspekcji połączeń SSL/TLS do pliku tekstowego i wysyłała do systemu SIEM. 

Ważnym elementem dla mnie w tym projekcie jest poznanie biblioteki [Scapy](http://www.secdev.org/projects/scapy/), manipulującą na surowych pakietach sieciowych. 

---

[^1]: [Certificate Authority](https://en.wikipedia.org/wiki/Certificate_authority), urząd certyfikacji.


