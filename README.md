# LogIQ Consulting — Site vitrine

Site vitrine one-page pour la vente de business plans clé en main, avec
paiement en ligne via Stripe Payment Links. HTML/CSS/JS statique, sans
backend ni dépendances.

Tarification : offre de lancement à 250 CHF HT pendant le premier mois, puis
500 CHF HT (tarif normal).

## Fichiers

- `index.html` — page principale (hero, offre, tarif, FAQ, contact)
- `merci.html` — page de confirmation après paiement, redirige vers `brief.html`
- `brief.html` — formulaire de brief projet, envoyé par e-mail via Web3Forms
- `cgv.html` — conditions générales de vente
- `styles.css`, `script.js` — styles et interactions (menu mobile, FAQ en accordéon natif)

## Configurer le paiement Stripe (obligatoire avant mise en ligne)

⚠️ Le lien actuellement en ligne (`buy.stripe.com/eVq6oJ7ZH3sT4bz9992Ry00`) a été créé en **EUR**. Stripe ne
permet pas de changer la devise d'un Payment Link existant : il faut en recréer un neuf en CHF.

1. Crée un compte sur [stripe.com](https://dashboard.stripe.com/register) si tu n'en as pas déjà un.
2. Dans le Dashboard Stripe → **Payment links** → **Create payment link**.
3. Crée un produit "Business plan clé en main" à **250 CHF HT**, devise **CHF**, paiement unique (offre de
   lancement du 1er mois).
4. Dans les options du lien, configure la page de redirection après paiement vers
   `https://logiq-consulting.ch/merci.html` (onglet "After payment").
5. Copie l'URL du lien généré (`https://buy.stripe.com/...`).
6. Ouvre `index.html`, cherche `buy.stripe.com/eVq6oJ7ZH3sT4bz9992Ry00` (dans la section Tarif) et remplace le
   `href` par ta nouvelle URL en CHF.
7. Crée un second Payment Link à **500 CHF HT** pour le tarif normal. À la fin du mois de lancement, remplace le
   lien du bouton par celui-ci, et mets à jour le texte "250 CHF HT" / la date dans la section Tarif de `index.html`.

## Configurer le formulaire de brief (obligatoire avant mise en ligne)

Le formulaire `brief.html` envoie ses réponses par e-mail via [Web3Forms](https://web3forms.com), un service
gratuit qui ne demande pas de vrai compte (juste une adresse e-mail pour recevoir une clé d'accès).

1. Va sur [web3forms.com](https://web3forms.com) et crée une clé d'accès avec `contact@logiq-consulting.ch`.
2. Tu reçois la clé par e-mail (format `xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx`).
3. Ouvre `brief.html`, cherche `REMPLACER_PAR_TA_CLE_WEB3FORMS` et remplace-le par cette clé.
4. Chaque soumission du formulaire t'arrive par e-mail à l'adresse utilisée pour créer la clé.

Sans cette clé, le formulaire ne fonctionnera pas (les soumissions échoueront silencieusement côté Web3Forms).

## Mettre le site en ligne

N'importe quel hébergeur statique convient, par exemple :

- **Netlify** ou **Vercel** : glisser-déposer le dossier, ou connecter un dépôt Git.
- **GitHub Pages** : pousser ce dossier dans un dépôt et activer Pages.

Aucune étape de build n'est nécessaire : ce sont des fichiers statiques.

## Personnalisation

- Couleurs et espacements : variables CSS en haut de `styles.css` (`:root`).
- Adresse e-mail de contact : `contact@logiq-consulting.ch`, présente dans `index.html`, `merci.html` et `cgv.html`.
- Textes (offre, FAQ, à propos) : directement dans `index.html`.
