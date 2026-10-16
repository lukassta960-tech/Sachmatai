# Sachmatai — semestro darbo architektūra

## Repozitorijos patikra

Patikrinta GitHub repozitorija: https://github.com/lukassta960-tech/Sachmatai

Patikros metu repozitorija buvo tuščia (GitHub Contents API grąžino „This repository is empty“). Todėl šiame dokumente pateikiamas pradinis planas, o ne esamo kodo analizė. Technologijos parinktos kaip prielaida ir turi būti patvirtintos pagal dėstytojo reikalavimus.

## Tikslas

Sukurti šachmatų žaidimą, kuriame žmogus žaidžia prieš kompiuterį, mato ėjimų istoriją ir gali peržiūrėti rezultatų lentelę. Paskyros neprivalomos.

## Mažiausių sąnaudų technologijų variantas

Jei nėra konkrečių technologinių reikalavimų:
- React + TypeScript vartotojo sąsajai.
- `chess.js` šachmatų taisyklėms ir legalumo tikrinimui.
- Paprastas minimax su alpha-beta optimizavimu kompiuterio ėjimams, jei tokio sudėtingumo pakanka semestro darbui.
- `localStorage` vietinei rezultatų lentelei.
- Testavimo įrankiai parenkami pagal sukurtą projekto karkasą.

Tai sąmoningai vengia serverio, duomenų bazės ir autentifikavimo. `localStorage` rezultatai galioja tik tame naršyklės profilyje; tai nėra bendra internetinė reitingų lentelė. Jei dėstytojas reikalauja bendros lentelės ar paskyrų, reikės atskiro serverio ir duomenų bazės sprendimo.

## Pagrindinės funkcijos

1. Interaktyvi 8×8 šachmatų lenta.
2. Žaidėjas žaidžia baltaisiais, kompiuteris — juodaisiais.
3. Legalūs ėjimai ir taisyklių laikymasis, įskaitant šachą, matą, patą, lygiąsias, rokiruotę, en passant ir pėstininko paaukštinimą.
4. Ėjimų istorija, naujos partijos paleidimas ir partijos pabaigos pranešimas.
5. Kompiuterio ėjimo parinkimas; kiekvienas jo ėjimas turi būti legalus.
6. Pasirenkamas žaidėjo vardas ir vietinė rezultatų lentelė.
7. Aiškios instrukcijos, kaip projektą paleisti ir testuoti.

## Siūloma failų struktūra

Ši struktūra taikoma tik tuo atveju, jei projektas pradedamas nuo nulio ir pasirenkamas React + TypeScript. Jei vėliau atsiras kiti reikalavimai, struktūrą reikia pritaikyti, o ne aklai perrašyti.

```text
Sachmatai/
├── src/
│   ├── components/
│   │   ├── ChessBoard.tsx
│   │   ├── GameControls.tsx
│   │   ├── MoveHistory.tsx
│   │   └── Leaderboard.tsx
│   ├── chess/
│   │   ├── game.ts
│   │   ├── ai.ts
│   │   └── evaluation.ts
│   ├── services/
│   │   └── leaderboard.ts
│   ├── types/
│   │   └── index.ts
│   ├── App.tsx
│   └── main.tsx
├── tests/
│   ├── game.test.ts
│   ├── ai.test.ts
│   └── leaderboard.test.ts
├── package.json
└── README.md
```

### Modulių atsakomybės

- `ChessBoard`: lentos atvaizdavimas ir žmogaus ėjimų įvedimas.
- `game.ts`: partijos būsenos valdymas, naudojant šachmatų biblioteką.
- `ai.ts`: kompiuterio ėjimo pasirinkimas.
- `evaluation.ts`: pozicijos įvertinimas ir figūrų vertės.
- `leaderboard.ts`: rezultatų įrašymas, nuskaitymas ir rikiavimas.
- `tests/`: automatiniai pagrindinės logikos testai.

## Testavimo planas

- Atmetami nelegalūs ėjimai, priimami legalūs ėjimai.
- Teisingai atpažįstamas šachas, matas, patas ir lygiosios.
- Patikrinami rokiruotės, en passant ir paaukštinimo atvejai.
- Kompiuteris visada pasirenka legalų ėjimą.
- Pasibaigus partijai papildomi ėjimai neleidžiami.
- Naujos partijos paleidimas išvalo ankstesnę žaidimo būseną.
- Rezultatai išsaugomi, perskaitomi ir surikiuojami teisingai.
- Paleidžiami projekto testai ir build komanda; dokumentuojami tik realiai gauti rezultatai.

## Įgyvendinimo etapai

1. Patvirtinti dėstytojo reikalavimus ir technologijas.
2. Sukurti minimalų projektą ir paleidimo instrukcijas.
3. Įgyvendinti lentą, žaidimo būseną ir legalų žmogaus ėjimą.
4. Įgyvendinti kompiuterio ėjimus.
5. Pridėti ėjimų istoriją ir partijos pabaigos būsenas.
6. Pridėti vietinę rezultatų lentelę.
7. Parašyti ir paleisti testus, sutvarkyti README.

## Claude Code instrukcija

Pradėk nuo esamos repozitorijos failų, README, konfigūracijos, priklausomybių ir testų patikros. Repozitorija patikros metu buvo tuščia, bet prieš keisdamas failus tai patikrink dar kartą. Nepriskirk projektui neegzistuojančio kodo ir neperrašyk veikiančių sprendimų.

Sukurk veikiantį semestro lygio šachmatų žaidimą prieš kompiuterį. Jei nėra dėstytojo nurodytų technologijų, naudok React + TypeScript, `chess.js`, paprastą AI su minimax ir alpha-beta optimizavimu bei `localStorage` vietiniams rezultatams. Įgyvendink interaktyvią lentą, legalius ėjimus ir visas standartines šachmatų pabaigas bei specialiuosius ėjimus, ėjimų istoriją, naują partiją, partijos pabaigos pranešimą ir rezultatų lentelę. Nepridėk autentifikavimo, serverio ar duomenų bazės, nebent tai aiškiai reikalauja projekto ar dėstytojo reikalavimai. Atskirti UI, žaidimo logiką, AI ir rezultatų saugojimą, bet venk perteklinių abstrakcijų ir priklausomybių.

Pirmiausia trumpai apibendrink realią struktūrą ir pakeitimų planą, tada įgyvendink funkcionalumą. Parašyk testus legalumui, partijos pabaigoms, AI ėjimų legalumui ir rezultatų išsaugojimui. Paleisk realiai prieinamas testų ir build komandas; niekada neteigk, kad jos praėjo, jei jų nepaleidai. Pabaigoje nurodyk pakeistus failus, paleidimo komandas, testų rezultatus ir likusius apribojimus. Nešalink vartotojo pakeitimų ir neatlik destruktyvių veiksmų.

## Atviri klausimai

- Ar dėstytojas nurodė konkrečią programavimo kalbą ar karkasą?
- Ar rezultatų lentelė turi būti bendra visiems interneto naudotojams?
- Ar kompiuterio sudėtingumas turi būti pasirenkamas?
