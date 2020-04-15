---
title: Verwendung von Prozeduren | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], procedures
- procedures [ODBC], about procedures
ms.assetid: 7dc9e327-dd54-4b10-9f66-9ef5c074f122
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 31aeea226bc8c8aa41f748d1d9a97d55147c4d67
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81289097"
---
# <a name="when-to-use-procedures"></a>Verwendung von Prozeduren
Die Verwendung von Prozeduren bietet eine Reihe von Vorteilen, die alle auf der Tatsache basieren, dass sql-Anweisungen mithilfe von Prozeduren von der Anwendung in die Datenquelle verschoben werden. Was in der Anwendung verbleibt, ist ein interoperabler Prozeduraufruf. Zu diesen Vorteilen gehören:  
  
-   **Performance** Prozeduren sind in der Regel die schnellste Möglichkeit, SQL-Anweisungen auszuführen. Wie bei der vorbereiteten Ausführung wird die Anweisung in zwei separaten Schritten kompiliert und ausgeführt. Im Gegensatz zur vorbereiteten Ausführung werden Prozeduren nur zur Laufzeit ausgeführt. Sie werden zu einem anderen Zeitpunkt zusammengestellt.  
  
-   **Geschäftsregeln** Eine *Geschäftsregel* ist eine Regel über die Art und Weise, wie ein Unternehmen Geschäfte abschließt. Beispielsweise kann nur jemand mit dem Titel "Verkäufer" neue Aufträge hinzufügen. Wenn Sie diese Regeln in Prozeduren platzieren, können einzelne Unternehmen vertikale Anwendungen anpassen, indem sie die von der Anwendung aufgerufenen Prozeduren neu schreiben, ohne den Anwendungscode ändern zu müssen. Beispielsweise kann eine Auftragseingabeanwendung die Prozedur **InsertOrder** mit einer festen Anzahl von Parametern aufrufen. Wie **InsertOrder** implementiert wird, kann von Unternehmen zu Unternehmen unterschiedlich sein.  
  
-   **Austauschbarkeit** Eng mit der Platzierung von Geschäftsregeln in Verfahren verbunden ist die Tatsache, dass Verfahren ersetzt werden können, ohne die Anwendung neu zu kompilieren. Wenn sich eine Geschäftsregel ändert, nachdem ein Unternehmen eine Anwendung gekauft und installiert hat, kann das Unternehmen die Prozedur ändern, die diese Regel enthält. Aus der Sicht der Anwendung hat sich nichts geändert; Es ruft immer noch eine bestimmte Prozedur auf, um eine bestimmte Aufgabe zu erfüllen.  
  
-   **DBMS-spezifische SQL** Prozeduren bieten Anwendungen die Möglichkeit, DBMS-spezifische SQL zu nutzen und weiterhin interoperabel zu bleiben. Beispielsweise kann eine Prozedur für ein DBMS, die "Control-of-Flow-Anweisungen in SQL" unterstützt, einen Fehler abfangen und nach Fehlern wiederherstellen, während eine Prozedur auf einem DBMS, die keine "Control-of-Flow"-Anweisungen unterstützt, einfach einen Fehler zurückgibt.  
  
-   **Verfahren überleben Transaktionen** In einigen Datenquellen werden die Zugriffspläne für alle vorbereiteten Anweisungen für eine Verbindung gelöscht, wenn eine Transaktion festgeschrieben oder zurückgesetzt wird. Durch das Platzieren von SQL-Anweisungen in Prozeduren, die dauerhaft in der Datenquelle gespeichert sind, überleben die Anweisungen die Transaktion. Ob die Verfahren in einem vorbereiteten, teilweise vorbereiteten oder unvorbereiteten Zustand überleben, ist DBMS-spezifisch.  
  
-   **Getrennte Entwicklung** Verfahren können getrennt vom Rest der Anwendung entwickelt werden. In großen Unternehmen könnte dies eine Möglichkeit bieten, die Fähigkeiten hochspezialisierter Programmierer weiter zu nutzen. Mit anderen Worten, Anwendungsprogrammierer können Benutzeroberflächencode schreiben und Datenbankprogrammierer können Prozeduren schreiben.  
  
 Prozeduren werden in der Regel von vertikalen und benutzerdefinierten Anwendungen verwendet. Diese Anwendungen neigen dazu, feste Aufgaben auszuführen, und es ist möglich, Prozeduraufrufe in ihnen hart zu codieren. Beispielsweise kann eine Auftragseingabeanwendung die Prozeduren **InsertOrder**, **DeleteOrder**, **UpdateOrder**und **GetOrders**aufrufen.  
  
 Es gibt wenig Grund, Prozeduren aus generischen Anwendungen aufzurufen. Prozeduren werden in der Regel geschrieben, um eine Aufgabe im Kontext einer bestimmten Anwendung auszuführen, und haben daher keine Verwendung für generische Anwendungen. Eine Kalkulationstabelle hat z. B. keinen Grund, die soeben erwähnte **InsertOrder-Prozedur** aufzurufen. Darüber hinaus sollten generische Anwendungen zur Laufzeit keine Prozeduren erstellen, in der Hoffnung, eine schnellere Ausführung von Anweisungen bereitzustellen. Dies ist nicht nur wahrscheinlich langsamer als die vorbereitete oder direkte Ausführung, sondern erfordert auch DBMS-spezifische SQL-Anweisungen.  
  
 Eine Ausnahme bilden Anwendungsentwicklungsumgebungen, die Programmierern häufig die Möglichkeit bieten, SQL-Anweisungen zu erstellen, die Prozeduren ausführen und Programmierern die Möglichkeit bieten, Prozeduren zu testen. Solche Umgebungen rufen **SQLProcedures** auf, um verfügbare Prozeduren und **SQLProcedureColumns** aufzulisten, um die Eingabe-, Eingabe-/Ausgabe- und Ausgabeparameter, den Prozedurrückgabewert und die Spalten aller resultierenden Sätze aufzulisten, die durch eine Prozedur erstellt wurden. Diese Verfahren müssen jedoch im Voraus auf jeder Datenquelle entwickelt werden; Dazu sind DBMS-spezifische SQL-Anweisungen erforderlich.  
  
 Die Anwendung von Verfahren hat drei große Nachteile. Die erste ist, dass Prozeduren für jedes DBMS geschrieben und kompiliert werden müssen, mit dem die Anwendung ausgeführt werden soll. Dies ist zwar kein Problem für benutzerdefinierte Anwendungen, kann jedoch die Entwicklungs- und Wartungszeit für vertikale Anwendungen, die für die Ausführung mit einer Reihe von DBMS entwickelt wurden, erheblich erhöhen.  
  
 Der zweite Nachteil ist, dass viele DBMS keine Prozeduren unterstützen. Auch hier ist dies höchstwahrscheinlich ein Problem für vertikale Anwendungen, die für die Ausführung mit einer Reihe von DBMS entwickelt wurden. Um zu bestimmen, ob Prozeduren unterstützt werden, ruft eine Anwendung **SQLGetInfo** mit der Option SQL_PROCEDURES auf.  
  
 Der dritte Nachteil, der insbesondere auf Anwendungsentwicklungsumgebungen anwendbar ist, besteht darin, dass ODBC keine Standardgrammatik zum Erstellen von Prozeduren definiert. Das heißt, obwohl Anwendungen Prozeduren interoperable aufrufen können, können sie sie nicht interoperabel erstellen.
