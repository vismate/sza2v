# Színezhetőség

- k színezhetőség (k >= 1):
  - kiszínezhetők a csúcsai k színnel úgy, hogy bármely két szomszédos csúcsnak a színe különböző.
  - G = (V, E) k-színezhető, ha exists f: V -> {1, ..., k} leképzés, melyre forall x,y in V: f(x) = f(y) => {x,y} not in E.

- kSzínezés = {<G> | G k-színezhető}
- 2Színezés P-beli (páros gráfok)
- 3Színezés NP-teljes
- k Színezés NP-beli

- 3SAT <=p 3Színezés: elegendő minden phi 3KNF-hez polinom időben elkészíteni egy Gphi gráfot úgy, hogy phi kielégíthető <=> Gphi 3-színezhető.

- Klikk:
  - Egy G egyszerű, irányítattlan gráf egy teljes részgráfját klikknek nevezzük.
  - Klikk = {<G, k> | G-nek van k méretű klikkje} NP-teljes
  - Ha G-nek van k-méretű klikkje, akkor bármely kisebb k-ra is van.

- Független ponthalmaz:
  - Egy G egyszerű, irányítatlan gráf egy üres részgráfját független ponthalmaznak mondjuk.
  - FüggetlenPonthalmaz = {<G,k> | G-nek van k méretű független ponthalmaza} NP-teljes
  - Ha G-nek van k-méretű független ponthalmaza, akkor bármely kiseeb k-ra is van.

- Lefogó ponthalmaz:
  - A gráf minden élét érintő ponthalmaz.
  - LefogóPonthalmaz = {<G, k> | G-nek van k méretű lefogó ponthalmaza} NP-teljes
  - Ha G-nek van k méretű lefogó ponthalmaza, akkor bármely k <= k' <= |V(G)|-re is van.


- FüggetlenPonthalmaz <=p Klikk

- FüggetlenPonthalmaz <=p LefogóPonthalmaz: Ha van k méretű független ponthalmaz, akkor van |V(G)|-k méretű lefogó ponthalmaz.

- Hipergráf lefogó ponthalmaza NP-teljes.

# Hamilton út/kör

- Egy G gráf összes csúcsát pontosan egyszer tartalmazú út a Hamilton út.
- Egy G gráf összes csúcsát pontosan egyszer tartalmaző kört a Hamilton kör.

- HÚ = {<G,s,t> | van a G irányított gráfban s-ből t-be H-út} NP-teljes
- IHÚ = {<G,s,t> | van a G irányítatlan gráfban s és t végpontokkal H-út} NP-teljes
- IHK = {<G> | van a G irányítatlan gráfban H-kör} NP-teljes

- Utazóügsnök probléma: NP teljes.
