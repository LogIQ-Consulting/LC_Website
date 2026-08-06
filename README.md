# LogIQ Consulting — Site vitrine

Site vitrine one-page pour la vente de business plans clé en main, avec
paiement en ligne via Stripe Payment Links. HTML/CSS/JS statique, sans
backend ni dépendances.

## ⚠️ Mode temporaire (jusqu'au 2 octobre 2026)

`logiq-consulting.ch` est bloqué par le verrou obligatoire de 60 jours sur les nouveaux domaines `.ch`
(enregistré le 3 août 2026) : ni le site ni les e-mails `@logiq-consulting.ch` ne fonctionnent avant le
**2 octobre 2026**. En attendant :

- **Site en ligne sur** `https://goldenrod-beaver-337658.hostingersite.com` (URL de prévisualisation Hostinger,
  déjà active). Toute occurrence de "logiq-consulting.ch" dans les pages (mentions du Site dans les CGV, etc.)
  s'affiche automatiquement avec ce nom d'hôte temporaire tant qu'on y accède par cette URL — rien à faire.
- **E-mail de contact remplacé partout** par `logiq.consulting.2026@gmail.com` (dans `index.html`, `merci.html`,
  `cgv.html`, `brief.html`) car `contact@logiq-consulting.ch` ne reçoit rien pour l'instant.
- **À faire côté Stripe** : les deux Payment Links redirigent actuellement vers `logiq-consulting.ch/merci.html`
  après paiement — à changer manuellement dans le Dashboard Stripe (onglet "After payment" de chaque lien) pour
  pointer vers `https://goldenrod-beaver-337658.hostingersite.com/merci.html`, sinon le client atterrit sur une
  page qui ne répond pas après avoir payé.

**Après le 2 octobre**, une fois `logiq-consulting.ch` actif :

1. Remettre les serveurs de noms Hostinger (`ns1.dns-parking.com` / `ns2.dns-parking.com`) sur le domaine.
2. Remplacer `logiq.consulting.2026@gmail.com` par `contact@logiq-consulting.ch` dans les 4 fichiers listés
   ci-dessus (`grep -rl "logiq.consulting.2026@gmail.com" *.html` pour les retrouver).
3. Remettre les redirections Stripe "After payment" sur `https://logiq-consulting.ch/merci.html`.
4. Vérifier que le site répond bien sur `logiq-consulting.ch` avant de communiquer la nouvelle URL.

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
3. Configure la redirection après paiement vers `https://goldenrod-beaver-337658.hostingersite.com/merci.html`
   (onglet "After payment") — voir section "Mode temporaire" ci-dessus.
4. Copie l'URL générée. À la fin du mois de lancement (après le 3 septembre 2026), remplace dans `index.html`
   le lien du bouton par celui-ci et mets à jour le texte "270.– CHF" / la date dans la section Tarif.

⚠️ Pense aussi à mettre à jour la redirection "After payment" du lien de lancement existant
(`buy.stripe.com/3cI28t3JraVl23r8552Ry01`), qui pointe encore vers `logiq-consulting.ch/merci.html`.

## Configurer le formulaire de brief (obligatoire avant mise en ligne)

Le formulaire `brief.html` envoie ses réponses par e-mail via [Web3Forms](https://web3forms.com), un service
gratuit qui ne demande pas de vrai compte (juste une adresse e-mail pour recevoir une clé d'accès).

1. Va sur [web3forms.com](https://web3forms.com) et crée une clé d'accès avec `logiq.consulting.2026@gmail.com`
   (mode temporaire — repasse à `contact@logiq-consulting.ch` après le 2 octobre si tu veux recevoir les
   briefs sur ton adresse pro).
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
- Adresse e-mail de contact : actuellement `logiq.consulting.2026@gmail.com` (mode temporaire, voir plus haut),
  présente dans `index.html`, `merci.html`, `cgv.html` et `brief.html`.
- Textes (offre, FAQ, à propos) : directement dans `index.html`.
