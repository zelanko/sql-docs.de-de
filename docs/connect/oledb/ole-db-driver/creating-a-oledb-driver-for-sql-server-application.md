---
title: Erstellen eines OLE DB-Treibers für eine SQL Server-Anwendung | Microsoft-Dokumentation
description: Erfahren Sie mehr über die notwendigen Schritte zum Erstellen einer OLE DB-Treiber für SQL Server-Anwendung und zusätzliche Ressourcen.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, application creation
- applications [OLE DB Driver for SQL Server]
- OLE DB, creating applications
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ed150ea18d1141e6116efe177e65836c235cf703
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91727216"
---
# <a name="creating-an-ole-db-driver-for-sql-server-application"></a>Erstellen eines OLE DB-Treibers für eine SQL Server-Anwendung
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Die Erstellung eines OLE DB-Treibers für eine SQL Server-Anwendung umfasst die folgenden Schritte:  
  
1.  Herstellen einer Verbindung zu einer Datenquelle  
  
2.  Ausführen eines Befehls  
  
3.  Verarbeiten der Ergebnisse  
  
> [!NOTE]  
>  Verwenden Sie nach Möglichkeit die Windows-Authentifizierung. Wenn die Windows-Authentifizierung nicht verfügbar ist, fordern Sie die Benutzer auf, ihre Anmeldeinformationen zur Laufzeit einzugeben. Die Anmeldeinformationen sollten nicht in einer Datei gespeichert werden. Wenn Sie die Anmeldeinformationen persistent speichern müssen, sollten Sie sie mit der [Win32 Crypto-API](/windows/win32/seccng/cng-portal)verschlüsseln.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Herstellen einer Verbindung zu einer Datenquelle](../../oledb/ole-db-driver/establishing-a-connection-to-a-data-source.md)  
  
-   [Ausführen eines Befehls](../../oledb/ole-db-driver/executing-a-command.md)  
  
-   [Verarbeiten von Ergebnissen](../../oledb/ole-db-driver/processing-results.md)  
  
-   [Informationen zu OLE DB-Eigenschaften](../../oledb/ole-db-driver/about-ole-db-properties.md)  
  
-   [Verwenden der OUTPUT-Klausel mit OLE DB im OLE DB-Treiber für SQL Server](../../oledb/ole-db-driver/using-the-output-clause-with-ole-db-in-oledb-driver-for-sql-server.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [OLE DB-Treiber für SQL Server-Programmierung](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
