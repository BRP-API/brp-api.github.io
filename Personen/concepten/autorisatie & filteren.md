## Dataminimalisatie

Ieder request aan de BRP API Personenbbevat verplicht een fields parameter waarmee je aangeeft welke velden van de gevonden persoon of personen geleverd moeten worden. Om de privacy van de gevraagde personen te beschermen mag je uitsluitend die gegevens vragen waarvoor jouw organisatie doelbinding heeft/ geautoriseerd is *en wat op dat moment in het proces nodig is* voor de uit te voeren taak. 

## Filteren van de velden van de gevonden personen

Je vraagt een veld door het volledige pad van het veld op te geven in de fields parameter. Het volledige pad van een veld is de samenvoeging van de naam van het veld en de namen van zijn 'ouder' velden met een '.' karakter tussen de veld namen. Voorbeelden van volledige paden zijn:

- geboorte.datum (volledig pad van het geboortedatum veld van een persoon)
- kinderen.naam.voornamen (volledig pad van het voornamen veld van de kinderen van een persoon)

Zie de [fields](./features/fields.feature) en de [fields fout cases](./features/fields-fout-cases.feature) feature bestanden voor meer informatie en voorbeelden van het gebruik van veldpaden en de fields parameter. 

Het [fields-filtered-PersoonBeperkt.csv]({{ site.persoonBeperktFieldsCsvUrl }}){:target="_blank" rel="noopener"} bestand bevat een overzicht van de toegestane fields waarden voor de Zoek personen operaties. Voor de Raadpleeg persoon operatie kun je dit overzicht vinden in het [fields-filtered-Persoon.csv]({{ site.persoonFieldsCsvUrl }}){:target="_blank" rel="noopener"} bestand.

Snel en foutloos fields samenstellen voor de BRP API Personen? Gebruik de [fields tool](./fields){:target="_blank" rel="noopener"}.

### Filteren van datum en waardetabel velden

De {{ site.apiname }} API kent de volgende datum types:

- VolledigeDatum
- DatumOnbekend
- JaarDatum
- JaarMaandDatum

en de volgende waardetabel types:

- Waardetabel
- AdellijkeTitelPredicaatType

Bij het vragen van één of meerdere velden van deze types worden altijd alle velden van het gevraagde type geleverd. In het [fields](./features/fields.feature) feature bestand vind je voorbeelden hiervan onder de volgende rules:

- [Regel: Het vragen van één of meerdere velden van een 'waardetabel' veld levert alle velden van de 'waardetabel' veld](./features/fields.feature#rule-het-vragen-van-één-of-meerdere-velden-van-een-waardetabel-veld-levert-alle-velden-van-de-waardetabel-veld)
- [Regel: Het vragen van één of meerdere velden van een 'datum' veld levert alle velden van de 'datum' veld](./features/fields.feature#rule-het-vragen-van-één-of-meerdere-velden-van-een-datum-veld-levert-alle-velden-van-de-datum-veld)

### Standaard geleverde velden

Als onderstaande velden van toepassing zijn worden ze automatisch geleverd:

- geheimhoudingPersoonsgegevens
- inOnderzoek
- opschortingBijhouding
- rni
- verificatie
- indicatieVastgesteldVerblijftNietOpAdres

Automatisch geleverde velden mag je NIET vragen met de fields parameter.

### Filteren van verblijfplaats velden

Er zijn twee autorisatieprofielen voor verblijfplaats:

- geautoriseerd voor zowel verblijfplaats binnenland (Adres en Locatie) en verblijfplaats buitenland gegevens
- geautoriseerd voor alleen verblijfplaats binnenland (Adres en Locatie) gegevens

Als jouw organisatie of applicatie uitsluitend geautoriseerd is voor verblijfplaats binnenland gegevens kun je de standaard veldpaden van verblijfplaats niet gebruiken. Met deze veldpaden vraag je namelijk zowel verblijfplaats binnenland als verblijfplaats buitenland velden op. In plaats daarvan moet je de __verblijfplaatsBinnenland__ fields alias gebruiken. Daarmee geef je aan dat je uitsluitend verblijfplaats binnenland gegevens vraagt.

Meer informatie over het gebruik van de __verblijfplaatsBinnenland__ fields alias vind je in de featurebeschrijving van:

- [verblijfplaats fields alias](./features/persoon/verblijfplaats/fields-alias.feature)
- [verblijfplaats fields alias fout cases](./features/persoon/verblijfplaats/fields-alias-fout-cases.feature)

### Filteren van adresregels velden

De adresregelvelden van een persoon worden samengesteld uit de verblijfplaatsvelden van een persoon. Om de adresregelvelden te kunnen vragen moet jouw organisatie of applicatie minimaal geautoriseerd zijn voor de verblijfplaatsvelden waarmee de adresregelvelden worden samengesteld.

De twee autorisatieprofielen van verblijfplaats gelden ook voor het vragen van adresregelvelden. Als jouw organisatie of applicatie niet geautoriseerd is voor het vragen van adresregels van een verblijfplaats buitenland moet je de __adresseringBinnenland__ fields alias gebruiken om aan te geven dat je uitsluitend  binnenlandse adresregels vraagt.

Meer informatie over het gebruik van de __adresseringBinnenland__ fields alias vind je in de featurebeschrijving van:

- [adresregels fields alias](./features/persoon/adressering/adres-regels/fields-alias.feature)
- [adresregels fields alias fout cases](./features/persoon/adressering/adres-regels/fields-alias-fout-cases.feature)

### Filteren van partner velden

Als je partners van een persoon vraagt worden de gevraagde gegevens van actuele partners (= niet ontbonden huwelijk/geregistreerd partnerschap) geleverd. Heeft de persoon alleen ontbonden huwelijk/geregistreerd partnerschappen, dan worden alleen de gevraagde gegevens van het meest recente ontbonden huwelijk/geregistreerd partnerschap geleverd. Meer informatie vind je in de featurebeschrijving van [partnervelden vragen met fields](./features/persoon/partner/overzicht.feature) 

### Filteren van nationaliteitvelden

De {{ site.apiname }} API Personen kent de volgende nationaliteit types:

- Nationaliteit
- Staatloos
- BehandeldAlsNederlander
- VastgesteldNietNederlander
- Onbekend

en levert uitsluitend gegevens van actuele (= niet beëindigde) nationaliteiten. Meer informatie vind je de featurebeschrijving van [nationaliteitvelden vragen met fields](./features/persoon/nationaliteit/overzicht.feature) 


### Filteren van verblijfstitelvelden

Wanneer velden van de verblijfstitel wordt gevraagd, dan worden de gevraagde gegevens geleverd als de verblijfstitel niet is beëindigd. Gegevens van een verblijfstitel worden ook niet geleverd als de aanduiding gelijk is aan 'geen verblijfstitel (meer)'. Meer informatie vind je in de featurebeschrijving van [verblijfstitelvelden vragen met fields](./features/persoon/verblijfstitel/overzicht.feature)

## Eén of meer gevraagde velden zijn in onderzoek

Om een afnemer te informeren dat één of meer gevraagde velden in onderzoek zijn, worden de bijbehorende inOnderzoek en datumIngangOnderzoek velden ook geleverd.
Wanneer één of meer velden waaruit een andere veld wordt afgeleid (bijv. de adressering velden) in onderzoek zijn, dan is het afgeleide veld ook in onderzoek en wordt het inOnderzoekveld van het afgeleide veld ook geleverd. Meer informatie vind je in de featurebeschrijving van [in onderzoek](./features/in-onderzoek.feature) 

### Vastgesteld verblijft niet op adres

Als je verblijfplaatsgegevens of adresregels vraagt van een persoon waarvan na onderzoek is vastgesteld dat deze niet meer verblijft op het geregistreerde adres, wordt het **indicatieVastgesteldVerblijftNietOpAdres** veld met waarde true meegeleverd.

Meer informatie over **indicatieVastgesteldVerblijftNietOpAdres** vind je in de featurebeschrijving van:
- [vastgesteld verblijft niet op adres (verblijfplaats binnenland)](./features/persoon/verblijfplaats/adres/vastgesteld-verblijft-niet-op-adres.feature)
- [vastgesteld verblijft niet op adres (locatie)](./features/persoon/verblijfplaats/locatie/vastgesteld-verblijft-niet-op-adres.feature)
- [vastgesteld verblijft niet op adres (adresregels vragen bij personen raadplegen)](./features/persoon/adressering/adres-regels/vastgesteld-verblijft-niet-op-adres.feature)
- [vastgesteld verblijft niet op adres (adresregels vragen bij personen zoeken)](./features/persoon-beperkt/adressering/adres-regels/vastgesteld-verblijft-niet-op-adres.feature)

## Geen/null/false waarde, leeg object waarde en standaard waarde

Om de payload van een response klein te houden, is besloten om velden met de volgende waarden niet te leveren in de response:

- niet gevraagde velden. Deze velden hebben _null_ als waarde.
- gevraagde velden die de gevraagde persoon niet heeft. Deze velden hebben _null_ als waarde. Voorbeeld: je vraagt het naam.voorvoegsel veld van een persoon die geen voorvoegsel in zijn naam heeft.
- gevraagde velden hebben de _false_ waarde. Voorbeeld: je vraagt het indicatieCurateleRegister veld van een persoon die niet onder curatele is gesteld.
- gevraagde velden is een groep velden die de persoon niet heeft. Voorbeeld: je vraagt de verblijfstitel velden van een persoon die geen verblijfstitel heeft
- gevraagde velden heeft de __standaard__ waarde. In de BRP wordt de standaard waarde gebruikt om aan te geven dat een gegeven onbekend is. Voorbeeld: je vraagt het geboorte.plaats veld van een persoon van wie de geboorteplaats onbekend is
- gevraagde velden hebben geen aanduiding "in onderzoek".

