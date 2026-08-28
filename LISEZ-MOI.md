# Registre — Ramadan 1448

Application web installable, autonome et hors ligne. Une fois posée sur ton écran
d'accueil, elle n'a plus jamais besoin de réseau : tout est stocké dans le
navigateur du téléphone.

## Contenu

```
index.html              la page (interface + logique, un seul fichier)
manifest.webmanifest    nom, icônes, mode plein écran
sw.js                   service worker : met tout en cache pour le hors ligne
icons/                  icônes 192, 512 et maskable
```

## Mise en ligne sur GitHub Pages

1. Sur github.com, crée un dépôt public, par exemple `registre`.
2. **Add file → Upload files**, dépose les quatre éléments en gardant la
   structure (le dossier `icons` doit rester un dossier). Commit.
3. **Settings → Pages**. Sous *Source*, choisis `Deploy from a branch`, puis
   branche `main` et dossier `/ (root)`. Enregistre.
4. Après une minute, l'adresse apparaît en haut de la même page :
   `https://<ton-pseudo>.github.io/registre/`

L'hébergement doit être en HTTPS, sinon le service worker refuse de
s'enregistrer et le hors ligne ne fonctionnera pas. GitHub Pages est en HTTPS
par défaut, donc rien à faire.

## Installation sur Android

1. Ouvre l'adresse dans **Chrome** sur le téléphone.
2. Menu ⋮ → **Ajouter à l'écran d'accueil** (ou la bannière « Installer »
   proposée automatiquement).
3. Lance-la depuis l'icône : plus de barre d'adresse, comme une application.
4. Coupe les données mobiles et rouvre-la pour vérifier que le hors ligne
   fonctionne.

## Sauvegarde

Les coches vivent dans le stockage local de Chrome, sur ce téléphone
uniquement. Elles survivent aux redémarrages et aux mises à jour, mais pas à un
effacement des données du navigateur ni à un changement de téléphone.

Dans **Régler le plan**, deux boutons couvrent ce risque :

- **Exporter une sauvegarde** écrit un fichier `.json` dans tes téléchargements.
- **Restaurer** le relit, sur ce téléphone ou sur un autre appareil.

C'est aussi la façon de transporter ta progression vers un ordinateur : exporte
d'un côté, restaure de l'autre.

## Mettre à jour l'application

Modifie les fichiers dans le dépôt, puis **incrémente la version du cache** en
tête de `sw.js` :

```js
const CACHE = 'hifdh-v2';   // v1 → v2
```

Sans ce changement, le service worker continuera de servir l'ancienne version
depuis le cache.

## Les quatre états d'une page

Chaque pression sur une case la fait avancer d'un cran :

| État | Aspect | Compte pour |
|---|---|---|
| À venir | vide | 0 |
| Demi-page | moitié haute remplie | 0,5 page |
| Mémorisée | remplie en vert clair | 1 page |
| Consolidée | remplie en vert foncé | 1 page, murâja'a faite |

Une cinquième pression remet la case à zéro. Les indicateurs du haut comptent
les demi-pages pour 0,5, ce qui permet de suivre un rythme de 1,5 page par
semaine sans arrondir.

## Réglages

Le panneau **Régler le plan** permet d'ajuster le nombre de pages, la date de
départ, la date du premier jour de Ramadan et le numéro de la première page du
mushaf. Ce dernier champ remplace la numérotation 1–29 par les vrais numéros de
page de ton édition.

La date du 8 février 2027 est une estimation astronomique (calendrier Umm
al-Qura). La date effective au Sénégal sera annoncée la veille au soir ; le
champ de réglage permet de la corriger d'un jour le moment venu.
