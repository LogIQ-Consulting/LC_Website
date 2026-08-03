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

✅ Le lien de lancement est en place (`buy.stripe.com/3cI28t3JraVl23r8552Ry01`), confirmé à 270,00 CHF —
montant total dû qui correspond bien au prix affiché sur le site.

Note : ce Payment Link ne détaille pas la TVA (taxe à 0,00 CHF, 270 CHF considéré comme prix final). Si tu es
effectivement assujetti à la TVA suisse et veux que Stripe l'isole pour ta comptabilité, attache un taux de
taxe de 8.1 % **en mode "TVA incluse" (inclusive)** au prix — Dashboard Stripe → Produits → ce prix →
Paramètres → Fiscalité → Taux de taxe. Le montant facturé au client (270 CHF) ne change pas, seule la
répartition HT/TVA apparaît dans tes justificatifs. Vérifie ce point avec ton fiduciaire.

Reste à faire : le second Payment Link pour le tarif normal.

1. Dashboard Stripe → **Payment links** → **Create payment link**.
2. Crée un produit "Business plan clé en main — tarif normal" à **540 CHF**, devise **CHF**, paiement unique
   (même logique de taxe que ci-dessus).
3. Configure la redirection après paiement vers `https://logiq-consulting.ch/merci.html` (onglet "After payment").
4. Copie l'URL générée. À la fin du mois de lancement (après le 3 septembre 2026), remplace dans `index.html`
   le lien du bouton par celui-ci et mets à jour le texte "270.– CHF" / la date dans la section Tarif.

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
