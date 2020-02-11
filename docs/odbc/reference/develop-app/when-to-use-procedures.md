---
title: Verwendungsweise von Prozeduren | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6f25b629372bbe089489cccdbfa0258dafef3dd0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68078973"
---
# <a name="when-to-use-procedures"></a>Verwendung von Prozeduren
Die Verwendung von-Prozeduren bietet eine Reihe von Vorteilen, die auf der Tatsache basieren, dass using-Prozeduren SQL-Anweisungen von der Anwendung in die Datenquelle verschieben. Das verbleibende in der Anwendung ist ein interoperable Prozedur Aufruf. Zu diesen Vorteilen gehören:  
  
-   **Leistung** Prozeduren sind in der Regel die schnellste Möglichkeit, SQL-Anweisungen auszuführen. Wie bei der vorbereiteten Ausführung wird die-Anweisung in zwei separaten Schritten kompiliert und ausgeführt. Anders als bei der vorbereiteten Ausführung werden Prozeduren nur zur Laufzeit ausgeführt. Sie werden zu einem anderen Zeitpunkt kompiliert.  
  
-   **Geschäftsregeln** Eine *Geschäftsregel* ist eine Regel bezüglich der Art und Weise, in der ein Unternehmen geschäftlich funktioniert. So kann z. b. nur jemand mit dem Titel Sales Person berechtigt sein, neue Verkaufsaufträge hinzuzufügen. Durch das Platzieren dieser Regeln in Prozeduren können einzelne Unternehmen vertikale Anwendungen anpassen, indem Sie die von der Anwendung aufgerufenen Prozeduren umschreiben, ohne den Anwendungscode ändern zu müssen. Beispielsweise kann eine Anwendung für den Bestell Eintrag die Prozedur **InsertOrder** mit einer bestimmten Anzahl von Parametern aufrufen. die Art und Weise, wie **insertor** implementiert ist, kann von Unternehmen zu Unternehmen variieren.  
  
-   **Replaceability** Eine enge Beziehung zum Platzieren von Geschäftsregeln in Prozeduren ist die Tatsache, dass Prozeduren ohne erneutes Kompilieren der Anwendung ersetzt werden können. Wenn sich eine Geschäftsregel ändert, nachdem ein Unternehmen eine Anwendung gekauft und installiert hat, kann das Unternehmen die Prozedur ändern, die diese Regel enthält. Aus Sicht der Anwendung hat sich nichts geändert. Es wird immer noch ein bestimmtes Verfahren aufgerufen, um eine bestimmte Aufgabe auszuführen.  
  
-   **DBMS-spezifisches SQL** Mit Prozeduren können Anwendungen DBMS-spezifische SQL-Anwendungen ausnutzen und trotzdem interoperabel bleiben. Eine Prozedur in einem DBMS, die Anweisungen zur Ablauf Steuerung in SQL unterstützt, könnte z. b. nach Fehlern abgefangen und wieder hergestellt werden, während eine Prozedur in einem DBMS, die Anweisungen zur Ablauf Steuerung nicht unterstützt, möglicherweise einfach einen Fehler zurückgibt.  
  
-   **Prozeduren überleben Transaktionen** Bei einigen Datenquellen werden die Zugriffs Pläne für alle vorbereiteten Anweisungen für eine Verbindung gelöscht, wenn für eine Transaktion ein Commit oder ein Rollback ausgeführt wird. Durch das Platzieren von SQL-Anweisungen in Prozeduren, die dauerhaft in der Datenquelle gespeichert werden, überstehen die Anweisungen die Transaktion. Ob die Prozeduren in einem vorbereiteten, teilweise vorbereiteten oder nicht vorbereiteten Zustand bestehen, ist DBMS-spezifisch.  
  
-   **Separate Entwicklung** Prozeduren können getrennt vom Rest der Anwendung entwickelt werden. In großen Unternehmen stellt dies möglicherweise eine Möglichkeit dar, die Fähigkeiten von sehr spezialisierten Programmierern zu nutzen. Mit anderen Worten, Anwendungsprogrammierer können Benutzeroberflächen Code schreiben, und Daten Bank Programmierer können Prozeduren schreiben.  
  
 Prozeduren werden im Allgemeinen von vertikalen und benutzerdefinierten Anwendungen verwendet. Diese Anwendungen führen in der Regel feste Aufgaben aus, und es ist möglich, Prozedur Aufrufe in den Code auszuführen. Beispielsweise kann eine Anwendung für den Bestell Eintrag die Prozeduren **InsertOrder**, **DeleteOrder**, **UpdateOrder**und **GetOrders**aufrufen.  
  
 Es gibt kaum einen Grund, Prozeduren von generischen Anwendungen aufzurufen. Prozeduren werden in der Regel so geschrieben, dass Sie eine Aufgabe im Kontext einer bestimmten Anwendung ausführen und somit keine generischen Anwendungen verwenden können. Eine Kalkulations Tabelle hat z. b. keinen Grund, die soeben erwähnte **InsertOrder** -Prozedur aufzurufen. Außerdem sollten generische Anwendungen zur Laufzeit keine Prozeduren erstellen, um eine schnellere Anweisungs Ausführung bereitzustellen. Es ist nicht nur sehr wahrscheinlich langsamer als die vorbereitete oder direkte Ausführung, sondern erfordert auch DBMS-spezifische SQL-Anweisungen.  
  
 Eine Ausnahme hiervon sind Anwendungsentwicklungsumgebungen, die Programmierern häufig die Möglichkeit bieten, SQL-Anweisungen zu erstellen, die Prozeduren ausführen, und Programmierern eine Möglichkeit bieten, Prozeduren zu testen. In solchen Umgebungen werden **SQLProcedures** zum Auflisten der verfügbaren Prozeduren und **SQLProcedureColumns** zum Auflisten der Eingabe-, Eingabe-/Ausgabe-und Ausgabeparameter, des Rückgabewerts der Prozedur und der Spalten aller von einer Prozedur erstellten Resultsets aufgerufen. Diese Prozeduren müssen jedoch im Voraus für jede Datenquelle entwickelt werden. hierfür sind DBMS-spezifische SQL-Anweisungen erforderlich.  
  
 Es gibt drei wesentliche Nachteile bei der Verwendung von Prozeduren. Der erste besteht darin, dass Prozeduren für jedes DBMS geschrieben und kompiliert werden müssen, mit dem die Anwendung ausgeführt werden soll. Obwohl dies kein Problem für benutzerdefinierte Anwendungen ist, kann es die Entwicklungs-und Wartungszeit für vertikale Anwendungen, die auf eine Reihe von DBMSs ausgelegt sind, erheblich erhöhen.  
  
 Der zweite Nachteil ist, dass viele DBMSs keine Prozeduren unterstützen. Dies ist in der Regel ein Problem bei vertikalen Anwendungen, die auf eine Reihe von DBMSs ausgelegt sind. Um zu ermitteln, ob Prozeduren unterstützt werden, ruft eine Anwendung **SQLGetInfo** mit der SQL_PROCEDURES-Option auf.  
  
 Der dritte Nachteil, der insbesondere auf Anwendungsentwicklungsumgebungen anwendbar ist, besteht darin, dass ODBC keine Standard Grammatik zum Erstellen von Prozeduren definiert. Das heißt, obwohl Anwendungen interoperabel Prozeduren aufzurufen, können Sie diese nicht interoperabel erstellen.
