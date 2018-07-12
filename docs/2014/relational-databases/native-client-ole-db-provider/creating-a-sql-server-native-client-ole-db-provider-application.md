---
title: Erstellen einer SQL Server Native Client OLE DB-Anbieteranwendung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, application creation
- applications [SQL Server Native Client]
- OLE DB, creating applications
ms.assetid: f3ae6815-f32d-4913-a1a2-2ba2f20cfd88
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 769c151f6b115065b62b2b3b4f7d9fc61b408463
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37426799"
---
# <a name="creating-a-sql-server-native-client-ole-db-provider-application"></a>Erstellen einer SQL Server Native Client OLE DB-Anbieteranwendung
  Erstellen einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-anbieteranwendung sind die folgenden Schritte aus:  
  
1.  Herstellen einer Verbindungs mit einer Datenquelle.  
  
2.  Ausführen eines Befehls an.  
  
3.  Verarbeiten der Ergebnisse  
  
> [!NOTE]  
>  Verwenden Sie nach Möglichkeit die Windows-Authentifizierung. Wenn die Windows-Authentifizierung nicht verfügbar ist, fordern Sie die Benutzer auf, ihre Anmeldeinformationen zur Laufzeit einzugeben. Die Anmeldeinformationen sollten nicht in einer Datei gespeichert werden. Wenn Sie die Anmeldeinformationen persistent speichern müssen, sollten Sie sie mit der [Win32 Crypto-API](http://go.microsoft.com/fwlink/?LinkId=9504)verschlüsseln.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Herstellen einer Verbindung zu einer Datenquelle](establishing-a-connection-to-a-data-source.md)  
  
-   [Ausführen eines Befehls](executing-a-command.md)  
  
-   [Verarbeiten von Ergebnissen](processing-results.md)  
  
-   [Informationen zu OLE DB-Eigenschaften](about-ole-db-properties.md)  
  
-   [Verwenden der OUTPUT-Klausel mit OLE DB in SQL Server Native Client](using-the-output-clause-with-ole-db-in-sql-server-native-client.md)  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
