# singleton

Wzorzec projektowy, uważany za anti-pattern. Moim zdaniem niepotrzebnie.
Każdy wzorzec ma swoje zastosowanie, i każdy powinno się stosować w
odpowiednich sytuacjach.

Wzorzec ten umożliwia nam stworzenie tylko jednej instancji obiektu.

Jak zrealizować to w kodzie?

```js
const singleton = (function () {
    let instance = null;

    function create() {
        return {
            foo: 'bar'
        };
    }

    return {
        create: function () {
            if (!instance) {
                instance = create();
            }

            return instance;
        }
    };
})();

singleton.create() === singleton.create(); // true
```

Singleton pilnuje, żeby nie było możliwe stworzenie kolejnej instancji.
A w przypadku ponownej chęci stworzenia intancji zwraca referencję do tej pierwotnie utworzonej.
