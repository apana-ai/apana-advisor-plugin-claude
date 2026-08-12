---
name: apana-advisor-setup
description: Guide de connexion au serveur MCP Apana Advisor après installation du plugin. À lire quand l'utilisateur vient d'installer le plugin, quand un tool `apana-advisor` renvoie une erreur d'authentification (401), ou quand l'utilisateur demande comment se connecter, quel compte utiliser, ou pourquoi les outils Apana ne répondent pas.
---

# Connexion à Apana Advisor

Le plugin embarque un serveur MCP **distant** (`https://advisor.apana.ai/mcp`).
Rien à installer localement : ni binaire, ni clé API à coller dans un fichier.

## Comment l'accès fonctionne

L'authentification se fait par **OAuth contre Apana Account**, au premier appel
d'un tool. Le client MCP ouvre la page de connexion, l'utilisateur s'authentifie,
et le jeton est géré par le client — jamais saisi dans la conversation.

Si un tool renvoie une erreur d'authentification, c'est que la connexion OAuth
n'a pas été faite ou a expiré. Inviter l'utilisateur à relancer la connexion du
serveur MCP `apana-advisor` depuis son client, plutôt que de chercher une clé à
configurer : il n'y en a pas.

## Accès nécessaire

Apana Advisor est un outil **professionnel destiné aux conseillers en gestion de
patrimoine**. L'accès est provisionné par Apana — il n'y a pas d'inscription
publique. Un utilisateur sans compte Apana Advisor actif verra la connexion
échouer, quelle que soit sa configuration.

Ne pas proposer de contournement : sans accès, ce plugin ne peut pas fonctionner,
et répondre de mémoire sur ces sujets est exactement ce que le skill interdit.

## Vérifier que tout fonctionne

Appeler `get_context` sur une question patrimoniale simple, ou le prompt
`welcome` pour un tour guidé. Si l'appel remonte de la doctrine sourcée, la
connexion est bonne.

## Ce que le plugin apporte une fois connecté

- **`get_context`** — la doctrine patrimoniale Apana, sourcée et citée.
- **Simulateurs** (`list_simulators`, `simulate`, `compare_scenarios`…) — des
  moteurs de calcul fiscaux auditables, à jour de la loi de finances en vigueur.
- **Portefeuilles et fonds** (`analyze_portfolio`, `markowitz_optimize`…).
- **Prompts** `about` (cadre général) et `welcome` (prise en main).

Le principe directeur, porté par les instructions du serveur MCP : **l'IA ne
calcule pas, elle pilote des calculs**. Aucun chiffre ne doit sortir d'un
raisonnement libre du modèle.
