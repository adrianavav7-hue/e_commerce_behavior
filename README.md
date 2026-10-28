# 📊 E-commerce - analyse et prédiction des utilisateurs revenants

## 📌 Présentation du projet

Ce projet porte sur l’analyse du comportement des utilisateurs d’un site e-commerce à partir d’un jeu de données synthétique. Il s’agit d’un problème de classification binaire visant à prédire si un utilisateur est susceptible de revenir sur le site.

L’objectif est d’identifier les caractéristiques et les comportements associés aux utilisateurs revenants afin de mieux comprendre leur engagement et d’aider l’équipe marketing à adapter ses stratégies de fidélisation.

## 🎯 Objectifs

- Analyser le comportement des utilisateurs afin d’identifier le profil type d’un utilisateur revenant.
- Développer un modèle de classification capable de prédire si un utilisateur est susceptible de revenir sur le site.
- Concevoir un tableau de bord interactif avec Power BI pour visualiser les principaux indicateurs et résultats de l’analyse.
- Formuler des recommandations opérationnelles à destination de l’équipe marketing afin de favoriser le retour des utilisateurs et d’améliorer leur fidélisation.

## 📊 Données

Le jeu de données contient 8 000 observations et 14 variables décrivant les utilisateurs, leur comportement sur le site web et leurs achats.

Les variables étudiées sont les suivantes :

| Variable | Description |
|---|---|
| `user_id` | Identifiant unique de l’utilisateur |
| `age` | Âge de l’utilisateur |
| `gender` | Genre : homme ou femme |
| `device_type` | Type d’appareil utilisé : mobile, ordinateur ou tablette |
| `time_on_site` | Temps passé sur le site (minutes) |
| `pages_viewed` | Nombre de pages consultées |
| `previous_purchases` | Nombre d’achats antérieurs |
| `cart_items` | Nombre d’articles ajoutés au panier |
| `discount_seen` | Indique si une réduction a été affichée |
| `ad_clicked` | Indique si une publicité a été cliquée |
| `returning_user` | Variable cible : indique si l’utilisateur est déjà revenu sur le site |
| `avg_session_time` | Durée moyenne d’une session |
| `bounce_rate` | Taux de rebond de l’utilisateur |
| `purchase` | Indique si un achat a été effectué (0/1) |

## 🔎 Analyse exploratoire

L’analyse exploratoire montre que la répartition des variables est globalement équilibrée, à l’exception de la variable purchase, qui présente un déséquilibre important avec 99,83 % d’achats. Cette variable n’a donc pas été retenue comme cible de prédiction. L’étude se concentre plutôt sur la prédiction de returning_user, dont la répartition est plus équilibrée, avec 52 % d’utilisateurs revenants et 48 % de nouveaux utilisateurs.

L’analyse des valeurs extrêmes n’a pas révélé d’anomalies majeures, à l’exception de la variable avg_session_time, fortement corrélée à time_on_site. Afin d’éviter une redondance entre ces deux variables, avg_session_time a été exclue du modèle de machine learning.

La population étudiée est composée à parts égales d’hommes et de femmes. Le mobile est l’appareil le plus utilisé, représentant environ 60 % des observations.

Enfin, la comparaison des moyennes des variables numériques entre les utilisateurs revenants et les non-revenants met en évidence des profils globalement similaires. Les différences observées restent limitées et ne permettent pas, à elles seules, de distinguer clairement les deux groupes. 

## 🤖 Machine learning

Plusieurs modèles de classification ont été entraînés et comparés, avec pour objectif de privilégier la precision afin de limiter les faux positifs.

Avant l’optimisation des hyperparamètres, le modèle Gradient Boosting obtenait la meilleure précision, avec un score de 0,5315. Les performances des différents modèles restaient toutefois relativement proches.

Une optimisation des hyperparamètres a ensuite été réalisée à l’aide de GridSearchCV. À l’issue du GridSearchCV, la régression logistique obtient la meilleure précision parmi les modèles évalués, avec 52,05 %. Toutefois, l’écart entre les modèles reste faible et les performances demeurent limitées. Avec la régression logistique, environ un utilisateur sur deux prédit comme revenant est réellement un utilisateur revenant. Le modèle présente également un rappel élevé de 84,08 %, ce qui signifie qu’il identifie une grande partie des utilisateurs revenants. Ce rappel élevé indique que le modèle identifie une grande partie des utilisateurs revenants, mais sa précision montre que les prédictions positives restent limitées.

La régression logistique montre que la variable purchase est le facteur le plus fortement associé à la probabilité de retour d'un nouvel utilisateur. Les autres variables, comme le type d'appareil, le genre, le clic sur une publicité et le taux de rebond, présentent des coefficients plus faibles, ce qui suggère une influence plus limitée sur la prédiction. Certaines variables, telles que le temps passé sur le site et l'âge, ont une influence positive, mais modérée. Enfin, cette analyse mesure la contribution des variables aux décisions du modèle, mais ne permet pas de déterminer le sens de leur influence ni d'établir un lien de causalité.

En conclusion, les résultats obtenus montrent qu'il est possible de prédire, dans une certaine mesure, le retour d'un utilisateur à partir de données comportementales. Toutefois, les performances des modèles indiquent que des variables plus riches et plus représentatives du parcours utilisateur seraient nécessaires pour améliorer la qualité des prédictions. Ces perspectives constituent des pistes d'amélioration intéressantes pour de futurs travaux portant sur la fidélisation et la prédiction du comportement des utilisateurs.

## ⚠️ Limites

Le modèle repose sur un nombre relativement restreint de variables explicatives (11 variables), ce qui limite sa capacité à représenter toute la complexité du comportement des utilisateurs.

Plusieurs informations susceptibles d’améliorer les performances n’étaient pas disponibles dans le jeu de données, notamment l’historique détaillé des sessions, la fréquence des visites, la date de la dernière connexion, le nombre total d’interactions avec le site, les catégories de produits consultés, la source d’acquisition des utilisateurs (SEO, publicité ou réseaux sociaux) et les informations relatives aux paniers abandonnés.

Par ailleurs, le jeu de données étant synthétique, les résultats obtenus ne peuvent pas être directement généralisés à un véritable site e-commerce sans validation sur des données réelles. Enfin, les performances relativement proches des modèles et la précision limitée invitent à interpréter les prédictions avec prudence avant toute mise en œuvre opérationnelle.

## 💡 Recommandations marketing

1. Mettre en place des campagnes de fidélisation ciblées

Segmenter les utilisateurs selon leur historique d'achat et leur comportement de navigation. Proposer aux utilisateurs qui reviennent déjà des recommandations de produits personnalisées, des avantages fidélité ou des offres adaptées à leurs achats précédents.

2. Personnaliser les campagnes publicitaires

Tester différents messages et offres selon le type d'appareil, l'interaction avec les publicités et le comportement de navigation. Mesurer les résultats par segment pour déterminer quelles campagnes favorisent réellement le retour des utilisateurs.

3. Réengager les utilisateurs peu actifs

Mettre en place, avec le consentement requis, des campagnes de relance par e-mail ou publicité pour les utilisateurs qui montrent des signes de désengagement. Proposer des nouveautés, des recommandations pertinentes ou, lorsque cela est justifié, une offre promotionnelle.

4. Utiliser le modèle prédictif pour mieux cibler les actions

Exploiter les prédictions du modèle pour prioriser certaines actions de fidélisation, tout en tenant compte de ses limites. La régression logistique présente un rappel élevé, mais sa précision reste proche de 52 % : les prédictions positives doivent donc être considérées comme des indications, et non comme des certitudes.