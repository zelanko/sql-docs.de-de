---
title: ODBC-Treiberarchitektur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], architecture
ms.assetid: 21a62c7c-192e-4718-a16e-aa12b0de4419
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5d123bdf1ea3357a4846a223c41950c952c1af2d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67915533"
---
# <a name="odbc-driver-architecture"></a>ODBC-Treiberarchitektur
Treiber-Autoren müssen bewusst sein, dass die Treiberarchitektur auswirken kann, ob eine Anwendung die DBMS-spezifische SQL verwenden kann.  
  
 ![Zeigt die ODBC-Treiberarchitektur](../../../odbc/reference/develop-driver/media/odbcdriverovruarch.gif "ODBCDriverOvruArch")  
  
 [Dateibasierte Treiber](../../../odbc/reference/file-based-drivers.md)  
  
 Wenn der Treiber direkt auf die physischen Daten zugreift, fungiert als Quelle für den Treiber und Daten der Treiber. Der Treiber muss sowohl die ODBC-Aufrufe als auch die SQL-Anweisungen verarbeiten. Entwickler von dateibasierten Treibern müssen ihre eigenen Datenbank-Engines schreiben.  
  
 [DBMS-basierte Treiber](../../../odbc/reference/dbms-based-drivers.md)  
  
 Wenn eine separate Datenbank-Engine verwendet wird, den Zugriff auf physischen Daten, verarbeitet der Treiber ODBC-Aufrufe. Es übergibt SQL-Anweisungen auf, mit der Datenbank-Engine für die Sie verarbeiten.  
  
 [Netzwerkarchitektur](../../../odbc/reference/network-example.md)  
  
 Datei und DBMS-ODBC-Konfigurationen können in einem einzigen Netzwerk vorhanden sein.  
  
 [Andere Treiberarchitekturen](../../../odbc/reference/other-driver-architectures.md)  
  
 Wenn ein Treiber für die Arbeit mit einer Vielzahl von Datenquellen erforderlich ist, kann es als Middleware verwendet werden. Heterogenen Join-Engine-Architektur kann es sich um den Treiber, die als einen Treiber-Manager angezeigt werden machen. Treiber können auch auf Servern installiert werden, in dem sie durch eine Reihe von Clients freigegeben werden können.  
  
 Weitere Informationen zu Architektur, finden Sie unter [-Treiber-Manager](../../../odbc/reference/the-driver-manager.md) und [Treiberarchitektur](../../../odbc/reference/driver-architecture.md) im Abschnitt zu [ODBC-Architektur](../../../odbc/reference/odbc-architecture.md).  
  
 Weitere Informationen zu Treiberproblemen finden Sie in den Speicherorten, die in der folgenden Tabelle beschrieben.  
  
|Problem|Thema|Speicherort|  
|-----------|-----------|--------------|  
|Kompatibilitätsprobleme mit Anwendungen und Treiber|[Anwendung/Treiberkompatibilität](../../../odbc/reference/develop-app/application-and-driver-compatibility.md)|[Überlegungen zur Programmierung von](../../../odbc/reference/develop-app/programming-considerations.md), in der ODBC Programmer's Reference|  
|Schreiben von ODBC-Treiber|[Schreiben von ODBC-3.x-Treibern](../../../odbc/reference/develop-app/writing-odbc-3-x-drivers.md)|[Überlegungen zur Programmierung von](../../../odbc/reference/develop-app/programming-considerations.md), in der ODBC Programmer's Reference|  
|Treiber-Richtlinien für die Abwärtskompatibilität|[Treiber-Richtlinien für die Abwärtskompatibilität](../../../odbc/reference/appendixes/appendix-g-driver-guidelines-for-backward-compatibility.md)|[Anhang G: Treiber-Richtlinien für die Abwärtskompatibilität](../../../odbc/reference/appendixes/appendix-g-driver-guidelines-for-backward-compatibility.md), in der ODBC Programmer's Reference|  
|Herstellen einer Verbindung zu einem Treiber|[Auswählen einer Datenquelle oder eines Treibers](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md)|[Herstellen einer Verbindung mit einer Datenquelle oder einem Treiber](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md), in der ODBC Programmer's Reference|  
|Identifizieren von Treibern|[Anzeigen von Treibern](../../../odbc/admin/viewing-drivers.md)|[Anzeigen von Treibern](../../../odbc/admin/viewing-drivers.md), in der Onlinehilfe von Microsoft ODBC-Datenquellen-Administrator|  
|Aktivieren von Verbindungspooling|[ODBC-Verbindungspooling](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md)|[Herstellen einer Verbindung mit einer Datenquelle oder einem Treiber](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md), in der ODBC Programmer's Reference|  
|Unicode/ANSI-Treiber und -Verbindungsprobleme|[Unicode-Treiber](../../../odbc/reference/develop-app/unicode-drivers.md)|[Überlegungen zur Programmierung von](../../../odbc/reference/develop-app/programming-considerations.md), in der ODBC Programmer's Reference|  
  
## <a name="see-also"></a>Siehe auch  
 [Developing an ODBC Driver (Entwickeln eines ODBC-Treibers)](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)
