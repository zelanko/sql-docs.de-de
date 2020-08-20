---
description: ODBC-Treiberarchitektur
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1789d5799ed9eb15ace7ea263d1a5804c8e86e74
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476246"
---
# <a name="odbc-driver-architecture"></a>ODBC-Treiberarchitektur
Treiber-Writer müssen beachten, dass die Treiberarchitektur sich darauf auswirken kann, ob eine Anwendung DBMS-spezifisches SQL verwenden kann.  
  
 ![Stellt die ODBC-Treiberarchitektur dar.](../../../odbc/reference/develop-driver/media/odbcdriverovruarch.gif "Odbcdriverovruarch")  
  
 [Dateibasierte Treiber](../../../odbc/reference/file-based-drivers.md)  
  
 Wenn der Treiber direkt auf die physischen Daten zugreift, fungiert der Treiber sowohl als Treiber als auch als Datenquelle. Der Treiber muss sowohl ODBC-Aufrufe als auch SQL-Anweisungen verarbeiten. Entwickler von dateibasierten Treibern müssen eigene Datenbank-Engines schreiben.  
  
 [DBMS-basierte Treiber](../../../odbc/reference/dbms-based-drivers.md)  
  
 Wenn für den Zugriff auf physische Daten eine separate Datenbank-Engine verwendet wird, verarbeitet der Treiber nur ODBC-Aufrufe. SQL-Anweisungen werden zur Verarbeitung an die Datenbank-Engine weitergeleitet.  
  
 [Netzwerkarchitektur](../../../odbc/reference/network-example.md)  
  
 Datei-und DBMS-ODBC-Konfigurationen können in einem einzelnen Netzwerk vorhanden sein.  
  
 [Andere Treiberarchitekturen](../../../odbc/reference/other-driver-architectures.md)  
  
 Wenn ein Treiber für die Arbeit mit einer Vielzahl von Datenquellen erforderlich ist, kann er als Middleware verwendet werden. Die Architektur des heterogenen joinmoduls kann dazu führen, dass der Treiber als Treiber Manager angezeigt wird. Treiber können auch auf Servern installiert werden, wo Sie von einer Reihe von Clients gemeinsam genutzt werden können.  
  
 Weitere Informationen zur Treiberarchitektur finden Sie unter [Treiber-Manager](../../../odbc/reference/the-driver-manager.md) und [Treiberarchitektur](../../../odbc/reference/driver-architecture.md) im Abschnitt zur [ODBC-Architektur](../../../odbc/reference/odbc-architecture.md).  
  
 Weitere Informationen zu Treiber Problemen finden Sie in den in der folgenden Tabelle beschriebenen Speicherorten.  
  
|Problem|Thema|Standort|  
|-----------|-----------|--------------|  
|Kompatibilitätsprobleme mit Anwendungen und Treibern|[Anwendungs-/Treiberkompatibilität](../../../odbc/reference/develop-app/application-and-driver-compatibility.md)|[Überlegungen zur Programmierung](../../../odbc/reference/develop-app/programming-considerations.md)in der ODBC-Programmier Referenz|  
|Schreiben von ODBC-Treibern|[Schreiben von ODBC-3.x-Treibern](../../../odbc/reference/develop-app/writing-odbc-3-x-drivers.md)|[Überlegungen zur Programmierung](../../../odbc/reference/develop-app/programming-considerations.md)in der ODBC-Programmier Referenz|  
|Treiber Richtlinien für die Abwärtskompatibilität|[Treiberrichtlinien für Abwärtskompatibilität](../../../odbc/reference/appendixes/appendix-g-driver-guidelines-for-backward-compatibility.md)|[Anhang G: Treiber Richtlinien für](../../../odbc/reference/appendixes/appendix-g-driver-guidelines-for-backward-compatibility.md)die Abwärtskompatibilität in der ODBC-Programmier Referenz|  
|Herstellen einer Verbindung mit einem Treiber|[Auswählen einer Datenquelle oder eines Treibers](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md)|[Herstellen einer Verbindung mit einer Datenquelle oder einem Treiber](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md)in der ODBC-Programmier Referenz|  
|Identifizieren von Treibern|[Anzeigen von Treibern](../../../odbc/admin/viewing-drivers.md)|[Anzeigen von Treibern](../../../odbc/admin/viewing-drivers.md)in der Online Hilfe des Microsoft ODBC-Datenquellen-Administrators|  
|Aktivieren von Verbindungspooling|[ODBC-Verbindungs Pooling](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md)|[Herstellen einer Verbindung mit einer Datenquelle oder einem Treiber](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md)in der ODBC-Programmier Referenz|  
|Unicode/ANSI-Treiber und Verbindungsprobleme|[Unicode-Treiber](../../../odbc/reference/develop-app/unicode-drivers.md)|[Überlegungen zur Programmierung](../../../odbc/reference/develop-app/programming-considerations.md)in der ODBC-Programmier Referenz|  
  
## <a name="see-also"></a>Siehe auch  
 [Developing an ODBC Driver (Entwickeln eines ODBC-Treibers)](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)
