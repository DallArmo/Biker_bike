# Handoff pre coding agenta: demo platformy pre motorkárov

**Pracovný názov:** RideLocal  
**Trh:** Bratislava, Brno a výlety po Česku a Slovensku  
**Typ výstupu:** klikateľné, responzívne demo webovej platformy  
**Dátum podkladov:** 18. október 2026

## 1. Cieľ

Vytvor vizuálne presvedčivé demo, v ktorom si motorkár vie:

1. prezerať odporúčané trasy na interaktívnej mape a v zozname;
2. nájsť skupinovú jazdu alebo vytvoriť vlastnú;
3. poslať inému jazdcovi žiadosť o priateľstvo a chatovať s prijatými priateľmi;
4. nastaviť profil podľa svojho jazdeckého štýlu, motorky a obvyklej dĺžky jázd.

Demo má pôsobiť ako reálny produkt, ale nemusí mať produkčný backend. Seedované dáta a používateľské interakcie môžu fungovať na strane klienta a ukladať sa do localStorage. Všetky dôležité tlačidlá musia mať viditeľnú funkciu.

## 2. Cieľoví používatelia a hlavná hodnota

Platforma je určená jazdcom z Bratislavy, Brna a okolia, ktorí chcú objavovať dobré lokálne cesty, nájsť ľudí s podobným tempom a plánovať spoločné výjazdy. Má podporovať krátke večerné jazdy aj celodenné a viacdňové výlety.

**Hlavná veta produktu:**  
„Nájdi svoju ďalšiu trasu a ľudí, s ktorými ju pôjdeš.“

## 3. Rozsah dema

### Zahrnúť

- prehliadanie trás na mape aj v kartovom zozname;
- filtre podľa krajiny, regiónu, dĺžky jazdy a štýlu;
- detail trasy s trasovými bodmi, orientačnými údajmi a zaujímavými zastávkami;
- komunitnú nástenku skupinových jázd;
- vytvorenie, pripojenie a odpojenie od jazdy;
- profily jazdcov, žiadosti o priateľstvo a demo chat;
- editovateľný profil jazdca;
- lokalizáciu rozhrania v slovenčine a češtine; viditeľný prepínač SK / CZ.

### Mimo rozsahu prvej ukážky

- reálne používateľské účty, autentifikácia a produkčný backend;
- živé zdieľanie GPS polohy alebo sledovanie jázd;
- push notifikácie, platby, rezervácie a marketplace;
- navigácia turn-by-turn alebo záruka aktuálneho stavu ciest;
- nahrávanie skutočných používateľských príspevkov na verejný server.

Neskrývaj nefunkčné časti za tlačidlá. Ak niečo nie je súčasťou dema, vynechaj to alebo to označ ako „čoskoro“.

## 4. Navigácia a obrazovky

Použi štyri hlavné sekcie:

1. **Trasy** – interaktívna mapa, vyhľadávanie, filtre a detaily trás.
2. **Skupinové jazdy** – zoznam jázd, detail jazdy a formulár na vytvorenie.
3. **Priatelia a chat** – vyhľadanie jazdcov, žiadosti a konverzácie.
4. **Profil** – údaje jazdca, motorka a preferencie.

Na mobile použi spodnú navigačnú lištu a veľké dotykové prvky. Na desktope môže byť hlavná navigácia bočná. Pri mapovej obrazovke nech mapa zaberá väčšinu plochy a zoznam trás nech sa dá pohodlne otvoriť ako panel.

## 5. Funkčné požiadavky

### 5.1 Trasy a mapa

- Zobraz mapu so zakreslenými trasami a značkami pre štart, cieľ a hlavné zastávky.
- Po výbere karty zvýrazni príslušnú trasu; po výbere línie alebo značky otvor jej detail.
- Filtre: Česko / Slovensko, región, približná dĺžka, krátka / poldeň / celý deň / viac dní, scenická / zákrutová / pohodová / turistická.
- Detail trasy má obsahovať názov, krátky opis, krajinu a región, poradie zastávok, orientačnú vzdialenosť a čas, štýl jazdy, odporúčané prestávky, zdroj návrhu a upozornenie, kedy boli údaje naposledy overené.
- Zobrazenie kilometrov a času počítaj z reálneho plánovača podľa trásových bodov, ak je dostupný. Ak nie, použi označený orientačný údaj zo zdroja; nevymýšľaj presnú vzdialenosť.
- Pridaj tlačidlo „Otvoriť trasu v navigácii“ alebo „Kopírovať trasové body“. Ak integrácia navigácie nie je pripravená, tlačidlo môže zobraziť detail trasy s jej bodmi.
- Všetky trasy sú určené pre bežné cestné motocykle. Aplikácia nesmie navrhovať prejazd cez cestu so zákazom vjazdu alebo trasu, ktorá vyžaduje jazdu po chodníku či cyklotrase.

**Mapová implementácia pre demo:** Leaflet alebo obdobná knižnica s dlaždicami od poskytovateľa, ktorý povoľuje dané použitie. Pri OpenStreetMap vždy zobraz viditeľné označenie „© OpenStreetMap contributors“ s odkazom na licenciu. Pre verejné nasadenie treba skontrolovať podmienky poskytovateľa máp a limity dlaždíc.

### 5.2 Skupinové jazdy

Každá karta jazdy obsahuje:

- názov a krátky opis;
- dátum, čas a miesto štartu;
- vybranú trasu alebo trasové body;
- približnú dĺžku;
- tempo: pohodové / stredné / svižné;
- počet prihlásených a maximálnu kapacitu;
- organizátora a jeho profil;
- tlačidlo „Pridať sa“ alebo „Odhlásiť sa“.

Používateľ môže vytvoriť jazdu formulárom s názvom, dátumom a časom, štartom, trasou, tempom, kapacitou a poznámkou. Po vytvorení sa jazda objaví na nástenke. Po pridaní alebo odhlásení sa správne zmení počet účastníkov a tlačidlo. Pri plnej kapacite zobraz „Plná“; čakaciu listinu môžeš simulovať.

Seedni aspoň štyri ukážkové jazdy: dve v okolí Brna, jednu z Bratislavy na Pezinskú Babu a jednu celodennú horskú jazdu na Slovensku. Aspoň jedna jazda má byť plná, aby bolo vidieť stav kapacity.

### 5.3 Priatelia a chat

- Zoznam odporúčaných jazdcov s menom, mestom, motorkou a stručným profilom.
- Vyhľadávanie podľa mena alebo mesta.
- Stavy priateľstva: nepridaný, žiadosť odoslaná, čakajúca žiadosť, priateľ.
- Tlačidlá na odoslanie, prijatie a zrušenie žiadosti.
- Chat sa otvorí z profilu priateľa alebo zo zoznamu konverzácií.
- Používateľ môže odoslať demo správu; správa sa ihneď zobrazí v konverzácii a zostane uložená v localStorage.
- Chat je dostupný iba pri prijatom priateľstve. Pri ostatných profiloch zobraz výzvu „Najprv si pridajte jazdca medzi priateľov“.
- Pridaj aspoň tri ukážkové profily a dve predvyplnené konverzácie.

### 5.4 Profil jazdca

Profil musí ísť upraviť a po obnovení stránky zostať uložený. Polia:

- prezývka alebo zobrazované meno;
- domovské mesto – napr. Bratislava alebo Brno;
- typ jazdca: touring, adventure, sport, naked, cruiser, commuter, enduro/dual-sport, skúter, iné;
- štýl jazdy: scenické a pokojné jazdy, zákruty, dlhé cestovanie, adventure, každodenné dochádzanie;
- obvyklá dĺžka výjazdu: do 100 km, 100–250 km, 250–400 km, viac ako 400 km, viacdňové výlety;
- preferované tempo: pohodové, stredné, svižné;
- motorka: značka, model a voliteľne objem;
- preferovaná veľkosť skupiny a krátke „O mne“.

Nepýtaj sa na presnú domácu adresu ani verejne nezobrazuj aktuálnu polohu.

## 6. Počiatočný výber trás na seedovanie

Trasy nižšie sú podklad pre demo katalóg. Zdroje označujú obľúbené alebo odporúčané úseky a navrhované prejazdy; nie všetky poskytujú hotový GPX súbor. Coding agent má vytvoriť vlastnú geometriu z uvedených bodov cez vhodný plánovač trás a pred zobrazením overiť prístupnosť. Neber približnú trasu z článku ako aktuálnu navigáciu.

### Česko

#### A. Brno – Buchlovské kopce

**Trasové body:** Brno → Bučovice → Střílky → Buchlovice → hrad Buchlov → Velehrad → Uherské Hradiště → Brno.  
**Charakter:** južná Morava, zákrutové úseky, hrady a obce. Úsek Střílky–Buchlovice na ceste I/50 sa v motorkárskych odporúčaniach spomína ako známy zákrutový úsek; v kartičke ho označ ako úsek vyžadujúci rozumné tempo a pozornosť.  
**Zdroj:** [Motorkáři.cz – trasy Moravou a Sliezskom](https://www.motorkari.cz/cestovani/akce-predstavujeme/nejlepsi-trasy-ii-morava-a-slezsko-20597.html); [Moto-pneu – tipy na moto výlety na južnej Morave](https://www.moto-pneu.cz/cs/blog/10-tipu-na-motovylet-jizni-morava).

#### B. Brno – Pálava a Mikulov

**Trasové body:** Brno → Pohořelice → Dolní Věstonice → Pavlov → Mikulov → Lednice → Hustopeče → Brno.  
**Charakter:** scenická, pohodovejšia jazda cez vinársku krajinu a južnú Moravu. Vhodná ako kratšia až poldeňová jazda; presnú vzdialenosť nech určí plánovač.  
**Zdroj:** [Brnolove – výjazdy z Brna](https://www.brnolove.cz/na-motorce-z-brna/).

#### C. Jeseníky a Červenohorské sedlo

**Trasové body:** Šumperk → Velké Losiny → Červenohorské sedlo → Karlova Studánka → Rýmařov → Skřítek → Šumperk.  
**Charakter:** horská a zákrutová celodenná jazda. Červenohorské sedlo a Jeseníky patria medzi odporúčané motorkárske úseky.  
**Zdroj:** [VisitCzechia – Česko zo sedla motocykla](https://www.visitczechia.com/en-us/news/2022/07/n-czech-republic-on-motorbike).

#### D. Šumava a Lipno

**Trasové body:** Blatná → Zadov → Kvilda → Volary → Horní Planá → Lipno nad Vltavou.  
**Charakter:** dlhšia scenická jazda; zdroj uvádza približne 234 km a 4 h 15 min čistej jazdy. Ide o trasu od štartu k cieľu, nie uzavretý okruh.  
**Zdroj:** [Oficiálny motocyklový sprievodca južnými Čechami](https://www.jiznicechy.cz/en/top/80-guide-moto-en-boheme-du-sud).

#### E. Kokořínsko a Bezděz

**Trasové body:** Mělník → Kokořínský důl → Kokořín → Houska → Bezděz → Mělník.  
**Charakter:** scenické údolie, lesné cesty a historické zastávky; vhodná ako regionálny okruh.  
**Zdroj:** [VisitCzechia – Česko zo sedla motocykla](https://www.visitczechia.com/en-us/news/2022/07/n-czech-republic-on-motorbike).

#### F. Beskydy a Kysuce – cezhraničný okruh

**Trasové body:** Frýdek-Místek → Čeladná → Rožnov pod Radhoštěm → Velké Karlovice → Makov → Jablunkov → Bílá → Staré Hamry → Frýdek-Místek.  
**Charakter:** celodenný horský okruh cez české Beskydy a slovenské Kysuce.  
**Dôležité:** neplánuj prejazd cez Pustevny bez overenia aktuálnych zákazov vjazdu. V zdrojoch sa opisuje obmedzený prístup pre motorové vozidlá. Trasové body a cestnú dostupnosť skontroluj v plánovači.  
**Zdroj:** [NaEnduru – moto výlet v Beskydách](https://naenduru.cz/moto-vylet-beskydy/); [Ostravalove – motovýlety z Ostravy](https://www.ostravalove.cz/motovylety-z-ostravy/).

### Slovensko

#### G. Bratislava – Pezinská Baba

**Trasové body:** Bratislava → Pezinok → Pezinská Baba → Pernek → Vinosady → Modra → Bratislava.  
**Charakter:** lokálny kratší až poldeňový výjazd, vhodný pre komunitné jazdy z Bratislavy. Pezinská Baba je zaradená medzi najkrajšie cesty Slovenska a úsek Pernek–Vinosady je uvedený v databáze motorkárskych ciest.  
**Zdroj:** [Slovakia.travel – TOP 10 najkrajších ciest](https://slovakia.travel/top-10-najkrajsich-ciest-na-slovensku); [Slovakia.travel – Pezinská Baba](https://slovakia.travel/pezinska-baba); [BestBikingRoads – Pernek–Vinosady](https://www.bestbikingroads.com/motorcycle-roads/slovakia/slovakia/ride/503-pernek-vinosady-pezinska-baba).

#### H. Malá Fatra, Orava a Donovaly

**Trasové body:** Žilina → Strečno → Terchová → Vrátna → Zázrivá → Oravský Podzámok → Dolný Kubín → Ružomberok → Donovaly → Banská Bystrica → Martin → Žilina.  
**Charakter:** celodenný horský okruh cez známe oblasti; zdroj uvádza približne 263 km. V detailoch môžeš vyzdvihnúť Strečno, Vrátna dolinu, Oravský hrad a Donovaly.  
**Zdroj:** [Rollway – motorkárske trasy na Slovensku](https://www.rollway.cz/motorkarske-trasy-slovensko/).

#### I. Liptov, Čertovica a Slovenský raj

**Trasové body:** Liptovský Mikuláš → Liptovský Hrádok → Čertovica → Brezno → Telgárt → Dobšinská ľadová jaskyňa → Hrabušice → Poprad → Štrbské Pleso → Liptovský Mikuláš.  
**Charakter:** dlhý horský okruh; zdroj uvádza približne 261 km. V detaile zdôrazni, že ide o celodenný výlet a trasu treba pred jazdou skontrolovať pre počasie a uzávery.  
**Zdroj:** [Rollway – motorkárske trasy na Slovensku](https://www.rollway.cz/motorkarske-trasy-slovensko/).

#### J. Liptovská Mara, Huty a Orava

**Trasové body:** Liptovský Mikuláš → Liptovská Mara → horský priechod Huty → Zuberec → Tvrdošín → Dolný Kubín → Ružomberok → Liptovský Mikuláš.  
**Charakter:** scenická jazda medzi Liptovom a Oravou. Horský priechod Huty (Liptovská Mara–Zuberec) je v oficiálnom výbere najkrajších slovenských ciest.  
**Zdroj:** [Slovakia.travel – TOP 10 najkrajších ciest](https://slovakia.travel/top-10-najkrajsich-ciest-na-slovensku).

#### Ďalšie slovenské úseky pre rozšírenie

Do ďalšej vlny katalógu zváž úseky Donovaly, Hnúšťa–Jelšava, okolie Spišského hradu, Hodruša–Hámre, Manínsku tiesňavu a Sorošku. Sú súčasťou oficiálneho výberu najkrajších ciest Slovenska. Pred vytvorením celých okruhov treba doplniť a overiť presné trasové body.

## 7. Dáta a interakcie

Demo môže používať lokálne JSON seed dáta. Minimálne objekty:

- **Route:** ID, názov, krajina, región, opis, štart, cieľ, zoradené trasové body, geometria čiary na mape, kilometre, odhad času, štýlové tagy, zastávky, URL zdrojov a dátum overenia.
- **RiderProfile:** ID, meno, mesto, typ jazdca, štýl jazdy, obvyklý rozsah vzdialenosti, tempo, motorka a bio.
- **GroupRide:** ID, názov, organizátor, dátum/čas, štart, vybraná trasa, tempo, kapacita, zoznam účastníkov a poznámka.
- **Friendship:** dvojica používateľov a stav žiadosti.
- **Conversation / Message:** účastníci chatu, správy, čas a odosielateľ.

Zmeny v demo aplikácii ukladaj do localStorage. Priprav tlačidlo „Obnoviť demo dáta“, aby sa dalo vrátiť do pôvodného stavu.

## 8. Vizuálny smer

- Moderný motorkársky produkt, nie pretekársky alebo agresívny vzhľad.
- Výrazná mapa, čitateľné route karty a jasné označenie miest, vzdialenosti a tempa.
- Použi kontrastné tmavé texty, svetlé pozadie a jeden výrazný akcent (napr. oranžová alebo limetková).
- Na mobile sú primárne akcie dostupné bez presného mierenia; karty sa dajú používať jednou rukou.
- Profily majú pôsobiť osobne: avatar/monogram, mesto, motorka a jazdecké preferencie.
- Všetok text musí byť krátky, prirodzený a lokalizovaný. Nenechávaj v UI Lorem ipsum ani technické placeholdery.

## 9. Kritériá prijatia

Demo je hotové, keď:

1. trasy sa zobrazia na mape aj v zozname a výber jednej synchronizuje mapu s detailom;
2. filtre krajiny, regiónu, štýlu a vzdialenosti menia výsledky;
3. používateľ vie vytvoriť jazdu a vidí ju na nástenke;
4. pripojenie a odhlásenie menia účastníkov a počet miest;
5. žiadosť o priateľstvo mení stav a prijatý priateľ sa dá otvoriť v chate;
6. odoslaná správa sa zobrazí v konverzácii;
7. profil sa dá upraviť a zmeny zostanú po obnovení stránky;
8. demo funguje na úzkom mobilnom displeji aj desktope;
9. prepnutie SK/CZ preloží hlavné navigačné a akčné texty;
10. mapa má viditeľné licenčné označenie a detail každej trasy obsahuje upozornenie, že aktuálny stav a prístupnosť treba pred jazdou overiť.

## 10. Poznámky k dátam a bezpečnosti

- Trasy sú kurátorské návrhy zo zdrojov uvedených vyššie, nie záruka aktuálnej prejazdnosti ani bezpečnosti.
- Pri každej trase zobraz dátum posledného overenia; pri demo dátach jasne uveď, že ide o ukážkové informácie.
- Nezobrazuj presnú adresu používateľa, jeho živú polohu ani súkromné údaje.
- Nepoužívaj cudzie fotografie, GPX súbory alebo mapové dlaždice bez povoleného použitia a atribúcie.
- Zdroje článkov slúžia ako podklad na výber oblastí a zastávok. Geometriu trasy vytvor a over samostatne podľa aktuálnej cestnej siete a pravidiel prístupu.

## 11. Zdroje použité pri výbere trás

1. [VisitCzechia – The Beauty of the Czech Republic from the Seat of a Motorbike](https://www.visitczechia.com/en-us/news/2022/07/n-czech-republic-on-motorbike)
2. [South Bohemia – Motorcycle Guide to South Bohemia](https://www.jiznicechy.cz/en/top/80-guide-moto-en-boheme-du-sud)
3. [Slovakia.travel – TOP 10 najkrajších ciest na Slovensku](https://slovakia.travel/top-10-najkrajsich-ciest-na-slovensku)
4. [Slovakia.travel – Pezinská Baba](https://slovakia.travel/pezinska-baba)
5. [Rollway – Motorkářské trasy na Slovensku](https://www.rollway.cz/motorkarske-trasy-slovensko/)
6. [Motorkáři.cz – Najlepšie trasy Moravou a Sliezskom](https://www.motorkari.cz/cestovani/akce-predstavujeme/nejlepsi-trasy-ii-morava-a-slezsko-20597.html)
7. [Brnolove – Na motorce z Brna](https://www.brnolove.cz/na-motorce-z-brna/)
8. [NaEnduru – Moto výlet Beskydy](https://naenduru.cz/moto-vylet-beskydy/)
9. [Ostravalove – Motovýlety z Ostravy](https://www.ostravalove.cz/motovylety-z-ostravy/)
10. [BestBikingRoads – Pernek–Vinosady / Pezinská Baba](https://www.bestbikingroads.com/motorcycle-roads/slovakia/slovakia/ride/503-pernek-vinosady-pezinska-baba)
11. [Moto-pneu – Tipy na motovýlet na južnej Morave](https://www.moto-pneu.cz/cs/blog/10-tipu-na-motovylet-jizni-morava)

*Pred prípadným verejným spustením treba zvlášť preveriť aktuálne uzávierky, zákazy vjazdu, mapové licencie a spracovanie osobných údajov. Tento dokument je zadanie pre demo, nie právne stanovisko.*
