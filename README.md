# Wavelength

*[English](#english) · [Français](#français)*

---

## English

An online version of the **Wavelength** board game — play with friends, in person around a table or remotely with a voice call running alongside (Discord, FaceTime, phone, whatever works). A dial, a clue, and the fun of guessing (or not) what's in the other person's head.

🔗 **Play:** https://nojikodaisy.github.io/wavelength/

### The idea

One person (the **Psychic**) rotates each round and sees where a **secret target** sits on a dial, between two opposite words (e.g. *Cold* ↔ *Hot*). They give a clue that tries to nudge the rest of the group toward that position, without giving it away.

Everyone else moves a shared needle on the dial together, in real time, then locks in their answer. The closer the needle lands to the target, the more points the team scores (4, 3, 2, or 0). The Psychic role rotates every round, and the score adds up for the whole team.

#### How a round goes

1. **Theme** — out loud, the group agrees on the two ends of the spectrum (e.g. *Terrible* / *Amazing*), the Psychic types them in. A "random idea" button suggests ready-made themes if inspiration is running low.
2. **Clue** — the Psychic sees the target and gives a clue meant to evoke it.
3. **Guess** — everyone except the Psychic moves the needle together, then locks it in.
4. **Reveal** — the target zone is shown, the round's score is added to the team score.

### How to play

No sign-up, no install, nothing to pay for. One person opens the link above and clicks **Create a game**: their browser becomes the game's host (just keep that tab open — no need to host anything yourself). They then send the generated link to everyone else, who join by typing in their name — and you're off.

You need at least 2 players to start. Ideally, play with a group that can talk live (same room, or a voice call running alongside): the fun of the game is in the back-and-forth of picking the spectrum and guessing together — the site just handles the dial and the scores.

Each player can also personalize their own display, without affecting anyone else:
- **🎨 Change theme** — 5 color palettes to choose from.
- **FR / EN** — the game can switch to English for a given player (interface text, the randomly suggested themes) while others stay in French if they prefer.

### Under the hood

The whole game lives in a single `index.html` file (HTML, CSS, vanilla JS — no framework, no build step), hosted for free on GitHub Pages.

- **Networking**: direct browser-to-browser connection over [WebRTC](https://developer.mozilla.org/en-US/docs/Web/API/WebRTC_API), via [PeerJS](https://peerjs.com/), using PeerJS's public server only for the initial handshake — game data then flows directly between players.
- **Model**: the browser of whoever creates the game acts as the server (host-authoritative). Other clients send it their actions, it validates them and sends the full game state back to everyone.
- **Dial**: drawn in SVG, generated in JS (trigonometry), with drag-and-drop (Pointer Events) and keyboard navigation (arrow keys).
- **Local storage**: nickname, color palette, and chosen language are kept in `localStorage` (specific to each browser, so to each player); the game state (host side) and the player's id are kept in `sessionStorage`, so the page can be reloaded without losing everything.

#### Running the project locally

No dependencies to install: just serve the file.

```bash
npx serve .
# or
python -m http.server 8000
```

Then open `http://localhost:8000` (or whichever port is shown).

### Known limitations

- The target is currently sent to every client in the game state (visible via the browser's dev tools); it should only be sent to the Psychic before the reveal.
- No integrity check (SRI) on the PeerJS script loaded from the CDN.
- No authentication: a player could impersonate another player's id.
- IP addresses are visible between players (normal behavior for a direct WebRTC connection).
- Monolithic code: a rewrite in Vite + TypeScript, with separate modules (game rules, networking, rendering), would be more maintainable long-term.

### License

Personal project, no specific license defined for now.

---

## Français

Une version en ligne du jeu de société **Wavelength** — à jouer entre amis, en vrai autour d'une table ou à distance avec un appel vocal ouvert (Discord, FaceTime, téléphone, peu importe). Un cadran, un indice, et la bonne humeur de deviner (ou pas) ce que l'autre a en tête.

🔗 **Jouer :** https://nojikodaisy.github.io/wavelength/

### Le principe

Une personne (le **médium**) tourne à chaque manche et voit où se trouve une **cible secrète** sur un cadran, entre deux mots opposés (ex. *Froid* ↔ *Chaud*). Elle donne un indice qui essaie de pousser le reste du groupe vers cette position, sans la révéler.

Tous les autres joueurs bougent ensemble, en temps réel, une aiguille partagée sur le cadran, puis valident leur réponse. Plus l'aiguille est proche de la cible, plus l'équipe marque de points (4, 3, 2 ou 0). On tourne le rôle de médium à chaque manche, le score s'accumule pour toute l'équipe.

#### Déroulé d'une manche

1. **Thème** — à l'oral, le groupe choisit les deux bouts du spectre (ex. *Nul* / *Génial*), le médium les tape. Un bouton « idée au hasard » propose des thèmes tout faits si l'inspiration manque.
2. **Indice** — le médium voit la cible et donne un indice qui doit l'évoquer.
3. **Devine** — tout le monde sauf le médium bouge l'aiguille ensemble puis valide.
4. **Révélation** — la zone cible s'affiche, le score de la manche s'ajoute au score d'équipe.

### Comment y jouer

Pas d'inscription, pas d'installation, rien à payer. Une personne ouvre le lien ci-dessus et clique sur **Créer une partie** : son navigateur devient l'hôte de la partie (il faut juste garder cet onglet ouvert, pas besoin d'héberger quoi que ce soit). Elle envoie ensuite le lien généré aux autres, qui le rejoignent en entrant leur pseudo — et c'est parti.

Il faut au moins 2 joueurs pour lancer la partie. Idéalement, jouez avec un groupe qui peut se parler en direct (même pièce, ou appel vocal lancé à côté) : tout le sel du jeu est dans la discussion pour choisir le spectre et pour deviner ensemble, le site ne fait que gérer le cadran et les scores.

Chaque joueur peut aussi personnaliser son propre affichage, sans que ça affecte les autres :
- **🎨 Changer de thème** — 5 palettes de couleurs au choix.
- **FR / EN** — le jeu peut basculer en anglais pour un joueur donné (les textes de l'interface, les thèmes proposés au hasard), pendant que les autres restent en français si ça leur chante.

### Sous le capot

Tout le jeu tient dans un seul fichier `index.html` (HTML, CSS, JS vanilla — pas de framework, pas d'étape de build), hébergé gratuitement sur GitHub Pages.

- **Réseau** : connexion directe entre navigateurs en [WebRTC](https://developer.mozilla.org/fr/docs/Web/API/WebRTC_API), via [PeerJS](https://peerjs.com/), avec le serveur public PeerJS pour la mise en relation uniquement — les données de jeu circulent ensuite directement entre joueurs.
- **Modèle** : le navigateur de la personne qui crée la partie fait office de serveur (host-authoritative). Les autres clients lui envoient leurs actions, il valide et renvoie l'état complet de la partie à tout le monde.
- **Cadran** : dessiné en SVG, généré en JS (trigonométrie), avec glisser-déposer (Pointer Events) et navigation au clavier (flèches).
- **Stockage local** : le pseudo, la palette de couleurs et la langue choisis sont gardés dans `localStorage` (propres à chaque navigateur, donc à chaque joueur) ; l'état de la partie (côté hôte) et l'identifiant du joueur sont gardés dans `sessionStorage`, pour pouvoir recharger la page sans tout perdre.

#### Lancer le projet en local

Aucune dépendance à installer : servez simplement le fichier.

```bash
npx serve .
# ou
python -m http.server 8000
```

Puis ouvrez `http://localhost:8000` (ou le port indiqué).

### Limites connues

- La cible est actuellement envoyée à tous les clients dans l'état de partie (visible via les outils de développement du navigateur) ; elle devrait n'être transmise qu'au médium avant la révélation.
- Pas de vérification d'intégrité (SRI) sur le script PeerJS chargé depuis le CDN.
- Aucune authentification : un joueur pourrait usurper l'identifiant d'un autre.
- Les adresses IP sont visibles entre joueurs (comportement normal d'une connexion WebRTC directe).
- Code monolithique : une refonte en Vite + TypeScript, avec des modules séparés (règles du jeu, réseau, rendu), serait plus maintenable à terme.

### Licence

Projet personnel, sans licence spécifique définie pour l'instant.
