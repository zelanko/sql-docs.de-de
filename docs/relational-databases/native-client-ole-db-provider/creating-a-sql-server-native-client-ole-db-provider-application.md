---
description: Erstellen einer SQL Server Native Client OLE DB-Anbieteranwendung
title: Erstellen einer OLE DB-App
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, application creation
- applications [SQL Server Native Client]
- OLE DB, creating applications
ms.assetid: f3ae6815-f32d-4913-a1a2-2ba2f20cfd88
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 98f01da2a10e5cc3a1311df8c6171649d2e6e734
ms.sourcegitcommit: 4d370399f6f142e25075b3714e5c2ce056b1bfd0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91864818"
---
# <a name="creating-a-sql-server-native-client-ole-db-provider-application"></a>Erstellen einer SQL Server Native Client OLE DB-Anbieteranwendung
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Das Erstellen einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter Anwendung umfasst die folgenden Schritte:  
  
1.  Herstellen einer Verbindung zu einer Datenquelle  
  
2.  Ausführen eines Befehls  
  
3.  Verarbeiten der Ergebnisse  

> [!NOTE]  
>  Verwenden Sie nach Möglichkeit die Windows-Authentifizierung. Wenn die Windows-Authentifizierung nicht verfügbar ist, fordern Sie die Benutzer auf, ihre Anmeldeinformationen zur Laufzeit einzugeben. Die Anmeldeinformationen sollten nicht in einer Datei gespeichert werden. Wenn Sie die Anmeldeinformationen persistent speichern müssen, sollten Sie sie mit der [Win32 Crypto-API](/windows/win32/seccng/cng-portal)verschlüsseln.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Herstellen einer Verbindung zu einer Datenquelle](../../relational-databases/native-client-ole-db-provider/establishing-a-connection-to-a-data-source.md)  
  
-   [Ausführen eines Befehls](../../relational-databases/native-client-ole-db-provider/executing-a-command.md)  
  
-   [Verarbeiten von Ergebnissen](../../relational-databases/native-client-ole-db-provider/processing-results.md)  
  
-   [Informationen zu OLE DB-Eigenschaften](../../relational-databases/native-client-ole-db-provider/about-ole-db-properties.md)  
  
-   [Verwenden der OUTPUT-Klausel mit OLE DB in SQL Server Native Client](../../relational-databases/native-client-ole-db-provider/using-the-output-clause-with-ole-db-in-sql-server-native-client.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
