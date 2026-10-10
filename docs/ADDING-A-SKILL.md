# Ajouter une skill à la marketplace

Une skill = un plugin. Un plugin peut contenir plusieurs skills liées, mais par défaut on garde
**un plugin par skill** pour que chacun installe à la carte.

## 1. Créer le plugin depuis le squelette

```bash
NAME=ma-skill
cp -r templates/plugin-skeleton plugins/$NAME
mv plugins/$NAME/skills/SKILL_NAME plugins/$NAME/skills/$NAME
grep -rl SKILL_NAME plugins/$NAME | xargs sed -i "s/SKILL_NAME/$NAME/g"
```

Puis remplir :
- `plugins/$NAME/skills/$NAME/SKILL.md` — la skill (frontmatter `name` + `description` obligatoires) ;
- `plugins/$NAME/.claude-plugin/plugin.json` — description, auteur, mots-clés ;
- `plugins/$NAME/README.md` — doc utilisateur : usage, sortie, coût.

## 2. La déclarer dans le catalogue

Ajouter une entrée dans `.claude-plugin/marketplace.json` → `plugins[]` :

```json
{
  "name": "ma-skill",
  "description": "…",
  "version": "1.0.0",
  "author": { "name": "…" },
  "source": "./plugins/ma-skill",
  "category": "…"
}
```

Et une ligne dans le tableau « Skills disponibles » du `README.md` racine.

## 3. Avant de partager une skill personnelle : la nettoyer

Une skill extraite d'un setup perso porte souvent des dépendances invisibles. Vérifier qu'elle ne contient :
- aucun chemin absolu (`/home/…`, `~/.claude/…`) ni script local absent du plugin ;
- aucun nom de hook, d'agent ou de variable propre à un poste ;
- aucun secret, token, nom de client ou donnée personnelle ;
- aucun jargon privé non expliqué.

```bash
grep -rnE '/home/|~/\.claude|TOKEN|SECRET|api[_-]?key' plugins/$NAME
```

## 4. Valider puis tester localement

```bash
claude plugin validate .                    # le catalogue
claude plugin validate plugins/$NAME        # le plugin
claude plugin marketplace add ./            # marketplace locale, sans push
claude plugin install $NAME@acs-skills
```

## 5. Publier

Branche + PR, jamais de push direct sur `main`. Pour une mise à jour d'une skill existante,
**incrémenter `version`** dans `plugin.json` *et* dans `marketplace.json` : c'est ce qui permet à
`claude plugin update` de voir le changement.

Ajouter ensuite le prompt d'installation du plugin dans le README (même modèle que `deepdive`).
