# Uitgangspunten MIM-kennisskill

Dit document legt de uitgangspunten vast voor de kennisbank `mim-kennis` (stap 1 van de takenlijst). Het vervangt de tabel met aannames in `overdracht.md` §3. Alle volgende stappen werken binnen deze uitgangspunten; wijzigingen lopen via een nieuw besluit in het [besluitenlog](https://claude.ai/code/artifact/6a7e5a19-b172-4fc1-893f-e17692ded30a).

Vastgesteld: 19 oktober 2026 · Eigenaar: Mats Braster (Geonovum)

De versie in het Claude-project is leidend. De kopie in de lokale projectmap is een afschrift. Dit document is een projectdocument en wordt niet meeverpakt in de skill.

---

## 1. Doel en product

| # | Uitgangspunt | Besluit |
|---|--------------|---------|
| U1 | De kennisbank is het product. Hij is platformneutraal geschreven in markdown, zonder Claude-specifieke afhankelijkheden in de inhoud. De Claude-skill is één verpakking ervan. | B10 |
| U2 | Het primaire gebruik is **uitleggen**: vragen over MIM correct beantwoorden. Modelleren, toetsen en transformeren mogen de kennis gebruiken, maar zijn geen ontwerpdoel van versie 1. | B11 |
| U3 | De kennisbank bedient vier doelgroepen: nieuwkomers, architecten en beleidsmedewerkers, ontwikkelaars en data-engineers, en informatiemodelleurs. | B12 |

Gevolg van U1: platformspecifieke aanwijzingen (zoals de description en leesregels voor Claude) staan alleen in `SKILL.md`, niet in de kennisbestanden.

---

## 2. Bron

| # | Uitgangspunt | Besluit |
|---|--------------|---------|
| U4 | De normatieve bron is MIM 1.2, vastgestelde versie van 13 juni 2024: <https://docs.geostandaarden.nl/mim/def-st-mim-20240613>. | B8 |
| U5 | De repository [Geonovum/MIM-Werkomgeving](https://github.com/Geonovum/MIM-Werkomgeving) is werkbron. Waar de repo afwijkt van de vastgestelde versie, geldt de vastgestelde versie en wordt de afwijking vastgelegd. | B8 |
| U6 | De MIM-bronbestanden komen in de projectkennis van het Claude-project, zodat ook chats zonder gekoppelde computer ermee kunnen werken. Dit gebeurt in stap 2. | B19 |
| U7 | De bron gaat altijd boven de voorkennis van het model. | overdracht §7 |

---

## 3. Scope van versie 1

| # | Uitgangspunt | Besluit |
|---|--------------|---------|
| U8 | Binnen scope: het metamodel algemeen, de afspraken en regels, en beide uitdrukkingsvormen: UML en Linked Data, inclusief de transformatie naar RDF. | B9 |
| U9 | Buiten scope: extensies (Kadaster, NEN3610 en andere). Die volgen in een latere versie als aparte bestanden boven op de kern. | B9 |
| U10 | Buiten scope: een deterministische toetslaag, transformatiescripts en andere verpakkingen. Zie `overdracht.md` §12. | B1 |

---

## 4. Inhoud en schrijfwijze

| # | Uitgangspunt | Besluit |
|---|--------------|---------|
| U11 | Taal is Nederlands. Engelse termen staan alleen in de woordenlijst. | B15 |
| U12 | Letterlijke MIM-tekst en eigen uitleg staan altijd gescheiden. Letterlijke tekst krijgt een paragraafverwijzing. | overdracht §6 |
| U13 | Uitleg is **gelaagd**: eerst de kern in gewone taal, daarna de precieze MIM-formulering met paragraafverwijzing. Zo werkt dezelfde tekst voor alle vier doelgroepen. | B12 |
| U14 | Normatieve en toelichtende tekst zijn herkenbaar onderscheiden (frontmatter `status`). | overdracht §6 |
| U15 | MIM neemt geen semantiek over van UML. MIM-begrippen worden nooit ingevuld met UML-betekenis. | overdracht §7 |
| U16 | Regelt MIM 1.2 iets niet, of staat het niet in de kennisbank, dan meldt de agent dat. Voorkennis mag daarna alleen, expliciet gemarkeerd als niet gebaseerd op de bron. | B17 |

---

## 5. Tegenstrijdigheden in MIM

| # | Uitgangspunt | Besluit |
|---|--------------|---------|
| U17 | Tegenstrijdigheden worden niet stilzwijgend opgelost. Ze worden gemeld en vastgelegd in `bekende-onduidelijkheden.md`, met vindplaats en voorlopige lezing. | projectinstructie |
| U18 | Terugmelden aan MIM-beheer (GitHub-issues of mim@geonovum.nl) valt voorlopig buiten het project. Dat kan later apart worden besloten. | B18 |

---

## 6. Kwaliteit

| # | Uitgangspunt | Besluit |
|---|--------------|---------|
| U19 | Evaluatieset van 35 vragen: 10 feitelijk, 8 onderscheidend, 7 toepassend, 5 valkuilen, 5 versieverschillen. Elke vraag heeft een verwacht antwoord en een MIM-paragraaf. | B13 |
| U20 | Eerst een nulmeting zonder kennisbank, daarna dezelfde vragen met. Doel: minimaal 90 % correct. Daarnaast wordt gekeken of de agent de juiste bestanden opent. | B13 |
| U21 | Omdat uitleggen het primaire gebruik is (U2), toetsen de vragen vooral uitleg. De categorie *toepassend* vraagt om uitleg bij een situatie, niet om het maken van een model. | B13 |
| U22 | Inhoudelijke review door twee ervaren MIM-modelleurs uit de community (stap 9). Wie dat zijn, is nog open. | open punt |

---

## 7. Naam, versie en beheer

| # | Uitgangspunt | Besluit |
|---|--------------|---------|
| U23 | Werknaam `mim-kennis`; versie `mim-kennis 1.0 (MIM 1.2)`. | B15 |
| U24 | Eigenaar is Mats Braster (Geonovum). Hij houdt de kennisbank bij als MIM wijzigt. | B14 |
| U25 | De kennisbank blijft binnen de projectgroep AI-ready geostandaarden. Bredere publicatie is een later besluit. | B16 |
| U26 | MIM valt onder CC BY 4.0. Ook bij intern gebruik krijgt letterlijke MIM-tekst een bronvermelding. | gegeven |

---

## 8. Adviespunt richting Geonovum

| # | Uitgangspunt | Besluit |
|---|--------------|---------|
| U27 | De robots.txt van docs.geostandaarden.nl blokkeert geautomatiseerde toegang. Voor een AI-ready standaard werkt dat tegen. Het traject neemt als adviespunt mee: een `llms.txt` of een expliciet toegestane machineleesbare publicatie. Dit valt buiten de scope van de kennisbank zelf. | B20 |

---

## 9. Open punten

- Wie zijn de twee reviewers uit de MIM-community? Moet rond zijn vóór stap 9.
- Op welke commit van MIM-Werkomgeving wordt gewerkt? De lokale clone staat op master `3990766`; in stap 2 toetsen aan de vastgestelde versie.
