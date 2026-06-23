Tu es UX/UI designer et prototypiste front HTML/CSS/JS, spécialisé dans les écrans de logiciels hospitaliers DPI.
 
Je veux que tu me génères une maquette HTML/CSS/JS interactive, en un seul fichier autonome, pour un écran de prescription médicamenteuse hospitalière avec adaptation des doses selon les moments de prise.
 
Contexte métier :
- périmètre logiciel DPI hospitalier
- prescription de thérapeutiques médicamenteuses
- écran de paramétrage d’une prescription d’insuline
- logique d’adaptation de dose selon glycémie et selon le moment de prise
 
Contraintes générales :
- produire un seul fichier HTML autonome, avec CSS et JS inclus
- style visuel proche d’un logiciel hospitalier historique / métier
- interface en français
- rendu compact, lisible, métier
- aucune bibliothèque externe
- maquette interactive
- code clair et structuré
 
Structure attendue de l’écran :
1. bandeau haut
2. libellé de prescription :
   - “INSULINE LISPRO 100 UI/ml sol inj stylo prérempli”
3. sous-libellé de synthèse de la prescription
4. section “Motif de la prescription”
5. bloc principal “Prescriptions”
6. champs :
   - Unité de prescription
   - Constante à mesurer *
   - Voie d'admin. *
7. section “Mode”
   avec 2 radios :
   - “Adaptation unique”
   - “Adaptation par moment”
   La valeur sélectionnée par défaut est “Adaptation par moment”
8. périodicité :
   - “Tous les” / “1” / “jours”
9. composant de sélection horaire
10. pavés bleus des moments
11. option :
   - “Respect strict des horaires”
12. date/heure/durée :
   - “Commencer le”
   - date
   - heure
   - “pendant”
   - nombre
   - “jours”
13. tableau des doses
14. bloc Conditionnelle
15. bloc Commentaires
16. boutons bas d’écran :
   - Retour
   - Enregistrer
   - Signer
 
Contraintes de contenu et d’ergonomie :
- ne pas afficher :
  - “Une seule fois”
  - “Récurrence avec horaires”
  - “Récurrence sans horaire”
  - “Prise immédiate”
  - “Ajouter une conditionnelle”
- dans le bloc Conditionnelle, afficher seulement :
  - “Aucune”
  - “Ajouter une condition”
 
Moments standards affichés par défaut :
- Matin (06:01)
- Après-midi (12:01)
- Soirée (18:01)
- Nuit (22:01)
 
Comportement du bouton "+" :
- afficher le bouton + à droite du dernier pavé visible
- ne pas afficher le + dans le tableau
- ne pas afficher le + à côté d’un libellé “Moments de prise”
- le clic sur + affiche un composant de sélection horaire au-dessus des pavés
- ce composant doit être visuellement fidèle à une frise horaire compacte de 00h00 à 23h00 avec :
  - un libellé “Précision”
  - une valeur “60 min”
- le composant est masqué par défaut
- au clic sur un créneau horaire, le moment est ajouté immédiatement
- ne pas afficher de boutons “Ajouter” ou “Annuler” dans ce composant
- après sélection d’un horaire, le composant se referme
 
Comportement d’ajout d’un moment :
- le pavé du moment ajouté doit afficher uniquement l’horaire sélectionné, par exemple :
  - 07h00
  - 21h00
- ne jamais utiliser de libellé métier prédéfini comme “Coucher” dans le pavé ni dans l’entête de colonne
- l’ajout d’un moment crée :
  - un nouveau pavé bleu
  - une nouvelle colonne dans le tableau
- les cellules de dose de la nouvelle colonne sont initialisées à :
  - 0 UI
  - 0 UI
  - 0 UI
  pour toutes les lignes existantes
- la cohérence chronologique doit être respectée :
  - si j’ajoute 07h00, le pavé doit se placer entre Matin (06:01) et Après-midi (12:01)
  - et la colonne 07h00 doit se placer entre les colonnes Matin et Après-midi
- empêcher les doublons horaires :
  - si un horaire existe déjà, ne pas créer de doublon
  - mettre éventuellement la colonne existante en évidence brièvement
 
Suppression d’un moment ajouté :
- les moments standards ne sont pas supprimables
- les moments ajoutés doivent afficher une croix “✕” à la place de la case à cocher
- le clic sur la croix supprime :
  - le pavé
  - la colonne correspondante du tableau
 
Tableau des doses :
- positionner le tableau sous la zone date/heure/durée et juste avant le bloc Conditionnelle
- première colonne : “Bornes glycémie”
- colonnes suivantes : une colonne par moment visible
 
Bornes glycémie :
- la première colonne ne doit pas être en texte statique
- elle doit proposer un mécanisme de saisie des bornes
- structure de départ :
  - première ligne : “< x”
  - ligne intermédiaire : “x à y”
  - dernière ligne : “≥ y”
- les bornes doivent être éditables
 
Synchronisation des bornes :
- si la borne haute d’une ligne change, la borne basse de la ligne suivante se met à jour
- si la borne basse d’une ligne intermédiaire change, la borne haute de la ligne précédente se met à jour
- la chaîne des bornes doit rester continue et cohérente
 
Ajout dynamique de lignes de bornes :
- ajouter un bouton “+ ajouter une ligne”
- le clic ajoute une ligne intermédiaire de bornes avant la dernière ligne
- la ligne ajoutée doit être du type :
  - “x à y”
- la ligne ajoutée doit aussi ajouter une ligne de doses pour tous les moments
- les lignes intermédiaires ajoutées doivent pouvoir être supprimées via une croix
- la suppression d’une ligne doit recalculer la cohérence des bornes restantes
 
Libellés à utiliser impérativement :
- “Mode”
- “Adaptation unique”
- “Adaptation par moment”
- “Voie d'admin.”
- “Bornes glycémie”
- “Enregistrer”
 
Texte des pavés standards :
- Matin (06:01)
- Après-midi (12:01)
- Soirée (18:01)
- Nuit (22:01)
 
Texte descriptif sous les pavés :
- utiliser le vocabulaire “adaptation … appliquée”
- pas “barème … appliqué”
 
Boutons bas d’écran :
- Retour
- Enregistrer
- Signer
 
Attendu technique :
- fournir le code HTML complet, prêt à copier-coller
- inclure tout le CSS et le JS dans le même fichier
- produire directement la version finale sans explication longue
- soigner la cohérence des comportements interactifs
- conserver une structure de code facile à relire et à modifier
 
Si certains choix fonctionnels sont ambigus, privilégie :
1. cohérence chronologique
2. cohérence métier
3. simplicité d’usage
4. rendu visuel proche d’un ancien logiciel hospitalier