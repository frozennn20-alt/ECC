# Pécule

Application de budget personnel en une seule page (`pecule.html`), en français.

Version en ligne (privée, liée au compte Claude du propriétaire) :
<https://claude.ai/artifact/5sBjhzjZE4wAhxH8JbwPSG>

## Ce que fait l'application

- **Mois** : reste à dépenser, montant par jour jusqu'à la fin du mois, rythme
  de dépense comparé au budget, suivi par catégorie, historique sur six mois.
- **Opérations** : liste des dépenses et revenus par jour, recherche, filtres,
  modification et suppression.
- **Budgets** : revenus en plusieurs versements (par exemple un acompte et un
  solde, chacun avec son jour de paie), épargne répartie sur plusieurs comptes,
  charges fixes déduites automatiquement, budget par catégorie avec
  répartition proposée.
- Un virement vers un compte d'épargne (livret, LDDS, assurance vie, coffre…)
  est reconnu comme de l'épargne, pas comme une dépense, et relié au bon
  compte par son nom ou son montant. La carte « Épargne du mois » montre ce
  qui est versé et ce qui reste à verser.
- Un virement de salaire collé est relié au bon versement (par son nom, les
  mots « salaire / acompte / paie », ou le montant le plus proche) : le
  montant réellement reçu remplace le montant prévu pour le mois.
- **Notifs** : guide pour relier les notifications de paiement du téléphone
  (Raccourcis sur iPhone, MacroDroid sur Android) et testeur de lecture.
- Lecture du texte d'une notification bancaire : montant, commerçant, date,
  dépense ou revenu, et catégorie devinée. Pécule retient la catégorie
  choisie pour chaque commerçant.
- Bilan du mois par Claude et export CSV (dans la version en ligne).

## Stockage des données

- Publiée sur claude.ai : les données sont dans l'espace privé de chaque
  personne (`data/users/<id>`), synchronisées entre ses appareils. Personne
  d'autre ne les lit, même si la page est partagée.
- Ouverte directement dans un navigateur : les données restent dans le
  `localStorage` de ce navigateur.

## Liens d'ajout rapide

| Lien | Effet |
| --- | --- |
| `#ajout` | Ouvre l'écran d'ajout, prêt à coller une notification |
| `#d-2390-carrefour-city` | Ouvre l'écran d'ajout avec 23,90 € chez Carrefour City |
| `?notif=<texte>` | Lit le texte d'une notification (hébergement personnel uniquement) |
| `?montant=12,50&marchand=Lidl` | Préremplit une dépense (hébergement personnel uniquement) |

Sur claude.ai, seuls les liens en `#` sont transmis à la page.

## Limites

Une page web ne peut pas lire les notifications des autres applications.
L'automatisation du téléphone copie la notification et ouvre Pécule ; il reste
à coller le texte et valider. Sur iPhone, l'automatisation « Transaction » ne
se déclenche que pour les paiements Apple Pay.
