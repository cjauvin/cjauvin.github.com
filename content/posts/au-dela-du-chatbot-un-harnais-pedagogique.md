---
title: "Au-delà du chatbot : un harnais pédagogique"
date: 2026-07-25T10:29:33-04:00
draft: false
---

_Cet article a aussi été publié sur mon [Substack](https://cjauvin.substack.com/p/au-dela-du-chatbot-un-harnais-pedagogique)._

Dans le contexte de la révolution en cours dans le monde de l'IA, on peut
parfois avoir l'impression que les néologismes apparaissent de manière trop
rapide et désordonnée, et qu'il est difficile de suivre leur évolution. Le fait
que ces néologismes apparaissent tout d'abord en anglais n'aide pas, car la
plupart n'obtiennent jamais de traductions satisfaisantes ou officielles, et on
est donc condamnés, en tant que francophones, à les utiliser tels quels dans nos
phrases.

## Les agents

Dans les semaines qui ont suivi l'introduction de ChatGPT, en novembre 2022, un
nouveau terme est rapidement apparu dans la sous-culture de l'IA : *agent*. Ce
terme existait en fait depuis longtemps, pour désigner la notion d'un programme
autonome (d'IA ou non), capable de prendre des décisions, et d'évoluer par
lui-même dans un contexte inconnu. Mais l'introduction des LLM lui a donné un
nouveau souffle de vie. Un problème subsistait toutefois avec la notion d'agent :
ce n'était pas si clair, ce *qu'est* un agent. Plusieurs définitions existaient
en parallèle.

Au bout d'un certain temps à macérer dans cette incertitude sémantique, le
blogueur Simon Willison a publié un billet intitulé [I think "agent" may finally
have a widely enough agreed upon definition to be useful jargon
now](https://simonwillison.net/2025/Sep/18/agents/). La définition d'un agent est
donc devenue : *un modèle (LLM) qui tourne dans une boucle, dans le but
d'accomplir un but.*

## Les outils

Ceci n'était que le début de la révolution "agentique". Car ce n'est pas
suffisant, pour un modèle, de "tourner dans une boucle", pour accomplir un but.
Le modèle doit aussi avoir accès à des outils, pour pouvoir accomplir des
actions. Tout d'abord qu'est-ce que cela veut dire, pour un modèle, d'utiliser un
outil? Un modèle exprime le besoin d'utiliser un outil de la même manière qu'il
le fait pour le choix de ses réponses : en émettant une série de mots (tokens) à
cet effet. Si je demande à un LLM, par exemple, quelle sera la température à
Montréal demain, il peut répondre essentiellement de trois manières :

1. Il peut inventer (halluciner) une réponse
2. Il peut reconnaitre qu'il ne le sait pas
3. Il peut décider de faire une recherche avec un outil (l'API d'un service météo)

Dans le cas 3, l'environnement dans lequel s'exécute le modèle lui permettra,
momentanément, d'invoquer un outil pour consulter un aspect du monde extérieur,
et la réponse lui sera retournée (sous forme textuelle), qu'il pourra ensuite
utiliser.

## Un harnais agentique

L'informatique agentique a très vite emboité le pas sur cette idée, et les
systèmes pour le développement de code ont très vite évolué. Claude Code, apparu
en février 2025, constitue un des outils agentiques les plus connus et populaires
à ce jour. Claude Code est capable d'utiliser des outils locaux sur un ordinateur
(pour lire, chercher et modifier des fichiers par exemple) ce qui lui permet de
travailler de manière beaucoup plus efficace et intégrée à un projet de
développement (que s'il était un simple chatbot). Mais il faut comprendre que
Claude Code est plus que simplement la *capacité*, pour un modèle, d'utiliser des
outils; il s'agit en fait d'un programme complexe (écrit dans le langage
TypeScript), qui orchestre et organise les interactions entre un modèle (comme
Claude ou ChatGPT) et des outils se trouvant sur un ordinateur particulier (comme
*grep*, *ls*, ou autres outils classiques de la console Unix ou Linux, qui sont
utilisés depuis des décennies par les développeurs).

Dans la foulée de l'évolution des outils de ce genre, un nouveau terme est apparu
pour les décrire : *harness* (harnais). Un harnais est donc un assemblage
logiciel, qui organise, orchestre le travail concret effectué par un modèle, dans
un contexte donné.

## Un harnais pédagogique

J'ai proposé récemment un prototype pour un nouveau type de cours en ligne, dont
le déroulement est organisé autour d'une conversation dialectique avec un modèle.
Si ma proposition était seulement basée sur un chatbot classique, le modèle
pourrait converser, répondre à des questions des étudiants, mais il ne pourrait
pas.. *donner* le cours. Un cours n'est pas une conversation sans forme ni
structure, il s'agit plutôt d'une séquence ordonnée et procédurale, basée sur une
arborescence de documents, d'exercices, de travaux à accomplir, etc. Un modèle ne
peut donc pas, à lui seul, implémenter le substrat d'un cours. Mon prototype
introduit donc l'idée d'un *harnais pédagogique*, pour permettre au modèle de
suivre la procédure d'un cours. La matière du cours, sous forme classique
(essentiellement des textes, ou des pages web, pour un cours en ligne) sert de
substrat de base, la référence canonique. Mais elle est ensuite organisée dans
une structure de donnée nommée *beat,* qui permet d'exprimer certaines
contraintes. Par exemple, tant qu'un étudiant n'aura pas répondu de manière
satisfaisante à une question de développement de la part du modèle, ce dernier
pourra réessayer, de différentes manières, d'atteindre son but. Le *beat* ne sera
pas terminé tant que certaines exigences ne seront pas remplies. Certains
matériels pédagogiques non-textuels, comme des images ou des applets
interactives, peuvent également être introduits et utilisés aux moments opportuns
dans le déroulement du cours, et c'est la mission du harnais pédagogique
d'orchestrer le tout. Le harnais pédagogique joue un rôle similaire à celui du
harnais agentique (i.e. Claude Code) : il s'agit d'une couche applicative qui
sert à l'orchestration d'une tâche complexe (donner le cours), qui sera accomplie
par un modèle.

Mon idée de harnais pédagogique ressemble un peu à des idées classiques en
intelligence artificielle classique (bien avant l'émergence de l'apprentissage
automatique et des LLM modernes) : les *frames*, de Marvin Minsky, et les
*scripts*, de Roger Schank. Ces mécanismes permettaient de représenter les
particularités d'une situation ou d'un contexte donné, de manière à permettre à
un "moteur applicatif" de les exploiter, de manière programmatique.
