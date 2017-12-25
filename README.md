# javascript-clean-code

Brakuje mi miejsca w Internecie, gdzie raz, a porządnie naczytałbym się o tym:
* jakimi zasadami powinienem się kierować pisząc każdą linijkę swojego kodu,
* jak stworzyć strukturę, która odpowiednio oddzieli mi wszystkie warstwy aplikacji,
* jak pisać swój kod, żeby inni od razu go zrozumieli,
* jak korzystać rozsądnie z dobrodziejstw NPMa,
* jak pisać kod, na jakie rzeczy warto zwrócić uwagę,
* jak zlokalizować miejsce gdzie aplikacja zamula i jak sprawić, aby aplikacja działała szybciej,
* jak testować aplikacje, jakie testy są mi potrzebne i jaką pełnią rolę.

Tworząc ten projekt chciałbym wyjaśnić możliwie wszystkie aspekty
projektowania / pisania / testowania aplikacji za którą się zabieramy.

Omówię tu wszelakie wzorce, dobre praktyki, od linterów, przez wzorce projektowe,
strukturalne, po wzorce które opłaca się stosować w aplikacjach enterprise.

Dodatkowo skupię się na omówieniu zastosowanych technik w popularnych bibliotekach / narzędziach / frameworkach.

## Spis treści:

* debug
* init
* linters
* npm
* patterns
    * architectural-patterns
    * basic-patterns
        * behavioral-patterns
            * iterator
            * mediator
            * observer
            * strategy
            * visitor
        * concurrency-patterns
            * active-object
            * reactor
            * scheduler
        * creational-patterns
            * builder
            * dependency-injection
            * factory
            * [singleton](patterns/basic-patterns/creational-patterns/singleton.md)
        * structural-patterns
            * adapter
            * bridge
            * composite
            * decorator
            * facade
            * module
            * proxy
    * other-patterns
        * GRASP
        * SOLID
            * dependency-inversion-principle
            * interface-segregation-principle
            * liskov-substitution-principle
            * open-closed-principle
            * single-responsibility-principle
        * DRY
        * KISS
        * SoC
* tests
    * e2e
    * unit

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
wypuszczać codziennie przynajmniej jedną publikację,
zawierającą wyjaśnienie danego zagadnienia / podejścia czy wzorca.
Wraz z puszczaniem kolejnych commitów będę aktualizował spis treści - aktywne linki.

Powyższa struktura będzie stopniowo modyfikowana i rozszerzana.
