---
title: Verarbeiten einer SQL-Anweisung | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: edf912bf3b8073a05dd900cd00511715020ee0c2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63045500"
---
# <a name="processing-a-sql-statement"></a>Verarbeiten von SQL-Anweisungen
Ehe wir näher auf die Techniken für die Verwendung von SQL programmgesteuert, ist es erforderlich, die erläutern, wie eine SQL-Anweisung verarbeitet wird. Die Schritte gelten für alle drei Verfahren, zur Verfügung, obwohl jedes Verfahren sie zu unterschiedlichen Zeitpunkten führt. Die folgende Abbildung zeigt die Schritte beteiligt, bei der Verarbeitung einer SQL-Anweisung, die den Rest dieses Abschnitts erläutert werden.  
  
 ![Schritte zum Verarbeiten einer SQL-Anweisung](../../odbc/reference/media/pr01.gif "pr01")  
  
 Um eine SQL-Anweisung zu verarbeiten, führt ein DBMS die folgenden fünf Schritte aus:  
  
1.  Das DBMS analysiert zunächst die SQL-Anweisung. Es umbricht die Anweisung, in einzelne Wörter, die Token bezeichnet, stellt sicher, dass die Anweisung ein gültiges Verb und gültige Klauseln und So weiter. Syntaxfehler und Rechtschreibfehler können in diesem Schritt erkannt werden.  
  
2.  Das DBMS überprüft, ob die Anweisung. Er überprüft die Anweisung für den Systemkatalog. Sind alle Tabellen, die mit dem Namen in der Anweisung in der Datenbank vorhanden? Führen Sie alle Spalten vorhanden sind, und sind die Spaltennamen eindeutig? Verfügt der Benutzer die erforderlichen Berechtigungen zum Ausführen der Anweisung? In diesem Schritt können bestimmte semantische Fehler erkannt.  
  
3.  Das DBMS generiert einen Access-Plan für die Anweisung. Der Access-Plan ist eine binäre Darstellung der Schritte, die erforderlich sind, um die Anweisung auszuführen. Es ist das DBMS-Äquivalent von ausführbarem Code.  
  
4.  Das DBMS wird den Zugriffsplan optimiert. Es wird untersucht, verschiedene Möglichkeiten, um die Access-Plan durchzuführen. Kann ein Index zum Beschleunigen der Suche werden verwendet? Sollte das DBMS wenden Sie zuerst eine Suchbedingung in der Tabelle ein und verknüpfen Sie es anschließend mit Tabelle B, oder sollte es mit der Verknüpfung beginnen und verwenden Sie anschließend die Suchbedingung? Kann eine sequenzielle Suche über eine Tabelle vermieden oder reduziert werden, um eine Teilmenge der in der Tabelle? Nach der Untersuchung der alternativen, wählt das DBMS eine davon.  
  
5.  Das DBMS führt die Anweisung mit der Access-Plan.  
  
 Beim Zugriff auf die Datenbank, die sie benötigen und die Zeitspanne, während die dafür variieren die Schritte, die zum Verarbeiten einer SQL-Anweisung auf. Analysieren eine SQL-Anweisung erfordert keinen Zugriff auf die Datenbank und kann sehr schnell erfolgen. Die Optimierung auf der anderen Seite ist eine sehr CPU-intensiv verarbeiten und benötigt Zugriff auf den Systemkatalog. Für eine komplexe, mehreren Tabellen basierende Abfrage kann der Optimierer Tausende von verschiedenen Methoden zum Ausführen derselben Abfrage durchsuchen. Die Kosten der Ausführung der Abfrage ineffizient ist jedoch in der Regel so hoch, dass mehr als die Zeit, die bei der Optimierung in höhere Geschwindigkeit der abfrageausführung wiederhergestellt wird. Dies ist sogar noch wichtig, wenn derselbe optimierten Zugriffsplan zum Ausführen von Abfragen immer wieder verwendet werden kann.
