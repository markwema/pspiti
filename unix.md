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
