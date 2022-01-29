---
title: "Il y a au moins quatre types de programme"
date: 2022-01-29T11:58:40-05:00
draft: false
summary: ""
---

* Un **SCRIPT** est un programme pour accomplir une tâche déterminée,
  souvent assez procédurale par nature, qui utilise peu de mécanismes
  d'abstraction, et qui peut souvent se contenter de celles offertes
  par la librairie standard (du langage dans lequel il est écrit). Un
  script peut être composé d'autres scripts, et sa complexité est très
  variable. Un script est idéalement documenté, mais ça sera
  typiquement à l'usage de son propre utilisateur (possiblement son
  "moi futur", qui aura oublié les détails). L'interface d'un script
  est souvent textuelle, via la ligne de commande.

* Une **APPLICATION** fait référence à un concept plus large, qui
  effectue souvent une collection de tâches (aussi généralement
  procédurales) d'une manière intégrée, et nécessitant souvent la
  coordination de ressources ou de composantes externes (une base de
  données par exemple). Une application gère et sert souvent un groupe
  d'usagers, et elle fera souvent usage des abstractions définies par
  un ensemble de librairies, et sera aussi souvent définie dans le
  contexte méthodologique et opérationel d'un framework. La
  documentation qui accompagne une application est souvent pour usage
  interne, à l'intention des programmeurs. L'interface d'une
  application est souvent de nature visuelle (GUI).

* La **LIBRAIRIE** est un type de logiciel qui propose des composantes
  réutilisables, des concepts et des abstractions (permettant de
  modéliser un domaine ou un problème particulier), en tant que "blocs
  de construction", ce qui constitue son interface (qui est donc de
  nature surtout logique et conceptuelle). Son but est strictement
  d'être utilisée par d'autres programmes. La documentation d'une
  librairie est particulièrement cruciale, et l'alliage entre les
  abstractions logicielles proposées et les explications jouent
  souvent un rôle important dans la perception de qualité, ou sa
  popularité.

* Le **FRAMEWORK** est une librairie augmentée d'une méthodologie (et
  souvent philosophie) de développement, dont l'usage va déterminer la
  forme et le style du programme qui l'utilise. Il est souvent aussi
  une "collection de bonnes pratiques", qui résolvent des problèmes
  structuraux et récurrents, bien connus et documentés. Sa
  documentation est souvent quasiment un manifeste, qui tente de
  convaincre les usagers des bénéfices techniques qu'ils pourront
  retirer de son usage.
