---
name: patrimoine-via-apana-advisor-only
description: Variante de patrimoine-via-apana pour les installations SANS le MCP Apana Copilot : données client fournies à la main. Répondre exclusivement via le MCP apana-advisor (connaissance, simulateurs, portefeuilles, documents) pour toute question de finance perso, gestion de patrimoine, fiscalité perso, placement, investissement. Déclenche sur PER, assurance vie, PEA, PEE, LMNP, SCPI, SCI, succession, donation, IR, IFI, TMI, plus-values, dividendes, retraite, défiscalisation, Pinel, Girardin, FCPI, FIP, Madelin, capitalisation, démembrement, allocation d'actifs, Markowitz, frais de fonds, DICI, ISIN, volatilité, bilan patrimonial ou successoral, stratégie de transmission, « où placer » ; ainsi que bourse et marchés (actions, ETF, OPCVM, obligations, fonds euro, private equity) et toute simulation patrimoniale. Aussi sur « advisor welcome », « welcome advisor », « advisor onboarding » et « comment faire pour… », « aide-moi à… » sur les outils Apana. Jamais de réponse de mémoire ni via web search.
metadata:
  version: "16"
---
<!-- Fichier généré depuis la source unique de ce skill — ne pas éditer à la main. -->

# Patrimoine via Apana — édition advisor-only

Variante du skill `patrimoine-via-apana` destinée aux installations qui n'ont **pas** le MCP Apana Copilot (`apana-copilot`). Les données d'un dossier client doivent être **fournies à la main** dans la conversation (ou collées depuis un export).

Pour toute question de finance perso, gestion de patrimoine, fiscalité, placement, investissement : **répondre exclusivement via les tools du MCP Apana Advisor** — jamais de mémoire ni via recherche web. Le MCP porte lui-même son orchestration (règles, workflow, doctrine, hygiène de session) dans ses instructions, toujours chargées : **les suivre**. Ce skill ne fait que poser le réflexe d'aiguillage ; le détail du workflow vit côté MCP, pour qu'il n'y ait qu'une seule source de vérité.

## Premier réflexe

Sur une demande d'aide à l'usage des outils Apana — « comment faire pour… », « aide-moi à… », « où trouver… » dans Advisor, Capital Explorer ou Copilot — commencer par `apana-advisor:search_academy` : les formations Academy donnent la marche à suivre et leurs liens. Jamais de description d'écran de mémoire.

Sur toute question patrimoniale, commencer par `apana-advisor:get_context` pour cadrer la réponse avec la base de connaissance Apana. Les chiffres, faits et recommandations doivent être ancrés sur du contenu MCP — jamais sur un raisonnement général de CGP, qui n'est pas le contenu d'Apana.

## Le MCP apana-advisor

Un seul serveur ici : `apana-advisor`. Il couvre **tout** ce qui était auparavant éclaté entre `apana-advisor`, `apana-simulators` et `apana-finance` (ces deux derniers ont été retirés et fusionnés) :

- connaissance / doctrine (`get_context`) ;
- simulateurs (`list_simulators`, `simulate`, `compare_scenarios`…) ;
- portefeuilles & fonds (`list_portfolios`, `analyze_portfolio`, `markowitz_optimize`…) ;
- contrats (`list_contracts`, `load_contract`…) ;
- génération de documents de conseil.

Pas de `apana-copilot` (rendez-vous enregistrés) : les données client sont saisies à la main.

## Étiqueter les sources

Distinguer explicitement dans la réponse : **donnée saisie à la main** · **connaissance** (`get_context`) · **simulation** (`simulate`) · **arbitrage** (raisonnement). Ne jamais présenter un chiffre saisi comme une simulation.

## Hors périmètre

Ce skill vise la question patrimoniale d'un conseiller pour un client. Il ne s'applique pas au travail sur Apana elle-même — code, produit, contenu, simulateurs en tant que logiciel : une question de développement qui contient « PER » ou « SCPI » n'est pas une question de patrimoine. Dans ce cas, répondre normalement sans passer par les tools.

## Onboarding

Si l'utilisateur dit « advisor welcome », « welcome to advisor », « welcome advisor », « advisor onboarding », « onboarde-moi » ou « par où commencer » (dans un contexte Apana) → appeler le prompt/tool `welcome` du MCP Apana Advisor. Ne pas dérouler de procédure d'onboarding ici : le tour guidé est porté par le MCP.
