# facade - fasada

Wzorzec fasady służy do uproszczenia dostępu do złożonego systemu.
Fasadę implementuje się zwykle jako pośrednią warstwę między
złożonymi klasami naszej aplikacji, a klientem, który chciałby
w możliwie uproszczony i ujednolicony sposób korzystać z udostępnionych
mu dobrodziejstw, dbając jednocześnie, aby nie miał dostępu do reszty.

Przykładem zastosowania wzorca fasady jest stworzenie API dostępowego.

Stwórzmy wewnętrzną klasę w systemie - TV.

```js
class TV {
    isOn = false;
    program = 1;

    turnOn() {
        this.isOn = true;
    }

    turnOff() {
        this.isOn = false;
    }

    changeProgram(number) {
        this.program = number;
    }
}
```

Teraz chcielibyśmy skorzystać z wzorca fasady, aby umożliwić klientowi,
który się podłączy tylko włączanie i wyłączanie telewizora.
Natomiast zmiana programów z tego poziomu będzie niemożliwa.

```js
class API {
    constructor(tv) {
        this.tv = tv;
    }

    turnOnTV() {
        this.tv.turnOn();
    }

    turnOffTV() {
        this.tv.turnOff();
    }
}

const api = new API(new TV());

api.turnOnTV();
api.turnOffTV();
```

Dzięki wzorcowi fasady udostępniliśmy ujednolicony interfejs, dzięki
któremu mamy kontrolę nad operacjami wykonywanymi na wyższej klasie.

Wyprzedzając pytania o prywatność właściwości tv. Na potrzeby prostego
przykładu pominąłem blokowanie dostępu do tej właściwości.
W celu osiągnięcia prywatności można skorzystać ze wzorca modułu,
typescript'a / flow, czy przez kombinację z ES6 proxy albo eksperymentalnego
jeszcze z ES next - #private (candidate - stage 3).
