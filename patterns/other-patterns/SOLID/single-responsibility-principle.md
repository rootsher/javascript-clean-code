# (S)OLID - SRP - Single Responsibility Principle

**SOLID** - mnemonik autorstwa Roberta Cecila Martina (Wujka Boba).

**SRP** - zasada mówiąca, że każdy nasz moduł / nasza klasa powinna mieć
jeden i tylko jeden powód do zmiany.

## Co to oznacza i po co mi to?

Celem stosowania zasady SRP jest **zredukowanie późniejszych kosztów
zmiany istniejących wymagań**. Moduł / klasa powinna być odpowiedzialna tylko
i wyłącznie za jeden obszar naszej aplikacji. Jeśli wiele rzeczy w kodzie
będzie od siebie zależeć, późniejsze zmiany w jednym miejscu mogą
wpływać na inne miejsce **(1)**, co wiąże się z poświęceniem dodatkowego czasu na
naprawę innego, niepotrzebnie zależnego kodu.

Jeżeli wystąpiła potrzeba zmiany istniejących wymagań, w kodzie źródłowym
powinno być **jedno miejsce, gdzie tej zmiany można dokonać**.
Dodatkowo w miejscu tym powinien znajdować się **kod tylko dla tej zmiany**.
Kod innych zmian powinien leżeć w innym, oddzielnym miejscu - dzięki temu
minimalizujemy ilość miejsc, które należy dotknąć w celu modyfikacji.
Rozdzielając w ten sposób kod łatwiej jest nam później ponownie go wykorzystywać.

**(1)** Stosując zasadę SRP unikamy skutków ubocznych (side-effects), które moga
pojawić się podczas modyfikowania istniejących wymagań.