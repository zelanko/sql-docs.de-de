---
description: Verarbeiten von SQL-Anweisungen
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b4ce614f6dcf4c1fe0ab1e1c806b966b4267e7fe
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476217"
---
# <a name="processing-a-sql-statement"></a>Verarbeiten von SQL-Anweisungen
Bevor Sie die Techniken zur programmgesteuerten Verwendung von SQL erörtern, muss erläutert werden, wie eine SQL-Anweisung verarbeitet wird. Die erforderlichen Schritte gelten für alle drei Techniken, obwohl die einzelnen Techniken Sie zu unterschiedlichen Zeitpunkten ausführen. In der folgenden Abbildung werden die Schritte zum Verarbeiten einer SQL-Anweisung gezeigt, die im restlichen Teil dieses Abschnitts erläutert werden.  
  
 ![Schritte zum Verarbeiten einer SQL-Anweisung](../../odbc/reference/media/pr01.gif "pr01")  
  
 Ein DBMS führt die folgenden fünf Schritte aus, um eine SQL-Anweisung zu verarbeiten:  
  
1.  Das DBMS analysiert zunächst die SQL-Anweisung. Die Anweisung wird in einzelne Wörter unterteilt, die als Token bezeichnet werden, und es wird sichergestellt, dass die Anweisung über ein gültiges Verb und gültige Klauseln verfügt usw. In diesem Schritt können Syntax Fehler und falsche Rechtschreib folgen erkannt werden.  
  
2.  Das DBMS überprüft die-Anweisung. Die-Anweisung wird anhand des System Katalogs überprüft. Sind alle Tabellen, die in der-Anweisung benannt sind, in der Datenbank vorhanden? Sind alle Spalten vorhanden, und sind die Spaltennamen eindeutig? Verfügt der Benutzer über die erforderlichen Berechtigungen zum Ausführen der Anweisung? Bestimmte Semantik Fehler können in diesem Schritt erkannt werden.  
  
3.  Das DBMS generiert einen Zugriffs Plan für die-Anweisung. Der Zugriffs Plan ist eine binäre Darstellung der Schritte, die erforderlich sind, um die Anweisung auszuführen. Dies ist die DBMS-Entsprechung von ausführbarem Code.  
  
4.  Das DBMS optimiert den Zugriffs Plan. Es werden verschiedene Möglichkeiten zum Durchführen des Zugriffs Plans untersucht. Kann ein Index verwendet werden, um eine Suche zu beschleunigen? Sollte das DBMS zuerst eine Such Bedingung auf Tabelle a anwenden und es dann mit Tabelle B verknüpfen, oder sollte es mit dem Join beginnen und danach die Such Bedingung verwenden? Kann eine sequenzielle Suche durch eine Tabelle vermieden oder auf eine Teilmenge der Tabelle reduziert werden? Nach dem untersuchen der alternativen wählt das DBMS eine davon aus.  
  
5.  Das DBMS führt die Anweisung durch Ausführen des Zugriffs Plans aus.  
  
 Die Schritte, die zum Verarbeiten einer SQL-Anweisung verwendet werden, variieren je nach Umfang des benötigten Datenbankzugriffs und der benötigten Zeit. Die Ausführung einer SQL-Anweisung erfordert keinen Zugriff auf die Datenbank und kann sehr schnell erfolgen. Die Optimierung ist dagegen ein sehr CPU-intensiver Prozess und erfordert Zugriff auf den System Katalog. Bei einer komplexen, Multitable-Abfrage kann der Optimierer tausende unterschiedlicher Methoden zum Ausführen derselben Abfrage untersuchen. Die Kosten für eine ineffiziente Ausführung der Abfrage sind jedoch in der Regel so hoch, dass die für die Optimierung aufgewendeten Zeit mehr als eine höhere Ausführungsgeschwindigkeit bei der Abfrage ist. Dies ist noch wichtiger, wenn ein optimierter Zugriffs Plan immer wieder verwendet werden kann, um wiederkehrende Abfragen auszuführen.
