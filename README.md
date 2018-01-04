# javascript-clean-code

Brakuje mi miejsca w Internecie, gdzie raz, a porządnie naczytałbym się o poniższym, mianowicie:
* jakimi zasadami powinienem się kierować pisząc każdą linijkę swojego kodu,
* jak stworzyć strukturę, która odpowiednio oddzieli mi wszystkie warstwy aplikacji,
* jak pisać swój kod, żeby inni od razu go zrozumieli,
* jak korzystać rozsądnie z dobrodziejstw package manager'ów,
* jak pisać kod, na jakie rzeczy warto zwrócić uwagę,
* jak zlokalizować miejsce gdzie aplikacja zamula i jak sprawić, aby aplikacja działała szybciej,
* jak testować aplikacje, jakie testy są mi potrzebne i jaką pełnią rolę.

Tworząc ten projekt chciałbym wyjaśnić możliwie wszystkie aspekty
projektowania / pisania / testowania aplikacji za którą się zabieramy.

Omówię tu wszelakie wzorce, dobre praktyki, od linterów, przez wzorce projektowe,
strukturalne, po wzorce które opłaca się stosować w aplikacjach klasy enterprise.

Dodatkowo skupię się na omówieniu zastosowanych technik w popularnych bibliotekach / narzędziach / frameworkach.

## Spis treści:

* debug
    * chrome devtools
    * mobile debugger
* init
* linters
    * eslint, jslint, jshint, jscs
* package managers
    * npm, yarn, bower
* patterns
    * Architectural patterns
    * Basic patterns
        * Behavioral patterns
            * iterator
            * mediator
            * observer
            * [strategy](patterns/basic-patterns/behavioral-patterns/strategy.md)
            * visitor
        * Concurrency patterns
            * active-object
            * reactor
            * scheduler
        * Creational patterns
            * builder
            * dependency injection
            * factory
            * [singleton](patterns/basic-patterns/creational-patterns/singleton.md)
        * Structural patterns
            * adapter
            * bridge
            * composite
            * decorator
            * [facade](patterns/basic-patterns/structural-patterns/facade.md)
            * module
            * proxy
    * Other patterns
        * GRASP - General responsibility assignment software patterns
            * controller
            * creator
            * high cohesion
            * indirection
            * information expert
            * low coupling
            * polymorphism
            * protected variations
            * pure fabrication
        * SOLID
            * [Single Responsibility Principle (SRP)](patterns/other-patterns/SOLID/single-responsibility-principle.md)
            * Open / Closed Principle (OCP)
            * Liskov Substitution Principle (LSP)
            * Interface Segregation Principle (ISP)
            * Dependency Inversion Principle (DIP)
        * [DRY - Don't Repeat Yourself](patterns/other-patterns/DRY.md)
        * [KISS - Keep It Simple, Stupid](patterns/other-patterns/KISS.md)
        * SoC - Separation of Concerns
* tests
    * E2E - End-to-End
        * selenium, nightwatch, browserstack
    * Unit testing
        * mocha, jest
* React
    * component lifecycle methods
    * component communication
* Angular
* Vue.js

## Issues:

Do projektu zachęcam tworzyć issues :)

Jeśli:
* nie ma na liście wzorca, którego chcesz zrozumieć,
* któreś z moich tłumaczeń podlega otwartej dyskusji,
* lub po prostu nie rozumiesz jakiejś treści..

..utwórz proszę issue!

Chciałbym dbać o jakość tworzonych materiałów.

## Od autora:

Tworzone treści będą zawierały informację dla czytelnika, jaki
stopień zaawansowania musi posiadać. Cel jaki sobie postawiłem to
wypuszczać raz na kilka dni jedną aktualizację,
zawierającą wyjaśnienie danego zagadnienia / podejścia czy wzorca.
Wraz z puszczaniem kolejnych commitów będę aktualizował spis treści - aktywne
linki.

Powyższa struktura będzie stopniowo modyfikowana i rozszerzana.
