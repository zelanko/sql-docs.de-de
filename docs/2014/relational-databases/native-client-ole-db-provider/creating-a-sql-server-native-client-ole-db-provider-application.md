---
title: Erstellen einer SQL Server Native Client OLE DB Anbieter Anwendung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, application creation
- applications [SQL Server Native Client]
- OLE DB, creating applications
ms.assetid: f3ae6815-f32d-4913-a1a2-2ba2f20cfd88
author: rothja
ms.author: jroth
ms.openlocfilehash: dd8ef192fb17a5b2719481fa43fd06b370868c62
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85056042"
---
# <a name="creating-a-sql-server-native-client-ole-db-provider-application"></a>Erstellen einer SQL Server Native Client OLE DB-Anbieteranwendung
  Das Erstellen einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter Anwendung umfasst die folgenden Schritte:  
  
1.  Herstellen einer Verbindung zu einer Datenquelle  
  
2.  Ausführen eines Befehls  
  
3.  Verarbeiten der Ergebnisse  
  
> [!NOTE]  
>  Verwenden Sie nach Möglichkeit die Windows-Authentifizierung. Wenn die Windows-Authentifizierung nicht verfügbar ist, fordern Sie die Benutzer auf, ihre Anmeldeinformationen zur Laufzeit einzugeben. Die Anmeldeinformationen sollten nicht in einer Datei gespeichert werden. Wenn Sie die Anmeldeinformationen persistent speichern müssen, sollten Sie sie mit der [Win32 Crypto-API](https://go.microsoft.com/fwlink/?LinkId=9504)verschlüsseln.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Herstellen einer Verbindung zu einer Datenquelle](establishing-a-connection-to-a-data-source.md)  
  
-   [Ausführen eines Befehls](executing-a-command.md)  
  
-   [Ergebnisverarbeitung](processing-results.md)  
  
-   [Informationen zu OLE DB-Eigenschaften](about-ole-db-properties.md)  
  
-   [Verwenden der OUTPUT-Klausel mit OLE DB in SQL Server Native Client](using-the-output-clause-with-ole-db-in-sql-server-native-client.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
