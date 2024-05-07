---
layout: page-with-side-nav
title: BRP API 
---
# Welkom bij de {{ site.apiname }}
Breng jouw dienstverlening verder met de actuele informatieproducten van de BRP API.

Ben je afnemer van De BRP? Dan biedt deze API jou de mogelijkheid om informatieproducten in te bouwen in de taalapplicaties van jouw organisatie. Deze informatieproducten worden doorlopend door RvIG verbeterd en geactualiseerd. Dat hoef jij dus niet te doen. Omdat jouw taakapplicatie minder gegevens hoeft te verwerken, zet jouw organisatie tegelijkertijd ook een stap op het gebied van dataminimalisatie.

De {{ site.apiname }} biedt naast persoonsgegevens uit de BRP de volgende informatieproducten:
- Adressering: aanschrijfwijze, aanhef, een verwijzing naar een persoon die je in de lopende tekst van een brief kunt gebruiken en adresregels die altijd passen op een vensterenvelop.
- Gezag (over welke minderjarige(n) heeft de persoon het gezag, wie is de eventuele andere gezagshouder, en wie zijn de gezaghouder(s) van een minderjarig persoon)
- Leeftijd (in jaren)
- Voorletters
- Volledige Naam (met adellijke titels en predicaten, zonder gebruik van de naam van de partner)
- Bewoning (wie er samen in een woning woonde gedurende een bepaalde periode, of op een peildatum).

De BRP API voorziet direct in klantbehoeften, waardoor jouw organisatie minder persoonsgegevens hoeft te verwerken. De juridische grondslag hiervoor is het [Experimentbesluit Dataminimalisatie](https://zoek.officielebekendmakingen.nl/stb-2024-96.html), ter voorbereiding op een stucturele wetswijziging.

## Planning en Roadmap
De BRP API is live sinds mei 2023 en bestaat uit de onderdelen Personen, [Bewoning]({{ site.pagesBaseUrl }}/Haal-Centraal-BRP-bewoning){:target="_blank" rel="noopener"} en [Reisdocumenten]({{ site.pagesBaseUrl }}/Haal-Centraal-Reisdocumenten-bevragen){:target="_blank" rel="noopener"}. Rond 1 juli 2024 wordt [Verblijfplaatshistorie]({{ site.pagesBaseUrl }}/Haal-Centraal-BRP-historie-bevragen){:target="_blank" rel="noopener"} verwacht, waarmee je verblijfplaatsen van een persoon kunt opvragen op een peildatum of in een bepaalde periode. 

## Aansluiten en voorwaarden
Afnemers van de BRP met een autorisatiebesluit mogen de BRP API gebruiken. Iedere deelnemer sluit een convenant met RvIG. Voor de technische aansluiting is een API Gateway nodig. Aansluiten kan via Diginetwerk met gebruik van een TLS verbinding (PKIO certificaat) en een OAuth 2.0 token (OAuth 2.0 client credentials flow).

Stuur een mail naar [info@RvIG](mailto:info@rvig) voor een kennismakingmakingsgesprek en onboarding. [Download]({{ site.onboardingUrl }}){:target="_blank" rel="noopener"} en lees het onboardingproces.

## Contact
* Heb je een vraag? Neem contact op met de Product Owner [{{ site.PO-naam }}], [{{ site.PO-email }}](mailto:{{ site.PO-email }}) 
* Bug Melden
  [Maak een bug issue aan >>](https://github.com/BRP-API/Haal-Centraal-BRP-bevragen/issues/new?assignees=&labels=bug&template=bug_report.md&title=)
* Verbeteringen doorgeven
  [Maak een verbeter issue aan >>](https://github.com/BRP-API/Haal-Centraal-BRP-bevragen/issues/new?assignees=&labels=enhancement&template=enhancement.md&title=)

* Product Owner: Cathy Dingemanse, [{{ site.PO-email }}](mailto:{{ site.PO-email }})
* Developer en customer zero: Melvin Lee, [{{ site.CZ-email }}](mailto:{{ site.CZ-email }})
* Tester: Frank Samwel, [{{ site.Tester-email }}](mailto:{{ site.Tester-email }})

## Licentie
Copyright &copy; RvIG 2024
Licensed under the [EUPL]({{ masterBranchUrl }}/LICENCE.md){:target="_blank" rel="noopener"}
