# Seance 18 - Prompt nettoyage scoring CRM

```text
Tu es un RevOps data engineer senior, spécialiste nettoyage de bases B2B, scoring commercial, CRM, conformité et préparation de campagnes de prospection.

MISSION
Tu dois reprendre le fichier enrichi avec Apify :
@~/Desktop/mon-business/08-enrichissement-apify/leads-apify-enriched.xlsx

Tu dois créer une base CRM propre, dédupliquée, scoreée et prête pour la prospection.
Le but n'est pas d'envoyer des emails.
Le but est de préparer une base solide pour la séance suivante.

FICHIER DE SORTIE
Crée :
~/Desktop/mon-business/09-bdd-prospection/leads-clean-crm.xlsx
~/Desktop/mon-business/09-bdd-prospection/leads-clean-crm.csv
~/Desktop/mon-business/09-bdd-prospection/rapport-clean-crm.md

Crée aussi :
~/Desktop/mon-business/09-bdd-prospection/dedupe-map.csv
~/Desktop/mon-business/09-bdd-prospection/quality-issues.csv
~/Desktop/mon-business/09-bdd-prospection/outreach-segments.md

ENTRÉE
Lis toutes les colonnes existantes :
- colonnes Serper
- colonnes dg_
- colonnes apify_
- priority_score
- priority_class
- personalized_angle
- suggested_offer
- outreach_message

CONTRAINTE
Ne supprime aucune donnée utile.
Si tu fusionnes des lignes, conserve toutes les sources.
Ne modifie pas les fichiers précédents.
Crée une nouvelle version propre.

PHASE 0 — AUDIT INITIAL
Analyse :
- total lignes
- total lead_id uniques
- total SIRET
- doublons probables
- emails présents
- téléphones présents
- contacts complets
- lignes à vérifier
- lignes non contactables
- distribution par segment, ville, statut data.gouv, statut Apify

Écris le diagnostic dans rapport-clean-crm.md.

PHASE 1 — NORMALISATION
Normalise :
- company_name
- domain
- website
- email
- phone
- city
- postal_code
- dg_siren
- dg_siret
- apify links sociaux

Emails :
- lowercase
- retire mailto:
- supprime espaces
- valide syntaxe simple
- sépare plusieurs emails
- choisis un primary_email
- conserve all_emails
- crée email_quality

Téléphones :
- retire espaces inutiles
- conserve format lisible
- distingue fixed/mobile si possible
- choisis primary_phone
- conserve all_phones
- crée phone_quality

Sites :
- domain sans www
- website en https si possible
- retire paramètres tracking

PHASE 2 — DÉDUPLICATION
Déduplique avec cette priorité :
1. dg_siret
2. dg_siren + domain
3. domain + city
4. primary_email
5. primary_phone
6. company_name normalisé + city + address

Quand tu fusionnes :
- garde le meilleur priority_score
- garde la meilleure donnée email
- garde la meilleure donnée téléphone
- garde tous les source_urls
- garde toutes les source_pages
- concatène les notes utiles
- écris dedupe-map.csv

Crée merge_reason :
- same_siret
- same_siren_domain
- same_domain_city
- same_email
- same_phone
- same_name_city_address

PHASE 3 — VALIDATION QUALITÉ
Crée quality_flags :
- missing_email
- missing_phone
- weak_data_gouv_match
- weak_apify_contact
- conflicting_email
- conflicting_phone
- no_source_for_contact
- closed_company
- bad_fit
- duplicate_merged
- manual_review_required

Crée quality_status :
- CLEAN_READY
- READY_WITH_WARNING
- NEEDS_MANUAL_REVIEW
- DO_NOT_CONTACT
- ENRICH_LATER

Règles :
- LOW_CONFIDENCE, NOT_FOUND, entreprise fermée = DO_NOT_CONTACT ou NEEDS_MANUAL_REVIEW.
- CONTACT_COMPLETE + HIGH_CONFIDENCE = CLEAN_READY.
- EMAIL_ONLY + HIGH/MEDIUM = CLEAN_READY ou READY_WITH_WARNING.
- PHONE_ONLY = READY_WITH_WARNING.
- SOCIAL_ONLY = ENRICH_LATER ou manual review.

PHASE 4 — SCORE FINAL
Calcule final_lead_score sur 100 :

legal_confidence_score /20
- SIRET confirmé
- entreprise active
- code APE cohérent
- dg_match_status fort

contactability_score /25
- email exploitable
- téléphone exploitable
- source officielle
- pas de conflit

fit_score_final /20
- segment prioritaire
- ville ou zone prioritaire
- taille plausible
- category cohérente

pain_score_final /20
- pain_signals
- review_evidence
- personalized_angle
- suggested_offer cohérente

timing_score_final /15
- recrutement
- privatisation
- réservation
- ouverture
- actualité
- signaux d'urgence

Classes :
- A+ : 85-100
- A : 70-84
- B : 55-69
- C : 40-54
- D : moins de 40

PHASE 5 — SEGMENTATION OUTREACH
Crée outreach_segment :
- privatisation_groupes
- agent_vocal_appels
- avis_reputation
- reservation_no_show
- recrutement_staffing
- menu_contenu
- crm_fidelisation
- general_ai_ops

Crée offer_angle_final :
- Assistant email privatisations/groupes
- Audit appels ratés + agent vocal IA
- Automatisation réponses avis Google
- Relance clients et no-show
- Assistant recrutement / candidatures
- Automatisation menu du jour et réseaux
- Mini CRM fidélisation

Crée message_personalization_basis :
- avis Google
- site web
- page contact
- page privatisation
- téléphone
- outil réservation
- data.gouv
- autre

PHASE 6 — ACTION RECOMMANDÉE
Crée final_next_action :
- Email personnalisé
- Appel puis email
- Email puis appel
- LinkedIn / Instagram
- Formulaire contact
- Vérification manuelle
- Enrichir plus tard
- Ne pas contacter

Règles :
- A+/A + primary_email = Email personnalisé
- A+/A + phone only = Appel puis email
- B + email = Email doux / faible volume
- C = Enrichir plus tard ou vérification
- D = Ne pas contacter

PHASE 7 — CLASSEUR EXCEL
Crée leads-clean-crm.xlsx avec ces onglets :

1. CRM_DASHBOARD
KPIs :
- lignes source
- leads dédupliqués
- CLEAN_READY
- READY_WITH_WARNING
- NEEDS_MANUAL_REVIEW
- DO_NOT_CONTACT
- A+ / A / B / C / D
- email ready
- phone ready
- taux contactable
- taux exclu

Graphiques :
- final_class
- quality_status
- canal recommandé
- top segments
- top villes

2. MASTER_CRM
Toutes les lignes finales dédupliquées.
Colonnes minimum :
lead_id_final, original_lead_ids, company_name, domain, website, dg_siren, dg_siret, dg_raison_sociale, dg_nom_commercial, primary_email, all_emails, email_quality, primary_phone, all_phones, phone_quality, city, address, segment, outreach_segment, offer_angle_final, final_lead_score, final_class, quality_status, final_next_action, recommended_contact_channel, personalized_angle, outreach_message, source_urls, apify_source_pages, notes.

3. READY_FOR_EMAIL
Seulement les lignes avec primary_email et quality_status CLEAN_READY ou READY_WITH_WARNING.

4. READY_FOR_CALL
Seulement les lignes avec primary_phone.

5. READY_FOR_SOCIAL
Seulement Instagram/LinkedIn/Facebook exploitables.

6. MANUAL_REVIEW
Toutes les lignes à vérifier.

7. DO_NOT_CONTACT
Entreprises fermées, mauvais fit, match faible, conflit critique.

8. OUTREACH_SEGMENTS
Vue par segment : volume, score moyen, canal, angle, offre.

9. MESSAGE_ANGLES
Une ligne par segment avec :
segment, pain, offer_angle, proof_needed, email_hook, call_hook.

10. DEDUPE_MAP
Toutes les fusions.

11. QUALITY_ISSUES
Toutes les anomalies.

12. OUTREACH_QUEUE
File d'attente triée :
rank, lead_id_final, company_name, final_class, channel, primary_email, primary_phone, message, status, owner, send_after, notes.

13. SCORING_RULES
Toutes les règles de score.

MISE EN FORME
- filtres
- première ligne figée
- couleurs par final_class et quality_status
- dashboard lisible
- colonnes larges
- aucune donnée secrète
- pas de formules cassées

PHASE 8 — RAPPORT
Crée rapport-clean-crm.md avec :
- résumé de la base
- nombre initial vs final
- doublons fusionnés
- taux email
- taux téléphone
- taux CLEAN_READY
- top segments
- top canaux
- limites
- recommandations pour la séance prospection automatisée

CONFORMITÉ
La base doit être utilisée pour une prospection B2B pertinente.
Conserve les sources.
Prépare une future colonne opt_out_status.
Ne contacte pas les lignes DO_NOT_CONTACT.
Ne crée pas de données inventées.

CONTRÔLE FINAL
Avant de finir :
- vérifie que le XLSX s'ouvre
- vérifie que MASTER_CRM est dédupliqué
- vérifie que READY_FOR_EMAIL contient seulement des emails
- vérifie que DO_NOT_CONTACT est exclu de OUTREACH_QUEUE
- vérifie que final_lead_score est entre 0 et 100
- vérifie que chaque ligne a final_next_action

MESSAGE FINAL
Réponds seulement :
"Base CRM nettoyée.
Fichiers :
- leads-clean-crm.xlsx
- leads-clean-crm.csv
- rapport-clean-crm.md

Lignes source : X
Leads finaux : Y
Doublons fusionnés : Z
CLEAN_READY : A
READY_WITH_WARNING : B
NEEDS_MANUAL_REVIEW : C
DO_NOT_CONTACT : D
Prêts email : E
Prêts appel : F"
```

## Prompt complémentaire - Nettoyage final de tout le projet

```text
Tu es un data ops senior, spécialiste rangement de projets, consolidation de fichiers de leads, nettoyage CRM et préparation de prospection automatisée prudente.

MISSION
Le dossier de génération de leads de l'élève est devenu trop lourd, désorganisé ou ambigu :
@/Users/fort/Desktop/mon-business/06-leads-gratuits-massif

Cette adresse est le dossier à nettoyer dans cet exemple. Si le projet de l'élève utilise un autre chemin, adapte-toi au chemin réel donné par l'utilisateur.

Tu dois analyser tout le dossier, pas seulement un fichier.
Tu dois reconstruire une infrastructure finale propre, logique et stratégique pour la suite.
Le but n'est pas d'envoyer des messages.
Le but est de garder une seule base Excel opérationnelle et de supprimer le chaos opérationnel.

Le prompt doit rester généraliste :
- ne suppose pas que les fichiers portent les mêmes noms que dans l'exemple
- ne suppose pas que les colonnes ont les mêmes noms
- ne suppose pas que les données utiles sont à la racine du dossier
- ne suppose pas qu'un fichier récent est forcément le bon
- décide à partir du contenu, de la structure, de la qualité et des doublons

RÈGLE ABSOLUE
Ne lance aucune prospection.
Ne te connecte à aucun outil d'envoi.
Ne supprime rien définitivement.
Ne casse pas les fichiers sources.
Ne modifie pas les fichiers sources originaux.
Ne garde qu'un seul fichier XLSX opérationnel pour la suite.
Tous les autres fichiers doivent être documentés, ignorés ou archivés.

ENTRÉE
Analyse récursivement tout le dossier :
~/Desktop/mon-business/06-leads-gratuits-massif/

Repère :
- tous les fichiers à la racine
- tous les fichiers dans les sous-dossiers
- CSV, XLSX, XLS, JSON, TXT, MD, HTML si présents
- exports bruts
- fichiers enrichis
- fichiers de mapping
- fichiers de déduplication
- bases finales candidates
- versions intermédiaires
- fichiers de test
- fichiers temporaires
- logs
- scripts
- notes de stratégie
- doublons probables
- dossiers utiles
- dossiers inutiles
- bases exploitables
- bases à ignorer
- fichiers déjà nettoyés

Détecte les fichiers de leads par leur contenu, pas seulement par leur nom.
Exemples d'indices :
- présence d'entreprises
- emails
- téléphones
- sites web
- domaines
- villes
- adresses
- URLs sources
- profils sociaux
- scores
- colonnes CRM
- lignes structurées répétées

SORTIE OBLIGATOIRE
Crée ou remets au propre un seul dossier final :
~/Desktop/mon-business/09-bdd-prospection/PROSPECTION_READY/

Structure finale attendue :
- leads-prospection-ready.xlsx
- README.md
- rapport-nettoyage-projet.md
- manifest-fichiers.csv
- _archive_raw/
- _archive_raw/used_sources/
- _archive_raw/duplicate_or_old_versions/
- _archive_raw/temp_logs_tests/
- _archive_raw/manual_review_sources/
- _archive_raw/non_lead_documents/

Règle de structure :
Le seul fichier XLSX opérationnel à la racine doit être :
leads-prospection-ready.xlsx

Si d'anciens XLSX doivent être conservés, ils vont dans _archive_raw/ et doivent être marqués comme archives.
Aucun fichier dans _archive_raw/ ne doit être utilisé directement pour prospecter.
La séance 19 doit lire uniquement :
~/Desktop/mon-business/09-bdd-prospection/PROSPECTION_READY/leads-prospection-ready.xlsx

PHASE 0 — AUDIT DU DOSSIER
Analyse :
- taille totale du dossier
- nombre de fichiers
- nombre de dossiers
- nombre de CSV
- nombre de XLSX
- nombre d'autres fichiers exploitables
- nombre de doublons probables
- fichiers les plus lourds
- fichiers qui ressemblent à des sources de leads
- fichiers qui ressemblent à des résultats enrichis
- fichiers probablement obsolètes ou intermédiaires
- fichiers indispensables pour comprendre le projet
- fichiers à archiver avec raison
- risques du dossier actuel

Écris le diagnostic dans rapport-nettoyage-projet.md.

PHASE 1 — INVENTAIRE ET TRI
Crée manifest-fichiers.csv avec :
- path
- file_name
- extension
- size_mb
- last_modified
- role_detected
- keep_status
- reason

Valeurs keep_status :
- keep_final
- use_as_source
- archive_used_source
- archive_raw
- archive_duplicate
- archive_old_version
- ignore_temp
- ignore_non_lead
- manual_review

Valeurs role_detected possibles :
- final_database_candidate
- enriched_lead_source
- raw_lead_source
- dedupe_mapping
- query_or_scraping_input
- strategy_note
- script_or_code
- temp_file
- log_file
- duplicate
- old_version
- non_lead_document
- unknown

Règle :
Ne travaille pas au hasard. Chaque fichier déplacé ou ignoré doit avoir une raison.
Ne classe pas un fichier comme inutile simplement parce que son nom est bizarre.
Lis sa structure ou un échantillon avant de décider.

PHASE 2 — SÉLECTION STRATÉGIQUE DES SOURCES
Avant de fusionner, choisis les sources à utiliser.

Priorise les fichiers qui ont :
- le plus de champs exploitables
- des emails ou téléphones propres
- des sources ou URLs
- des données enrichies
- une structure tabulaire claire
- une date récente si plusieurs versions semblent identiques
- moins de doublons

Ne priorise pas automatiquement :
- le plus gros fichier
- le fichier le plus récent
- le fichier appelé final
- le fichier appelé massif

Crée dans rapport-nettoyage-projet.md une section :
"Sources retenues pour consolidation"
avec :
- fichier
- raison
- nombre de lignes estimé
- colonnes principales
- limites

PHASE 3 — CONSOLIDATION DES DONNÉES
Identifie les fichiers qui contiennent vraiment des leads.
Fusionne seulement les données utiles.
Déduplique les lignes.
Normalise les colonnes.
Garde les sources.
Garde les meilleurs contacts.
Exclus les lignes dangereuses ou non exploitables.

Règles de lecture :
- si un fichier est gros, lis-le par chunks ou échantillonne avant traitement complet
- si un XLSX contient plusieurs onglets, inspecte tous les onglets
- si les colonnes ne correspondent pas, crée un mapping intelligent
- si une donnée est absente, laisse vide au lieu d'inventer
- conserve toujours les sources dans source_files et source_urls

Règles de déduplication :
Déduplique progressivement avec :
- domain
- website normalisé
- primary_email
- primary_phone
- company_name normalisé + city
- source_url si disponible

Quand deux lignes se ressemblent, fusionne les meilleurs champs :
- email le plus exploitable
- téléphone le plus exploitable
- website le plus clair
- source la plus précise
- notes cumulées
- meilleure classification qualité

Le fichier final leads-prospection-ready.xlsx doit contenir :

1. DASHBOARD
Résumé lisible du fichier.

2. MASTER_CRM
Base finale dédupliquée et propre.

3. READY_FOR_EMAIL
Seulement les lignes avec email exploitable.

4. READY_FOR_CALL
Seulement les lignes avec téléphone exploitable.

5. READY_FOR_SOCIAL
Seulement les profils sociaux exploitables.

6. OUTREACH_QUEUE
File d'attente prête pour la prospection automatisée.

7. DO_NOT_CONTACT
Lignes exclues.

8. MANUAL_REVIEW
Lignes à vérifier.

9. SOURCE_AUDIT
Sources et fichiers utilisés.

10. CLEANUP_LOG
Résumé des choix de nettoyage.

11. COLUMN_MAPPING
Mapping entre colonnes sources et colonnes finales.

Colonnes minimum dans MASTER_CRM :
lead_id_final, company_name, website, domain, city, address, primary_email, all_emails, email_quality, primary_phone, all_phones, phone_quality, social_links, source_files, source_urls, final_class, quality_status, outreach_segment, final_next_action, campaign_status, opt_out_status, notes.

Valeurs quality_status :
- CLEAN_READY
- READY_WITH_WARNING
- NEEDS_MANUAL_REVIEW
- DO_NOT_CONTACT

Valeurs final_class :
- A+
- A
- B
- C
- DO_NOT_CONTACT

PHASE 4 — ORGANISATION DU DOSSIER FINAL
Dans PROSPECTION_READY, garde une structure lisible :

PROSPECTION_READY/
- leads-prospection-ready.xlsx
- README.md
- rapport-nettoyage-projet.md
- manifest-fichiers.csv
_archive_raw/
- used_sources/
- duplicate_or_old_versions/
- temp_logs_tests/
- manual_review_sources/
- non_lead_documents/

Règle :
- aucun autre XLSX opérationnel à la racine
- aucun CSV opérationnel concurrent à la racine
- les fichiers sources conservés vont dans _archive_raw/
- les fichiers incertains vont dans manual_review_sources/
- README.md doit dire clairement : "Pour la séance 19, utiliser uniquement leads-prospection-ready.xlsx"

PHASE 5 — RÈGLES QUALITÉ
Vérifie :
- pas de doublons critiques dans MASTER_CRM
- pas de ligne DO_NOT_CONTACT dans OUTREACH_QUEUE
- pas de ligne sans source
- pas de données inventées
- pas de fichier final en plusieurs versions
- pas de CSV opérationnel concurrent
- pas de XLSX opérationnel concurrent
- un seul fichier final pour la séance suivante
- OUTREACH_QUEUE contient seulement des lignes actionnables ou à vérifier
- READY_FOR_EMAIL contient seulement des emails exploitables
- READY_FOR_CALL contient seulement des téléphones exploitables
- MANUAL_REVIEW récupère les cas ambigus

PHASE 6 — PRÉPARATION PROSPECTION AUTOMATISÉE
OUTREACH_QUEUE doit être utilisable par la séance 19.
Chaque ligne doit avoir :
- lead_id_final
- company_name
- recommended_channel
- email ou téléphone si disponible
- outreach_segment
- final_class
- quality_status
- final_next_action
- campaign_status = draft ou pending_review
- opt_out_status vide
- notes

Règle :
Par défaut, rien n'est approved.
Tout doit rester en brouillon ou pending_review.
Aucun message ne doit être envoyé.
Aucun outil d'envoi ne doit être connecté.

PHASE 7 — README POUR LA SUITE
README.md doit expliquer simplement :
- ce que contient le dossier
- quel fichier ouvrir
- quel fichier utiliser pour la séance 19
- pourquoi les archives ne doivent pas servir à prospecter
- quels onglets utiliser
- ce qui reste à vérifier manuellement
- qu'aucune prospection n'a été lancée

CONTRÔLE FINAL
Avant de finir :
- vérifie que leads-prospection-ready.xlsx existe
- vérifie que c'est le seul XLSX opérationnel du dossier final
- vérifie que le fichier s'ouvre
- vérifie que les onglets attendus existent
- vérifie que OUTREACH_QUEUE ne contient pas DO_NOT_CONTACT
- vérifie que README.md explique quoi utiliser
- vérifie que rapport-nettoyage-projet.md explique ce qui a été archivé ou ignoré
- vérifie que manifest-fichiers.csv couvre tous les fichiers analysés
- vérifie que la structure finale est claire
- vérifie qu'aucun envoi n'a été lancé

MESSAGE FINAL
Réponds seulement :
"Projet leads nettoyé.
Dossier final :
- PROSPECTION_READY

Fichier Excel opérationnel :
- leads-prospection-ready.xlsx

Fichiers analysés : X
Fichiers archivés : Y
Leads finaux : Z
Prêts email : A
Prêts appel : B
À vérifier : C
Exclus : D

Mode : prêt pour prospection automatisée, mais aucun envoi lancé."
```
