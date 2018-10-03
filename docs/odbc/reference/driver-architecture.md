---
title: Treiberarchitektur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC architecture [ODBC], drivers
- drivers [ODBC], architecture
ms.assetid: c5003413-0cc1-4f41-b877-a64e2f5ab118
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a8e49b89d233880652f4b19879ff8e658bc4abe1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47628398"
---
# <a name="driver-architecture"></a>Treiberarchitektur
Treiberarchitektur fällt in zwei Kategorien unterteilt, je nachdem welche Softwareprozessen SQL-Anweisungen:  
  
-   **Dateibasierte Treiber** der Treiber greift direkt auf die physischen Daten. In diesem Fall fungiert der Treiber als Treiber und die Datenquelle ein; wird verarbeitet, also ODBC-Aufrufe und SQL-Anweisungen. DBASE-Treiber sind beispielsweise dateibasierten Treibern, da dBASE nicht bietet, dass eine eigenständige Datenbank-Engine den Treiber verwenden kann. Es ist wichtig zu beachten, dass die Entwickler von dateibasierten Treibern eigene Datenbank-Engines schreiben müssen.  
  
-   **DBMS-basierten Treibern** der Treiber verwendet wird, greift die physikalischen Daten über eine separate Datenbank-Engine auf. In diesem Fall verarbeitet der Treiber ODBC-Aufrufe an; Es übergibt SQL-Anweisungen auf, mit der Datenbank-Engine für die Sie verarbeiten. Oracle-Treiber sind beispielsweise DBMS-basierten Treibern, da Oracle verfügt über eine eigenständige Datenbank-Engine, die der Treiber verwendet. Wo sich die Datenbank-Engine befindet, ist unerheblich. Es kann sich auf dem gleichen Computer wie der Treiber oder einem anderen Computer im Netzwerk befinden; Es kann auch über ein Gateway zugegriffen werden.  
  
 Treiberarchitektur ist in der Regel nur für Treiber Writer interessant. Treiberarchitektur macht, also in der Regel keinerlei Auswirkung auf die Anwendung. Die Architektur kann jedoch beeinflussen, ob eine Anwendung die DBMS-spezifische SQL verwenden kann. Microsoft Access bietet z. B. eine eigenständige Datenbank-Engine. Ist ein Microsoft Access-Treiber DBMS-basierten – greift auf die Daten über diese-Engine – die Anwendung kann Microsoft Access – SQL-Anweisungen an die Engine für die Verarbeitung übergeben.  
  
 Jedoch ist der Treiber dateibasierte – d. h., er enthält eine proprietäre-Engine, die auf die Microsoft® Access-MDB-Datei direkt zugreift, alle Versuche, Microsoft Access-spezifische SQL-Anweisungen an die Engine übergeben werden voraussichtlich zu einem Syntaxfehler führt. Der Grund ist, dass die proprietäre-Engine wahrscheinlich nur ODBC-SQL implementiert ist.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Dateibasierte Treiber](../../odbc/reference/file-based-drivers.md)  
  
-   [DBMS-basierte Treiber](../../odbc/reference/dbms-based-drivers.md)  
  
-   [Netzwerkbeispiel](../../odbc/reference/network-example.md)  
  
-   [Andere Treiberarchitekturen](../../odbc/reference/other-driver-architectures.md)
