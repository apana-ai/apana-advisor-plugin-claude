# Apana Advisor

Plugin Claude pour les **conseillers en gestion de patrimoine** : doctrine
patrimoniale sourcée et simulateurs fiscaux auditables, à jour du droit français
en vigueur.

Principe directeur : **l'IA ne calcule pas, elle pilote des calculs.** Aucun
chiffre ne sort d'un raisonnement libre du modèle — les montants viennent de
moteurs de calcul versionnés et testés, la doctrine vient d'une base de
connaissance citée avec ses sources.

## Ce que le plugin apporte

- **Doctrine patrimoniale** — fiscalité, transmission, retraite, immobilier,
  placements financiers. Chaque réponse est ancrée sur du contenu sourcé, pas
  sur la mémoire du modèle.
- **Simulateurs auditables** — impôt sur le revenu, PER, assurance-vie, SCPI,
  LMNP, bilan successoral, droits de donation, IFI, statut du dirigeant, et
  d'autres. Chaque simulation renvoie ses hypothèses et ses avertissements
  doctrinaux.
- **Analyse de portefeuille** — composition, frais, optimisation, comparaison à
  une cible.
- **Génération de documents de conseil.**

Le plugin embarque le serveur MCP Apana Advisor, présent au répertoire de
connecteurs, ainsi qu'un skill qui apprend au modèle à passer par ces outils
plutôt que de répondre de mémoire sur des sujets où une approximation coûte
cher.

## Accès

Apana Advisor est un **outil professionnel**. L'accès est provisionné par Apana :
il n'y a pas d'inscription publique. Sans compte Apana Advisor actif, la
connexion échoue et le plugin ne peut rien faire.

La connexion se fait par OAuth au premier appel d'un outil — il n'y a ni clé API
à coller, ni binaire à installer. Voir `SETUP.md`.

## Installation

```
/plugin install apana-advisor
```

Puis lancer une question patrimoniale, ou demander « onboarde-moi sur Advisor »
pour un tour guidé.

## Périmètre et responsabilité

Ce plugin est un **outil d'aide à la décision destiné à des professionnels**. Il
ne remplace pas le conseil : le conseiller reste le professionnel qui engage sa
responsabilité, vérifie les hypothèses et présente les conclusions à son client.

Les données transmises aux outils restent dans les systèmes Apana. Ce plugin
n'expose aucun accès à un CRM ni à des dossiers clients : les données d'un
dossier sont fournies à la main dans la conversation.

## Contenu

```
.claude-plugin/plugin.json   manifeste
.mcp.json                    serveur MCP distant Apana Advisor
SETUP.md                     guide de connexion
skills/                      skill de déclenchement patrimonial
```

## Support

https://advisor.apana.ai
