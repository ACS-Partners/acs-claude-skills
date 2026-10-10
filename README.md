# ACS Claude Skills

Marketplace publique de skills [Claude Code](https://claude.com/claude-code) partagées par ACS Partners.
Chaque skill est un **plugin** indépendant : on installe celles qu'on veut, on les met à jour d'une commande.
**Aucun compte GitHub n'est nécessaire.**

## Skills disponibles

| Plugin | Ce qu'il fait | Doc |
|---|---|---|
| `deepdive` | Exploration adverse en 5 lentilles (thèse, antithèse, socratique, avocat du diable, synthèse), finit par une décision en 3 lignes | [plugins/deepdive/README.md](plugins/deepdive/README.md) |

## Prérequis

1. Claude Code installé (`claude --version`).
2. `git` installé (`git --version`) — Claude Code s'en sert pour télécharger la marketplace.

Pas de compte GitHub, pas de connexion : le dépôt est public.

## Installation — prompt à copier-coller dans Claude Code

Ouvre `claude` dans un terminal et colle :

```text
Installe la marketplace de skills ACS et le plugin deepdive :
1. Vérifie que `git` est installé (`git --version`) ; sinon, dis-moi comment l'installer sur mon système et arrête-toi.
2. Lance `claude plugin marketplace add ACS-Partners/acs-claude-skills`.
3. Lance `claude plugin install deepdive@acs-skills`.
4. Vérifie avec `claude plugin list` que deepdive est bien installé et activé, et montre-moi la sortie.
5. Rappelle-moi de redémarrer Claude Code pour charger la skill, puis de taper `/deepdive <mon sujet>`.
```

### Ou en une seule commande (Claude Code ≥ 2.1.275)

Dans une session Claude Code ouverte :

```
/plugin install deepdive --marketplace ACS-Partners/acs-claude-skills
```

### Ou à la main

```bash
claude plugin marketplace add ACS-Partners/acs-claude-skills
claude plugin install deepdive@acs-skills
# redémarrer Claude Code, puis :  /deepdive <sujet>
```

## Mettre à jour

```bash
claude plugin marketplace update acs-skills
claude plugin update deepdive@acs-skills
```

Prompt équivalent : *« Mets à jour la marketplace acs-skills et tous ses plugins installés, puis montre-moi `claude plugin list`. »*

## Désinstaller

```bash
claude plugin uninstall deepdive@acs-skills
claude plugin marketplace remove acs-skills
```

## Structure

```
.claude-plugin/marketplace.json     ← catalogue : liste des plugins publiés
plugins/<plugin>/
  .claude-plugin/plugin.json        ← manifeste du plugin (nom, version)
  README.md                         ← doc utilisateur du plugin
  skills/<skill>/SKILL.md           ← la skill elle-même
templates/plugin-skeleton/          ← point de départ pour une nouvelle skill
docs/ADDING-A-SKILL.md              ← procédure d'ajout
```

Ajouter une skill : voir [docs/ADDING-A-SKILL.md](docs/ADDING-A-SKILL.md).
