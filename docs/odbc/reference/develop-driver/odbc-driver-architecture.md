---
title: ODBC-Treiberarchitektur | Microsoft Docs
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
ms.openlocfilehash: 712de6a7a3f80ce1cd3ca854a88765dbfa531356
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294558"
---
# <a name="odbc-driver-architecture"></a>ODBC-Treiberarchitektur
Treiberautoren müssen sich bewusst sein, dass die Treiberarchitektur beeinflussen kann, ob eine Anwendung DBMS-spezifische SQL verwenden kann.  
  
 ![Stellt die ODBC-Treiberarchitektur dar.](../../../odbc/reference/develop-driver/media/odbcdriverovruarch.gif "ODBCDriverOvruArch")  
  
 [Dateibasierte Treiber](../../../odbc/reference/file-based-drivers.md)  
  
 Wenn der Treiber direkt auf die physischen Daten zugreift, fungiert der Treiber sowohl als Treiber als auch als Datenquelle. Der Treiber muss sowohl ODBC-Aufrufe als auch SQL-Anweisungen verarbeiten. Entwickler von dateibasierten Treibern müssen ihre eigenen Datenbankmodule schreiben.  
  
 [DBMS-basierte Treiber](../../../odbc/reference/dbms-based-drivers.md)  
  
 Wenn ein separates Datenbankmodul für den Zugriff auf physische Daten verwendet wird, verarbeitet der Treiber nur ODBC-Aufrufe. Es übergibt SQL-Anweisungen zur Verarbeitung an das Datenbankmodul.  
  
 [Netzwerkarchitektur](../../../odbc/reference/network-example.md)  
  
 Datei- und DBMS-ODBC-Konfigurationen können in einem einzigen Netzwerk vorhanden sein.  
  
 [Andere Treiberarchitekturen](../../../odbc/reference/other-driver-architectures.md)  
  
 Wenn ein Treiber mit einer Vielzahl von Datenquellen arbeiten muss, kann er als Middleware verwendet werden. Die heterogene Join-Engine-Architektur kann dazu beitragen, dass der Treiber als Treiber-Manager angezeigt wird. Treiber können auch auf Servern installiert werden, wo sie von einer Reihe von Clients gemeinsam genutzt werden können.  
  
 Weitere Informationen zur Treiberarchitektur finden Sie unter [Treiber-Manager](../../../odbc/reference/the-driver-manager.md) und [Treiberarchitektur](../../../odbc/reference/driver-architecture.md) im Abschnitt [über ODBC-Architektur](../../../odbc/reference/odbc-architecture.md).  
  
 Weitere Informationen zu Treiberproblemen finden Sie in den in der folgenden Tabelle beschriebenen Speicherorten.  
  
|Problem|Thema|Position|  
|-----------|-----------|--------------|  
|Kompatibilitätsprobleme mit Anwendungen und Treibern|[Anwendungs-/Treiberkompatibilität](../../../odbc/reference/develop-app/application-and-driver-compatibility.md)|[Programmierüberlegungen](../../../odbc/reference/develop-app/programming-considerations.md), in der Referenz des ODBC-Programmierers|  
|Schreiben von ODBC-Treibern|[Schreiben von ODBC-3.x-Treibern](../../../odbc/reference/develop-app/writing-odbc-3-x-drivers.md)|[Programmierüberlegungen](../../../odbc/reference/develop-app/programming-considerations.md), in der Referenz des ODBC-Programmierers|  
|Treiberrichtlinien für Abwärtskompatibilität|[Treiberrichtlinien für Abwärtskompatibilität](../../../odbc/reference/appendixes/appendix-g-driver-guidelines-for-backward-compatibility.md)|[Anhang G: Treiberrichtlinien für Die Abwärtskompatibilität](../../../odbc/reference/appendixes/appendix-g-driver-guidelines-for-backward-compatibility.md), in der Referenz des ODBC-Programmierers|  
|Herstellen einer Verbindung mit einem Treiber|[Auswählen einer Datenquelle oder eines Treibers](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md)|[Herstellen einer Verbindung mit einer Datenquelle oder einem Treiber](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md)in der REFERENZ des ODBC-Programmierers|  
|Identifizieren von Treibern|[Anzeigen von Treibern](../../../odbc/admin/viewing-drivers.md)|[Anzeigen von Treibern](../../../odbc/admin/viewing-drivers.md)in der Onlinehilfe des Microsoft ODBC-Datenquellenadministrators|  
|Aktivieren des Verbindungspoolings|[ODBC-Verbindungspooling](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md)|[Herstellen einer Verbindung mit einer Datenquelle oder einem Treiber](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md)in der REFERENZ des ODBC-Programmierers|  
|Unicode/ANSI-Treiber- und Verbindungsprobleme|[Unicode-Treiber](../../../odbc/reference/develop-app/unicode-drivers.md)|[Programmierüberlegungen](../../../odbc/reference/develop-app/programming-considerations.md), in der Referenz des ODBC-Programmierers|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Developing an ODBC Driver (Entwickeln eines ODBC-Treibers)](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)
