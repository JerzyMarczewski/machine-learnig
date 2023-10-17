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

### p.158

Klasa LinearSVC regularyzuje punkt obciążenia, dlatego należy najpierw wyśrod-
kować zbiór uczący, odejmując od niego wartość średnią. Jeżeli skalujemy dane za
pomocą klasy StandardScaler, proces ten jest przeprowadzany automatycznie.
Ponadto wyznacza wartość hinge w hiperparametrze loss, gdyż nie jest ona domyślna.
Na koniec, uzyskasz lepszą wydajność, jeśli wstawisz wartość False do hiperpara-
metru dual, chyba że w zestawie uczącym znajduje się więcej cech niż przykładów
(w dalszej części rozdziału przyjrzymy się uważniej dualności).

### p.184

Mam nadzieję, że dostrzegasz już olbrzymi potencjał drzew decyzyjnych: są zrozumiałe i łatwe do
interpretacji, przystępne, wszechstronne i wydajne. Mają jednak kilka ograniczeń. Po pierwsze, jak
pewnie zdążyłaś/zdążyłeś zauważyć, algorytm drzewa decyzyjnego uwielbia ortogonalne granice decy-
zyjne (wszystkie podziały są przeprowadzane prostopadle do osi odciętych), przez co model ten
jest wrażliwy na rotację zbioru uczącego. Na przykład rysunek 6.7 przedstawia prosty, liniowo roz-
dzielny zestaw danych: na lewym wykresie próbki są z łatwością rozdzielane, natomiast na prawym
wykresie te same dane zostały obrócone o 45° i granica decyzyjna jest tu niepotrzebnie skomplikowana.
Pomimo tego, że drzewo decyzyjne zostało perfekcyjnie dopasowane do danych, istnieje duże ryzyko,
że model ten nie będzie zbyt dobrze przeprowadzał uogólniania. Jednym ze sposobów ograniczenia
tego problemu jest wprowadzenie algorytmu analizy głównych składowych (PCA; patrz rozdział 8.),
dzięki któremu model staje się lepiej zorientowany wobec danych uczących.

### p.187

Załóżmy, że zadajesz skomplikowane pytanie tysiącom losowo dobranych osób, a następnie łączysz
uzyskane odpowiedzi. W wielu przypadkach okazuje się, że taka zbiorcza odpowiedź jest lepsza
od opinii eksperta. Jest to tak zwana mądrość tłumu. Podobne zjawisko następuje, gdy połączymy
przewidywania grupy predyktorów (np. klasyfikatorów albo regresorów) — często otrzymamy w ten
sposób lepsze prognozy niż uzyskane przez najlepszy pojedynczy model. Grupę predyktorów nazy-
wamy zespołem (ang. ensemble), zatem omawiana technika nosi miano uczenia zespołowego
(ang. ensemble learning), a używany w niej algorytm — metody uczenia zespołowego (ang. ensemble
learning method).

### p.187

Bardzo prostą metodą uzyskania jeszcze lepszego klasyfikatora jest połączenie prognoz wyliczanych
przez poszczególne klasyfikatory i wybranie klasy, która uzyskała najwięcej głosów. Klasyfikator
wykorzystujący mechanizm głosowania większościowego jest nazywamy klasyfikatorem głosującym
większościowo

### p.189

Metody zespołowe sprawują się najlepiej, gdy poszczególne predyktory są od siebie
w jak największym stopniu uniezależnione. Jednym ze sposobów osiągnięcia tego
stanu jest uczenie klasyfikatorów za pomocą odmiennych algorytmów. Zwiększamy
w ten sposób prawdopodobieństwo, że klasyfikatory te będą popełniały zupełnie
różne rodzaje błędów, co prowadzi do poprawienia dokładności zespołu.

### p.190

Gdy próbkowanie jest przeprowadzane ze zwracaniem (ang. sampling with replacement), mechanizm
ten jest nazywany agregacją1 (ang. bagging; nazwa jest skrótem angielskiego pojęcia bootstrap aggre-
gating2, czyli agregacja przykładów wstępnych). Z kolei jeśli próbkowanie jest przeprowadzane bez
zwracania (ang. sampling without replacement), to mamy do czynienia z wklejaniem3 (ang. pasting).

### p.194

Rozwiązanie to okazuje się szczególnie przydatne, gdy zajmujemy się wielowymiarowymi zbiorami
danych (np. obrazami). Proces próbkowania zarówno przykładów uczących, jak i cech nosi nazwę
metody rejonów losowych7 (ang. random patches method). Z kolei pozostawienie przykładów uczą-
cych (np. bootstrap=False i max_samples=1.0) przy jednoczesnym próbkowaniu samych cech
(np. bootstrap_features=True i/lub wartość max_features mniejsza od 1.0) to tak zwana metoda
podprzestrzeni losowych8 (ang. random subspaces method).

### p.197

AdaBoost

Nowy predyktor może korygować swojego poprzednika poprzez zwracanie większej uwagi na przy-
kłady uczące, dla których poprzedni algorytm pozostał niedotrenowany. W ten sposób kolejne
predyktory koncentrują się coraz bardziej na najtrudniejszych przypadkach. Właśnie ta technika
jest wdrażana przez algorytm AdaBoost.

Przykładowo, w celu stworzenia klasyfikatora AdaBoost pierwszy klasyfikator bazowy (taki jak
drzewo decyzyjne) zostaje wytrenowany i użyty do uzyskania prognoz dla zbioru uczącego. Teraz
następuje zwiększenie względnej wagi nieprawidłowo sklasyfikowanych próbek uczących. Drugi kla-
syfikator jest uczony za pomocą zaktualizowanych wag, wylicza predykcje dla zbioru uczącego,
wagi zostają zaktualizowane itd. (rysunek 7.7).

### p.200

gradient boosting

Inną bardzo popularną techniką wzmacniania jest wzmacnianie gradientowe. Podobnie jak algo-
rytm AdaBoost, wzmacnianie gradientowe dodaje kolejne predyktory do zespołu w sposób sekwen-
cyjny, gdzie każdy następny poprawia poprzednika. Jednak nie aktualizujemy tu wag przykładów
po każdym przebiegu, lecz próbujemy dopasować predyktor do błędu resztowego (ang. residual error)
popełnionego przez poprzedni predyktor.

### p.209

Wiele problemów uczenia maszynowego obejmuje tysiące, a nawet miliony cech opisujących każdy
przykład uczący. Z tego powodu proces uczenia nie tylko przebiega bardzo powoli, ale, jak się wkrótce
przekonamy, utrudnia również znalezienie dobrego rozwiązania. Problem ten jest często nazywany
klątwą wymiarowości (ang. curse of dimensionality).

### p.211

W teorii jednym z rozwiązań klątwy wymiarowości mogłoby być zwiększenie zbioru danych uczących
w celu osiągnięcia wystarczającej gęstości przestrzeni danych. Niestety, w praktyce oznacza to, że liczba
przykładów wymaganych do osiągnięcia zakładanej gęstości wzrasta wykładniczo wraz z liczbą
wymiarów. Przy 100 wymiarach (znacznie mniej, niż znajduje się w zbiorze danych MNIST) w celu
wyuczenia próbek znajdujących się średnio w odległości 0,1 od siebie (przy założeniu, że są one
równomiernie rozmieszczone we wszystkich wymiarach) wymagana byłaby liczba przykładów prze-
kraczająca liczbę atomów znajdujących się w obserwowalnym Wszechświecie4
