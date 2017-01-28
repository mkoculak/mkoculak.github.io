---
layout: post
title:  Python od zera - Instalacja środowiska
date:   2017-01-23
subject: Krótki poradnik jak zainstalować Pythona wraz z udogodnieniamia dla początkujących programistów.
image: 
image-opacity: 0.8
tag:
- python
- Anaconda
- Spyder
---

<!-- more -->

# Od czego by tu zacząć...
Początkujący użytkownik czegokolwiek nie ma zbytnio pojęcia, w jaki sposób zabrać się za nową rzecz. Niezależnie czy chce pierwszy raz skorzystać z odkurzacza, metra czy języka programowania. Prowadząc zajęcia dość łatwo zauważyć, że osoby początkujące potrzebują jasnych i prostych instrukcji a nie rozwlekłych dywagacji o możliwych opcjach czy pietnastu sposobów na zrobienie tego samego zadania.  
Niestety, społeczność programistów zazwyczaj tworzy narzędzia użyteczne dla osób, które już mają pewien poziom wiedzy. Podobnie instrukcje łatwo wpadają w żargon lub brak jakichkolwiek wyjaśnień dla podejmowanych kroków. Ja sam pewnie też nie jestem już wolny od tych mechanizmów, ale nie mam tego obciążenia wiedzą, jak ludzie będący programistami. :)  
Dlatego poniższa instrukcja kierowana jest do osób, które posiadają ogólną wiedzę na temat obsługi komputera, ale nie miały do tej pory żadnego doświadczenia programistycznego.

## Jeden Python, różne wersje
Pierwsza trudność pojawia się już na samym początku, ponieważ nie da się po prostu "pobrać Pythona". Nie dość, że ciągle istnieją dwie równoległe wersje (2.7 i 3.5), to jeszcze można trafić na produkty różnych firm, fundacji, czy nawet pojedynczych hobbystów.  
Dobra wiadomość jest taka: to wszystko jest dokładnie ten sam język programowania. Zła wiadomość: wybór między wersjami jest bardzo istotny z perspektywy początkującego użytkownika. Doświadczony programista dostosuje pod siebie w zasadzie każdy produkt. My jednak chcielibyśmy coś, czego nie trzeba będzie na samym początku całkowicie przebudowywać. Proponuję Wam zatem konkretne rozwiązanie, które moim zdaniem jest najlepiej dostosowane do początku przygody z Pythonem.

#### Ważna uwaga 
Zarówno ten poradnik, jak i wszystkie materiały na tej stronie, dostosowywane są do wykorzystania Pythona w kontekście naukowym, czyli przede wszystkim zbierania, analizowania oraz wizualizacji danych. Moim zdaniem te porady przydadzą się każdemu, ale jeśli istnieje specjalna dystrybucja dostosowana do Twoich potrzeb/zainteresowań, wtedy być może lepiej jest skorzystać właśnie z niej.  
My natomiast przejdziemy do opisu i instalacji <strong>Anacondy</strong>.

<img style="width: 70%; margin-top: 4rem; margin-bottom: 3rem;" src=" https://www.continuum.io/sites/all/themes/continuum/assets/images/logos/logo-horizontal-large.svg">

## Czym jest Anaconda
Anaconda jest dystrybucją Pythona przygotowywaną przez firmę Continuum Analytics, którą można pobrać pod [tym linkiem](https://www.continuum.io/downloads). Jest ona dedykowana do zastosowań naukowych, posiada zatem prawie wszystkie potrzebne nam biblioteki. Omijamy zatem konieczność samodzielnego ich instalowania. Na stronie wystarczy wybrać plik odpowiadający systemowi operacyjnemu, którego ma się na komputerze oraz wskazać wersję Pythona. Osobiście polecam wybrać wersję 3.x, ponieważ tylko ona jest aktywnie rozwijana. Co prawda jest jeszcze trochę programów i bibliotek, które działają tylko w wersji 2, ale będą one sukcesywnie zanikać. Ostatni wybór dotyczy 32- czy 64-bit. Na tym etapie nie ma to większego znaczenia, więc wybierzcie 64-bit, bo to jednak bardziej przyszłościowe.  
Plik jest spory, ściągnięcie i zainstalowanie go może trochę potrwać. Dokładne szczegóły instalacji widzicie obok linków do pobierania. Wystarczy za nimi podążać - to zazwyczaj jedna, dwa kroki.

### Środowisko Anacondy
<img style="float: right; margin-top: 1rem; margin-left: 2rem;" src="/assets/images/notes/anaconda/anaconda_install.png">
Anaconda to nie tylko dystrybucja języka programowania, ale cały ekosystem powiązanych aplikacji, które starają się ułatwić i zautomatyzować pracę z Pythonem. Tutaj widzicie elementy, które zostały zainstalowane na moim Windowsie. Pokrótce omówimy sobie najważniejsze z nich.

**Anaconda Navigator** - można traktować go jako taki "punkt dowodzenia" dla Anacondy, ponieważ pozwala na uruchomienie innych usług oraz dostęp do funkcjonalności niedostępnych z poziomu menu Windowsa. Z naszej perspektywy najistotniejsze jest to, że w zakładce **Home** mamy dostęp do Jupyter Notebooka oraz do Spydera, o których więcej informacji niżej. Oprócz tego, zakładki Learning i Community pozwalają na dostęp do materiałów tutorialowych oraz przeróżnych stron, istotnych z perspektywy użytkowników (np. stron konferencji branżowych, for dyskusyjnych etc). Warto je przejrzeć poszukując materiałów do nauki albo odpowiedzi na pytania dotyczące Anacondy czy Pythona w ogóle.

**Anaconda Prompt** to w zasadzie typowy wiersz poleceń (inaczej zwany terminalem), który podpięty jest bezpośrednio do naszej dystrybucji Pythona. Dzięki temu możemy bardzo szybko wykonać podstawowe i niezbędne czynności, np. instalacja pakietów czy aktualizacja tych już obecnych. Do tego wszystkiego służyć będą komendy **condy**, czyli menadżera pakietów Anacondy. Dostępny jest również drugi popularny menadżer **pip**, któy ma dostęp do znaczenie większej ilości pakiektów (conda natomiast jest pod dużo lepszą kontrolą twórców, którzy dbają, by wszystko działało jak należy). Przykładowo, żeby uaktualnić wszystkie zainstalowane pakiety wystarczy wpisać do prompta:
```
conda update --all
```
Możemy też bezpośrednio z prompta uruchomić nasz główny interfejs - Jupytera:
```
jupyter notebook
```

```python
import numpy as np
def funkcja(argument):
  stala = 'tekst'
  druga = 5
  return np.mean(druga)
```


/marcin
