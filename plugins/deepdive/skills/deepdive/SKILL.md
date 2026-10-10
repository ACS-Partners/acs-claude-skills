---
name: deepdive
description: Multi-methodology deep exploration skill. USE WHEN deepdive, deep dive, socratic, dialectic, six hats, CLA, causal layered analysis, scenario planning, competing hypotheses, design thinking, five whys, explore deeply, approfondis, exploration profonde, réflexion approfondie, analyser en profondeur.
---

# DeepDive

Exploration adverse multi-perspectives. Ce que le skill apporte est la **diversité adverse**, pas la discipline : une page, zéro protocole, zéro checkpoint utilisateur.

## Les 5 lentilles

Passe le sujet sous chacune — sous-agents parallèles si l'enjeu le mérite, sinon single-context en changeant réellement de posture à chaque passe :

1. **Thesis** — la lecture la plus forte du sujet, et pourquoi elle tient.
2. **Antithesis** — la lecture opposée, la plus forte possible : jamais un homme de paille.
3. **Socratic** — les prémisses non interrogées : que faut-il croire pour que ça tienne ?
4. **Devil's Advocate** — le mode d'échec que personne n'a nommé.
5. **Synthesis** — ce qui survit aux quatre, et à quel prix.

## Trois règles dures

- **Contradiction interne obligatoire** — le rapport nomme au moins une tension *à l'intérieur* de la position qu'il défend. Zéro contradiction = passe non faite, recommence.
- **Angle jamais considéré** — si ≥ 3 perspectives convergent, le consensus est suspect : produis explicitement l'angle que personne n'a pris.
- **Findings incrémentaux** — écris chaque finding dès qu'il est établi (sous-agent : sur disque, `.audit/<slug>/<lentille>.md`, et ne retourne qu'un pointeur 1-ligne). Jamais de lot final : une interruption ne doit pas coûter toute la passe.

## Sondes

Surface exécutable → **exécute** (tests, requêtes, état live, `gh`, logs) avant de conclure ; du raisonnement pur sur du code n'est pas un finding. Pas de surface runtime → validation statique (contradictions, références mortes, critères vérifiables). Fait extérieur mouvant (version, flag, API) → vérifie-le (WebSearch / docs / `gh`) : un jour, une option qu'on croyait absente de Claude Code s'est révélée native depuis des mois et a redirigé tout un diagnostic — un fait invisible sans recherche externe.

## Contrat de sortie

```
## Agreements       — ce qui tient, avec la preuve
## Disagreements    — les tensions non résolues, chacune attribuée
## Open Questions   — ce qu'il faudrait mesurer pour trancher
## Minority Report  — la position minoritaire, conservée telle quelle
## Décision        — trois lignes, obligatoires : ce qui change · ce qui reste · la prochaine action (ou « rien »)
```

`## Décision` est la sortie que quelqu'un lit quand il ne lit rien d'autre : trois lignes, pas de
paragraphe, pas de renvoi. Elle vaut seule — un deepdive finit par elle. Motif : un deepdive dont
la décision n'est pas écrite est remplacé par le premier artefact suivant (un plan de plusieurs
milliers de lignes a porté le poids d'une décision de trois lignes, et a été jugé comme tel).

Pour la synthèse finale, utilise le modèle le plus capable disponible ; les lentilles déléguées peuvent tourner sur un modèle plus léger.

Cadrages optionnels quand le sujet les appelle — une ligne d'instruction suffit, pas un fichier : CLA (litanie / systémique / vision-du-monde / mythe), Five Whys, Six Hats, hypothèses concurrentes (ACH), scénarios multi-futurs, design thinking.
