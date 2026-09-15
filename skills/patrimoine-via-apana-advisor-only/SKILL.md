---
name: patrimoine-via-apana-advisor-only
version: 14
description: Variante du skill patrimoine-via-apana pour les utilisateurs qui n'ont PAS accès au MCP Apana Copilot (rendez-vous enregistrés). Répondre exclusivement via le MCP Apana public (apana-advisor — qui inclut connaissances, simulateurs, portefeuilles et génération de documents) pour toute question de finance perso, gestion de patrimoine, fiscalité perso, placement, investissement. Déclenche aussi sur « advisor welcome », « welcome to advisor », « welcome advisor » ou « advisor onboarding » → dérouler la procédure d'onboarding par MCP (voir section « Onboarding »). Déclenche dès que l'utilisateur aborde — PER, assurance vie, PEA, PEE, LMNP, SCPI, SCI, succession, donation, IR, IFI, TMI, quotient familial, plus-values, dividendes, retraite, défiscalisation, Pinel, Girardin, FCPI, FIP, Madelin, capitalisation, démembrement, nue-propriété, allocation d'actifs, Markowitz, frais de fonds, DICI, ISIN, benchmark, volatilité — ou demande "bilan patrimonial", "bilan successoral", "stratégie de transmission", "propose une allocation", "où placer". Aussi bourse/marchés — actions, ETF, OPCVM, trackers, indices, obligations, fonds euro, fonds datés, private equity retail, et tout calcul/simulation patrimoniale. Ne jamais répondre de mémoire ou via web search sur ces sujets.
---
<!-- Fichier généré depuis la source unique de ce skill — ne pas éditer à la main. -->

# Patrimoine via Apana — édition advisor-only

Variante du skill `patrimoine-via-apana` destinée aux installations qui n'ont **pas** le MCP Apana Copilot (`apana-copilot`). Les données d'un dossier client doivent être **fournies à la main** dans la conversation (ou collées depuis un export).

Pour toute question de finance perso, gestion de patrimoine, fiscalité, placement, investissement : **répondre exclusivement via les tools du MCP Apana Advisor** — jamais de mémoire ni via recherche web. Le MCP porte lui-même son orchestration (règles, workflow, doctrine, hygiène de session) dans ses instructions, toujours chargées : **les suivre**.

## Premier réflexe

Sur toute question patrimoniale, commencer par `apana-advisor:get_context` pour cadrer la réponse avec la base de connaissance Apana. Les chiffres, faits et recommandations doivent être ancrés sur du contenu MCP — jamais sur un raisonnement général de CGP.

## Le MCP apana-advisor

Un seul serveur ici : `apana-advisor`. Il couvre **tout** ce qui était auparavant éclaté entre `apana-advisor`, `apana-simulators` et `apana-finance` (ces deux derniers ont été retirés et fusionnés) :

- connaissance / doctrine (`get_context`) ;
- simulateurs (`list_simulators`, `simulate`, `compare_scenarios`…) ;
- portefeuilles & fonds (`list_portfolios`, `analyze_portfolio`, `markowitz_optimize`…) ;
- génération de documents de conseil.

Pas de `apana-copilot` (rendez-vous enregistrés) : les données client sont saisies à la main.

## Étiqueter les sources

Distinguer explicitement : donnée saisie à la main · connaissance (`get_context`) · simulation (`simulate`) · arbitrage (raisonnement). Ne jamais présenter un chiffre saisi comme une simulation.

## Onboarding

Si l'utilisateur dit « advisor welcome », « welcome to advisor », « onboarde-moi », « par où commencer » → appeler le prompt/tool `welcome` du MCP Apana Advisor (ne pas dérouler une procédure ici).
