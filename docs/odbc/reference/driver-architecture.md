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
ms.openlocfilehash: b593c3bd8619f0fbba47357f312479c2cd14063b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63254239"
---
# <a name="driver-architecture"></a>Treiberarchitektur
Treiberarchitektur fällt in zwei Kategorien unterteilt, je nachdem welche Softwareprozessen SQL-Anweisungen:  
  
-   **Dateibasierte Treiber** der Treiber greift direkt auf die physischen Daten. In diesem Fall fungiert der Treiber als Treiber und die Datenquelle ein; wird verarbeitet, also ODBC-Aufrufe und SQL-Anweisungen. DBASE-Treiber sind beispielsweise dateibasierten Treibern, da dBASE nicht bietet, dass eine eigenständige Datenbank-Engine den Treiber verwenden kann. Es ist wichtig zu beachten, dass die Entwickler von dateibasierten Treibern eigene Datenbank-Engines schreiben müssen.  
  
-   **DBMS-basierten Treibern** der Treiber verwendet wird, greift die physikalischen Daten über eine separate Datenbank-Engine auf. In diesem Fall verarbeitet der Treiber ODBC-Aufrufe an; Es übergibt SQL-Anweisungen auf, mit der Datenbank-Engine für die Sie verarbeiten. Oracle-Treiber sind beispielsweise DBMS-basierten Treibern, da Oracle verfügt über eine eigenständige Datenbank-Engine, die der Treiber verwendet. Wo sich die Datenbank-Engine befindet, ist unerheblich. Es kann sich auf dem gleichen Computer wie der Treiber oder einem anderen Computer im Netzwerk befinden; Es kann auch über ein Gateway zugegriffen werden.  
  
 Treiberarchitektur ist in der Regel nur für Treiber Writer interessant. Treiberarchitektur macht, also in der Regel keinerlei Auswirkung auf die Anwendung. Die Architektur kann jedoch beeinflussen, ob eine Anwendung die DBMS-spezifische SQL verwenden kann. Microsoft Access bietet z. B. eine eigenständige Datenbank-Engine. Wenn ein Microsoft Access-Treiber basiert auf der DBMS - greift auf die Daten über diese-Engine – kann die Anwendung Microsoft Access-SQL-Anweisungen an die Engine für die Verarbeitung übergeben.  
  
 Allerdings sind, wenn der Treiber ist – d. h., er enthält eine proprietäre-Engine, die auf die Microsoft® Access-MDB-Datei, direkt zugreift - alle Versuche, Microsoft Access-spezifische SQL-Anweisungen an die Engine übergeben voraussichtlich zu einem Syntaxfehler führt. Der Grund ist, dass die proprietäre-Engine wahrscheinlich nur ODBC-SQL implementiert ist.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Dateibasierte Treiber](../../odbc/reference/file-based-drivers.md)  
  
-   [DBMS-basierte Treiber](../../odbc/reference/dbms-based-drivers.md)  
  
-   [Netzwerkbeispiel](../../odbc/reference/network-example.md)  
  
-   [Andere Treiberarchitekturen](../../odbc/reference/other-driver-architectures.md)
