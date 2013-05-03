# UNIX

## Powłoka sh

### Składnia wywołania
```
sh [-acefhiknstuvx] argumenty
```

---------------------------


### Definicje podstawowe

__odstępy__ znak tabulacji -TAB lub SPACJA

__nazwa__ ciąg liter, cyfr i znaków nie zaczynający się od cyfry

__parametry__ nazwa, cyfra lub którykolwiek ze znaków: "*", "@", "#","?", "-", "$", "!"

-----------------------------

### Składnia

__Proste_polecenie__

ciąg miepustych słów oddzielonych ostępami. Pierwsze słowo jest nazwą polecenia/programu do wywołania. 
Prócz przypadków wymienionych poniżej pozostałe słowa są przekazywane jako argumenty do wykonywanego  polecenia.
Nazwa polecenia przekazywana jest jako parameter zerowy.


__Przykład__


  cat plik1 plik2
  
  "cat" - polecenia, "plik1", "plik2" - argumenty
  
__Potok__

Polecenie lub sekwencja poleceń (niekoniecznie prostych) oddzielonych od siebie znakiem "|" lub "*".
Standardowe wyjście każdego polecenia stanowi standardowe wejście następnego polecenia.
Każde polecenie wykonywane jest jako osobny proces (być może za wyjątkiem oststniego, jeśli jest ono poleceniem
wbudowanym). Powłoka czeka, aż ostanie polecenie potoku zakończy działanie.



__Kody powrotu__

Jeśli polecenie zakończyło się poprawnie, jego kod powrotu wynosi 0, w przeciwnym przypadku jest on większy od 128.
Kod powrotu potoku równy jest kodowi powrotu jego ostatniego polecenia.

__ Przykład__

```
ls /home | grep abcd | more
```
``ls /home``` pierwsze polecenie

``grep abcd`` drugie polecenie

```more`` trzecie polecenie

### Lista

Lista to jedno, lub więcej prostych poleceń lub potoków, oddzielonych znakami ";", "&", "&&", "||".
Lista zakończona jest znakiem ";", "&" lub znakiem nowej linii. Znaki ";" i "&" mają równe i niższe piorytety
niż "||", "&&". Powłoka czeka, aż wykonanie poprzedzającego znak ";" potoku zostanie zakończone. Znak "&" powoduje, 
że poprzedzający go potok zostanie wykonany synchronicznie (w tle)-powłoka nie czeak na zakończenie pracy potoku.
Symbole "&&" i "||" używane są w celu warunkowego wykonania  listy po ich prawej stronie. Lista po prawej stronie
symbolu "&&" zostanie wykonana tylko wtedy, gdy potok po jego lewej stronie zwróci zerwoy kod powrotu.
Lista po prawej stronie symbolu "||" zostanie wykonana tylko wtedy zostanie wykonana tylko wtedy, gdy potok po jego 
lewej stronie zwróci niezerwoy kod powrotu. Dowowlna liczba znaków "NOWA LINIA" może zastępować w liście średniki.

__Przykłądy__

```
./my_job dane | sort -r | store & emacs prog.c
```

Lista składa się z dwóch potoków. Pierwszy potok składa się z poleceń "./my_job dane | sort -r | store"
i wykonywany jest w tle. Drugie polecenie "emacs prog.c" wywoływany jest synchronicznie: powłoka czeka na jego
zakończenie przed wyświetleniem kolejnego monitu.
```
test a -gt b && echo "Źle, nieprawda, że a>b"
test a -gt b || echo "dobrze, nieprawda, że a>b"
```
 Wykonanie pierwszej listy nie powoduje wyświetlenia żadnego komunikatu: praogram test zwróci wartość niezerową
 , a więc plecenie 'ech ..." nie zostanie wykonane.  W drugim przykładzie wyświetlony zostanie komunikat
 "dobrze, nieprawda, że a>b".

### Słowa specjalne

Specjalne zbnaczenie słów jest rozpoznawalne, gdy są one perwszym słowem oraz nie są cytowane;

```
if then for case esacfor while until do done {}
```

### Komentarze

Słowa zaczynające się zankiem "#" i wszystkei następne, aż do znaku nowej linii, są przez powłokę ignorowane

### Polecenia

Polecenie jest to proste_polecenie leb jedna z następujących konstrukcji:

```
for nazwa [in słowo ...] do lsta done
```

lista będzie  wykonana raz dla każdej kolejenj wartości zmiennej _nazwa_. Zmienna _nazwa_ będzie przyjmowała wartosci
z ciągu "_słowo_". Jeżeli fraza "_in słowo ..._' zoatnie pominięta, zmienna _nazwa_ będzie przyjmowała kolejne
wartości parametrów pozycyjnyhc (czyli argumentów wywłąnia) powłoki.
