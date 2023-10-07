# UMZSIT

### p. 136

"W rozdziale 2. korzystaliśmy z metody sprawdzianu krzyżowego do oszacowania wydajności uogól-
niania modelu. Jeżeli model sprawuje się dobrze wobec danych uczących, ale według metryk kroswali-
dacji nie radzi sobie z generalizowaniem, to znaczy, że ulega przetrenowaniu. W przypadku, gdy
model nie radzi sobie zarówno ze zbiorem uczącym, jak i z uogólnianiem, jest niedotrenowany.
Jest to jeden ze sposobów na stwierdzenie, czy model jest za prosty lub zbyt złożony."

### p.138

Kompromis pomiędzy obciążeniem a wariancją
Ważną konsekwencją rozważań łączących statystykę z uczeniem maszynowym jest fakt, że błąd generali-
zacji modelu można wyrazić w postaci sumy trzech odmiennych rodzajów błędów:
 Obciążenie (ang. bias): ta składowa błędu uogólnienia wynika z nieprawidłowych założeń, np.
założenia, że dane są liniowe, podczas gdy w rzeczywistości są opisane funkcją kwadratową. Model
o wysokiej wartości obciążenia ma największą szansę na niedotrenowanie wobec danych uczących.

 Wariancja (ang. variance): ta składowa wynika z nadmiernej czułości modelu na drobne wahania
w wartościach danych uczących. Model cechujący się dużą liczbą stopni swobody (np. wielostopniowy
model wielomianowy) prawdopodobnie będzie miał dużą wariancję, a przez to będzie przetrenowy-
wany wobec danych uczących.

 Błąd nieredukowalny (ang. irreducible error): ta składowa stanowi konsekwencję zaszumienia
danych. Jedynym sposobem pozbycia się jej jest oczyszczenie danych (np. naprawa źródeł danych
takich jak zepsute czujniki lub wykrywanie i usuwanie elementów odstających).

Zwiększanie złożoności modelu zazwyczaj zwiększa jego wariancję i zmniejsza obciążenie. Odwrotny
proces następuje w przypadku uproszczenia modelu. Dlatego mówimy tu u kompromisie.

### p.142

Ważną własnością regresji metodą LASSO jest fakt, że dąży ona do całkowitej eliminacji wag w naj-
mniej istotnych cechach (np. poprzez zmianę ich wartości na 0). Przykładowo, linia przerywana
na prawym wykresie (rysunek 4.18; wykres o wartości α = 10-7
) przypomina niemalże liniowy wykres
funkcji kwadratowej: wszystkie wagi cech wielomianowych wyższego stopnia są równe zeru. Innymi
słowy, regresja metodą LASSO automatycznie przeprowadza dobór cech i generuje model rzadki
(tj. zawierający niewiele niezerowych wag cech)

### p.144

Kiedy więc należy stosować regresję liniową (tj. nieregularyzowaną), a kiedy metodę grzbietową,
LASSO albo elastyczną siatkę? Niemal zawsze warto wprowadzić chociaż odrobinę regularyzacji,
dlatego staraj się unikać zwykłej regresji liniowej. Dobrym domyślnym rozwiązaniem okazuje się
regresja grzbietowa, ale jeśli podejrzewasz, że będzie przydatnych tylko kilka cech, lepiej wybrać
metodę LASSO lub elastycznej siatki, ponieważ, jak już wiemy, dążą one do zerowania wag naj-
mniej użytecznych cech. Generalnie bardziej preferowana jest metoda elastycznej siatki, gdyż
metoda LASSO zaczyna nieprawidłowo działać, gdy liczba cech przewyższa liczbę próbek uczą-
cych lub gdy istnieje silna korelacja pomiędzy kilkoma cechami.
