# 2-oji užduotis: Supaprastintos blokų grandinės (blockchain) kūrimas

Pagrindinis šios užduoties tikslas yra sukurti supaprastintą blokų grandinę (angl. *blockchain*), kurios galima supaprastinta struktūra yra pateikta žemiau:

![Hashing](img/Blockchain-represented-as-Linked-List-Data-Structure.png)

Išskirtume kelis tokios svarbius blokų grandinės aspektus:

- Blokų grandinė (blockchain) susidaro iš sąrašo vienas po kito einančių blokų, susietų prieš tai buvusio bloko hash'u. 

- Kiekvieno iš blokchain grandinės bloko struktūra yra sudaryta iš dviejų esminių komponentų: **antraštės** (angl. *header*), kurią šiuo atveju sudaro:

  - Prieš tai buvusio bloko hash'as (`Prev Block Has`)
  - Laiko žymės (`Timestamp`)
  - Jūsų blokams naudojamos duomenų struktūros versija (`Version`)
  - Visų bloko transakcijų binarinio Merkle medžio hash'as (`Merkel Root Hash`)
  - Atsitiktinis skaičius, kuris buvo panaudotas reikiamo sudėtingumo (nusakomo iš eilės einančių nulių skaičiumi hash'o pradžioje) naujojo bloko hash'ui gauti (`Nonce`)
  - Naujojo bloko hash'o radimo sudėtingumas (`Difficulty Targer`)

  ir **pagrindinės** (angl. *body*) bloko duomenų dalies, kurią sudaro visos į konkretų bloką įeinančios transakcijos.

## Pirminė užduoties formuluotė

Sukurkite "centralizuotą" blokų grandinę (blockchain'ą) ir susimuliuokite blokų grandinės veikimą kuo natūralesnėmis sąlygomis. Norint tai pasiekti, preliminari veiksmų seka (nebūtinai eilės tvarka, kokia čia nurodyta ir nebūtinai tokia seka :smile: galėtų būti tokia:

1. Sugeneruoti ~1000 tinklo vartotojų (aka user'ių), kurie turėtų, bent tris atributus: `vardą`, viešąjį raktą (`public_key`) ir tam tikros valiutos (galite pasivadinti savo vardu :smile: atsitiktinį balansą, nuo 100 iki 1000000 ribose.
2. Sugeneruoti tam tikrą skaičių, pvz. 10000 atsitiktinių transakcijų tarp visų vartotojų, kurių metu jie vienas kitam atlikinėtų pinigų pervedimus.
3. Iš šių transakcijų atrinkti 100-ą (tarsime, kad blokas talpins apie 100 transakcij7) ir jas priskirti naujam sugeneruotam blokui, kurį kitame žingsnyje dar reikės "validuoti" - iškąsti. Bloko struktūra nurodyta auščiau, tačiau reikšmių tikslumas ir griežtumas priklauso nuo reikalavimų realizacijos versijai (žr. žemiau).
4. Realizuoti naujų blokų kasimo (angl. *mining*) Proof-of-Work (PoW) procesą, kurio tikslas yra surasti naujam blokui hash'ą, kuris tenkintų `Difficulty Targer` reikalavimą.
5. Naują bloką pridėti prie blokų grandinės ir 3-5 žingsnius kartoti tol, kol yra laisvų transakcijų nesančių blokuose.

## Reikalavimai versijai (`v0.1`) (Preliminarus terminas: 2019-10-18)

Visus šios užduoties žingsnius realizuokite taip kaip Jūsų dabartinis *blockchain* supratimas sako, arba tiesiog kaip Jums patogiau. 


Iš karto norime užbėgti įvykiams už akių ir pasakyti, kad kitose versijose atsiras griežtesni reikalavimai, atsižvelgiant kaip iš tiesų blockchain veikia, tokie kaip pvz. transakcijų validavimas, naujojo bloko hash'o gavimas kur input'as į hash'o funkciją yra sudarytas iš bloko antraštės parametrų, transakcijų Merkle medžio hash'as ir pan. Viskas bus sukonkretinta.
