---
title: Auswählen einer SQL-Grammatik | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], SQL grammar
- SQL grammar [ODBC], selecting
ms.assetid: 4e0d189b-e407-47e0-92a9-f9982230dd0e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2ca9911d3c88f2f540ff1332d77a2e1ebc6a4942
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299160"
---
# <a name="choosing-an-sql-grammar"></a>Auswählen einer SQL-Grammatik
Die erste Entscheidung, die beim Erstellen von SQL-Anweisungen getroffen werden soll, ist die grammatikalische Grammatik, die verwendet werden soll. Zusätzlich zu den Grammatiken, die von den verschiedenen Normungsgremien wie Open Group, ANSI und ISO zur Verfügung stehen, definiert praktisch jeder DBMS-Anbieter seine eigene Grammatik, die jeweils geringfügig vom Standard abgeht.  
  
 [Anhang C: SQL Grammar](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md)beschreibt die minimale SQL-Grammatik, die alle ODBC-Treiber unterstützen müssen. Diese Grammatik ist eine Teilmenge der Einstiegsebene von SQL-92. Treiber können zusätzliche Grammatik unterstützen, um den von SQL-92 definierten Zwischen-, Voll- oder FIPS 127-2-Übergangsstufen zu entsprechen. Weitere Informationen finden Sie unter SQL Minimum Grammar in Anhang C: SQL Grammar und SQL-92.For more information, see [SQL Minimum Grammar](../../../odbc/reference/appendixes/sql-minimum-grammar.md) in Appendix C: SQL Grammar, and SQL-92.  
  
 Anhang C definiert auch *Escapesequenzen,* die Standardgrammatik für allgemein verfügbare Sprachfeatures enthalten, z. B. äußere Verknüpfungen, die nicht von der SQL-92-Grammatik abgedeckt werden. Weitere Informationen finden Sie weiter unten in diesem Abschnitt unter [ODBC Escape Sequences](../../../odbc/reference/appendixes/odbc-escape-sequences.md) in Anhang C: SQL Grammar und [Escape Sequences](../../../odbc/reference/develop-app/escape-sequences.md).  
  
 Die ausgewählte Grammatik wirkt sich darauf aus, wie der Treiber die Anweisung verarbeitet. Treiber müssen SQL-92 SQL und die ODBC-definierten Escapesequenzen in DBMS-spezifischeSQL ändern. Da die meisten SQL-Grammatiken auf einem oder mehreren der verschiedenen Standards basieren, leisten die meisten Treiber wenig oder gar keine Arbeit, um diese Anforderung zu erfüllen. Es besteht oft nur darin, nach den von ODBC definierten Escapesequenzen zu suchen und sie durch DBMS-spezifische Grammatik zu ersetzen. Wenn ein Treiber auf Grammatik stößt, die er nicht erkennt, geht er davon aus, dass die Grammatik DBMS-spezifisch ist, und übergibt die SQL-Anweisung ohne Änderung an die Datenquelle für die Ausführung.  
  
 Daher gibt es wirklich zwei Möglichkeiten der Grammatik zu verwenden: die SQL-92-Grammatik (und die ODBC-Escape-Sequenzen) und eine DBMS-spezifische Grammatik. Von den beiden ist nur die SQL-92-Grammatik interoperabel, daher sollten alle interoperablen Anwendungen sie verwenden. Anwendungen, die nicht interoperabel sind, können die SQL-92-Grammatik oder eine DBMS-spezifische Grammatik verwenden. DBMS-spezifische Grammatiken haben zwei Vorteile: Sie können alle Features ausnutzen, die nicht von SQL-92 abgedeckt sind, und sie sind geringfügig schneller, da der Treiber sie nicht ändern muss. Das letztgenannte Feature kann teilweise erzwungen werden, indem das SQL_ATTR_NOSCAN Anweisungsattribut gesetzt wird, wodurch der Treiber die Suche nach Escapesequenzen verhindert und ersetzt.  
  
 Wenn die SQL-92-Grammatik verwendet wird, kann die Anwendung ermitteln, wie sie vom Treiber geändert wird, indem sie **SQLNativeSql**aufruft. Dies ist häufig nützlich, wenn Anwendungen gedebugft werden. **SQLNativeSql** akzeptiert eine SQL-Anweisung und gibt sie zurück, nachdem der Treiber sie geändert hat. Da sich diese Funktion in der Core-Schnittstellenkonformitätsebene befindet, wird sie von allen Treibern unterstützt.
