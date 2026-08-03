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

Le lien actuellement en ligne (`buy.stripe.com/eVq6oJ7ZH3sT4bz9992Ry00`) est bien en **CHF**, montant 250.00 CHF.

⚠️ **Il manque la TVA suisse (8.1 %) sur ce Payment Link** : le checkout affiche actuellement "Taxe : 0,00 CHF",
alors que le site annonce "250 CHF **HT**" (donc TVA en plus). Deux options :

- Dashboard Stripe → **Produits**, ouvre le prix associé à ce Payment Link, et attache un taux de taxe de
  8.1 % (Paramètres → Fiscalité → Taux de taxe, à créer si pas déjà fait) ; ou
- Si tu n'es pas encore effectivement assujetti à la TVA suisse (franchise en base), retire la mention "HT"
  du site et des CGV et considère 250 CHF comme prix final TTC — vérifie ce point avec ton fiduciaire.

Pour le second Payment Link (tarif normal) :

1. Dashboard Stripe → **Payment links** → **Create payment link**.
2. Crée un produit "Business plan clé en main" à **500 CHF HT**, devise **CHF**, paiement unique, avec le même
   taux de taxe 8.1 % attaché.
3. Configure la redirection après paiement vers `https://logiq-consulting.ch/merci.html` (onglet "After payment").
4. À la fin du mois de lancement (après le 3 septembre 2026), remplace le lien du bouton dans `index.html` par
   celui-ci, et mets à jour le texte "250 CHF HT" / la date dans la section Tarif.

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
