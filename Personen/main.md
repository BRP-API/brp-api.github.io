---
layout: page-with-side-nav
title: BRP API 
---
# Welkom bij de {{ site.apiname }}
## Zoek en raadpleeg persoonsinformatie met de {{ site.apiname }}

De {{ site.apiname }} biedt de mogelijkheid om zoek- en raadpleegfunctionaliteit van persoonsinformatie uit de Basisregistratie Personen (BRP) in te bouwen in taakapplicaties van jouw organisatie. Naast de vertrouwde persoonsgegevens levert {{ site.apiname }} ook informatieproducten:
- Adressering: aanschrijfwijze, aanhef, een verwijzing naar een persoon in de lopende tekst van een brief, en adresregels die altijd passen op een vensterenvelop.
- Gezag (over minderjarige(n), alle gezagshouders en het type gezag)  
- Leeftijd (in jaren)
- Voorletters
- Volledige naam (met adellijke titels en predicaten, zonder gebruik van de naam van de partner)
- Bewoning (wie er samen in een woning woonde gedurende een bepaalde periode, of op een peildatum).

Deze informatieproducten worden voortdurend verbeterd door de RvIG. Door de {{ site.apiname }} te gebruiken innoveert jouw organisatie automatisch mee. Tegelijkertijd hoeft jouw organisatie minder persoonsgegevens te verwerken, omdat de {{ site.apiname }} direct in klantbehoeften voorziet. Daarmee zet je een grote stap vooruit op het gebied van dataminimalisatie en voldoet jouw organisatie je beter aan de AVG. De juridische grondslag voor het bewerken van persoonsgegevens is geregeld in het [Experimentbesluit Dataminimalisatie](https://zoek.officielebekendmakingen.nl/stb-2024-96.html), ter voorbereiding op een stucturele wetswijziging.

## Getting Started
De volgende stappen helpen jou op weg om jouw applicatie van de juiste persoonsinformatie uit de BRP te voorzien:
1. Controleer of jouw organisatie of klant een [autorisatiebesluit](https://publicaties.rvig.nl/Besluiten_en_modelautorisaties/Besluiten/BRP_besluiten) heeft. Aansluiten mag alleen met een autorisatiebesluit.
2. Bedenk welke functie(s) en welke informatieproducten van de {{ site.apiname }} je wilt gebruiken. Hiervoor zal RvIG samen met u een aanvullend autorisatiebesluit opstellen. Voor gemeenten is dit niet nodig.
3. Gebruik de [Getting Started] tutorial om te leren hoe je je eerste API call kunt doen!

## Documentation
De documentatie is alsvolgt opgebouwd:

Concepten, die opheldering geven over alles wat belangrijk is om aan te kunnen sluiten
Tutorials, ter introductie en verduidelijking hoe je de API kunt gebruiken
Tooling, die je sneller op weg kan helpen met het aansluiten op de Personen API met de fields parameter 
De API specificatie

## Planning en Roadmap
De BRP API is live sinds mei 2023 en bestaat uit de onderdelen Personen, [Bewoning]({{ site.pagesBaseUrl }}/Haal-Centraal-BRP-bewoning){:target="_blank" rel="noopener"} en [Reisdocumenten]({{ site.pagesBaseUrl }}/Haal-Centraal-Reisdocumenten-bevragen){:target="_blank" rel="noopener"}. Rond 1 juli 2024 wordt [Verblijfplaatshistorie]({{ site.pagesBaseUrl }}/Haal-Centraal-BRP-historie-bevragen){:target="_blank" rel="noopener"} verwacht, waarmee je verblijfplaatsen van een persoon kunt opvragen op een peildatum of in een bepaalde periode. 

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
