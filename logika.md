# Ítéletlogika

- Formula:
  - Ítéletváltozó
  - Formula negáltja
  - Két formula összekapcsolása binér művelettel

- Szerkezzeti fa:
  - Bináris fa
  - Levelei ítéletváltozók
  - Egy csúcs gyerekei a csúcs formula közvetlen részformulái
  - Fő logikai összekötő csak a gyökérben szerepel

- Zárojelelhagyás: precedencia szerint (+ külső zárójel)
- Az implikáció jobbra zájeleződik

- Interpretáció: függvény, mely ítéletváltozókhoz igazságértéket rendel (I: Var(F) -> {i,h})

- Igazságérték interpretációban: rekurzív definíció
  - x -> Bi(x) = I(x)
  - f -> Bi(!f) = !Bi(f)
  - f, g -> Bi(f . g) = Bi(f) . Bi(g)

- Ítélettábla: egy-egy sor egy-egy interpretáció (2^n). Utolsó oszlop: Bi(f)

- Kielégíthetőség, tautológia, tautologikus következmény, tautologikus ekvivalencia.

- Tautologikus ekvivalencia: f => g és g => f

- F formulahalmaz és f formula:
  - f akkor és csak akkor kielégíthetetlen, ha !f tautológia
  - F => f akkor és csak akkor, ha F U {!f} kielégíthetetlen

- Literál: x vagy !x (x ítéletváltozó)

- Elemi diszjunkció (klóz): különböző alapú literálok diszjunkciója

- Konjuktív normálforma: klózok konjukciója.

- Diszjunktív normálforma: elemi konjukciók diszjunkciója.

- Minden formulához megadható DNF és KNF.

- KNF koinstrukció:
  1. Implikációk eliminálása
  2. !-operátorok bevitele közvetlen ítéletváltozók elé
  3. A formula 2 szintűvé lapítása

- Rezolvens: két pontosan 1 komplemens literálpárt tartalmazó klóz resolvense a komplemens literálpár elhagyásával, 
a megmaradt literálok összevagyolásával kapjuk.

- Rezolúciós levezetés: Egy S klózhalmazból a C klóz levezetése egy olyan véges klózsorozat, ahol minden elemre igaz:
  - az eredeti klózhalmaz eleme, vagy
  - vagy már a sorozatban lévő két klóz rezolvense 

- S klózhalmaz kielégíthetetlen <=> S-ből levezethető az üresklóz.

- Ha egy I interpretáció kielégíti C1 és C2 klózt, akkor ezek rezolvensét is kielégíti.

# Elsőredű logika

- Szimbólumhalmaza:
  - predikátumszimbólumok
  - függvényyszimbólumok
  - konstansszimbólumok
  - individuumváltozók
  - kvantorok
  - () és ,

- Predikátumoknak, függvényeknek és konstansoknak van aritása. (konstansoknál ez 0)

- Term: 
  - individuumváltozó
  - konstans
  - f(t1, t2, ... tar) (f függvény, tn term)

- Formula:
  - p(t1, ... tar) (atomi formula, p predikátum, t term)
  - !F
  - F . G
  - (forall / exists)x F
  - (F és G formulák)

- Szerezeti fa értelmezhető formulákra és termekre is.

- Interpretáció: I = <U, Ipred, Ifunc, Icnst> rendezett négyes:
  - U: univerzum, tetszüleges nemüres halmaz.
  - Ipred: predikátumszimbólumhoz rendel egy az aritásának megfelelő relációt U felett.
  - Ifunc: függvényszimbólumokhoz hozzárendel egy az aritásának megfelelő műveletet U-n.
  - Icnst: minden konstanshoz hozzárendel egy elemet U-ból.

- Változókiértékelés (kappa): Ind -> U leképzés

- |t|^{I, kappa} a t term értéke egy I interpretáció és kappa változókiértékelés mellett:
  - ha x individuumváltozó, akkor kappa(x)
  - ha c konstans, akkor c^I
  - f(t1, t2, ...) esetén f^I(|t1|^{I, kappa}, ...)

- hasonlóképp definiáljuk egy f formula igazságértékét egy I interpretációban, kappa változókiértékelés mellett.

- kappa* kappa x veriánsa, ha minden y != x esetén kappa(y) = kappa*(y)

- Egy individuumváltozó kötött egy formulában, ha kvantor hatáskörében van.

- Ha minden individuumváltozó minden előfordulása kötött egy formulában, akkor zárt, egyébként nyitott formuláról beszélünk.

- Kielégíthető, logikailag igaz, logikailag ekvivalens, logikai következmény...
