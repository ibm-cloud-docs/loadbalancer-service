---

copyright:
  years: 2018
lastupdated: "2018-11-21"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Traitement des incidents liés à des messages d'erreur
{: #error-message-troubleshooting}

Cette rubrique fournit des informations sur les messages d'erreur courants liés à la création/mise à jour d'une instance de l'équilibreur de charge IBM© Cloud. 

| Erreur | Explication  | Solution  |
| ------------- | ------------- | ----- |
| `Le nombre maximal d'équilibreurs de charge, `n`, est atteint.`| Nous n'autorisons que 50 instances d'équilibreur de charge par compte. | Assurez-vous que vous n'avez pas plus de 50 instances d'équilibreur de charge par compte. |
| `Le nombre maximal de protocoles spécifiés, `n`, dans la commande du produit d'équilibrage de charge est atteint.` | Seuls deux protocoles peuvent être ajoutés lors de la mise à disposition d'un équilibreur de charge.  | Si vous avez besoin de davantage de protocoles, une fois la mise à disposition effectuée, vous pouvez en ajouter jusqu'à 10 à partir de l'onglet **Protocoles** dans le flux de gestion des équilibreurs de charge. Pour plus d'informations, voir [Surveillance et gestion de votre service](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-monitoring-and-managing-your-service). |
| `Le nombre maximal d'instances de serveur spécifiées, `n`, dans la commande du produit d'équilibrage de charge est atteint.` | Seuls dix serveurs peuvent être ajoutés lors de la mise à disposition d'un équilibreur de charge. | Si vous avez besoin de davantage de serveurs, une fois la mise à disposition effectuée, vous pouvez en ajouter jusqu'à 50 à partir de l'onglet **Instances de serveur** dans le flux de gestion des équilibreurs de charge. Pour plus d'informations, voir [Surveillance et gestion de votre service](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-monitoring-and-managing-your-service). |
| `Le nom d'équilibreur de charge doit être une chaîne comprise entre 1 et 40 caractères.` | Le nom d'équilibreur de charge est obligatoire. Utilisez uniquement des caractères alphanumériques (ou les caractères spéciaux '-' et '.') pour le nom. Celui-ci ne doit pas non plus commencer ou se terminer par un caractère spécial, ni dépasser 40 caractères. | Entrez un nom d'équilibreur de charge unique. Par exemple, "ui-servers" ou "backend-servers".|
| `Erreur de format détectée dans le nom d'équilibreur de charge spécifié.` | Le nom d'équilibreur de charge est obligatoire. Utilisez uniquement des caractères alphanumériques (ou les caractères spéciaux '-' et '.') pour le nom. Celui-ci ne doit pas non plus commencer ou se terminer par un caractère spécial, ni dépasser 40 caractères. | Entrez un nom d'équilibreur de charge unique. Par exemple, "ui-servers" ou "backend-servers".|
| `Un équilibreur de charge portant le même nom (insensible à la casse) existe déjà.` | Un équilibreur de charge portant le même nom existe déjà. | Entrez un nom d'équilibreur de charge unique pour continuer, par exemple, "ui-servers" ou "backend-servers". |
| `La description d'équilibreur de charge doit être une chaîne et ne doit pas excéder 255 caractères.` | La description d'équilibreur de charge doit être une chaîne qui n'excède pas 255 caractères. | Limitez la description à 255 caractères. |
| `Le port de front end 80 est déjà utilisé.` | Vous avez peut-être entré un port de front end qui est déjà utilisé. | Entrez un port de front end unique. |
| `Le numéro de port de back end doit être un nombre entier.` | Vous avez peut-être entré une valeur de port de back end non valide. | Entrez un numéro de port de back end compris entre 1 et 65535. |
| `Puisque le protocole et le port ne sont pas modifiables dans le moniteur d'état, cette erreur est impossible à partir de l'interface utilisateur.`| Votre sous-réseau privé n'est pas de type standard et ne peut pas être utilisé pour créer l'équilibreur de charge. | Prenez contact avec le support IBM. |
| `Le sous-réseau privé `xyz` doit comporter au moins `n` adresses IP libres.` | Le sous-réseau privé sélectionné ne comporte aucune adresse IP libre. | Pour plus d'informations, vérifiez ces [étapes de traitement des incidents](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-load-balancer-provisioning-troubleshooting). |
| `Le VLAN de sous-réseau privé spécifié figure sur le routeur `xyz`. Or, aucun VLAN public avec `n` adresses IP libres n'a été trouvé sur le même routeur.` | Cela se produit car vous avez sélectionné l'option **Allouer à partir du sous-réseau public à partir de ce compte** lors de la mise à disposition. | Sélectionnez l'option **Allouer à partir du pool de systèmes IBM** ou contactez le support IBM.|
| `Le VLAN de sous-réseau privé spécifié figure sur le routeur `xyz`. Or, aucun sous-réseau public avec `n` adresses IP libres n'a été trouvé avec VLAN sur le même routeur.` | Cela se produit car vous avez sélectionné l'option **Allouer à partir du sous-réseau public à partir de ce compte** lors de la mise à disposition. | Sélectionnez l'option **Allouer à partir du pool de systèmes IBM** ou contactez le support IBM.|
| `La nouvelle description spécifiée doit être une chaîne.`| La description entrée n'est peut-être pas valide. | Entrez une description d'équilibreur de charge valide de 255 caractères au maximum. |
| `Un élément de facturation est requis pour traiter une annulation pour l'identificateur unique universel d'équilibreur de charge uuid=aaaa-bbbb-cccc-dddd.` | Des informations sur la facturation sont manquantes ou non valides pour votre compte et l'équilibreur de charge ne peut pas être annulé. | Prenez contact avec le support IBM. |
| `Une erreur interne s'est produite. Impossible de récupérer les données.` | Les données de métriques ne peuvent pas être extraites | Rechargez la page. Si le problème persiste, contactez le support IBM. |
| `Le numéro de port de front end doit être un entier compris entre 1 et 65535, à l'exclusion de la plage de 56500 à 56520.` |Vous avez peut-être entré un numéro de port de front end compris entre 56500 et 56520. | Entrez un numéro de port unique compris entre 1 et 65535, à l'exclusion de la plage de 56500 à 56520. |
| `Le numéro de port de back end doit être un nombre entier.` | Vous avez peut-être entré une valeur de port de back end non valide. | Entrez un numéro de port de back end compris entre 1 et 65535. |
| `Le numéro de port de back end doit être un entier compris entre 1 et 65535, à l'exclusion de la plage de 56500 à 56520.` | Vous avez peut-être entré un port de back end compris entre 56500 et 56520.| Entrez un numéro de port de back end compris entre 1 et 65535, à l'exclusion de la plage de 56500 à 56520. |
| `Le protocole HTTP de back end n'est pas compatible avec le protocole TCP de front end.` | Vous avez peut-être sélectionné une combinaison de protocole de back end et de protocole de front end qui ne sont pas compatibles. | Sélectionnez une combinaison valide de protocole de back end et de protocole de front end, sous la forme : `<br> HTTP-HTTP <br> HTTPS-HTTP <br> TCP-TCP` |
| `Une pondération de membre <some value> est fournie pour le membre abcd-xxxx-yyyy-2222. La valeur de pondération autorisée est comprise entre 0 et 100 `| Vous avez peut-être entré une pondération non valide. | Entrez une valeur de pondération comprise entre 0 et 100. |
| `Un problème s'est produit lors de l'extraction des serveurs.` | Ce problème peut se produire suite à des dépassements de délai de réseau. | Rechargez la page. Si le problème persiste, contactez le support IBM.|
