- Eldönthető (R-beli) problémákkal foglalkozunk.

- TIME(f(n)) = {L | L eldönthető Ordo(f(n)) időkorlátos determinisztikus TG-vel}
- NTIME(f(n)) = {L | L eldönthető Ordo(f(n)) időkorlátos NTG-vel}
- P = UNION_k>=1 TIME(n^k)
- NP = UNION_k>=1 NTIME(n^k)

- NTIME(f(n)) része= TIME(2^Ordo(f(n)))

- P része= NP

- Sejtés: P != NP (bizonyítani nem tudjuk)

# Polinóm idejű visszavezetés

- Az f: Sigma* -> Delta* szófüggvény polinom időben kiszámítható, ha van olyan polinom időkorlátos TG, ami kiszámítja.


- L1 része= Sigma* polinom időben visszavezethető L2 része= Delta*-ra, ha van olyan f polinom időben kiszámítható szófüggvény, hogy
w in L1 <=> f(w) in L2. Jelölés: L1 <=p L2

- Ha L1 <=p L2 és L2 P, akkor L1 is P
- Ha L1 <=p L2 és L2 NP, akkor L1 is NP

- A polinom, idejű visszavezetés tranzitív.

# C-teljesség

- Legyen C egy bonyolultsági osztály. Egy L nyelv C-nehéz, ha minden L' in C esetén L' <=p L

- Legyen C egy bonyolultsági osztály. Egy L nyelv C-teljes, ha L in C és L C-nehéz.

- Sepciális esetben: NP teljes egy L nyelv
  - L in NP
  - L NP nehéz, azaz minden L' in NP esetén L'<=p L

- Legyen L egy NP-teljes probléma. Ha L in P, akkor P = NP.
- Eszerint, ha valaki talál egy polinom idejű megoldást egy NP teljes problémára, akkor bizonyítja, hogy P = NP
- Mivel még senki sem talált ilyet, ezért az NP-teljes problémákra úgy tekinthetünk, mint bár eldönthető, de hatékonyan nem eldönthető problémákra.


- SAT = {<phi> | phi kielégíthető nulladrendű knf}
- Cook-Levin tétel: SAT NP-teljes.

- Ha L NP teljes, L <=p L' és L' in NP, akkor L' NP teljes.

- kSAT = {<phi> | phi kielégíthető kKNF}
  - 3SAT NP-teljes
  - 2SAT P-beli

- HORNSTAT = {<phi> | phi kielégíthető Horn formula}
  - Horn formula: olyan KNF, amelynek minden tagja legfeljebb egy negálatlan literált tartalmaz.
  - HORNSTAT P-beli

# Példák
- Diophantoszi egyenlőtlenségrendszer NP-nehéz
- Részletösszeg NP-teljes
- Hátizsák probléma NP-teljes (Részletösszeg <=p Hátizsák)
- Partíció NP-teljes (Részletösszeg <=p Partíció)
- Ládapakolás NP-teljes (Partíció <=p Ládapakolás)

# NP lehetséges szerkezete

- L NP köztes, ha L in NP, L not in P és L nem NP-teljes.
- Ladner tétele: Ha P != NP, akkor létezik NP-köztes nyelv.
- Ezt nem tusjuk igazolni

- Lehetséges NP köztes problémák:
  - Gráfizomorfizmus: Két gráf izomorf, ha a csúcshalmazaik közt létezik olyan bijekció, amely esetén a bijekcióval leképzett csúcsok közötti élek megmaradnak.
    - Részgráfizomorfizmus NP-teljes.
  - Prímfaktorizáció


# coNP

- coC = {L | L komplementere in C}
- Ha C zárt polinomidejű visszavezetésre, akkor coC is.

- coNP zárt a polinomidejű visszavezetésre nézve

- L C-teljes <=> L komlementere coC teljes.

- P = coP

- Példák coNP-re:
  - kielégíthetetlen nulladrendű formulák halmaza: UNSAT coNP-teljes
  - nulladrendű tautológiák halmaza: TAUT coNP-teljes

- Ha L coNP-teljes és L in NP, akkor NP = coNP
- Sejtés: NP != coNP
- Sejtés: P != NP metszet coNP

# Tárbonyolultság

- Offline TG:
  - Olyan TG, melynek első szallagja csak olvasható, a többi írható is.
  - Minden TG-hez megadható vele ekvivalens offline TG.
  - Nemdeterminisztikus is van.
  - Számító OTG: legalább 2 szallagos számító TG, amelynek első szallagja csak olvasható, az utolsó szallagja csak írható.

- OTG többlet tárigénye adott inputra: azon munkaszalagon lévő cellák száma, amelyen fej járt.
- f(n) többletkorlátos OTG: bármely inputra legfeljebb f(|input|) a többlet tárigénye.
  - NOTG-nél a legnagyobb többlet tárigényű számítást kell figyelembe venni.

- SPACE(f(n)) = {L | L eldönthető Ordo(f(n)) többletkorlátos OTG-vel}
- NSPACE(f(n)) = {L | L eldönthető Ordo(f(n)) többlet tárkorlátos NOTG-vel}
- PSPACE = UNION_k>=1 SPACE(n^k)
- NPSPACE = UNION_k>=1 NSPACE(n^k)
- L = SPACE(log n)
- NL = NSPACE(log n)

- Elér = {<G,s,t> | G-ben van s-ből t-be út}
- Elér in TIME(n^2)
- Elér in SPACE(log^2 n)
- Elér in NL

- Savitch tétele: Ha f(n) >= log n, akkor NSPACE(f(n)) része= SPACE(f^2(n)):
  - PSPACE = NPSPACE
  - NL része= P

- NL = coNL
- NL része PSPACE és P része EXPTIME
