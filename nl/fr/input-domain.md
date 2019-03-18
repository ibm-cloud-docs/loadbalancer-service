---



copyright:
  years: 2017
lastupdated: "2018-06-20"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Entrer des informations relatives à votre domaine
Entrez des informations sur le domaine que vous souhaitez protéger et pour lequel vous souhaitez fournir un équilibrage de charge global.

1. Cliquez sur **Vue d'ensemble** sur le côté gauche de l'écran Démarrage. Entrez votre nom de domaine (ou votre nom de sous-domaine) et cliquez sur **Ajouter un domaine**. 
    
    <img src="images/Reliability3.png" alt="drawing" style="width: 300px;"/>
    
    **Remarque :** IBM Cloud Internet Services n'est pas un enregistreur DNS, par conséquent, ce domaine (ou sous-domaine) doit avoir été préalablement créé.

    Sous la section Détails du service, vous constaterez que le domaine nouvellement ajouté est à l'état En attente. 

    <img src="images/Reliability4.png" alt="drawing" style="width: 300px;"/>    

2. Accédez à la page d'administration pour votre domaine avec votre enregistreur DNS respectif et déléguez votre domaine/sous-domaine aux serveurs de noms IBM en définissant des enregistrements de serveur de noms.

Un délai de 24 heures peut s'écouler avant la réplication de vos informations dans la base de données DNS. Une fois ce processus terminé, votre domaine passe à l'état Actif. 

<img src="images/Reliability5.png" alt="drawing" style="width: 300px;"/>    
