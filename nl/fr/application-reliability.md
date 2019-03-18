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

# Amélioration de la fiabilité et de l'évolutivité des applications à l'aide de l'équilibrage de charge global d'IBM Cloud Internet Services
Si vous possédez un site Web d'e-commerce ou si vous hébergez une application à laquelle vos utilisateurs finaux doivent pouvoir accéder en permanence, la disponibilité et les performances 24*7 de votre application sont sûrement des enjeux majeurs pour vous. 

Les fonctionnalités d'équilibrage de charge global disponibles avec IBM Cloud Internet Services (CIS) permettent d'améliorer et l'évolutivité de vos applications tout en fournissant la meilleure expérience d'utilisateur final qui soit. Ce guide fournit une revue de projet relative à la configuration de l'équilibrage de charge global.  

## Ce que vous allez accomplir

Au cours de cette procédure détaillée, vous apprendrez à configurer une opération d'installation et configuration semblable à celle illustrée ci-dessous.

<img src="images/Reliability1.png" alt="drawing" style="width: 300px;"/>

Dans cet exemple, les ressources d'application sont déployées dans deux emplacements de centre de données, l'un situé sur la côte Ouest des Etats-Unis et l'autre sur la côte Est des Etats-Unis. Les utilisateurs finaux sont susceptibles d'accéder à cette application partout dans le monde. 

Tâche  | Description
------------- | -------------
[Créer une instance CIS](create-cis.html) | Commencez par créer votre instance CIS (IBM Cloud Internet Services) à l'aide du
portail client d'IBM.
[Entrer des informations relatives à votre domaine](input-domain.html) | Entrez des informations sur le domaine que vous souhaitez protéger et pour lequel vous souhaitez fournir un équilibrage de charge global.
[Commencer la configuration de l'équilibreur de charge global](begin-config.html) | Commencez à configurer votre équilibreur de charge global.
[Identifier vos ressources d'application](identify-app-resources.html) | Identifiez les ressources de votre application, par exemple, les pools d'origines et les mécanismes de diagnostic d'intégrité.
[Définir l'équilibreur de charge global](define-global-lb.html) | Définissez la configuration de votre équilibreur de charge global en spécifiant un nom d'hôte, en ajoutant et en ajustant vos pools d'origines et en définissant des règles supplémentaires pour contrôler la façon dont le trafic est acheminé aux clients.
