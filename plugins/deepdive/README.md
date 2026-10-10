# deepdive

Exploration adverse d'un sujet (décision, architecture, stratégie, diagnostic) sous cinq lentilles,
avec des règles qui empêchent le consensus de complaisance. La sortie finit **toujours** par une
décision en trois lignes.

## Installation

Dans Claude Code (≥ 2.1.275) :

```
/plugin install deepdive --marketplace ACS-Partners/acs-claude-skills
```

Autres méthodes et prompt à copier-coller : [README racine](../../README.md#installation--prompt-à-copier-coller-dans-claude-code).

## Utilisation

```
/deepdive Faut-il migrer notre supervision vers un service cloud ?
```

Ou en langage naturel : *« fais un deep dive sur… »*, *« approfondis… »*, *« analyse socratique de… »*,
*« six hats sur… »* — la skill se déclenche sur ces mots-clés.

## Ce que fait la skill

**Cinq lentilles**, passées l'une après l'autre (ou en sous-agents parallèles si l'enjeu le justifie) :

1. **Thesis** — la lecture la plus forte du sujet.
2. **Antithesis** — la lecture opposée la plus forte, jamais un homme de paille.
3. **Socratic** — les prémisses que personne n'interroge.
4. **Devil's Advocate** — le mode d'échec que personne n'a nommé.
5. **Synthesis** — ce qui survit aux quatre, et à quel prix.

**Trois règles dures :**

- au moins une contradiction *interne* à la position défendue, sinon la passe est refaite ;
- si 3 perspectives ou plus convergent, l'angle que personne n'a pris est produit explicitement ;
- les findings sont écrits au fil de l'eau (`.audit/<slug>/` pour les sous-agents), jamais en lot final.

**Sondes :** quand il y a quelque chose d'exécutable (code, API, logs), la skill exécute avant de
conclure ; quand un fait externe peut avoir bougé (version, option, API), elle le vérifie en ligne.

## Format de sortie

```
## Agreements       — ce qui tient, avec la preuve
## Disagreements    — les tensions non résolues, chacune attribuée
## Open Questions   — ce qu'il faudrait mesurer pour trancher
## Minority Report  — la position minoritaire, conservée telle quelle
## Décision         — 3 lignes : ce qui change · ce qui reste · la prochaine action
```

Si tu ne lis qu'une section, lis **Décision**.

## Cadrages optionnels

Demande-les dans le prompt : CLA (analyse causale en couches), Five Whys, Six Hats, hypothèses
concurrentes (ACH), scénarios multi-futurs, design thinking.
Exemple : `/deepdive en Six Hats : passer l'équipe en semaine de 4 jours`.

## Coût

Une passe complète en sous-agents parallèles consomme nettement plus de tokens qu'une réponse
simple. Pour un sujet léger, précise *« en single-context »*.

## Version

1.0.0 — extraite du système personnel de Yannick, sans dépendance à celui-ci.
