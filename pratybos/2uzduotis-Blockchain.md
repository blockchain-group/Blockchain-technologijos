# 2-oji užduotis: Supaprastintos blokų grandinės (blockchain) kūrimas

Pagrindinis šios užduoties tikslas yra sukurti supaprastintą blokų grandinę (angl. *blockchain*), kurios galima struktūra yra pateikta žemiau:

![Hashing](img/Blockchain-represented-as-Linked-List-Data-Structure.png)

Išskirtume kelis svarbius blokų grandinės aspektus:

- Blokų grandinė (blockchain) susidaro iš sąrašo vienas po kito einančių blokų, kurių kiekvienas susietas su prieš tai buvusio bloko hash'u. 

- Kiekvieno iš blokchain grandinės bloko struktūra yra sudaryta iš dviejų esminių komponentų: **antraštės** (angl. *header*), kurią šiuo atveju sudaro:

  - Prieš tai buvusio bloko hash'as (`Prev Block Hash`)
  - Laiko žymės (`Timestamp`)
  - Jūsų blokams naudojamos duomenų struktūros versija (`Version`)
  - Visų bloko transakcijų binarinio Merkle medžio hash'as (`Merkel Root Hash`)
  - Atsitiktinis skaičius, kuris buvo panaudotas reikiamo sudėtingumo (nusakomo iš eilės einančių nulių skaičiumi hash'o pradžioje) naujojo bloko hash'ui gauti (`Nonce`)
  - Naujojo bloko hash'o radimo sudėtingumas (`Difficulty Target`)

  ir **pagrindinės** (angl. *body*) bloko duomenų dalies, kurią sudaro visos į konkretų bloką įeinančios transakcijos.

## Pirminė užduoties formuluotė

Sukurkite "centralizuotą" blokų grandinę (blockchain'ą) ir susimuliuokite blokų grandinės veikimą kuo natūralesnėmis sąlygomis. Norint tai pasiekti, preliminari veiksmų seka (nebūtinai eilės tvarka, tokia kokia čia nurodyta) galėtų būti tokia:

1. Sugeneruoti ~1000 tinklo vartotojų (aka user'ių), kurie turėtų bent tris atributus: `vardą`, viešąjį _hash_ raktą (`public_key`) ir tam tikros valiutos (galite pasivadinti savo vardu :smile: ) atsitiktinį balansą, pvz. nuo 100 iki 1000000 vienetų.
2. Sugeneruoti tam tikrą skaičių, pvz., transkacijų pol'ą sudarytą iš 10000 atsitiktinių transakcijų (jų struktūrą kol kas yra neformalizuota) tarp visų vartotojų, kurių metu jie vienas kitam atlikinėtų pinigų pervedimus.
3. Iš šių transakcijų atsitiktinai pasirinkti 100-ą (tarsime, kad blokas talpins apie 100 transakcijų) ir jas priskirti naujam sugeneruotam blokui (kurį kitame žingsnyje dar reikės "iškąsti"), kurio struktūra nurodyta paveiksle aukščiau.
4. Realizuoti naujų blokų kasimo (angl. *mining*) Proof-of-Work (PoW) procesą, kurio tikslas yra surasti naujam blokui hash'ą, tenkinantį `Difficulty Targer` reikalavimą, t.y., hash'o pradžioje esančių nulių skaičių.
5. Suradus tokį naujo bloko hash'ą, bloką pridėti prie grandinės. Kartoti 3-5 žingsnius tol, kol yra laisvų transakcijų.

## Reikalavimai versijai (`v0.1`) (Preliminarus terminas: 2019-10-18)

- Visus šios užduoties žingsnius realizuokite taip, kaip Jūsų dabartinis *blockchain* supratimas sako. Hash'avimo procesui turite naudoti Jūsų pirmąjam darbui sukurtas _hash_ funkcijas.


Iš karto norime užbėgti įvykiams už akių ir pasakyti, kad kitose užduoties versijose atsiras griežtesni reikalavimai, atsižvelgiant kaip iš tiesų _blockchain_ veikia ar yra realizuota. Kaip pvz., atsiras transakcijų validavimas; naujojo bloko hash'o gavimas, kur input'as į hash'o funkciją yra sudarytas iš bloko antraštės parametrų; transakcijų Merkle medžio hash'o gavimas ir pan. Viskas bus sukonkretinta greitu laiku.
