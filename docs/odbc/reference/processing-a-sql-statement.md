---
title: Verarbeiten einer SQL-Anweisung | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- sending SQL statements to DBMS [ODBC]
- SQL statements [ODBC], processing
- SQL [ODBC], processing statements
- statement processing [ODBC]
- SQL statements [ODBC]
- ODBC [ODBC], SQL
ms.assetid: 96270c4f-2efd-4dc1-a985-ed7fd5658db2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 349a62034d598c1bfb44b891b91359d5ff184b7e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280520"
---
# <a name="processing-a-sql-statement"></a>Verarbeiten von SQL-Anweisungen
Bevor Sie die Techniken für die programmgesteuerte Verwendung von SQL diskutieren, müssen Sie die Verarbeitung einer SQL-Anweisung besprechen. Die beteiligten Schritte sind allen drei Techniken gemeinsam, obwohl jede Technik sie zu unterschiedlichen Zeiten ausführt. Die folgende Abbildung zeigt die Schritte bei der Verarbeitung einer SQL-Anweisung, die im weiteren Verlauf dieses Abschnitts erläutert werden.  
  
 ![Schritte zum Verarbeiten einer SQL-Anweisung](../../odbc/reference/media/pr01.gif "pr01")  
  
 Um eine SQL-Anweisung zu verarbeiten, führt ein DBMS die folgenden fünf Schritte aus:  
  
1.  Das DBMS analysiert zuerst die SQL-Anweisung. Es teilt die Anweisung in einzelne Wörter auf, die als Token bezeichnet werden, stellt sicher, dass die Anweisung über ein gültiges Verb und gültige Klauseln verfügt usw. In diesem Schritt können Syntaxfehler und Rechtschreibfehler erkannt werden.  
  
2.  Das DBMS überprüft die Anweisung. Die Anweisung wird mit dem Systemkatalog überprüft. Sind alle in der Anweisung genannten Tabellen in der Datenbank vorhanden? Sind alle Spalten vorhanden und sind die Spaltennamen eindeutig? Verfügt der Benutzer über die erforderlichen Berechtigungen zum Ausführen der Anweisung? In diesem Schritt können bestimmte semantische Fehler erkannt werden.  
  
3.  Das DBMS generiert einen Zugriffsplan für die Anweisung. Der Zugriffsplan ist eine binäre Darstellung der Schritte, die zum Ausführen der Anweisung erforderlich sind. Es ist das DBMS-Äquivalent von ausführbarem Code.  
  
4.  Das DBMS optimiert den Zugriffsplan. Es werden verschiedene Möglichkeiten zur Durchführung des Zugangsplans untersucht. Kann ein Index verwendet werden, um eine Suche zu beschleunigen? Soll das DBMS zunächst eine Suchbedingung auf Tabelle A anwenden und dann mit Tabelle B verknüpfen, oder sollte es mit der Verknüpfung beginnen und die Suchbedingung danach verwenden? Kann eine sequenzielle Suche durch eine Tabelle vermieden oder auf eine Teilmenge der Tabelle reduziert werden? Nachdem das DBMS die Alternativen untersucht hat, wählt es eine davon aus.  
  
5.  Das DBMS führt die Anweisung aus, indem es den Zugriffsplan ausführt.  
  
 Die Schritte, die zum Verarbeiten einer SQL-Anweisung verwendet werden, variieren in der Menge des Datenbankzugriffs, den sie benötigen, und der Zeit, die sie benötigen. Das Analysieren einer SQL-Anweisung erfordert keinen Zugriff auf die Datenbank und kann sehr schnell durchgeführt werden. Die Optimierung hingegen ist ein sehr CPU-intensiver Prozess und erfordert Zugriff auf den Systemkatalog. Bei einer komplexen Abfrage mit mehreren Tabellen kann der Optimierer Tausende von verschiedenen Möglichkeiten zur Durchführung derselben Abfrage untersuchen. Die Kosten für die ineffiziente Ausführung der Abfrage sind jedoch in der Regel so hoch, dass die für die Optimierung aufgew. Dies ist umso wichtiger, wenn derselbe optimierte Zugriffsplan immer wieder verwendet werden kann, um sich wiederholende Abfragen auszuführen.
