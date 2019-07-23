---
title: Erstellen eines OLE DB-Treibers für eine SQL Server-Anwendung | Microsoft-Dokumentation
description: Erstellen eines OLE DB-Treibers für eine SQL Server-Anwendung
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
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 4f7861e02b1ed203911f4e3f86575a9688c861fb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68015663"
---
# <a name="creating-an-ole-db-driver-for-sql-server-application"></a>Erstellen eines OLE DB-Treibers für eine SQL Server-Anwendung
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Das Erstellen eines OLE DB Treibers für SQL Server Anwendung umfasst die folgenden Schritte:  
  
1.  Herstellen einer Verbindung zu einer Datenquelle  
  
2.  Ausführen eines Befehls  
  
3.  Verarbeiten der Ergebnisse  
  
> [!NOTE]  
>  Verwenden Sie nach Möglichkeit die Windows-Authentifizierung. Wenn die Windows-Authentifizierung nicht verfügbar ist, fordern Sie die Benutzer auf, ihre Anmeldeinformationen zur Laufzeit einzugeben. Die Anmeldeinformationen sollten nicht in einer Datei gespeichert werden. Wenn Sie die Anmeldeinformationen persistent speichern müssen, sollten Sie sie mit der [Win32 Crypto-API](https://go.microsoft.com/fwlink/?LinkId=9504)verschlüsseln.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Herstellen einer Verbindung zu einer Datenquelle](../../oledb/ole-db-driver/establishing-a-connection-to-a-data-source.md)  
  
-   [Ausführen eines Befehls](../../oledb/ole-db-driver/executing-a-command.md)  
  
-   [Verarbeiten von Ergebnissen](../../oledb/ole-db-driver/processing-results.md)  
  
-   [Informationen zu OLE DB-Eigenschaften](../../oledb/ole-db-driver/about-ole-db-properties.md)  
  
-   [Verwenden der OUTPUT-Klausel mit OLE DB im OLE DB-Treiber für SQL Server](../../oledb/ole-db-driver/using-the-output-clause-with-ole-db-in-oledb-driver-for-sql-server.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [OLE DB-Treiber für SQL Server-Programmierung](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
