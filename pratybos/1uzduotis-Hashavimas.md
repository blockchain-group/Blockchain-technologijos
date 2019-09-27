# 1-oji užduotis: Hash generatorius

Maišos funkcijos (angl. *hash function*) yra labai svarbi *blockchain* (pvz. *Bitcoin*) protokolų dalis. Hash'avimo metu bet koks įvedimo tekstas (*m*) matematinės *hash* funkcijos dėka (*h = h(m)*) yra paverčiamas unikaliu fiksuoto dydžio pseudo-atsitiktiniu skaičiumi, vadinamu *maišos kodu*. Tradicinė tokių *hash* generatorių veikimo schema yra:

![Hashing](img/hashing.png)

Kad geriau suvokti užduoti, rekomenduotina pasibandyti, kaip veikia vieni geriausiai ir plačiausiai naudojamų [maišos kodo genetorių](https://emn178.github.io/online-tools/sha256.html).

## Užduoties formuluotė

Sukurkite Jūsų (t.y. pabandykite neieškoti *hash* funkcijų pavyzdžių Internete) maišos (*hash*) funkciją (*hash* kodų generatorių), kuris pasižymėtų šiais *hash* funkcijoms keliamais reikalavimais:

1. Maišos funkcijos įėjimas (angl. *input*) gali būti <u>bet kokio dydžio</u> simbolių eilutė (angl. *string*).
2. Maišos funkcijos išėjimas (angl. *output*) visuomet yra <u>to paties fiksuoto dydžio</u> rezultatas.
3. Maišos funkcija yra deterministinė, t. y., tam pačiam įvedimui (angl. *input*'ui) išvedimas (angl. *output*'as) <u>visuomet</u> yra tas pats.
4. Maišos funkcijos reikšmė/kodas (hash‘as) bet kokiai input reikšmėi yra apskaičiuojamas nesunkiai - efektyviai.
5. Iš funkcijos rezultato (*output*'o) praktiškai neįmanoma atgaminti įvedimo (*input*'o).
6. Praktiškai neįmanoma surasti tokių dviejų skirtingų argumentų (*input*'ų), kad jiems gautume tą patį *hash*'ą, t. y.,: *m1 != m2*, bet *h(m1) = h(m2)*.
7. Bent minimaliai pakeitus įvedimą, pvz.vietoj "Lietuva" pateikus "lietuva", maišos funkcijos rezultatas-kodas turi skirtis iš esmės:

| Įvedimas (*input*) | Išvedimas (*hash'as* gautas iš  SHA256)                      |
| ------------------ | ------------------------------------------------------------ |
| lietuva            | f51f6afefb2616f48bbddeeada2d729244a00fa0817f9ceb5c5419aa04b31172 |
| Lietuva            | 5109820f748796128b8bafd3806d05511bc89ad77fc3cda960facf37a639bc7f |
| Lietuva!           | f4ac741acca7dd6f5f7e6fd1e382eca604a26ba21a83a6a2215d7be830a8faa6 |


### Reikalavimai versijai (`v0.1`) (Preliminarus terminas: 2019-09-26)

- Pagal užduoties formuluotę, realizuokite *hash*'ų generatorių (pageidautina `C++` kalboje). Programos realizavimas turi būti versijuojamas (pageidautina *git*'e) ir patalpintas Jūsų Github'e.
- Realizacijoje *input*'ą, esantį išoriniame faile, reikia nurodyti per pateikta `Command Line Argument`'ą. Tačiau turi būti galimybė paduoti ir simbolių eilutę, aka `string`'ą.
- Atlikite eksperimentinę analizę (žr. Komentarai dėl pradinio eksperimentinio tyrimo-analizės), kurios metu įsitikinkite, kad Jūsų *hash* funkcija-generatorius iš tiesų pasižymi aukščiau aprašytais *hash* funkcijoms keliamais reikalavimais. Atliktą tyrimą išsamiai aprašykite `README` faile.
- Eksperimentinis tyrimas-analizė turi būti atkartojamas, t. y., paskaitos metu reikės pademonstruoti, kaip vyksta tyrimas ir kaip argumentavote, kad Jūsų maišos funkcija pasižymi šiomis savybėmis.
- Apraytikite savo funkcijos idėją ir eksperimentinio tyrimo vykdymą ir rezultatus ataskaitoje.

### Komentarai dėl eksperimentinio tyrimo-analizės atlikimo

1. Susikurkite testinių įvedimo failų pavyzdžių, tokių kad:
  - Bent du failai būtų sudaryti tik iš vieno, tačiau skirtingo, simbolio.
  - Bent du failai būtų sudaryti iš daug visiškai skirtingų simbolių (> 10000 simbolių)
  - Bent du failai būtų sudaryti iš daug simbolių ir skirtųsi vienas nuo kito tik vienu simboliu.
  - Tuščias failas
Ir išveskite output'us. Nepriklausomai nuo Input'o, Output'ai turi būti vienodo dydžio. Tokiu būdu pademonstruosite, kad Jūsų _hash funkcija_ atitinka 1-3-ą reikalavimus.
2. Ištirkite Jūsų sukurtos hash funkcijos efektyvumą: tuo tikslu suhash'uokite kiekvieną eilutę iš [konstitucija.txt](https://github.com/blockchain-group/Blockchain-technologijos/blob/master/pratybos/konstitucija.txt) failo. Reiktų čia matuoti, tik hash'avimo funkcijos veikimo laiką (be input'o nuskaitymo/parengimo). Reiktų pateikti bendrą suminį visų hash'avimų laiką.
  - (Advanced užduotis - norintiems papildomų balų) Pabandykite kaip įmanoma __objektyviau__ palyginti Jūsų Hash funkcijos spartą su `MD5`, `SHA-1`, `SHA-256` ar kita gerai žinoma hash funkcija. Paliekame Jums sugalvoti, kaip atlikti tokį tyrimą objektyviai!
3. Susigeneruokite bent 100 000 atsitiktinių simbolių eilučių (`string`'ų) __porų__ (apsiribokite iki 5 simbolių eilučių ilgiu) ir patikrinkite, kad visais atvejais gautieji __porų__ hash'ai nesutampa. Tokiu būdų bent dalinai įsitikinsite, kad Jūsų hash funkcija atitinka 6-ą reikalavimą.
4. Susigeneruokite bent 100 000 atsitiktinių simbolių eilučių (`string`'ų) porų, tokių kad skirtųsi jos tik vienu simboliu (apsiribokite iki 5 simbolių eilučių ilgiu) ir įvertinkite Jūsų gautų hash'ų procentinį "skirtingumą" __bitų lygmenyje__. Išveskite iš minimalią, maksimalią ir vidurkines "skirtingumo" reikšmes. Tokiu būdų įsitikinsite, kaip gerai Jūsų hash funkcija atitinka 7-ą reikalavimą.

### Darbo vertinimas (Terminas: 2019-10-03)

- Iki 2.0 balų gausite atlikę visas aukščiau aprašytas užduotis pagal pateiktus reikalavimus.
- Bus atsižvelgiama į kūrybiškumą - ar nėra atkartoti kiti žinomi algoritmai.

### Papildoma užduotis (0,5 balo) (Terminas: 2019-10-03)

**Papildomų 0.5 balų surinkimas originalesnis**. Pirmiausia reiktų visas Jūsų grupės/pogrupio sukurtas hash funkcijas/generatorius apjungti/integruoti į vieno iš Jūsų programą  ir tuomet atlikti visą aukščiau aprašytą **lyginamąją analizę** (pagal 2-ą ir 4-ą eksperimentinio tyrimo-analizės atlikimo punktus) naudojant visus Jūsų grupės/pogrupio sukurtus hash generatorius. Gautus grupės/pogrupio rezultatus už abidvi užduotis - agreguokite. Tuomet jeigu Jūsų sukurtas _hash_ generatorius pateks tarp 25% geriausių Jūsų grupėje/pogrupyje (Q1 - pirmasis kvartilis), gausite papildomus 0,5 balo, o jeigu tarp 25% - 50% geriausių Jūsų grupėje/pogrupyje (Q2 - antrasis kvartilis), gausite papildomus 0,25 balo.
