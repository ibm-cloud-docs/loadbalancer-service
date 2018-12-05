---

copyright:
  years: 2018
lastupdated: "2018-11-14"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Traitement des incidents liés à des messages d'erreur
Cette rubrique fournit des informations sur les messages d'erreur courants liés à la création/mise à jour d'une instance de l'équilibreur de charge IBM Cloud. 

| Erreur |Explication | Solution  |
| ------------- | ------------- | ----- |
| `Le nombre maximal d'équilibreurs de charge, `n`, est atteint.`| Nous n'autorisons que 50 instances d'équilibreur de charge par compte. | Assurez-vous que vous n'avez pas plus de 50 instances d'équilibreur de charge par compte. |
| `Le nombre maximal de protocoles spécifiés, `n`, dans la commande du produit d'équilibrage de charge est atteint.` | Seuls deux protocoles peuvent être ajoutés lors de la mise à disposition d'un équilibreur de charge. | Si vous avez besoin de davantage de protocoles, une fois la mise à disposition effectuée, vous pouvez en ajouter jusqu'à 10 à partir de l'onglet **Protocoles** dans le flux de gestion des équilibreurs de charge. Pour plus d'informations, voir [Surveillance et gestion de votre service](/docs/infrastructure/loadbalancer-service/managing-lb.html#monitoring-and-managing-your-service). |
| `Le nombre maximal d'instances de serveur spécifiées, `n`, dans la commande du produit d'équilibrage de charge est atteint.` | Seuls dix serveurs peuvent être ajoutés lors de la mise à disposition d'un équilibreur de charge. | Si vous avez besoin de davantage de serveurs, une fois la mise à disposition effectuée, vous pouvez en ajouter jusqu'à 50 à partir de l'onglet **Instances de serveur** dans le flux de gestion des équilibreurs de charge. Pour plus d'informations, voir [Surveillance et gestion de votre service](/docs/infrastructure/loadbalancer-service/managing-lb.html#monitoring-and-managing-your-service). |
| `Le nom d'équilibreur de charge doit être une chaîne comprise entre 1 et 40 caractères.` | Le nom d'équilibreur de charge est obligatoire. Utilisez uniquement des caractères alphanumériques (ou les caractères spéciaux '-' et '.') pour le nom. Celui-ci ne doit pas non plus commencer ou se terminer par un caractère spécial, ni dépasser 40 caractères.|Entrez un nom d'équilibreur de charge unique. Par exemple, "ui-servers" ou "backend-servers".|
| `Erreur de format détectée dans le nom d'équilibreur de charge spécifié.`  Le nom d'équilibreur de charge est obligatoire. Utilisez uniquement des caractères alphanumériques (ou les caractères spéciaux '-' et '.') pour le nom. Celui-ci ne doit pas non plus commencer ou se terminer par un caractère spécial, ni dépasser 40 caractères.|Entrez un nom d'équilibreur de charge unique. Par exemple, "ui-servers" ou "backend-servers".|
|Un équilibreur de charge portant le même nom (insensible à la casse) existe déjà. |Un équilibreur de charge portant le même nom existe déjà. |Entrez un nom d'équilibreur de charge unique afin de pouvoir continuer. Par exemple, ui-servers, backend-servers, etc. |
| La description d'équilibreur de charge doit être une chaîne et ne doit pas excéder 255 caractères. | La description d'équilibreur de charge doit être une chaîne et ne doit pas excéder 255 caractères. |Entrez une description d'équilibreur de charge valide qui n'excède pas 255 caractères. |
| Le port frontal `80` est déjà utilisé. | Vous avez peut-être entré un doublon de port frontal qui est déjà utilisé. |Entrez un port frontal unique. |
| Le port de back end doit être un nombre entier. | Vous avez peut-être entré une valeur de port de back end non valide. | Entrez une valeur de port de back end valide comprise entre 1 et 65535. |
|Puisque le protocole et le port ne sont pas modifiables dans le moniteur d'état, cette erreur est impossible à partir de l'interface utilisateur.| Le sous-réseau privé `xyz` n'est pas de type standard, par conséquent, il ne peut pas être utilisé pour créer un équilibreur de charge.|Prenez contact avec le support IBM. |
|Le sous-réseau privé `xyz` doit comporter au moins `n` adresses IP libres. |Le sous-réseau privé sélectionné ne comporte pas d'adresses IP libres. |Pour plus d'informations, vérifiez ces [étapes de traitement des incidents](/docs/infrastructure/loadbalancer-service/troubleshooting-provisioning.html#insufficient-ip-addresses-in-your-subnet). |
|Le VLAN de sous-réseau privé spécifié figure sur le routeur `xyz`. Or, aucun VLAN public avec `n` adresses IP libres n'a été trouvé sur le même routeur. |Cela se produit car vous avez sélectionné l'option "Allouer à partir du sous-réseau public à partir de ce compte" durant la mise à disposition. |Sélectionnez l'option "Allouer à partir du pool de systèmes IBM" ou contactez le support IBM. |
|Le VLAN de sous-réseau privé spécifié figure sur le routeur `xyz`. Or, aucun sous-réseau public avec `n` adresses IP libres n'a été trouvé avec VLAN sur le même routeur. |Cela se produit car vous avez sélectionné l'option "Allouer à partir du sous-réseau public à partir de ce compte" durant la mise à disposition. |Sélectionnez l'option "Allouer à partir du pool de systèmes IBM" ou contactez le support IBM. |
|La nouvelle description spécifiée doit être une chaîne. | Vous avez peut-être entré une description non valide. |Entrez une description d'équilibreur de charge valide qui n'excède pas 255 caractères. |
|Un élément de facturation est requis pour traiter une annulation pour l'identificateur unique universel d'équilibreur de charge=`aaaa-bbbb-cccc-dddd`.| |Prenez contact avec le support IBM. |
|Une erreur interne s'est produite. Impossible de récupérer les données. |Les données de métriques ne peuvent pas être extraites. |Rechargez la page. Si le problème persiste, contactez le support IBM. |
|Le port frontal doit être un entier compris entre 1 et 65535, à l'exclusion de la plage 56500-56520.|Vous avez peut-être entré un port frontal compris entre 56500 et 56520. |Entrez un numéro de port unique compris entre 1 et 65535, à l'exclusion de la plage 56500-56520.|
| Le port de back end doit être un nombre entier. | Vous avez peut-être entré une valeur de port de back end non valide. | Entrez une valeur de port de back end valide comprise entre 1 et 65535. |
|Le port de back end  doit être un entier compris entre 1 et 65535, à l'exclusion de la plage 56500-56520.|Vous avez peut-être entré un port de back end compris entre 56500 et 56520. |Entrez n'importe quel autre numéro de port de back end valide compris entre 1 et 65535, à l'exclusion de la plage 56500-56520.|
|Le protocole de back end `HTTP` n'est pas compatible avec le protocole frontal `TCP`.|Vous avez peut-être sélectionné une combinaison de protocole de back end et de protocole frontal qui n'est pas compatible. |Sélectionnez une combinaison de protocole de back end et de protocole frontal valide, comme ci-dessous : <br> HTTP-HTTP <br> HTTPS-HTTP <br> TCP-TCP|
|"Une pondération de membre `<some value>` est fournie pour le membre `abcd-xxxx-yyyy-2222`. La valeur de pondération admise est comprise entre 0 et 100. |Vous avez peut-être entré une pondération non valide. |Entrez une pondération comprise entre 0 et 100. |
|Un problème s'est produit lors de l'extraction des serveurs.|Cela est peut-être dû à des problèmes de dépassement de délai au niveau du réseau. |Rechargez la page. Si le problème persiste, contactez le support IBM. |
