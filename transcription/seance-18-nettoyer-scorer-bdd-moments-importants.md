# Séance 18 - Moments importants

## 00:00 - 03:43 - Objectif de la séance

Je pars de la base enrichie avec data.gouv et Apify. Une base enrichie n'est pas encore exploitable : je dois nettoyer, dédupliquer, scorer, segmenter et préparer le CRM avant toute prospection.

## 03:43 - 05:32 - Lancement dans Codex

Je lance Codex, je sélectionne le dossier du projet, je colle le prompt maître et je donne l'accès complet pour que l'agent puisse travailler sur les fichiers et générer les sorties attendues.

## 05:59 - 10:10 - Comprendre le prompt CRM

Le prompt demande de reprendre `leads-apify-enriched.xlsx`, de créer un dossier `09-bdd-prospection`, puis de produire `leads-clean-crm.xlsx`, `leads-clean-crm.csv`, `rapport-clean-crm.md`, `dedupe-map.csv`, `quality-issues.csv` et `outreach-segments.md`.

## 10:10 - 15:31 - Normalisation, déduplication et qualité

Je veux normaliser les emails, téléphones, domaines et sources, puis dédupliquer avec plusieurs clés : SIRET, SIREN + domaine, domaine + ville, email, téléphone, nom + ville + adresse. Le CRM doit ensuite produire des statuts qualité clairs : `CLEAN_READY`, `READY_WITH_WARNING`, `NEEDS_MANUAL_REVIEW`, `DO_NOT_CONTACT`, `ENRICH_LATER`.

## 15:31 - 19:59 - De la donnée au message

La base sert à préparer une prospection personnalisée. Je ne veux pas de messages génériques. Le CRM doit aider à savoir quoi dire, sur quel canal, et pourquoi le prospect peut être intéressé.

## 20:04 - 21:34 - Onglets et fichiers attendus

Le prompt impose des onglets : `CRM_DASHBOARD`, `MASTER_CRM`, `READY_FOR_EMAIL`, `READY_FOR_CALL`, `READY_FOR_SOCIAL`, `MANUAL_REVIEW`, `DO_NOT_CONTACT`, `OUTREACH_SEGMENTS`, `MESSAGE_ANGLES`, `DEDUPE_MAP`, `QUALITY_ISSUES`, `OUTREACH_QUEUE`, `SCORING_RULES`.

## 21:34 - 32:39 - Posture expert IA

La séance rappelle une méthode : transformer une demande client en mission claire, donner un prompt structuré, laisser l'IA construire, vérifier, corriger et améliorer. La compétence n'est pas seulement de copier un prompt, mais de savoir cadrer un système.

## 34:55 - 37:50 - Contrôle du classeur CRM

J'ouvre le fichier généré, je vérifie le dashboard et l'onglet `MASTER_CRM`. Les classes, statuts qualité et canaux recommandés deviennent visibles.

## 47:37 - 53:45 - Nettoyer l'organisation du dossier

Après avoir nettoyé l'intérieur des fichiers, je veux nettoyer l'organisation du dossier. Je demande à Codex de créer un seul dossier final `PROSPECTION_READY` avec un fichier opérationnel unique pour la séance 19.

## 53:45 - 01:01:43 - Dossier final prêt pour la séance 19

Le dossier final doit contenir une structure simple : `00-A-LIRE`, `01-BASE-EXCEL-A-UTILISER`, `02-AUDIT-QUALITE`, `03-STRATEGIE`. La séance suivante doit lire uniquement le fichier Excel final, sans repartir dans les anciens exports.
