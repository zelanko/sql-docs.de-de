---
title: Auswählen einer SQL-Grammatik | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299160"
---
# <a name="choosing-an-sql-grammar"></a>Auswählen einer SQL-Grammatik
Die erste Entscheidung, die Sie beim Erstellen von SQL-Anweisungen treffen müssen, ist die zu verwendende Grammatik. Zusätzlich zu den Grammatiken, die in den verschiedenen Standard Textteilen verfügbar sind, wie z. b. Open Group, ANSI und ISO, definiert praktisch jeder DBMS-Anbieter seine eigene Grammatik, die jeweils leicht vom Standard abweicht.  
  
 [Anhang C: SQL-Grammatik:](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md)beschreibt die minimale SQL-Grammatik, die alle ODBC-Treiber unterstützen müssen. Diese Grammatik ist eine Teilmenge der Einstiegsebene von SQL-92. Treiber können zusätzliche Grammatik unterstützen, um den von SQL-92 definierten Übergangs Ebenen zwischen, vollständig 127-2 oder von der durch SQL-definierten Übergangs Ebene zu entsprechen. Weitere Informationen finden Sie unter [minimale SQL-Grammatik](../../../odbc/reference/appendixes/sql-minimum-grammar.md) in Anhang C: SQL-Grammatik und SQL-92.  
  
 Anhang *C definiert auch* Escapesequenzen, die eine Standard Grammatik für häufig verfügbare sprach Features wie äußere Joins enthalten, die nicht von der SQL-92-Grammatik abgedeckt werden. Weitere Informationen finden Sie unter [ODBC](../../../odbc/reference/appendixes/odbc-escape-sequences.md) -Escapesequenzen in Anhang C: SQL [Escape Sequences](../../../odbc/reference/develop-app/escape-sequences.md)-Grammatik und Escapesequenzen weiter unten in diesem Abschnitt.  
  
 Die gewählte Grammatik wirkt sich darauf aus, wie der Treiber die Anweisung verarbeitet. Treiber müssen SQL-92 SQL und die ODBC-definierten Escapesequenzen in DBMS-spezifische SQL-Informationen ändern. Da die meisten SQL-Grammatiken auf einem oder mehreren der verschiedenen Standards basieren, führen die meisten Treiber nur wenig oder gar keine Arbeit aus, um diese Anforderung zu erfüllen. Sie besteht häufig nur aus der Suche nach den von ODBC definierten Escapesequenzen und der Ersetzung durch die DBMS-spezifische Grammatik. Wenn ein Treiber auf eine Grammatik stößt, wird davon ausgegangen, dass die Grammatik DBMS-spezifisch ist, und die SQL-Anweisung ohne Änderung an die Datenquelle zur Ausführung übergibt.  
  
 Daher gibt es wirklich zwei Optionen für die Grammatik: die SQL-92-Grammatik (und die ODBC-Escapesequenzen) und eine DBMS-spezifische Grammatik. Von den beiden ist nur die SQL-92-Grammatik interoperabel, sodass alle interoperablen Anwendungen Sie verwenden sollten. Anwendungen, die nicht interoperabel sind, können die SQL-92-Grammatik oder eine DBMS-spezifische Grammatik verwenden. DBMS-spezifische Grammatiken haben zwei Vorteile: Sie können alle Features ausnutzen, die nicht von SQL-92 abgedeckt werden, und Sie sind geringfügig schneller, da Sie vom Treiber nicht geändert werden müssen. Diese Funktion kann teilweise durch Festlegen des Attributs SQL_ATTR_NOSCAN Anweisung erzwungen werden, das den Treiber daran hindert, Escapesequenzen zu suchen und zu ersetzen.  
  
 Wenn die SQL-92-Grammatik verwendet wird, kann die Anwendung ermitteln, wie Sie vom Treiber durch Aufrufen von **SQLNativeSql**geändert wird. Dies ist beim Debuggen von Anwendungen häufig nützlich. **SQLNativeSql** akzeptiert eine SQL-Anweisung und gibt Sie zurück, nachdem der Treiber Sie geändert hat. Da diese Funktion den Übereinstimmungs Grad der Kernschnittstelle hat, wird Sie von allen Treibern unterstützt.
