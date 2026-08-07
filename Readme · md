# Darwin — assistant vocal personnel

PWA à fichier unique, hébergée sur GitHub Pages, cerveau IA gratuit (API Gemini).
Développé par DESSOUASSI Oboube Anaël David.

## Mise en ligne (5 minutes)

1. Crée un dépôt GitHub public (ex. `darwin`).
2. Mets-y `index.html`, `manifest.json`, `sw.js` et le dossier `icons/` à la racine.
3. Réglages du dépôt → **Pages** → Source : `main`, dossier `/ (root)`. Enregistre.
4. Ton app est en ligne sur `https://<ton-pseudo-github>.github.io/darwin/`.

## Premier lancement

1. Ouvre l'URL. Crée un code PIN à 4 chiffres (obligatoire, reste sur ton appareil).
2. Écran suivant : colle ta clé API Gemini directement dans l'onboarding — une seule fois, jamais redemandée après (ou saute cette étape si tu préfères le proxy zéro-clé, voir plus bas).
3. Active l'empreinte / Face ID si ton appareil le propose (recommandé, pas obligatoire).
4. Choisis une voix dans les Réglages, ajuste vitesse/tonalité si tu veux.
5. Installe l'app : menu du navigateur → « Ajouter à l'écran d'accueil » / « Installer l'application ».

## Option : ne jamais coller de clé API (recommandé)

Par défaut, tu colles ta clé Gemini une fois dans Réglages ⚙️, et elle reste sur l'appareil.
Si tu veux ne JAMAIS la voir ni la coller nulle part — même pas une fois — déploie `worker.js`
sur Cloudflare (gratuit, 5 min, instructions en haut du fichier), puis colle seulement
l'URL de ce Worker dans Réglages → « URL de proxy ». Cette URL n'est pas un secret : c'est
la clé Gemini elle-même qui reste cachée côté Cloudflare, jamais dans le navigateur ni sur GitHub.

## Pourquoi Darwin n'a pas de clé pré-intégrée

Il n'existe pas de clé « universelle gratuite » que je pourrais coller dans le code à ta place —
ni chez moi, ni chez Google. Toute clé collée en clair dans `index.html` serait visible par
n'importe qui visitant ton dépôt GitHub public, et se ferait épuiser ou voler en quelques heures.
Le Worker ci-dessus est la seule façon d'avoir un Darwin « prêt à l'emploi » sans ce risque.

## Pourquoi un seul cerveau IA (Gemini) plutôt que GPT + Claude + les autres

Brancher chaque marque séparément voudrait dire une clé API par marque à gérer — l'inverse de
ce que tu cherches. Un seul modèle de conversation correct (Gemini, ici) couvre déjà l'essentiel
de ce que ChatGPT ou Claude font en texte : discuter, écrire du code, expliquer, rédiger. Pas
besoin de cinq comptes pour ça. Nano Banana (génération d'image) est la seule brique à part,
déjà câblée, mais avec facturation Google obligatoire — voir plus bas.

## Ce qui marche vraiment

- Chat texte et vocal avec un vrai modèle Gemini (pas des réponses toutes faites).
- Réponses à voix haute, voix au choix, emojis et markdown filtrés avant la lecture.
- Mot-clé « Darwin » en écoute active (voir limite ci-dessous).
- Déverrouillage empreinte/visage via la biométrie native du téléphone (WebAuthn), + PIN de secours.
- Fonctionne hors-ligne pour l'interface (pas pour les réponses de l'IA, qui ont besoin du réseau).
- Toutes les données (clé API, PIN, conversations) restent en local, sur l'appareil.
- Génération d'images (Nano Banana) est câblée, mais Google exige un compte avec facturation activée pour ce modèle précis, même à 0 FCFA de conso réelle — voir aistudio.google.com/pricing si tu veux l'activer.

## Si le micro ou l'empreinte ne réagit pas

Neuf fois sur dix, c'est parce que le fichier est ouvert en local (double-clic, adresse qui
commence par `file://`) plutôt que déployé. Le micro, le mot-clé et l'empreinte/visage
demandent tous une vraie adresse **https://** pour fonctionner — c'est une règle de sécurité
des navigateurs, aucun code ne peut la contourner. Depuis cette mise à jour, Darwin te le dit
lui-même au démarrage s'il détecte ce cas. Solution : déploie sur GitHub Pages (section
ci-dessus), puis teste sur `https://<ton-pseudo>.github.io/darwin/`, pas sur le fichier local.

Si tu es déjà en https:// et que l'empreinte refuse quand même : ton appareil n'a probablement
pas de capteur d'empreinte/Face ID configuré dans ses réglages système. Le PIN reste toujours
disponible dans ce cas — Darwin ne bloque jamais l'accès complètement.

## Limites honnêtes (pas des bugs à corriger, des règles du navigateur)

- **Mot-clé vocal** : n'écoute que si l'app est ouverte, l'écran allumé, l'onglet au premier plan. Aucun site web — Darwin compris — ne peut écouter en arrière-plan ou écran verrouillé.
- **Safari/iOS** : la reconnaissance vocale continue est moins fiable que sur Chrome/Edge. Ça vient du navigateur, pas du code.
- **Palier gratuit Gemini** : quelques dizaines de messages par jour selon le modèle. Au-delà, message d'erreur clair, réessaie dans la minute (voir `TEXT_MODEL` dans `index.html` pour changer de modèle).
- **Confidentialité** : sur le palier gratuit, Google peut utiliser tes échanges pour améliorer ses modèles. Si ça te gêne pour des sujets sensibles, active la facturation sur ton projet Google (ça bascule sur leurs conditions payantes, qui excluent l'entraînement).
- **Pas d'accès à WhatsApp, Instagram, SMS, appels, ou aux autres apps du téléphone.** Techniquement impossible depuis un site web — voir l'échange plus haut dans la conversation pour le détail.

## Fichiers

- `index.html` — l'app entière (HTML + CSS + JS)
- `manifest.json`, `sw.js` — installabilité et mode hors-ligne
- `worker.js` — proxy Cloudflare optionnel, pour ne jamais coller de clé (voir plus haut). Ne va PAS sur GitHub Pages, se déploie séparément sur Cloudflare.
- `icons/` — icônes générées depuis le motif de l'orbe
- `gen_logo.py`, `make_icons.py`, `icon-source.svg`, `logo-mark.svg` — sources du logo, si tu veux changer les couleurs plus tard
- `LICENSE.md` — licence propriétaire à ton nom
