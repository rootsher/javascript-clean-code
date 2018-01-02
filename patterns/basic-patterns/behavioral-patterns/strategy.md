# strategy - strategia

Wzorzec ten wymaga od nas zdefiniowania rodzajów strategii, których
będziemy w stanie użyć do rozwiązania pewnego problemu.
Stworzone strategie są zazwyczaj klasami oraz posiadają wspólny
interfejs.

Dodatkowo wzorzec strategii pozwala nam pozbyć się instrukcji
warunkowych oraz switch case'ów.

## Przykład

Najpierw przedstawię prosty przykład do refactoru:

```js
const action = 'login';

switch (action) {
    case 'login':
        service.login('login', 'pass');
        break;
    case 'register':
        service.register('login', 'pass');
        break;
    case 'reset-password':
        service.resetPassword('login');
        break;
}
```

Teraz refactor - stwórzmy strategie:

```js
// ./strategies.js

interface IStrategy {
    run();
}

class LoginStrategy implements IStrategy {
    run() {
        service.login('login', 'pass');
    }
}

class RegisterStrategy implements IStrategy {
    run() {
        service.register('login', 'pass');
    }
}

class ResetPasswordStrategy implements IStrategy {
    run() {
        service.resetPassword('login');
    }
}

export default {
    login: LoginStrategy,
    register: RegisterStrategy,
    'reset-password': ResetPasswordStrategy
};
```

Oraz jak pozbędziemy się switcha:

```js
// ./context.js

import strategies from './strategies';

const action = 'login';
const strategy = new strategies[action]();

strategy.run();
```

W tym momencie nie musimy dopisywać kolejnych warunków czy case'ów w kodzie.
Wystarczy, że dodamy kolejną strategię, i automatycznie zostanie obsłużona.
Dodatkowo strategie dają nam tą przewagę, że kod który ich używa nie musi wiedzieć
jak działają - wynosimy całą odpowiedzialność w inne miejsce.

Może przedstawiony przykład nie pokazuje w pełni siły tego wzorca - właściwie
przenieśliśmy jedną linijkę do oddzielnego pliku, stworzyliśmy jeszcze klasę,
i jedną metodę, bo tak. No właśnie nie do końca. Wyobraźmy sobie bardziej
złożonego case'a. Dzięki strategii mamy oddzielny byt jakim jest klasa,
całego naszego "case'a" możemy rozbić na metody, kod będzie o wiele przyjemniejszy
do czytania, późniejszej rozbudowy i testów.
