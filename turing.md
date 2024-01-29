
# Grammatika

- G = <N, Sigma, P, S>:
  - N: nemterminális
  - Sigma: terminális
  - S in N: kezdőszimbólum
  - P szabályrendszer: x -> y alakú szabályok véges halmaza, ahol x és y terminálisokból vagy nemterminálisokból álló szó. (x ben van legalább egy nemterminális)

- Grammatikaosztályok:
  0. nincs koréátozás
  1. minden szabály u1 A u2 -> u1 v u2 alakú, ahol u1,u2,v tetszőleges stringek és A egy nemterminális és v nem epsilon.
  2. minden szabály A -> v alakú, ahol A nemterminális és v egy tetszőleges string
  3. minden szabály A -> uB bagy A -> u alakú, ahol A,B nemterminális és u egy szó a terminálisok fölött.

- (0: mondatszerkezetű, 1: környezetfüggő, 2: környezetfüggetlen, 3: reguláris)

- L3 in L2 in L1 in L0


# Turing gép

- Ha egy algoritmikus probléma kimenete igaz, vagy hamis, akkor eldöntési problémáról beszélünk, különben számítási problémáról.

- Parciális algoritmus: bizonyos "nem"-példányokra (bemenetekre) nem terminál az algoritmus.

- Ha egy mindig termináló matematikai géppel fel tudjuk ismerni L(P)-t, akkor a P problémát algoritmikusan megoldottnak tekinthetjük.

- Church-Turing tézis: minden formalizálható probléma, ami megoldható algoritmussal, az megoldható Turing géppel is.

- M = <Q, Sigma, Gamma, phi, q0, qi, qn> rendezett hetes:
  - Q: állapotok véges, nemüres halmaza
  - q0,q1,qn: kezdő, elfogadó és elutasító állapotok.
  - Sigma: bemenet abc
  - Gamma: szalag abc
  - Sigma <= Gamma és _ in Gamma\Sigma
  - phi: átmenetfüggvény, amely a Q\{qi,qn} x Gamma egészén értelmezett. (Q\{qi, qn} x Gamma -> Q x Gamma x {L,S,R})

- Konfiguráció: uqv szó, ha 
  - q egy állapot
  - u,v szallag abc szavai
  - v nem üres

- Elfogadó és elutasító konfigurációk: megállási konfigurációk

- Konfiguráció átmenet: a jelenlegi állapot és a beolvasandó betű alapján, az átmenetfüggvénytől kapott akciót hajtjuk végre:
  - a beolvasott szimbólumot lecseréljük az új szimbólumra
  - megfelelő irányba mozgatjuk a fejet
  - az állapotot kicseréljük az új állapotra

- L(M): TG által felismert nyelv:
  - olyan bemenetek halmaza, amelyre a TG elfogadó állapotba jut
  - {u in Sigma* | q0u_ =>* x qi y, x,y in Gamma*, y != epsilon}

- Egy L nyelv Turing felismerhető, ha L = L(M) valamely M TG-re.

- Egy L nyelv eldönthető, ha létezik olyan M TG, mely minden bemeneten megállási konfigurációba jut és L(M) = L.

- Turing felismerhető = rekurzívan felsorolható = RE.

- Eldönthető =  rekurzív = R.

- R <= RE 

- Futási idő: megállási konfigurációba való jutás lépésszáma.

- f(n) időigényes TG: minden bemenetre a futási idő legfeljebb f(|input|).

# Többszallagos TG

- Ahány szallag annyi új szimbólum a beolvasott helyére és annyi lépési irány

- Csak egy állapot

- Az input az első szallagon van, a többi kezdetben üres.

- Minden többszallagos TG megadható vele ekvivalens egyszallagos TG.
  - Az így kapott TG Ordo(f(n)^2) időkorlátos lesz, ha f(n) legalább lineáris.


# Nemdeterminisztikus TG

- Itt az átmenetfüggvény akárhány rendezett hármast rendelhet egy állapotához. (akár 0-t is!)

- Akkor fogad el egy szót, ha az adott szóra legalább egy számítása elfogadó állapotban ér véget.

- Elakadó konfiguráció: az átmenetfüggvény üres kimenetű erre a konfigurációra.

- Számítási fa: 
  - Gyökeres fa, melynek csúcsai konfigurációkkal címkézettek
  - A kezdőállapot a gyökér
  - Egy csúcs gyerekei a belőlle levezethető konfigurációk

- Felismer egy L nyelvet, ha L(M) = L

- Eldönt egy nyelvet, ha felismeri és minden bemenethez tartozó számítási fa véges és levelei elfogadók vagy elutasítók. (nem akad meg és terminál)

- f(n) időkorlát: minden n hosszú bemenetre a számítási fa legfeljebb f(n) magas.

- Minden f(n) időkorlátos NTG-hez megadható egy vele ekvivalens 2^Ordo(f(n)) időkorlátos determinisztikus TG.

- Hosszlexikografikus rendezés:
  - Elsődleges rendezés: hossz
  - Másodlagos rendezés: abc

# TG elkódolása

- Tegyük fel, hogy az input abc = {0,1}. Ezt feltehetjük, mert egy nagyob input abc feletti szavak elkódolhatóak így.

- TG elkódolása <M>:
  - Q = {p1, ..., pk}, Gamma = {X1, ..., Xm}, D1 = R, D2 = S, D3 = L.
  - k >= 3, p1 = q0, pk-1 = qi, pk = qn,
  - m >= 3, X1 = 0, X2 = 1, X3 = _
  - phi(pi, Xj) = (pr, Xs, Dt) átmenet kódja: 0^i 10^j 10^r 10^s 10^t
  - Az átmenetek kódjainak felsorolása 11-el van elválasztva

- <M> 0-val kezdődik és végződik, nem tartalmaz 3 1-t egymás után.

- <M, w> = <M>111w

# Nem Turing-felismerhető nyelv

- Létezik ilyen: TG-k számossága megszámlálható ({0,1}*), viszont a {0,1} feletti nyelvek számossága continuum.

- L_átló Turing felismerhetetlen

- L_átló = {wi | wi not in L(Mi)}:
  - wi a {0,1}* halmaz i-ik eleme shortlex rendezés szerint
  - Mi a wi által kódolt TG (ha nem kódol TG-t, akkor tetsz. TG, ami nem fogad el semmit)


# Univerzális TG

- Lu = {<M,w> | w in L(M)}

- Lu in RE (rekurzívan felsorolható = Turing-felismerhető)

- Lu not in R (nem Turing-eldönthető)

- Univerzális TG (U): 4 szallag:
  1. szallag: <M,w> (csak olvasás)
  2. szallag: M aktuális szallagtartalma és a fej helyzete elkódolva
  3. szallag: M aktuális állapota elkódolva
  4. szallag: segéd

- Univerzális TG működése:
  1. Megnézi, hogy a bemenetén szereplő szó első része kódol-e TG-t. Ha nem => elutasítja a bemenetet
  2. felmásolja a w-t a 2. szallagra és a q0 kódját a 3.szallagra
  3. szimulálja M egy lépését
  4. Ha M aktuális állapota elfogadó/elutasító, akkor U is belép a saját elfogadó/elutasító állapotába, különben goto 3.

# RE és R tulajdonságok

- Ha L és komplementere in RE, akkor L in R

- RE nem zárt a komplementer képzésre

- Ha L in R, akkor komplemetere is R (R zárt a komplemeter képzésre)

# Számítási feladatok TG-vel

- Tegyük fel, hogy megfelelő kódolás alkalmazásával f értelmezési tartomány Sigma*, értékkészlete Delta* valamely Sigma, Delta abc-re

- M = <Q, Sigma, Delta, phi, q0, qi, (qn)> TG kiszámítja az f: Sigma* -> Delta* szófüggvényt, ha minden u bemenetre megáll, és ekkor f(u) Delta* eleme lesz olvasható az utolsó szalagján.

- Visszavezetés:
  - Az f függvény kiszámítható, ha van olyan TG, ami kiszámítja.
  - L1 része Sigma* visszavezethető L2 része Delta*-ra, ha van olyan f kiszámítható függvény, hogy w in L1 <=> f(w) in L2. Jelölés: L1 <= L2

- Ha L1 <= L2 és L2 RE, akkor L1 is RE
- Ha L1 <= L2 és L2 R, akkor L1 is R
- Ha L1 <= L2 és L1 nem RE, akkor L2 sem RE
- Ha L1 <= L2 és L1 nem R, akkor L2 sem R

# Megállási probléma

- Lh = {<M,w> | M megáll a w bemeneten}
- Lu része Lh

- Lh nem R (Lu visszavezethető Lh-ra, fordítva is)

- Lh Re

# Rice tétel

- Tetszőleges P része RE halmazt a rekurzívan felsorolható nyelvek egy tulajdonságának nevezzük.
- P triviális, ha P üres, vagy P = RE.

- LP = {<M> | L(M) in P}

- Ha P nem triviális, akkor LP nem R. (Rice tétele)

- Következmények:
  - Eldönthetetlen, hogy egy TG
    - az üres nyelvet ismeri-e fel.
    - véges nyelvet ismer-e fel.
    - környezetfüggetlen nyelvet ismer-e fel.
    - elfogadja-e az üres szót.

# Post megfelelkezési probléma

- Legyen Sigma egy abc és legyenek u1, ..., un, v1, ..., vn in Sigma+.
- A D = {u1/v1, ..., un/vn} halmazt dominókészletnek nevezzük.
- Az ui1/vi1 ... uim/vim dominósorozat (m >= 1, 1 <= i1, ..., im <= n) a D dominókészlet egy megoldásaa, ha ui1 ... uim = vi1 ... vim.

- PMP: 
 - Lpmp = {<D> | D-nek van megoldása}
 - Lpmp RE
 - Lpmp nem R

# Környezetfüggetlen grammatikákkal kapcsolatos eldönthetetlen algoritmikus problémák

- Lecf = {<G> | G egyértelmű CF grammatika}
- Lecf nem R
- Lpmp <= Lecf komplementere

- A determinisztikus veremautomatákkal felismerhető nyelvek osztálya zárt a komplemnterképzésre

- Eldönthetetlenek ezek a kérdések G1 és G2 CF grammatikákkal kapcsolatban:
  - L(G1) metszet L(G2) üreshalmaz-e
  - L(G1) =? L(G2)
  - L(G1) =? Gamma* valamely Gamma abc-re
  - L(G1) részhalmaza-e L(G2)-nek

- L3 része LdetVA része L2 része L1 része R része RE = L0

