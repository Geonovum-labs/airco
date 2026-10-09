# AI Ready Standaarden & CompliancePush

Geonovum, het Kadaster, ModelDesk B.V. en het ministerie van BZK, Directie Digitale Overheid werken samen aan het [innovatiebudget-project](https://www.digitaleoverheid.nl/overzicht-van-alle-onderwerpen/innovatie/innovatiebudget/toekenning-innovatiebudget-2026/) AI Ready Standaarden & CompliancePush. Met dit project verbeteren we de implementatie en verhogen we de adoptie van overheidsstandaarden. Dit doen we door:

1. deze standaarden geschikt te maken voor AI-consumptie, zodat voldoen aan overheidsstandaarden structureel onderdeel kan worden van AI-ondersteunde softwareontwikkeling;
2. een systeem te introduceren voor het automatisch bijhouden van software bij wijzigingen in standaarden.

We introduceren een AI readiness assessment kader en maken voor een aantal pilotstandaarden verschillende AI-hulpmiddelen. We toetsen in hoeverre dit AI-modellen helpt om standaarden correct te gebruiken. Ook bouwen we het CompliancePush-systeem voor de proactieve doorvoering in software van wijzigingen in standaarden.

## In deze repository

- Het [rapport met onze bevindingen](https://geonovum-labs.github.io/airco) (werkversie)
- Presentaties in de map [`slides/`](slides/)
- Het [projectbord met issues](https://github.com/orgs/Geonovum-labs/projects/3)
- In de toekomst: verwijzingen naar andere repositories waarin aan specifieke deliverables uit dit project gewerkt wordt

## Meedoen

Er is een werkgroep in oprichting voor beheerders van standaarden en ontwikkelaars van software die standaarden implementeert. Ook organiseren we open sprint reviews waar je je bij kunt aansluiten. Neem contact op met Linda van den Brink (Geonovum) voor meer informatie.

## Werken aan het rapport

Het rapport is een [ReSpec](https://respec.org/)-document, opgezet vanuit de [NL-ReSpec-template](https://github.com/Geonovum/NL-ReSpec-template) van Geonovum.

- Documentinstellingen (titel, status, editors, lokale bibliografie) staan in [`js/config.js`](js/config.js). De organisatiebrede instellingen komen uit de [Geonovum-config](https://tools.geostandaarden.nl/respec/config/geonovum-config.js).
- De inhoud staat per hoofdstuk in een markdownbestand in de root (`abstract.md`, `ch01.md`, ...).
- Hoofdstukken worden in [`index.html`](index.html) opgenomen met `data-include`:

  ```html
  <section
    data-include-format="markdown"
    data-include="ch01.md"
    class="informative"
  ></section>
  <section data-include-format="markdown" data-include="ch02.md"></section>
  ```

- Mermaid-diagrammen in markdown worden ondersteund, zie `mermaid.md`.
- Lokaal bekijken: start een HTTP-server in de root (bijvoorbeeld `python3 -m http.server`) en open `index.html` in de browser.

Zie de [Geonovum ReSpec handleiding](https://geonovum.github.io/handleiding-tooling/ReSpec/) en de [ReSpec documentatie](https://respec.org/docs/) voor meer mogelijkheden.

## Controles en publicatie

Bij iedere commit draait de `Main Workflow` (GitHub Actions). Die genereert `snapshot.html`, voert HTML-validatie, een WCAG-check en een linkcheck uit, en commit de snapshot terug. Bewerk `snapshot.html` niet handmatig. De samenvatting van de workflow toont of het document publicatiegereed is.

Publiceren gaat via GitHub Releases:

- **Pre-release** (vink "This is a pre-release" aan): publicatie op de testomgeving <https://test.docs.geostandaarden.nl/>
- **Release**: er wordt automatisch een pull request aangemaakt naar [Geonovum/docs.geostandaarden.nl](https://github.com/Geonovum/docs.geostandaarden.nl/pulls). Na goedkeuring staat het document op <https://docs.geostandaarden.nl/>

Controleer vóór een release dat de job `Snapshot + Checks` van de betreffende commit groen is en "Publicatiegereed: ja" toont.

## Licentie

Zie [LICENSE](LICENSE).
