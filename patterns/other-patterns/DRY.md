# DRY - Don't Repeat Yourself

Reguła mówiąca wprost - nie powtarzaj się.
Przekładając to na programowanie:

## DRY poprzez przeniesienie powtarzanego kodu do funkcji

Jeśli masz powtarzający się fragment kodu (albo lekko różniący się)
nawet w kilku miejscach, zastanów się, może warto wrzucić go do funkcji.

* przed:

```js
let i = 0;

while (i < 10) {
    i++;
    console.log(i);
}

// ---

let j = 0;

while (j < 20) {
    j++;
    console.log(j);
}

// ---

let k = 0;

while (k < 30) {
    k++;
    console.log(k);
}

```

* po:

```js
function loop(to) {
    let i = 0;

    while (i < to) {
        i++;
        console.log(i);
    }
}

loop(10);
loop(20);
loop(30);
```

## DRY poprzez wrapping / sloty

Wyobraźmy sobie, że mamy w naszej aplikacji widok, który serwuje różne
komponenty w zależności od parametru przekazanego w url'u.
Załóżmy też, że komponenty są do siebie bardzo podobne, że posiadają
dużo elementów wspólnych. Żeby zobrazować, załóżmy, że każdy z komponentów
składa się z header'a, content'u i footer'a - gdzie content jest w przypadku
każdego komponentu inny.

Przykładowa implementacja mogłaby wyglądać np. tak:

```jsx
// component-1.jsx
export function Component1() {
    return (
        <header>header</header>
        <main>
            Hello component-1!
        </main>
        <footer>footer</footer>
    );
};

// component-2.jsx
export function Component2() {
    return (
        <header>header</header>
        <main>
            Hello component-2!
        </main>
        <footer>footer</footer>
    );
};

// component-3.jsx
export function Component3() {
    return (
        <header>header</header>
        <main>
            Hello component-3!
        </main>
        <footer>footer</footer>
    );
};
```

Rozwiązanie to ma jednak w sobie pewną wadę - za każdym razem, gdy
będziemy chcieli zmieniać coś w headerze lub footerze, będziemy
musieli zmieniać to w każdym z plików.

Stosując wrapping implementacja mogłaby wyglądać np. tak:

```jsx
// wrapper.jsx
export function Wrapper(children) {
    return (
        <header>header</header>
        {children}
        <footer>footer</footer>
    );
};

// component-1.jsx
export function Component1(Wrapper) {
    return (
        <Wrapper>
            <main>
                Hello component-1!
            </main>
        </Wrapper>
    );
};

// component-2.jsx
export function Component2(Wrapper) {
    return (
        <Wrapper>
            <main>
                Hello component-2!
            </main>
        </Wrapper>
    );
};

// component-3.jsx
export function Component3(Wrapper) {
    return (
        <Wrapper>
            <main>
                Hello component-3!
            </main>
        </Wrapper>
    );
};
```

Stosując regułe DRY sprawiamy, że nasz kod staje się czytelniejszy,
bardziej zrozumiały i łatwiejszy do przetestowania oraz modyfikacji.
