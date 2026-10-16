# CLAUDE.md — bbl-report
<!-- Working rules for Claude in this repository (French). Code and docs are in English. -->

`bbl-report` : le contrat entre la tour de controle Blackberrylabs et ses modules — les types
Rust du rapport `bbl-report/1`, la serialisation, la validation, l'echelle de gravite en
mots, le test de conformite. Aucune logique metier, aucune lecture, aucune ecriture, aucun
reseau.

## Regles de travail

- BRIEF valide avant le code ; PLAN et JOURNAL tenus ; `00_cadrage/` hors git.
- Compatibilite avant : jamais `deny_unknown_fields` ; un champ ajoute garde la version ; un
  champ retire ou change de sens = `bbl-report/2`.
- Dependances : `serde`, `serde_json`, rien d'autre. La promesse « aucun `std::fs`, aucun
  `std::net` » est testee.
- Un changement ici se verifie sur les trois modules et la tour avant d'etre commite.
- Commits locaux libres ; `git push`, suppression de fichiers, tags : accord explicite.
  Commandes completes, chemin absolu (`cd /home/nushoko/Bureau/Logiciels/Bbl_report && …`).
- Anglais : code, commentaires, commits, README. Francais : pilotage.
- Seul nom cite : Alexandre Do.

## Identite git

Avant le **premier commit** : `git config user.name "Alexandre Do"` et
`git config user.email "277202463+Nimeria2026@users.noreply.github.com"` (config locale) ;
verifier `git log --format='%an <%ae>'` avant tout push.

## Reperes

- `src/lib.rs` : types, `Severity`, `Tone`, validation, `now_utc`, `peek_schema`.
- `src/conformance.rs` : `check(json)`.
- `tests/promises.rs` : aller-retour, champs inconnus, schema 2, regles de validation, promesse.
