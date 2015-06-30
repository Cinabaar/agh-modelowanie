
#View-dependent LoD

##Kompilacja i uruchomienie

~~~bash
git clone https://github.com/Cinabaar/agh-modelowanie
mkdir build
cd build
cmake ..
cd ../bin
./lod <plik>
~~~

##Obsługa programu

~~~
q - wyjście
h - help
l - zablokowanie w obecnym stanie
t - widok z góry
f - przełączanie między LoD a brak LoD
o - narysuj octree
w - poziom widoczności
c - przełączanie widoczności trójkątów zwróconych tyłem
i - przeładowanie
+/- - zwiększanie i zmniejszanie poziomu detali wewnętrznych
]/[ - zwiększanie i zmniejszanie poziumu detali na sylwetce
~~~

##Opis

Program umożliwia interaktywne obniżanie i zwiększanie poziomu detali danego modelu w zależności od podanych kryteriów. Dostępne krytera to:

- budżet trójkątów (+/-)
- szczegółowość sylwetki (]/[)

Dodatkowo niewidoczne trójkąty nie są w ogóle rysowane.

Screenshoty:

![](http://i.imgur.com/I3HdNhr.png)
Pełna rozdzielczość

![](http://i.imgur.com/dw3Ltzh.png)
Obniżony poziom detali

![](http://i.imgur.com/FVuGWqV.png)
Bardzo obniżony poziom detali, oraz obniżona szczegółowość sylwetki

![](http://i.imgur.com/2QvN3h3.png)
Wierzchołek struktury drzewiastej

##Działanie

Działanie programu jest zgodne z opisem przedstawionym w ramach prezentacji z Modelowania, którą można znaleźć na uplu.

Kluczowe elementy to:

- implementacja drzewa przekształceń modelu
- implementacja octree do wykrywania trójkątów poza widokiem

Pozostałe pliki stanowią głównie obudowę na wyświetlanie okna i renderowanie modelu.

Program obsługuje pliki w formacie .ply

##Bibliografia

Level of Detail for 3D Graphics, D. Luebke, et al.
Perceptually Guided Simplification of Lit, Textured Meshes, N. Williams, et al.
View-dependent simplification of arbitrary polygonal environments, D. Luebke, et al

