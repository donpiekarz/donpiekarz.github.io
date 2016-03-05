---
layout: post
title: Bocianie Gniazdo - pierwszy pakiet
summary: pierwszy przechwycony pakiet przez Bocianie Gniazdo!
tags:
- dajsiepoznac
- bocianiegniazdo
- stream
- python
- scapy

---

Tak więc konkurs [dajsiepoznac](http://www.maciejaniserowicz.com/daj-sie-poznac/) wystartował i trzeba było się jakoś pokazać i zainteresować tematem. Dlatego tego samego dnia streamowałem. 

[![streamuje](https://dl.dropboxusercontent.com/u/7939953/blog/streamuje-2016-03-01.png)](https://www.livecoding.tv/donpiekarz/videos/8Oy3J-plen-bocianie-gniazdo-3)

[W tamtym odcinku](https://www.livecoding.tv/donpiekarz/videos/8Oy3J-plen-bocianie-gniazdo-3) udało się przechwycić pierwszy pakiet. W zasadzie robi się to tak:


{% highlight python %}
import scapy.all

def packet_show(packet):
    packet.show()
	
def main():
    scapy.all.sniff(iface=args.interface, filter='icmp', prn=packet_show)
{% endhighlight %}

Krótkie objaśnienie interfejsu sniff:

- iface - interfejs na którym nasłuchujemy,
- filter - filtry zgodne z tcpdump,
- prn - funkcja uruchamiana dla każdego złapanego pakietu.


Ponieważ dość mało czasu mi zeszło na ten punkt to postanowiłem zająć się trochę [kolejnym]({% post_url 2016-02-21-bocianie-gniazdo-plan %}), czyli wyłapywania pakietów SSL/TLS. I tu zaczeły się schody. Bo okazuje się, że tcpdump nie ma wbudowanego filtra dla SSL/TLS (a wireshark ma, po postu: "ssl"). W kolejnym odcinku będę podchodzić do tego tematu.

A kolejny odcinek będzie za chwilę :)

