# LogIQ Consulting — Site vitrine

Site vitrine one-page pour la vente de business plans clé en main, avec
paiement en ligne via Stripe Payment Links. HTML/CSS/JS statique, sans
backend ni dépendances.

Tarification : offre de lancement à 270.– CHF TTC (TVA 8.1% incluse) pendant le premier mois, puis
540.– CHF TTC (tarif normal).

## Fichiers

- `index.html` — page principale (hero, offre, tarif, FAQ, contact)
- `merci.html` — page de confirmation après paiement, redirige vers `brief.html`
- `brief.html` — formulaire de brief projet, envoyé par e-mail via Web3Forms
- `cgv.html` — conditions générales de vente
- `styles.css`, `script.js` — styles et interactions (menu mobile, FAQ en accordéon natif)

## Configurer le paiement Stripe (obligatoire avant mise en ligne)

⚠️ Le site affiche désormais des prix **TTC arrondis** (270.– / 540.– CHF), différents du lien Stripe actuel
(`buy.stripe.com/eVq6oJ7ZH3sT4bz9992Ry00`) qui facture 250.00 CHF sans taxe. Il faut créer un nouveau Payment
Link à 270 CHF pour que le montant facturé corresponde au prix annoncé.

1. Dashboard Stripe → **Payment links** → **Create payment link**.
2. Crée un produit "Business plan clé en main — offre de lancement" à **270 CHF**, devise **CHF**, paiement
   unique. Si tu es effectivement assujetti à la TVA suisse, attache un taux de taxe de 8.1 % **en mode
   "TVA incluse" (inclusive)** — Paramètres → Fiscalité → Taux de taxe — pour que 270 CHF reste le montant
   total facturé (pas 270 + taxe en plus). Si tu n'es pas encore assujetti (franchise en base), ne mets pas
   de taxe : 270 CHF est alors simplement le prix final.
3. Configure la redirection après paiement vers `https://logiq-consulting.ch/merci.html` (onglet "After payment").
4. Copie l'URL générée, ouvre `index.html`, cherche `REMPLACER_PAR_TON_LIEN_270CHF` (section Tarif) et remplace
   le `href` par cette URL.
5. Fais la même chose pour le tarif normal à **540 CHF** (même logique de taxe incluse). À la fin du mois de
   lancement (après le 3 septembre 2026), remplace le lien du bouton par celui-ci et mets à jour le texte
   "270.– CHF" / la date dans la section Tarif.

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
