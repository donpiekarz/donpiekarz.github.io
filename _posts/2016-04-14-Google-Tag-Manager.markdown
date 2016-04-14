---
layout: post
title: Google Tag Manager
summary: krótki wpis czym to jest i jaki problem rozwiązuje
tags:
- google-tag-manager
- google-analytics
- dajsiepoznac

---

Ciekawe we mnie jest to, że często bardziej mnie interesuje jak coś zrobić niż faktycznie to zrobić. Wystarczy popatrzeć na większość moich projektów. Podobnie jest też z tym blogiem, bardziej chciałem go zrobić fajnym niż faktycznie go prowadzić. I tak też zachciałem mieć statystyki z tego co czytelnicy klikają. Chciałem wiedzieć, czy udostępniają na Fejsiku lub Twitterku. 

Spodziewałem się, że to po prostu będzie włączenie czegoś na stronie Google Analytics a w najgorszym przypadku dodanie jakiegoś prostego kodu javascript na stronę. 

Wg [tego](https://support.google.com/analytics/answer/1136960?hl=pl) trzeba dodać kawałek jsa na strone, ok. Trafiam [tutaj](https://developers.google.com/analytics/devguides/collection/analyticsjs/events) a tam jest opis API, hmmm. To gdzie ten js? Okazuje się, że jest jakiś kodzik do wklejenia, ale to już grubsza sprawa. W między czasie zacząłem się zastanawiać czym jest ten Google Tag Manager, którego mi tak często Google podpowiadało. 

# Google Tag Manager

Jest to narzędzie wielkości Google Analytics, którym głównym celem jest wstrzykiwanie w stronę innych Java Scriptów. Google Tag Manager rozwiązuje problem częstych zmian strony w przypadku osadzania kolejnych jsów na stronie. 

Przykładowo, mamy sklep internetowy i na nim tylko Google Analytics. Sklep przygotowała nam Firma. Po miesiącu dochodzimy do wniosku, że chcemy wrzucić na niego Facebooka, płacimy Firmie za dodanie kawałka kodu js na stronę. Po kolejnym miesiącu chcemy dodać kolejny fragment jsa. I tak w kółko. W przypadku Google Tag Manager dodamy go raz, a wszystkie inne wyklikamy sobie z portalu GTM. 

I tak po osadzeniu GTM włączyłem sobie Google Analytics, w kilka kliknięć. Dodanie śledzenia kliknęć wymagało już doczytania i zrozumienia czym są '[tagi](https://support.google.com/tagmanager/answer/3281060?hl=pl&ref_topic=3281056)', '[reguły](https://support.google.com/tagmanager/answer/6106961?hl=pl&ref_topic=3441647)' i '[makra/zmienne](https://support.google.com/tagmanager/answer/6106899?hl=pl&ref_topic=3441647)'. 

Efekt jest taki:
![statystyki kliknieć](https://dl.dropboxusercontent.com/u/7939953/blog/statystyki_klikniec_small.png)


Widać na tym, że np czytelnicy na wpisie o [celu w bocianim gniezdzie]({% post_url 2016-02-17-bocianie-gniazdo-cel %}) wchodzą na strony scapy i Wikipedię. A we wpisie o [pierwszym pakiecie]({% post_url 2016-03-05-bocianie-gniazdo-pierwszy-pakiet %}), ktoś kliknął w zrzut ekranu ze streama. 

I teraz będę wiedział jak, ktoś poda mój wpis dalej na Facebooku lub Twitterze!

## z czego korzystałem:
- wstęp do GTM - [Rewolucja w konfiguracji zdarzeń na stronie za pomocą Google Tag Managera](http://www.marketinglab.pl/rewolucja-w-konfiguracji-zdarzen-na-stronie-za-pomoca-google-tag-managera/)
- Bardzo rozbudowany przewodnik w pdfie po GTM v1 (teraz jest v2, ale da się ogarnąć) - [Google Tag Manager - Nie dla programistów](http://www.marketinglab.pl/wp-content/uploads/2014/03/gtm_przewodnik_marketinglab.pdf)

Serdecznie polecam oba!

