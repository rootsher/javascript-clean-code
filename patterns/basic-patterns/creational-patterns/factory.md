# factory

Wzorzec fabryki umożliwia nam uzależnienie kodu od abstrakcji, a
nie od klas rzeczywistych ([DIP](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design))). Pozwala nam to na maksymalne ukrycie
jawnego tworzenia instancji danej klasy. Dzięki fabryce nie będziemy
uzależnieni od konkretnej implementacji, a nasz kod będzie otwarty
na rozbudową, ale zamknięty na modyfikacje ([OCP](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design))).

Poniżej przykład kodu do refactoru:

```js
let instance = null;

if (color === 'red') {
    instance = new RedCar();
} else if (color === 'blue') {
    instance = new BlueCar();
}
```

Powyższy kod nie wygląda jeszcze tak strasznie. A co się stanie, jeśli
będziemy chcieli go rozbudować? Wtedy stworzymy jakiegoś potworka z
instrukcji warunkowych, wiedzącego o wszystkim. Dojdą nowe samochody,
gdzie instancje będziemy tworzyć w inny sposób, albo nawet w kilka
osób w zespole trzeba będzie takiego potworka rozszerzać. Same problemy.
Z pomocą przychodzi nam kilka sposobów realizacji wzorca fabryki.

## simple factory (prosta fabryka)

W prostej fabryce chodzi o to, aby przenieść jawne tworzenie instancji
gdzieś indziej, np. do klasy / funkcji. Dzięki temu podmiot korzystający
z naszej fabryki nie będzie wiedział jak była tworzona instancja klasy,
którą potrzebuje - uzależniamy kod od abstrakcji.

```js
class Factory {
    createCar(color) {
        if (color === 'red') {
            return new RedCar();
        } else if (color === 'blue') {
            return new BlueCar();
        }
    }
}

class CarManager {
    constructor(factory) {
        this.factory = factory;
    }

    create(color) {
        return this.factory.createCar(color);
    }
}

const carManager = new CarManager(new Factory());

const redCar = carManager.create('red');

redCar.drive();
redCar.stop();
```

Ważne jest, że metoda `SimpleCarFactory->createCar` powinna zwracać instancje
mające wspólne klasy bazowe (w procesie dziedziczenia) lub implementujące
wspólny interfejs (tak, aby podmiot korzystający z instancji z góry wiedział
jakie możliwości ma obiekt).

## static factory (fabryka statyczna)

Fabryka statyczna przypomina prostą fabrykę, tyle, że metoda
tworząca instancję jest statyczna. Dzięki temu podczas korzystania z naszej
fabryki nie musimy tworzyć jej instancji i możemy odwołać się
bezpośrednio do metody statycznej.

Przykład:

```js
class Factory {
    static createCar(color) {
        if (color === 'red') {
            return new RedCar();
        } else if (color === 'blue') {
            return new BlueCar();
        }
    }
}

class CarManager {
    create(color) {
        return Factory.createCar(color);
    }
}

const carManager = new CarManager();

const redCar = carManager.create('red');

redCar.drive();
redCar.stop();
```

Rozwiązanie to ma jednak pewną wadę. Poprzez rezygnację z tworzenia
instancji fabryki ograniczamy sobie możliwość jej rozszerzania poprzez
dziedziczenie. Przez to każde rozszerzenie naszej fabryki będzie musiało
odbywać się przez przekazanie kolejnego parametru do naszej statycznej
metody, co sprawia, że nasze obiekty będą ze sobą ściśle powiązane, a
w końcu nie o to nam chodzi. Dlatego uważam, że statyczna fabryka nas
ogranicza. Z pomocą dziedziczenia możemy spokojnie rozszerzyć naszą
fabrykę, zachowując tym samym luźne powiązanie między współpracującymi
obiektami - oczywiście zachowując wspólny interfejs między klasami fabryki.

### method factory (metoda fabrykująca)

Wzorzec metody fabrykującej umożliwia nam jeszcze bardziej dokładne
rozdzielenie odpowiedzialności między tworzeniem instancji w fabryce,
a samym tworzeniem fabryki.

Wyobraźmy sobie, że mamy do zrobienia kilka samochodów. Do produkcji
zaangażowało się dwóch chętnych - Tom i John. Każdy z nich ma swoją fabrykę
samochodów i robi je na swój sposób. Spróbujmy zobrazować ich fabryki
w postaci kodu.

```js
class TomFactory {}

class JohnFactory {}
```

Każda z fabryk ma za zadanie utworzyć samochód, więc spokojnie te klasy
mogą dziedziczyć po wspólnej klasie bazowej, posiadając wspólną metodę.
Metoda ta z założenia wzorca powinna być abstrakcyjna - jako, że w JS
póki co nie da się w łatwy sposób utworzyć klasy / metody abstrakcyjnej,
musimy w tym momencie przyjąć w głowie takie założenie. Sama abstrakcja
na klasie uniemożliwi nam utworzenie jej instancji, a abstrakcja na metodzie
wymusi implementacje na klasach pochodnych.

```js
/**
 * @abstract
 */
class BaseFactory {
    /**
     * @abstract
     */
    createCar() {}
}

class TomFactory extends BaseFactory {}

class JohnFactory extends BaseFactory {}
```

Teraz możemy przejść do implementacji tworzenia samochodów w poszczególnych
fabrykach.

```js
class TomFactory extends BaseFactory {
    createCar(color) {
        if (color === 'red') {
            return new RedTomCar();
        } else if (color === 'blue') {
            return new BlueTomCar();
        }
    }
}

class JohnFactory extends BaseFactory {
    createCar(color) {
        if (color === 'red') {
            return new RedJohnCar();
        } else if (color === 'blue') {
            return new BlueJohnCar();
        }
    }
}

const tomFactory = new TomFactory();
const johnFactory = new JohnFactory();

const redTomCar = tomFactory.createCar('red');
const redJohnCar = johnFactory.createCar('red');
```

Tak jak widać dzięki wzorcowi metody fabrykującej mogliśmy utworzyć
dwie oddzielne fabryki (implementujące wspólny interfejs), które kolejnie
na swój sposób mogą tworzyć interesujący nas podmiot.

### abstract factory (fabryka abstrakcyjna)

TBA

---

Na potrzeby uproszczenia artykułu i skoncentrowania się na samym wzorcu
fabryki, specjalnie pominąłem użycie wzorca strategii przy instrukcjach
warunkowych. Rozważam także - na potrzeby tego artykułu - użycie
typescript / flow.
