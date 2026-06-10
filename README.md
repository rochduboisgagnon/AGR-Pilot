# AGR Labs Remote Center

Pilote le Claude Code de ta machine depuis ton telephone. L'intelligence (Claude Code, MCP, skills, acces aux fichiers) tourne sur ton ordinateur toujours allume ; ton telephone n'est qu'un ecran. Rien ne sort de ton reseau prive.

> Ce depot est le **canal de distribution** : il contient uniquement les installeurs (Releases) et cette presentation. Aucun code source. Le developpement se fait dans un depot prive.

## Telecharger

Derniere version : voir l'onglet **[Releases](../../releases/latest)**.

| Plateforme | Fichier | Comment |
|---|---|---|
| Windows | `Remote-Center.exe` | Telecharge, double-clic. Tout est dedans, ca s'installe et se met a jour seul. |
| macOS | `Remote-Center.dmg` | Telecharge, ouvre le .dmg, glisse l'app dans Applications. |

Un seul fichier par plateforme : le serveur est embarque dans l'app. Pas besoin d'installer Git ni Node.

## Prerequis

1. **Tailscale** installe et connecte au meme compte sur l'ordinateur hote et sur le telephone (https://tailscale.com/download). MagicDNS et HTTPS Certificates actives une fois dans l'admin Tailscale.
2. **Claude Code** installe et connecte sur l'hote (abonnement Claude requis ; connexion OAuth, jamais de cle API).

## Comment ca marche

- L'app hote demarre un serveur local qui pilote Claude Code et l'expose a ton telephone via Tailscale, en HTTPS, **uniquement a l'interieur de ton reseau prive**.
- Sur le telephone : installe l'app, scanne le QR affiche par l'hote (il contient l'adresse et un jeton d'acces).
- Les mises a jour sont automatiques : l'app telecharge le nouvel installeur, **verifie son empreinte SHA-256**, puis se remplace.

## Securite

- Frontiere de confiance : le reseau **Tailscale**. Le serveur n'est jamais expose a l'Internet public.
- **Jeton d'acces obligatoire** par defaut : l'adresse a scanner contient le jeton ; sans lui, l'API refuse tout.
- Les binaires publies ici sont verifies par empreinte SHA-256 avant d'etre executes (publies dans `version.json`).

## Support

Question, probleme ou signalement de securite : **support@agrlabs.ca**.

## Licence

MIT. Voir [LICENSE](LICENSE).
