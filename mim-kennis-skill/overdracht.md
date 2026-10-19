# Overdracht: MIM-kennisskill

Dit document legt de keuzes en uitgangspunten vast uit het voorbereidende gesprek over de MIM-skill. Het is bedoeld als startpunt voor alle chats in dit project. Besluiten die later worden genomen en de voortgang per stap staan in het [besluitenlog](https://claude.ai/code/artifact/6a7e5a19-b172-4fc1-893f-e17692ded30a) (Claude Doc).

De versie van dit document in het Claude-project is leidend. De kopie in de lokale projectmap is een afschrift.

Opgesteld: 19 oktober 2026 · Bijgewerkt: 19 oktober 2026

---

## 1. Doel

Het project valt onder het traject AI-ready standaarden en compliance push. Het doel is MIM (Metamodel Informatie Modellering) beter begrijpbaar te maken voor AI, met een Claude-skill.

De eerste versie van de skill is een **kennisbestand**: hij geeft de context van MIM mee aan agents. Hij voert zelf geen taken uit zoals toetsen of transformeren. Die taken doet de agent die de kennis gebruikt.

---

## 2. Genomen besluiten

| # | Besluit | Toelichting |
|---|---------|-------------|
| B1 | De skill wordt opgezet als kennisbestand. | Breed inzetbaar voor verschillende agents. Een deterministische toetslaag kan later worden toegevoegd zonder de kennisbank te wijzigen. |
| B2 | Eén skill, geen opsplitsing per taak. | Uitleggen, modelleren, toetsen en transformeren steunen op dezelfde kennisbasis. Splitsen pas als metingen of beheer daar aanleiding toe geven. |
| B3 | Het werk gebeurt in een Claude-project. | Vaste instructies en gedeelde bronbestanden. Eén chat per stap uit de takenlijst. |

Latere besluiten (B4 en verder) staan in het besluitenlog.

---

## 3. Uitgangspunten en aannames

Punten met status **aanname** zijn gekozen omdat er nog geen besluit was. Ze kunnen worden bijgesteld.

| Onderwerp | Uitgangspunt | Status |
|-----------|--------------|--------|
| MIM-versie | MIM 1.2, vastgestelde versie van 13 juni 2024 | aanname |
| Scope | Alleen de kern. Extensies (Kadaster, NEN3610) in een latere versie | aanname |
| Taal | Nederlands; Engelse termen alleen in de woordenlijst | aanname |
| Werknaam | `mim-kennis` | aanname |
| Versienummer | mim-kennis 1.0 (MIM 1.2) | aanname |
| Evaluatieset | 35 vragen, doel minimaal 90 % correct met de skill | aanname |
| Review | Door twee ervaren MIM-modelleurs uit de community | aanname |
| Licentie | MIM valt onder CC BY 4.0; letterlijke tekst krijgt bronvermelding | gegeven |

---

## 4. Bronnen

**Primaire bron:** de repository [Geonovum/MIM-Werkomgeving](https://github.com/Geonovum/MIM-Werkomgeving) op GitHub. De commit waarop de kennisbank gebaseerd wordt, moet nog worden vastgelegd.

Te gebruiken bestanden:

- `Inleiding.md`
- `MetamodelAlgemeen.md`
- `AfsprakenRegels.md`
- `MetamodelUML.md`
- `MetamodelLD.md`
- `TransformatieRDF.md`
- `Versielog.md`
- `media/mim.ttl` (RDF-vocabulaire)
- `media/mim-shapes.ttl` (SHACL-shapes)

**Gepubliceerde versie:** <https://docs.geostandaarden.nl/mim/def-st-mim-20240613>. De algemene link <https://docs.geostandaarden.nl/mim/mim/> verwijst naar de laatst gepubliceerde versie.

**Opmerking:** de robots.txt van docs.geostandaarden.nl blokkeert geautomatiseerde toegang. Voor een AI-ready standaard werkt dat tegen. Een `llms.txt` of een expliciet toegestane machineleesbare publicatie is een mogelijk adviespunt richting Geonovum.

---

## 5. Kern van MIM in het kort

- MIM is een metamodel: de modelleertaal waarin informatiemodellen worden uitgedrukt.
- Er zijn vier beschouwingsniveaus: begrippen (1), conceptueel informatiemodel (2), logisch informatiemodel (3) en fysiek/technisch model (4). MIM richt zich alleen op niveau 2 en 3.
- Een model is altijd óf conceptueel óf logisch, nooit een mix.
- Kernelementen: Objecttype, Attribuutsoort, Gegevensgroep, Gegevensgroeptype, Generalisatie, Relatiesoort, Relatieklasse, Relatierol, Datatype.
- Datatypen: Primitief, Gestructureerd (met Data-elementen), Enumeratie, Referentielijst, Codelijst.
- Overige elementen: Constraint, Keuze (vijf use cases), Externe koppeling, en de packages Informatiemodel, Domein, Extern en View.
- Uitgangspunt van MIM: uitbreiden mag, afwijken niet. Eigen behoeften regel je via een extensie.
- Datatypen dragen geen semantiek: als je ze weglaat, mag er geen betekenis verloren gaan.
- MIM neemt geen semantiek over van UML. UML is alleen een uitdrukkingsvorm.
- MIM kent één bewuste modelleerkeuze: relatiesoort leidend of relatierol leidend.

---

## 6. Beoogde structuur van de skill

De kennisbank wordt opgebouwd in de map `mim-kennis/` in de lokale projectmap, naast `MIM-Werkomgeving/` (besluit B5).

```
mim-kennis/
├── SKILL.md                    wat MIM is, index, leesregels, grondregels
├── modelelementen/             één bestand per MIM-metaclass (circa 25)
├── metagegevens.md             matrix: per element verplicht/optioneel/default
├── onderwerpen/
│   ├── beschouwingsniveaus.md
│   ├── historie.md
│   ├── keuze.md
│   ├── waardelijsten.md
│   ├── naamgeving.md
│   └── extensies.md
├── onderscheidingen/
│   ├── gegevensgroep-vs-gestructureerd-datatype.md
│   ├── enumeratie-vs-referentielijst-vs-codelijst.md
│   └── relatieklasse-vs-objecttype.md
├── uitdrukkingen/
│   ├── uml.md
│   └── linked-data.md
├── versies.md                  verschillen 1.1.1 → 1.2
├── bekende-onduidelijkheden.md
└── woordenlijst.md             synoniemen, Engelse termen, afkortingen
```

### Vaste opbouw van een modelelementbestand

1. Definitie, letterlijk uit MIM 1.2, met paragraafnummer
2. Toelichting in gewone taal
3. UML-stereotype en LD-klasse
4. Toegestane metagegevens en bindingen met andere elementen
5. Voorbeeld en tegenvoorbeeld
6. Elementen waarmee het vaak verward wordt

### Frontmatter per bestand

`id`, `metaclass`, `bron` (paragraaf), `mim-versie`, `status` (normatief of toelichtend).

### Schrijfregel

Letterlijke MIM-tekst en eigen uitleg staan altijd gescheiden. Zo ziet een agent wat de standaard zegt en wat interpretatie is.

---

## 7. Grondregels voor SKILL.md

- Deze bron gaat boven de eigen voorkennis van het model.
- De inhoud geldt voor MIM 1.2.
- Er is onderscheid tussen normatieve en toelichtende tekst.
- MIM neemt geen semantiek over van UML; vul MIM-begrippen nooit in met UML-betekenis.
- De description triggert expliciet op MIM-termen, zoals MIM, informatiemodel, objecttype, attribuutsoort, metagegeven, stereotype, conceptueel/logisch, Geonovum en Imvertor.
- SKILL.md blijft ruim onder de 500 regels.

---

## 8. Bekende inconsistenties in MIM 1.2

Deze punten zijn tijdens de verkenning gevonden. De voorlopige lezing is een voorstel en moet in stap 6 van de takenlijst worden bevestigd.

| # | Inconsistentie | Vindplaats | Voorlopige lezing |
|---|----------------|-----------|-------------------|
| I1 | De definitie zegt dat een gegevensgroeptype relatiesoorten kan bevatten; de richtlijn zegt dat het alleen attribuutsoorten bevat. | §2.3.2.4 vs. §5.2 | Richtlijn uit §5.2 volgen en de tegenstrijdigheid melden |
| I2 | De toelichting bij Authentiek noemt "Gemeentelijk kerngegeven"; de waardebereiktabel noemt in plaats daarvan "Wettelijk gegeven". | §2.4.3.16 vs. §2.4.5.1 | Nog te bepalen |
| I3 | Aggregatietype wordt volgens de toelichting "gemodelleerd met een Attribuutsoort", maar de toepassing is Relatiesoort en Externe koppeling. | §2.4.3.23 | Nog te bepalen |
| I4 | Het stereotype heet «Gestructuurd datatype» en de RDF-klasse `mim:GestructuurdDatatype`; de tekst spreekt over "Gestructureerd datatype". | §3.1.2, §4.2.2 | Nog te bepalen |
| I5 | De koppeling tussen een MIM-instantie en een RDF-klasse gebruikt in de inleiding `rdfs:seeAlso`, in het LD-hoofdstuk en de transformatiebijlage `mim:equivalent`. | §1.9.3 vs. §4.1 | Nog te bepalen |

Deze lijst is ook bedoeld als terugkoppeling naar MIM-beheer bij Geonovum (GitHub-issues of mim@geonovum.nl).

---

## 9. Evaluatieset

- 35 vragen, elk met verwacht antwoord en MIM-paragraaf.
- Verdeling: 10 feitelijk, 8 onderscheidend, 7 toepassend, 5 valkuilen, 5 versieverschillen.
- Eerst een nulmeting zonder skill, daarna dezelfde vragen met skill.
- Naast correctheid ook nagaan of de agent de juiste bestanden opent.

---

## 10. Takenlijst

De voortgang per stap wordt alleen bijgehouden in het [besluitenlog](https://claude.ai/code/artifact/6a7e5a19-b172-4fc1-893f-e17692ded30a), sectie Voortgang (besluit B7). De [interactieve checklist](https://claude.ai/artifact/S8h1v6r3s5Tdgw6XKZh8hm) is een persoonlijk hulpmiddel: de vinkjes blijven alleen in de eigen browser bewaard en zijn niet leidend.

Stap 5 is gesplitst in vijf deelstappen, elk in een eigen chat (besluit B6).

| Stap | Taak | Oplevering |
|------|------|-----------|
| 1 | Uitgangspunten vastleggen | `uitgangspunten.md` |
| 2 | Bronmateriaal veiligstellen | map `bron/` met `BRON.md` |
| 3 | Evaluatievragen en nulmeting | `evaluatie/vragen.yaml`, `nulmeting.md` |
| 4 | Structuur en sjablonen bepalen | `sjablonen/`, `schrijfwijzer.md` |
| 5a | Modelelementen schrijven (circa 25 bestanden) | `modelelementen/` |
| 5b | Metagegevensmatrix opstellen | `metagegevens.md` |
| 5c | Onderscheidingen schrijven | `onderscheidingen/` |
| 5d | Onderwerpen schrijven | `onderwerpen/` |
| 5e | Uitdrukkingen, versieoverzicht en woordenlijst | `uitdrukkingen/`, `versies.md`, `woordenlijst.md` |
| 6 | Inconsistenties inventariseren | `bekende-onduidelijkheden.md` |
| 7 | SKILL.md schrijven | `SKILL.md` |
| 8 | Testen en bijsturen | `testrapport.md` |
| 9 | Inhoudelijke review | reviewverslag |
| 10 | Verpakken en beheer inrichten | `mim-kennis.skill`, beheerafspraken |

---

## 11. Open punten

De actuele stand van de open punten staat in het besluitenlog. Hieronder de punten uit de voorbereiding.

- Wie wordt eigenaar van de skill en houdt hem bij als MIM wijzigt?
- Op welke commit van MIM-Werkomgeving wordt de kennisbank gebaseerd?
- Wie zijn de twee reviewers uit de MIM-community?
- Moet de kennis alleen naar Claude-agents, of ook naar agents op andere platforms? In dat laatste geval is de kennisbank zelf het product en is de skill één verpakking ervan.

---

## 12. Mogelijke uitbreidingen na versie 1

- Deterministische toetslaag: SHACL-validatie tegen `mim-shapes.ttl`.
- Genummerde regelset met MOET/MAG/AANBEVOLEN en bronverwijzing per regel.
- Transformatiescripts (UML/XMI naar MIM-RDF, MIM naar RDFS/OWL/SHACL).
- Extensies als aparte referentiebestanden boven op de kern.
- Andere verpakkingen van dezelfde kennisbank, zoals gepubliceerde markdown of een MCP-server.
