# Edytor vi lub jego klon vim
## Informacje wstępne
__vi__ jest edytorem służącymdo przetwarzania wierszy, to znaczy ciągówznaków z kodów __ascii__ zakończonych znakiem
nowej linii. Sesja pracy z edytorem vi zaczyna się od wczytania pliku pobranego do edycji. Edytor zmienia tryb pracy
terminala na tzw. "raw mode". Początkowo edytor ustawia się w __trybie przyjmowania poleceń__.
Do trybu wydawania poleceń przechdzi się po naciśnięciu klawisza __[ESC}__
Do trybu edycju przechodzi się najczęściej za pomocą znaków jednoliterowych:
* __I__ wstaw tekst na początku linii w której jest kursor
* __i__ wstaw tekst przed pozycją kursora
* __o__ dodaje pustą linię poniżej pozycji kursora i wchodzi w tryb wstawiania w nowej linii tekstu
* __O__ dodaje pustą linię powyżej pozycji kursora i wchodzi w tryb wstawiania znaków w niej
* __a__ dodaje tekst bezpośrednio za bieżącą pozycją kursora
* __A__ dodaje tekst na końcu linii w której jest kursor
* __r__
* __R__
 

## Ruchy kursora

* __h__ kursor o jeden znak w lewo
* __j__ jedna linia w dół
* __k__ jedna linia w górę
* __l__ jeden znak w prawo
* __liczbaG__ przejści do linii o numerze __liczba__
* __[CTRL+F]__ jedna strona w dół
* __[CTRL+B]__ jedna strona w górę
* __[CTRL+D]__ pół strony w dół
* __[CTRL+F]__ pół strony do góry
* __0__  lub __^__ początek linii
* __$__ konic linii
* __H__ lewy górny róg ekranu
* __M__ linia w środku ekrane
* __L__ ostatnia linia ekranu


## Usuwanie tekstu

* __d$__ usuwa od pozycji kursora do  końca linii
* __d^__ usuwa od pozycji kursora do  początku linii
* __dw__ usuwa od pozycji kursora do  końca słowa
* __db__ usuwa od pozycji kursora do  początku słowa
* __dh__ usuwa przed kursorem
* __dl__ usuwa na pozycji kursora
* __dj__ usuwa od pozycji kursora do  nowej linii, ale ponieważ przekroczono garnice linii, efekt usunięcie 2 linii tekstu
* __x__ ja __dl__
* __X__ jak __dh__
* __D__ jak __d$__
* __dd__ usuwa linię w której jest kursor

## Zmiany lokalne

* __c__ (change) nowy_adres_kursora tekst_wstawiany [ESC]
* __cw__ zmienia znaki od bieżacej pozycji kursora do końca slowa
