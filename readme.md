# Azure Pipelines - pullrequest ARM validation

Bij een klant wordt er een pullrequest validatie gedaan op ARM templates. Dit is op syntactisch-niveau, dus verkeerde naamgeving, verkeerde format van IP-addressen, e.d. worden
gezien als een fout waardoor de pullrequest niet verder kan tot het opgelost is.

Situatie bij de klant:

Er is een generieke repository waar alle ARM templates in staan. Naast de generieke repository zijn er workloads, dit zijn "*spokes*".
In de workloads wordt de generieke repository aangeroepen, zodat er gebruik gemaakt kan worden van de generieke templates. Zie de [example](pullrequest/arm-validation/v1.0/example/validation.example.yml) op regels 13, 20, 25, 30 en 35.

Het [generieke template](pullrequest/arm-validation/v1.0/pipelines/validation.yml) verwacht input parameters en het type input is *object*. Dit object moet de volgende properties bevatten:
* name
* resourceGroup
* subscription
* templateFile
* parameterFile

In het generieke template wordt het object gebruikt om een N aantal jobs aan te maken die parallel draaien. De validatie wordt uiteindelijk gedaan door Azure CLI commando *az deployment group validate*.
Stel verder een *build validation* in zodat de validatie af gaat tijdens een pullrequest.

Resultaat:

![image](https://user-images.githubusercontent.com/3514513/128508696-b6c4ef8e-78e5-47b3-8b52-980daf9c78d1.png)
