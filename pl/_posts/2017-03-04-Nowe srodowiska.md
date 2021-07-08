---
layout: post
title:  Jeden Jupyter, wiele środowisk
date:   2017-03-04
subject: Wpis pokazuje jak rozszerzyć Jupytera o dodatkowe środowiska, np. inne instalacje Pythona, ale również inne języki programowania.
image: /assets/images/notes/170304_Nowe/jupiter.jpg
image-opacity: 0.8
category: pl
tag:
- python
- Anaconda
- Jupyter
- R
---

<!-- more -->

# Wszystko pod jednym dachem

Poniższy wpis pokazuje w jaki sposób można doinstalować do istniejącego środowiska pythona kolejne niezależne instacje. Zobaczymy też w jaki sposób możemy dodać do Jupytera interfejsy dla innych języków programowania.

## Mieć wszystkie pythony!

Użyteczność Anacondy i Jupytera nie kończy się na zaistalowaniu pakietu z wybraną wersją pythona. Może się przecież okazać, że oprócz zainstalowanego pythona 3, potrzebujemy go również w **wersji 2.7** (ciągle jest spoko bibliotek, które nie zostały uaktualnione, lub wręcz nigdy nie będą). Ściągnięcie kolejnego instalatora Anacondy wydaje się ogromnym marnowaniem zasobów. Pobieranie innych dystrybucji najpewniej wygeneruje więcej zamieszania niż korzyści. Na szczęście, twórcy Anacody przewidzieli te potrzeby i wbudowali mechanizm, który pozwoli pogodzić nie tylko różne wersje pythona, ale nawet stworzyć kilka osobnych instancji tej samej wersji pythona, jeśli tylko będziemy tego potrzebować. Przejdźmy zatem do dzieła.

Najważniejsze funkcje Anacondy dostępne są wyłącznie z poziomu jej terminala. Szczęśliwie, cała procedura wymaga wprowadzenia w zasadzie jednego polecenia. W tym celu otwieramy *Anaconda Prompt* i wstukujemy poniższy kod:
```bash
conda create -n py27 python=2.7
```
Conda utworzy nam nowe środowisko o nazwie **py27**, ale można nadać mu dowolną nazwę - jest ona potrzebna przede wszystkim do odróżnienia środowisk od siebie (w końcu możemy zapragnąć mieć kilka instalacji pythona 2.7). Po wciśnięciu klawisza enter conda przystąpi do dzieła i zainstaluje pythona oraz najwazniejsze biblioteki niezbędne do poprawnego funkcjonowania.

![Przebieg instalacji dodatkowego pythona 2.7](/assets/images/notes/170304_Nowe/install_environment.png)

Gotowe! Teraz wystarczy wprowadzić komendę **activate py27** a przełączymy się na nowo zainstalowane środowisko pythona 2.7. Nie interesuje nas jednak praca w terminalu, ale w Jupyterze, dlatego musimy do nowego pythona doinstalować tzw. *kernel* iPythona, który umożliwi korzystanie z tej instancji pythona w przeglądarce internetowej. W tym celu musimy przełączyć się do nowego środowiska i zainstalować co trzeba. Wprowadzamy do konsoli następujący kod:

```bash
activate py27
conda install notebook ipykernel
ipython kernel install
deactivate py27
```

Conda będzie potrzebowała chwili, żeby ściągnąć wszystkie biblioteki i je zainstalować. Trzecia linia kodu zainstaluje i skonfiguruje nowy kernel, dzięki czemu w oknie Jupytera w przeglądarce będziemy mogli wybrać utworzenie nowego notatnika opartego o Pythona 2.

## Wielojęzyczność programistyczna

Jupyter wyrasta bezpośrednio ze środowiska pythona, ale jako interfejs przeglądarkowy jest niezależny od jakiegokolwiek języka programowania. Co więcej, otwartość na inne języki jest traktowana jako jedna z największych zalet. Wystarczy zatem stworzyć odpowiedni *kernel* (zbiór instrukcji łączących Jupytera i dowolny język) i powinno być możliwe kodowanie w swoim ulubionym języku bez konieczności zmiany programu czy wychodzenia z przeglądarki. Z perspektywy pracy badawczej i analizy danych, najczęściej wybieranymi środowiskami (oprócz Pythona) są Matlab oraz R. Z każdym z nich możemy pracować w Jupyterze. Poniżej zobaczymy jak w prosty sposób dodać obsługę środowika R.

Pierwszym krokiem będzie zainstalowanie samego R. Najpewniejszym źródłem jest oczywiście [oficjalna strona projektu](https://www.r-project.org/). Wybieramy wersję odpowiednią dla naszego systemu operacyjnego i przechodzimy przez wszystkie kroki instalacji. Następnie musimy uruchomić R, najlepiej z uprawnieniami administratora, żeby mieć pewność, że wszystkie zmiany przebiegną poprawnie.  
Połączenie z Jupyterem osiągniemy dzięki bibliotece **IRkernel**, która zapewni wykonanie kodu wpisywanego do przeglądarki przez środowisko R. Informacje szczegółowe na temat tego projektu można znaleźć na [jego stronie](https://irkernel.github.io/). Przejdźmy zatem do instalacji. Po otworzeniu konsoli R powinniśmy zobaczyć białe okno ze znakiem **>** wskazującym na gotowość przyjęcia kodu. Wprowadźmy tam następujące komendy:
```R
install.packages(c('repr', 'IRdisplay', 'evaluate', 'crayon', 'pbdZMQ', 'devtools', 'uuid', 'digest'))
devtools::install_github('IRkernel/IRkernel')
``` 
Pierwsza linia pobierze i zainstaluje niezbędne biblioteki pomocnicze (konieczne będzie wskazanie serwera do pobierania, ale ta decyzja może jednie mieć wpływ na szbykość procesu). Druga ściągnie i zainstaluje główną bibliotekę z GitHuba.  
Ostatnim krokiem będzie sprawienie, że kernel będzie dostępny dla Jupytera. Żeby to osiągnąć wpisujemy do konsoli:
```R
IRkernel::installspec()
```
Jeśli zależy nam na instalacji ogólnosystemowej (domyślnie R instaluje wszystkie dodatkowe elementy tylko dla aktualnego użytkownika), musimy do nawiasu powyżej komendy wprowadzić - user = FALSE. Jeśli nie pojawią się jakieś niespodziewane błędy, po wykonaniu tych kroków będziemy mogli użyć w Jupyterze języka R. Rozwijana lista do wyboru środowiska notatnika powinna wyglądać mniej więcej tak:  
![Widok menu z dostępnymi nowymi kernelami](/assets/images/notes/170304_Nowe/menu.png)  
Rzucać się w oczy może dość niejasny sposób numeracji kolejnych środowisk (w szczególności Pythona). Wynika to trochę z konstrukcji Anacondy i Jupytera, które chcą wspierać możliwość wielu instancji tych samych języków. Najważniejsze to zapamiętać, która dystrybucja była naszą podstawową (w liście będzie opisana jako *conda root*).  

Obecnie możliwe jest zaimplementowanie obsługi kilkudziesięciu języków programowania i tym samym korzystanie z nich w obrębie jednej platformy. Oczywiście każdy wymaga zainstalowania podstawowego środowiska oraz właściwego kernelu, ale później wystarczy tylko jedno kliknięcie, by móc pracować obok siebie na kilku różnych językach. Najbardziej aktualna lista dostępnych kernelów znajduje się [pod tym adresem](https://github.com/jupyter/jupyter/wiki/Jupyter-kernels). Szczegółowe informacje o instalacji poszczególnych interfejsów można znaleźć na macierzystych stronach tych projektów.
/marcin
