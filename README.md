# Recensămintele României 2011 și 2021, localitate cu localitate

Datele recensămintelor din 2011 și 2021, curățate și legate între ele pentru toate cele **3.181 de unități administrativ-teritoriale** (municipii, orașe, comune) și **13.596 de sate și localități componente**.

Datele brute sunt publicate de INS în sute de fișiere Excel, cu formate diferite de la un recensământ la altul. Aici sunt aduse în câteva fișiere CSV simple, cu o cheie comună: **codul SIRUTA**. Pentru fiecare localitate, cele două recensăminte stau acum pe același rând.

Baza de date stă la baza site-ului **Satul care se stinge**, care arată depopularea fiecărui sat prin ferestre care se sting. Site-ul e inclus în folderul `site/`, ca un singur fișier HTML.

Autor: **Dorin Spoaller** (dorin.spoaller@ubbcluj.ro)

## Fișierele

Toate fișierele sunt în folderul `date/`, în format CSV cu codificare UTF-8 și virgulă ca separator.

| Fișier | Un rând pentru | Rânduri |
|---|---|---|
| `sate.csv` | fiecare sat sau localitate componentă | 13.596 |
| `uat.csv` | fiecare municipiu, oraș sau comună | 3.181 |
| `uat_varsta.csv` | fiecare UAT și an, cu grupe de vârstă de 5 ani | 6.362 |
| `uat_etnie.csv` | UAT × an × etnie | 146.326 |
| `uat_religie.csv` | UAT × an × religie | 143.145 |
| `uat_activitati_2021.csv` | UAT × activitate economică | 60.439 |
| `judete_educatie_2021.csv` | județ × nivel de educație | 2.192 |

### `sate.csv`

| Coloană | Ce conține |
|---|---|
| `siruta_sat` | codul SIRUTA al satului |
| `sat` | numele satului |
| `siruta_uat`, `uat`, `tip_uat`, `judet` | unitatea administrativă din care face parte (municipiu, oraș sau comună) |
| `pop_2011` | populația stabilă la 20 octombrie 2011 |
| `pop_2021` | populația rezidentă la 1 decembrie 2021 |
| `barbati_2021`, `femei_2021` | populația din 2021, pe sexe |
| `lat`, `lng` | coordonatele aproximative ale satului |

### `uat.csv`

| Coloană | Ce conține |
|---|---|
| `siruta_uat`, `uat`, `tip_uat`, `judet` | identificarea unității administrative |
| `pop_2011`, `pop_2021` | populația totală la cele două recensăminte |
| `copii_0_14_2011`, `copii_0_14_2021` | copii sub 15 ani |
| `peste_65_2011`, `peste_65_2021` | persoane de 65 de ani și peste |
| `locuinte_2021`, `locuinte_ocupate_2021` | locuințe convenționale, total și ocupate; diferența sunt locuințele goale, inclusiv casele de vacanță |
| `activi_2021`, `ocupati_2021`, `someri_2021` | populația activă din punct de vedere economic |
| `inactivi_2021`, `elevi_studenti_2021`, `pensionari_2021`, `casnici_2021`, `intretinuti_alte_persoane_2021`, `intretinuti_stat_2021`, `intretinuti_alte_surse_2021`, `alta_situatie_2021` | populația inactivă, pe categorii |

### `uat_varsta.csv`

Câte o coloană pentru fiecare grupă de vârstă de 5 ani (`varsta_0_4` … `varsta_85_plus`), pe două rânduri pentru fiecare UAT: unul pentru 2011, unul pentru 2021.

### `uat_etnie.csv` și `uat_religie.csv`

Format lung: `siruta_uat`, `uat`, `judet`, `an`, `etnie` sau `religie`, `persoane`.

Denumirile au fost unificate între cei doi ani; de exemplu, „Romano- catolica” din 2011 și „Romano-Catolica” din 2021 apar amândouă ca „Romano-catolică”. Unele categorii există doar într-un singur an: Chinezi și Ceangăi doar în 2011; Ruteni, Albanezi și Agnostici doar în 2021.

Categoria „Informație nedisponibilă” cuprinde persoanele care nu au răspuns la întrebare. În 2021 sunt mult mai multe decât în 2011, așa că pentru comparații între ani e mai corect să calculezi procentele din cei care au răspuns.

### `uat_activitati_2021.csv`

Persoanele ocupate după activitatea economică (secțiunile CAEN), pe fiecare UAT, în 2021.

### `judete_educatie_2021.csv`

Populația după nivelul de educație absolvit, pe județe, separat pe sexe și pe medii (urban, rural). INS nu a publicat educația pe comune pentru 2021.

Coloanele `nivel`, `subnivel` și `detaliu` păstrează ierarhia din tabelul INS. Ca să nu numeri aceeași persoană de două ori, adună doar rândurile de același nivel; rândurile cu `detaliu` sunt defalcări ale rândului lor părinte.

## Convenții

- **`*`** = valoare confidențială. INS nu publică valori sub 3 persoane. Valorile au fost păstrate așa cum le-a publicat INS, fără estimări.
- **`0`** = fenomenul nu există; în tabelele INS apare ca „-”.
- **Celulă goală** = data lipsește. De exemplu, satele care nu figurau separat în tabelul din 2011 nu au `pop_2011`.
- Comuna **Rădulești (Ialomița)** se numea **Brazii** în 2011; aici cele două denumiri sunt legate ca aceeași unitate.
- Populația din 2011 este **populația stabilă**, iar cea din 2021 este **populația rezidentă**. INS le tratează drept comparabile, dar metodologia diferă în detalii.
- Pentru București, cifrele sunt pentru tot municipiul; sectoarele apar ca localități separate doar în `sate.csv`.

## Surse

Toate cifrele provin de la **Institutul Național de Statistică (INS)**, din rezultatele definitive ale recensămintelor, disponibile pe [recensamantromania.ro](https://www.recensamantromania.ro).

**Recensământul populației și locuințelor 2021**
- Tabelul 1.22: populația rezidentă pe sexe, județe, municipii, orașe, comune și sate
- Tabelul 1.3.2: populația rezidentă pe grupe de vârstă, pe municipii, orașe și comune
- Tabelul 2.2.2: populația rezidentă după etnie, pe municipii, orașe și comune
- Tabelul 2.4.2: populația rezidentă după religie, pe municipii, orașe și comune
- Tabelul 3.1: populația după nivelul de educație absolvit, pe județe și medii
- Tabelul 5.29: populația activă și inactivă, pe localități
- Tabelul 5.30: populația ocupată pe activități ale economiei naționale, pe localități
- Tabelul 7.12: clădiri și locuințe, pe municipii, orașe și comune

**Recensământul populației și locuințelor 2011**
- Populația stabilă pe județe, municipii, orașe, comune și localități componente
- Tabelul 3: populația stabilă pe sexe și grupe de vârstă, pe municipii, orașe și comune
- Tabelul 8: populația stabilă după etnie, pe municipii, orașe și comune
- Tabelul 13: populația stabilă după religie, pe municipii, orașe și comune

**Coordonatele satelor** vin din [baza-de-date-localitati-romania](https://github.com/catalin87/baza-de-date-localitati-romania), publicată în domeniul public. 171 de sate nu au coordonate.

## Cum a fost construită

1. Tabelele INS au fost citite din fișierele Excel originale. Unele date pe comune se aflau pe a doua foaie a fișierelor.
2. Localitățile din 2011 și din 2021 au fost potrivite după județ, comună și numele satului, ignorând diacriticele și variantele de scriere (de exemplu „Râmnicelu” și „Rîmnicelu”). Codul SIRUTA vine din tabelele din 2021.
3. Verificări: suma populației pe UAT dă exact totalurile naționale INS, 20.121.641 în 2011 și 19.053.815 în 2021. 13.540 dintre cele 13.596 de sate au o cifră pentru 2011; restul nu apăreau separat în tabelul din 2011.

## Licență și citare

Datele aparțin **Institutului Național de Statistică**. Dacă le folosești, citează INS ca sursă.

Curățarea, unificarea și legarea datelor din acest repository sunt publicate sub licența [Creative Commons Atribuire 4.0 Internațional (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/deed.ro). Le poți folosi, modifica și republica liber, inclusiv în scop comercial, cu condiția să menționezi sursa.

Sugestie de citare:

> Spoaller, D. (2026). *Recensămintele României 2011 și 2021, localitate cu localitate* [set de date]. Pe baza datelor INS, RPL 2011 și RPL 2021.
