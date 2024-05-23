## Probeer en test de API in de proefomgeving

Je kunt de {{ site.apiname }} uitproberen op de proefomgeving met de volgende url: [{{ site.proefProxyUrl }}]. 

### Prerequisites
Je bent in het bezit van een apikey. Deze kun je aanvragen bij de product owner [{{ site.PO-email }}](mailto:{{ site.PO-email }}). 

### Uitproberen
Voeg de apikey toe aan een request met de __X-API-KEY__ header.

## Probeer en test de API lokaal

Van de {{ site.apiname }} Personen is een mock beschikbaar als een containerized applicatie. Deze kun je gemakkelijk hosten op een lokale machine of in een testomgeving. Het voordeel van deze oplossing ten opzichte van de proefomgeving is dat je je eigen testgevallen kunt toevoegen aan het JSON bestand. 
Standaard maakt de {{ site.apiname }} Personen mock gebruik van de [testdataset persoonslijsten proefomgevingen GBA-V](https://www.rvig.nl/media/288) als input om de productie situatie zo goed mogelijk te simuleren.

Je kunt het [docker compose bestand]({{ site.mainBranchUrl }}/docker-compose-mock.yml){:target="_blank" rel="noopener"} gebruiken om de {{ site.apiname }} Personen mock met behulp van [Docker Desktop](https://www.docker.com/products/docker-desktop) te draaien op een lokale machine.

Je kunt er ook voor kiezen om de [Kubernetes configuratie bestanden]({{ site.devBranchUrl}}/.k8s){:target="_blank" rel="noopener"} gebruiken om de {{ site.apiname }} Personen mock te draaien op een lokale machine. 

De volgende paragrafen beschrijven wat je moet doen om de {{ site.apiname }} Personen mock op een lokale machine te installeren en aan te roepen.

### Prerequisites

- [Docker Desktop](https://www.docker.com/products/docker-desktop) voor het hosten van containers
- Zet Kubernetes ondersteuning aan in Docker Desktop in het Settings/Kubernetes configuratie scherm ![Enable Kubernetes](../img/docker-desktop-enable-k8s.png)
om Docker Desktop te gebruiken om de containers te hosten met behulp van de Kubernetes engine. 

Optioneel kun je de volgende tools ook op de lokale machine installeren:

- [git](https://git-scm.com/downloads) voor het clonen van git repositories
- [Postman](https://www.postman.com/downloads/) voor het aanroepen van {{ site.apiname }}


### Gebruik Docker als container engine

- Download het [docker compose bestand]({{ site.mainBranchUrl }}/docker-compose.yml){:target="_blank" rel="noopener"}
- Start een command prompt window voor de map met het docker-compose.yaml bestand
- Start de {{ site.apiname }} Personen mock met behulp van de volgende statement:
  ```sh

  docker-compose -f docker-compose-mock.yml up -d

  ```
  De {{ site.apiname }} Personen mock is nu te benaderen via de url: *http://localhost:5001/haalcentraal/api/brp/personen*
- Valideer dat de {{ site.apiname }} mock draait met behulp van de volgende curl statement:
  ```sh

  curl --location --request POST 'http://localhost:5001/haalcentraal/api/brp/personen' \
  --header 'Content-Type: application/json' \
  --data-raw '{
      "type": "RaadpleegMetBurgerservicenummer",
      "burgerservicenummer": ["999993653"],
      "fields": ["burgerservicenummer"]
  }'

  ```
- Om de {{ site.apiname }} Personen mock container te stoppen voer je de volgende statement uit:
  ```sh

  docker-compose -f docker-compose-mock.yml down

  ```

### Gebruik Kubernetes als container engine

- Download de [kubernetes configuratie bestanden]({{ site.devBranchUrl }}/.k8s){:target="_blank" rel="noopener"}
- Start een command prompt window voor de map met de kubernetes manifest bestanden
- Start de {{ site.apiname }} en de mock met behulp van de volgende statement:
  ```sh

  kubectl apply -f .k8s/brppersonenmock-deployment.yaml \
                -f .k8s/brppersonenmock-service.yaml 

  ```
  De {{ site.apiname }} Personen mock is nu te benaderen via de url: *http://localhost:5001/haalcentraal/api/brp/personen*
- Valideer dat de {{ site.apiname }} Personen mock draait met behulp van de volgende curl statement:
  ```sh

  curl --location --request POST 'http://localhost:5001/haalcentraal/api/brp/personen' \
  --header 'Content-Type: application/json' \
  --data-raw '{
      "type": "RaadpleegMetBurgerservicenummer",
      "burgerservicenummer": ["999993653"],
      "fields": ["burgerservicenummer"]
  }'

  ```
- Om de {{ site.apiname }} Personen mock container te stoppen voer je de volgende statement uit:
  ```sh

  kubectl delete -f .k8s/brppersonenmock-deployment.yaml \
                 -f .k8s/brppersonenmock-service.yaml 

  ```
