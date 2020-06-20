---
title: SQL Server Native Client Unterstützung für localdb | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 127569d1-a9f7-49bf-a561-c084986a8871
author: rothja
ms.author: jroth
ms.openlocfilehash: d1adfcc0beba3b06028ddf4e4c7ddc6ca44faae9
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85011158"
---
# <a name="sql-server-native-client-support-for-localdb"></a>SQL Server Native Client-Unterstützung für LocalDB
  Ab [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]ist eine vereinfachte Version von SQL Server mit dem Namen LocalDB verfügbar. In diesem Thema wird erläutert, wie in einer LocalDB-Instanz eine Verbindung mit einer Datenbank hergestellt wird.  
  
## <a name="remarks"></a>Bemerkungen  
 Weitere Informationen zu LocalDB, einschließlich der Installation von LocalDB und der Konfiguration der LocalDB-Instanz, finden Sie unter:  
  
-   [SQL Server Express LocalDB-Verweis](../../sql-server-express-localdb-reference.md)  
  
-   [SQL Server 2014 Express LocalDB](../../../database-engine/configure-windows/sql-server-2016-express-localdb.md)  
  
 Zusammenfassend erlaubt LocalDB Ihnen Folgendes:  
  
-   Verwenden Sie `sqllocaldb.exe i`, um den Namen der Standardinstanz zu ermitteln.  
  
-   Verwenden Sie das Schlüsselwort der `AttachDBFilename`-Verbindungszeichenfolge, um anzugeben, welche Datenbankdatei der Server anfügen soll. Wenn `AttachDBFilename` Sie verwenden, wenn Sie den Namen der Datenbank nicht mit dem Schlüsselwort für die **Daten bankverbindungs** Zeichenfolge angeben, wird die Datenbank aus der localdb-Instanz entfernt, wenn die Anwendung geschlossen wird.  
  
-   Geben Sie in der Verbindungszeichenfolge eine LocalDB-Instanz an:  
  
```  
SERVER=(localdb)\v11.0  
```  
  
 Falls notwendig können Sie eine LocalDB-Instanz mit "sqllocaldb.exe" erstellen. Sie können auch "sqlcmd.exe" verwenden, um Datenbanken in einer LocalDB-Instanz hinzuzufügen und zu ändern. Beispiel: `sqlcmd -S (localdb)\v11.0`.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client-Funktionen](sql-server-native-client-features.md)  
  
  
