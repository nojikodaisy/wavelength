# Wavelength

*[English](#english) · [Français](#français)*

---

## English

An online version of the **Wavelength** board game, to play with friends in the same room or over a voice call.

🔗 **Play:** https://nojikodaisy.github.io/wavelength/

### How it works

Each round, one player (the **Psychic**) sees a secret target on a dial between two opposite words (e.g. *Cold* ↔ *Hot*) and gives a clue. The others move a shared needle together and lock in their guess. The closer they are, the more points the team scores (4, 3, 2 or 0). The Psychic role rotates every round.

One person clicks **Create a game** and sends the link to the others. Their browser hosts the game, so they need to keep the tab open. You need at least 2 players.

### Tech

A single `index.html` file (vanilla HTML/CSS/JS), hosted on GitHub Pages. Players connect browser to browser over WebRTC via [PeerJS](https://peerjs.com/), and the host's browser runs the game.

To run it locally: `python -m http.server 8000` and open `http://localhost:8000`.

---

## Français

Une version en ligne du jeu de société **Wavelength**, à jouer entre amis dans la même pièce ou en appel vocal.

🔗 **Jouer :** https://nojikodaisy.github.io/wavelength/

### Le principe

À chaque manche, un joueur (le **médium**) voit une cible secrète sur un cadran entre deux mots opposés (ex. *Froid* ↔ *Chaud*) et donne un indice. Les autres bougent ensemble une aiguille partagée puis valident. Plus ils sont proches, plus l'équipe marque de points (4, 3, 2 ou 0). Le rôle de médium tourne à chaque manche.

Une personne clique sur **Créer une partie** et envoie le lien aux autres. Son navigateur héberge la partie : elle doit garder l'onglet ouvert. Il faut au moins 2 joueurs.

### Technique

Un seul fichier `index.html` (HTML/CSS/JS sans framework), hébergé sur GitHub Pages. Les joueurs se connectent directement entre navigateurs en WebRTC via [PeerJS](https://peerjs.com/), et le navigateur de l'hôte fait tourner la partie.

En local : `python -m http.server 8000` puis ouvrir `http://localhost:8000`.
