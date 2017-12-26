# KISS - Keep It Simple, Stupid

"nie komplikuj, głuptasku"

Reguła ta nawiązuje do tego, żeby pisać swój kod w możliwie
najprostszy, zrozumiały dla innych sposób. Łączy w sobie
stosowanie wszystkich przydatnych praktyk dotyczących utrzymywania kodu,
całej jego struktury.

## Przykład 1 - niezrozumiała (wymagająca do zrozumienia czasu) instrukcja

* zamiast tak:

```js
function hasElement(arr, element) {
    let elementExists = false;

    for (let i = 0, len = arr.length; i < len; i += 1) {
        if (arr[i] === element) {
            elementExists = true;
            break;
        }
    }

    return elementExists;
}
```

Pisząc własną funkcję tego typu tworzymy koło na nowo. Warto zastanowić się
czy język w którym piszemy nie posiada owej funkcji lub nie ma w tym języku
napisanej jakiejś pomocniczej biblioteki, która taką implementację już zawiera.

Jeśli potrzebujemy utworzyć własną funkcję (np. ze względów
wydajnościowych) - nie trzymajmy jej implementacji w miejscu gdzie z niej korzystamy.
Wynieśmy ją np. gdzieś do utilsów.

* natomiast powyższy kod można napisać jeszcze prościej:

```js
!!~[1, 2, 3].indexOf(3)
```

* albo jeszcze prościej (łatwiej sprawdzić jak działa tylko indexOf, niż dodatkowo bitwise not (~) i rzutowanie do booleana (!!)):

```js
[1, 2, 3].indexOf(3) > -1
```

W kodzie, który jest do ogólnej modyfikacji (np. logika biznesowa), nie powinno
być takich rzeczy jak wyżej. Wszystkie konstrukcje powinny być na maksa
uproszczone, tak żeby czytelnik zrozumiał jak kod rozwiązuje problem, a nie z
jakich konstrukcji korzysta żeby go rozwiązać. Taki kod powinno się
czytać przyjemnie, zmienne / stałe / klasy / metody powinny być odpowiednio
ponazywane, tak, aby programista, który ma coś tam zmienić nie musiał domyślać się sensu
istnienia takiej i takiej konstrukcji. Dlatego uważam, że powyższy kod
wypadałoby jeszcze raz zmodyfikować i użyć czegoś co przedstawia nam
powód użycia konstrukcji, konkretne działanie, które jednocześnie opisuje
końcowy efekt.

```js
_.includes([1, 2, 3], 3)
```

Powyższy kod, wymaga znajomości funkcji "includes" z biblioteki
(w tym przypadku lodasha). Natomiast czytając kod, łatwo domyśleć się
co powyższa instrukcja realizuje. Dodatkowo, trzymając się reguły, że
każda funkcja powinna robić tylko jedną rzecz - łatwo będzie w przyszłości
podmienić implementację takiej funkcji (jeśli coś nam w niej nie pasuje).

Możemy także użyć funkcji z ES7 - includes:

```js
[1, 2, 3].includes(3)
```

Natomiast jeśli nasza aplikacja ma działać pod starszymi przeglądarkami
zalecam użycia funkcji z biblioteki (np. lodash) lub po prostu napisanie
własnej funkcji, ale z wyniesieniem jej implementacji gdzieś poza miejsce
gdzie jest używana.

## Przykład 2 - rezygnacja z instrukcji warunkowej

* zamiast tak:

```js
function check(a, b) {
    if (a === b) {
        return true;
    } else {
        return false;
    }
}
```

* spróbuj prościej:

```js
function check(a, b) {
    return (a === b);
}
```

---

Osobę która chce zrozumieć Twój kod nie obchodzi, że ta i ta
funkcja robi po drodze przypisanie do zmiennej, modyfikację w pętli,
instrukcję warunkową itd. Tą osobę interesuje wynik
końcowy, np. że ta i ta funkcja sprawdza czy element istnieje w tablicy.

Stosuj ogólnie znane praktyki, unikaj w kodzie własnych "potworków",
nie jedz spaghetti, skorzystaj z ogólnodostępnych narzędzi.

Korzystajmy z dobrodziejstw języka, wszędzie tam gdzie tylko to możliwe,
stabilne i obsługiwane.

Zawsze szukajmy prostszego rozwiązania naszego problemu, naprawdę
warto przed rozpoczęciem kodowania dokładniej go rozpisać.

Piszmy kod tak, aby programista, który go kiedyś przejmie
bez większego trudu mógł ten kod czytać jak książkę.
