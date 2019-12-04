# 4-oji užduotis: išmaniosios sutarties ir decentralizuotos aplikacijos kūrimas 

## Tikslas

Pagrindinis šios užduoties tikslas yra sukurti išmaniąją sutartį (angl. *smart contract*), kuri įgyvendintų tam tikrą verslo logiką ir galėtų užtikrinti jos "saugų" ir "patikimą" funkcionavimą decentralizuotame viešąjame tinkle. Išmaniosios sutarties valdymui ir verslo proceso dalyvių tarpusavio sąveikai palengvinti bus kuriama decentralizuota aplikacija su `Front-End`.

Šioje užduotyje išmanioji sutartis įgyvendinama **Solidyti** programavimo kalba ir turi būti adaptuota **Ethereum** *blockchain* tinklui. Šiai užduočiai atlikti Jums reikės:
 - Išmaniosios sutarties kūrimui rekomenduojama naudoti "*on-line*" įrankį [Remix IDE](https://remix.ethereum.org/), o testavimui ir diegimui [Truffle IDE](https://www.trufflesuite.com/), kurį reikia įdiegti į savo kompiuterį. 
 - Decentralizuotos aplikacijos testavimui galite naudoti [Ganache](https://www.trufflesuite.com/ganache) įrankį, kuris sukuria lokalų *Ethereum* tinklą. 
 - Jums taip pat prireiks kliento [MyEtherWallet](https://www.myetherwallet.com/) arba [MetaMask](https://metamask.io/), kuris įgalins sąsają su *Ethereum* tinklu.
 - Išmaniosios sutarties testavimui naudokite ir vieną iš viešųjų *Ethereum* testinių tinklų (angl. *testnet*), pvz., [Ropsten](https://ropsten.etherscan.io/) arba [RinkeBy](https://www.rinkeby.io/).

**Svarbu:** ši užduotis remiasi [Paskaitos (2019-11-29) medžiaga](https://github.com/blockchain-group/Blockchain-technologijos/blob/master/paskaitos/paskaita-ismanioji_sutartis.md), todėl prieš atliekant šią užduotį būtina susipažinti su nurodytosios paskaitos medžiaga. 

## Užduoties formuluotė (preliminarus terminas: 2019-12-13)

1. Aprašykite išmaniosios sutarties verslo modelio logiką, kurią įgyvendins išmanioji sutartis. 

   - **Planas minimum**: kad labai neapsunkinti užduoties, pasirinkite verslo modelį panašų į [Paskaita 2019-11-29](https://github.com/blockchain-group/Blockchain-technologijos/blob/master/paskaitos/paskaita-ismanioji_sutartis.md) medžiagoje pateiktą modelį. Verslo modelyje dalyvauja tokios šalys: `pirkėjas`, `pardavėjas`, `kurjeris`, o pati išmanioji sutartis užtikrina "saugų" prekių `pardavimą/pirkimą` ir `pristatymą`.  

   - **Planas maximum (papildomi 0,5 balo prie užduoties!)**: entuziastai, kurie pasirinks ir aprašys kitą verslo modelį ir jo pagrindų įgyvendins išmaniąją sutartį ir decentralizuotą aplikaciją, papildomai gaus 0,5 balo :smile:

2. Realizuokite pirmąjame žingsnyje aprašytą verslo logiką išmanioje sutartyje **Solidyti** kalboje.

3. Ištestuokite išmaniosios sutarties veikimą **Ethereum** **lokaliame** tinkle ir **Ethereum** **testiniame** tinkle  (pvz., *Ropsten*). 
4. Naudojant *Ethereum* testinio tinklo  `Etherscan` peržiūrėkite išmaniosios sutarties vykdymo "logus".
5. Sukurkite decentralizuotos aplikacijos `Front-End`ą (tinklapį arba mobiliąją aplikaciją), kuri įgalintų bendravimą su išmaniąja sutartimi. 
   - **Planas minimum**: minimalistinio dizaino ir minimalaus funkcionalumo aplikacija, kuri tiesiog užtirkintų sąveiką su verslo modelio dalyviais ir leistų aktyvuoti išmaniosios sutarties funkcijas, pateikti/nuskaityti sutarčiai reikalingus duomenis.
   - **Planas maximum (papildomai iki 1 balo prie užduoties!)**: praplėsto funkcionalamo (ir dizaino) aplikacija. Čia žiūrėkite kūrybiškai, atsižvelgiant į turimą laiką, patirtį ir galimybes :)

## Papildoma medžiaga

**Dokumentacijos**:

1. [Solidyti dokumentacija](https://solidity.readthedocs.io/en/v0.5.13/)
2. [Remix IDE dokumentacija](https://remix-ide.readthedocs.io/en/latest/)
3. [Truffle IDE dokumentacija](https://www.trufflesuite.com/docs)

**Išmaniųjų sutarčių ir decentralizuotų aplikacijų kūrimo pamokos ir pavyzdžiai**:

- <https://www.coursera.org/learn/smarter-contracts/>
- <https://www.coursera.org/learn/decentralized-apps-on-blockchain>
-  <https://www.dappuniversity.com/>
- <https://blockgeeks.com/guides/solidity/>