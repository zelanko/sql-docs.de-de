---
title: Neues in SQL Server Native Client |&#39;Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: e4d4fe39-0090-42a7-8405-6378370d11cb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d2a01b9d9d13bf5e9135d287553beb8b87c2dcd5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62638850"
---
# <a name="what39s-new-in-sql-server-native-client"></a>Neues in SQL Server Native Client&#39;
  
  [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] installiert [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Native Client. Es gibt keinen [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Native Client.  
  
 Der ODBC-Treiber in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client wird nicht mehr aktualisiert. Die Folgeversion des ODBC-Treibers in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, die [!INCLUDE[msCoName](../../includes/msconame-md.md)] ODBC-Treiber 11 für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] – Windows heißt, wird mit [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] installiert. Weitere Informationen zum [!INCLUDE[msCoName](../../includes/msconame-md.md)] ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on Windows finden Sie unter [Microsoft ODBC Driver 11 for SQL Server-Windows](https://www.microsoft.com/download/details.aspx?id=36434).  
  
 Der OLE DB-Anbieter von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client wurde zuletzt in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Native Client aktualisiert. Entwickler, die einen OLE DB-Anbieter für Verbindungen mit der aktuellen Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwenden möchten, müssen den in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Native Client enthaltenen OLE DB-Anbieter verwenden.  
  
 In den folgenden Themen werden wichtige neue [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-Funktionen in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] beschrieben.  
  
-   [SQL Server Native Client-Unterstützung für LocalDB](features/sql-server-native-client-support-for-localdb.md)  
  
-   [Metadatenermittlung](features/metadata-discovery.md)  
  
-   [Unterstützung für UTF-16 in SQL Server Native Client 11.0](features/utf-16-support-in-sql-server-native-client-11-0.md)  
  
-   [SQL Server Native Client-Unterstützung für hohe Verfügbarkeit, Notfallwiederherstellung](features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)  
  
-   [Zugreifen auf Diagnoseinformationen im Protokoll der erweiterten Ereignisse](features/accessing-diagnostic-information-in-the-extended-events-log.md)  
  
 Außerdem unterstützt ODBC in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client jetzt drei Funktionen, die im Windows 7-SDK der ODBC-Standardfunktionalität hinzugefügt wurden:  
  
-   Asynchrone Ausführung von Vorgängen mit Verbindungen. Weitere Informationen finden Sie unter [asynchrone Ausführung](https://go.microsoft.com/fwlink/?LinkID=191493).  
  
-   Erweiterbarkeit von C-Datentypen. Weitere Informationen finden Sie unter [C-Datentypen in ODBC](https://go.microsoft.com/fwlink/?LinkID=191495).  
  
     Um dieses Feature [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in Native Client zu unterstützen, kann SQLGetDescField (für `SQL_C_SS_TIME2` `time` -Typen `SQL_C_SS_TIMESTAMPOFFSET` ) oder `datetimeoffset`(für) `SQL_C_BINARY`anstelle von zurückgeben, wenn die Anwendung ODBC 3,8 verwendet. Weitere Informationen finden Sie [unter Datentyp Unterstützung für ODBC-Datums-und Uhrzeit Verbesserungen](features/date-and-time-improvements.md).  
  
-   Mehrfaches Aufrufen von `SQLGetData` mit einem kleinen Puffer, um einen großen Parameterwert abzurufen. Weitere Informationen finden Sie unter [Abrufen von Ausgabeparametern mit SQLGetData](https://go.microsoft.com/fwlink/?LinkID=191494).  
  
 In den folgenden Themen werden Änderungen des Verhaltens von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] beschrieben.  
  
-   Beim Aufrufen `ICommandWithParameters::SetParameterInfo`von muss der an den *pwszName* -Parameter übergebenen Wert ein gültiger Bezeichner sein. Weitere Informationen finden Sie unter [ICommandWithParameters](../native-client-ole-db-interfaces/icommandwithparameters.md).  
  
-   
  `SQLDescribeParam` gibt jetzt stets einen Wert zurück, der der ODBC-Spezifikation entspricht. Weitere Informationen finden Sie unter [SQLDescribeParam](../native-client-odbc-api/sqldescribeparam.md).  
  
-   [Verhaltensänderungen des ODBC-Treibers bei der Behandlung von Zeichenkonvertierungen](features/odbc-driver-behavior-change-when-handling-character-conversions.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client-Funktionen](features/sql-server-native-client-features.md)  
  
  
