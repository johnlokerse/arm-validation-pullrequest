# Introductie

Voor het valideren van ARM templates is er een generieke YAML template opgenomen in deze repository. Door parameters vanuit de workloads te  injecteren in het generieke component kan je de ARM templates valideren.

## Benodigde parameters/variables

Array variablen:
* name: naam van de job. 
* resourceGroup: de resource group waar de resources moeten komen te staan. 
* subscription: de naam van de subscription
* templateFile: de locatie van de template. Dit template zit in de generic repo. 
* parameterFile: de locatie van de parameter file. Dit parameter file zit in de repo van de workload.

## Voorbeeld

In de generieke repository staat een voorbeeld: [voorbeeld validatie pipeline](../example/validation.example.yml)