# LogIQ Consulting — Site vitrine

Site vitrine one-page pour la vente de business plans clé en main, avec
paiement en ligne via Stripe Payment Links. HTML/CSS/JS statique, sans
backend ni dépendances.

Tarification : offre de lancement à 250€ HT pendant le premier mois, puis
500€ HT (tarif normal).

## Fichiers

- `index.html` — page principale (hero, offre, tarif, FAQ, contact)
- `merci.html` — page de confirmation après paiement
- `styles.css`, `script.js` — styles et interactions (menu mobile, FAQ en accordéon natif)

## Configurer le paiement Stripe (obligatoire avant mise en ligne)

1. Crée un compte sur [stripe.com](https://dashboard.stripe.com/register) si tu n'en as pas déjà un.
2. Dans le Dashboard Stripe → **Payment links** → **Create payment link**.
3. Crée un produit "Business plan clé en main" à **250€ HT**, paiement unique (offre de lancement du 1er mois).
4. Dans les options du lien, configure la page de redirection après paiement vers
   `https://logiq-consulting.ch/merci.html` (onglet "After payment").
5. Copie l'URL du lien généré (`https://buy.stripe.com/...`).
6. Ouvre `index.html`, cherche `REMPLACER_PAR_TON_LIEN` (dans la section Tarif) et remplace le `href` par ton URL.
7. Crée un second Payment Link à **500€ HT** pour le tarif normal. À la fin du mois de lancement, remplace le
   lien du bouton par celui-ci, et mets à jour le texte "250€ HT" / la date dans la section Tarif de `index.html`.

## Mettre le site en ligne

N'importe quel hébergeur statique convient, par exemple :

- **Netlify** ou **Vercel** : glisser-déposer le dossier, ou connecter un dépôt Git.
- **GitHub Pages** : pousser ce dossier dans un dépôt et activer Pages.

Aucune étape de build n'est nécessaire : ce sont des fichiers statiques.

## Personnalisation

- Couleurs et espacements : variables CSS en haut de `styles.css` (`:root`).
- Adresse e-mail de contact : `contact@logiq-consulting.ch`, présente dans `index.html`, `merci.html` et `cgv.html`.
- Textes (offre, FAQ, à propos) : directement dans `index.html`.
