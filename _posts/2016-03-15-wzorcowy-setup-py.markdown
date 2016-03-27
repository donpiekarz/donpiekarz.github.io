---
layout: post
title: Wzorcowy setup.py
summary: omówienie głównego pliku projektu
tags:
- dajsiepoznac
- python

---

Tworząc nowy projekt skorzystałem z już istniejącego pliku setup.py, przygotowanego dla poprzedniego projektu. Przygotowując ten plik sporo się naczytałem i teraz przedstawiam krótki opis użytych pól. Zalecam używanie lub wzorowanie się na nim. 

Na początek cały kod ze [spellbooka](https://github.com/donpiekarz/spellbook):

_Formatowanie poniżej jest **brzydkie**, walczę ..._


{% highlight python linenos %}

#!/usr/bin/env python

import os

from setuptools import setup

from spellbooker import VERSION

here = os.path.abspath(os.path.dirname(__file__))

# Get the long description from the README file
with open(os.path.join(here, 'README.rst'), 'rU') as f:
    long_description = f.read()

required = [
    'future'
]

extras = {
    'with_dropbox': ['dropbox>=4.0.0']
}

setup(
    name='spellbook',
    version=VERSION,
    packages=['spellbooker'],
    url='https://github.com/donpiekarz/spellbook',
    download_url='https://github.com/donpiekarz/spellbook/tarball/' + VERSION,
    license='BSD',
    author='Bartlomiej Piekarski',
    author_email='poczta@example.org',
    description='store and search command lines',
    long_description=long_description,
    entry_points={
        'console_scripts': ['spellbook = spellbooker.application:main']
    },
    install_requires=required,
    extras_require=extras,
    classifiers=[
        # How mature is this project? Common values are
        #   3 - Alpha
        #   4 - Beta
        #   5 - Production/Stable
        'Development Status :: 3 - Alpha',

        # Indicate who your project is intended for
        'Intended Audience :: Developers',
        'Intended Audience :: System Administrators',
        'Intended Audience :: End Users/Desktop',
        'Intended Audience :: Science/Research',
        'Topic :: System :: Shells',
        'Topic :: System :: System Shells',

        # Pick your license as you wish (should match "license" above)
        'License :: OSI Approved :: BSD License',

        # Specify the Python versions you support here. In particular, ensure
        # that you indicate whether you support Python 2, Python 3 or both.
        'Programming Language :: Python :: 2',
        'Programming Language :: Python :: 2.6',
        'Programming Language :: Python :: 2.7',
        'Programming Language :: Python :: 3',
        'Programming Language :: Python :: 3.2',
        'Programming Language :: Python :: 3.3',
        'Programming Language :: Python :: 3.4',
        'Programming Language :: Python :: 3.5',
    ]
)

{% endhighlight %}

I teraz krok po kroku opiszę dane bloki, ciekawsze są wytłuszczone


## Linie:


1 - ustawienie środowiska uruchomieniowego

3 - import os, dla otwierania plików

**5** - importowanie lepszej funkcji setup, bardzo **ważne**!

7 - importowanie numeru wersji, zalecam umieszczać numer tam gdzie nie ma kodu, np. w pliku \_\_init\_\_.py.

**9 - 13** - dynamiczne wczytywanie długiego opisu z README

15 - 17 - lista wymaganych paczek

**19 - 21** - opcje rozszerzeń (patrz linia 38), słownik sympatycznych nazw i list paczek z tym związanych. 

24 - nazwa projektu

25 - numer wersji

26 - lista paczek wchodzących w skład projektu

27 - link do strony projektu

28 - link do pobrania kodu źródłowego

29 - licencja

30 - dane autora

31 - mail do autora

32 - krótki opis, który widać w pip

**33** - długi opis, który widać na stronie pypi, np [spellbook](https://pypi.python.org/pypi/spellbook)

**34 - 36** - Tworzenie jednego programu konsolowego nazwanego 'spellbook', którego główna funkcja znajduje się w 'spellbooker.application:main'. 

37 - lista wymaganych paczek

**38** - lista opcjonalnych paczek, będą zainstalowane tylko jeśli wspiera to pip i zostanie wywołany w specjalny sposób, np: {% highlight bash %} pip install spellbook[with_dropbox] {% endhighlight %}

**39-67** - odpowiadają za ustawienie tagów dla danej paczki. Jak widać są to informacje takie jak: dla kogo, licencja lub wspierane wersje Pythona. Pełna lista wszystkich [dostępnych kategorii](
https://pypi.python.org/pypi?%3Aaction=list_classifiers).


Pytania?

