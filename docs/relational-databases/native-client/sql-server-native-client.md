---
title: SQL Server Native Client | Microsoft-Dokumentation
ms.date: 04/14/2017
ms.prod: sql
ms.reviewer: ''
ms.custom: ''
ms.technology: native-client
ms.topic: conceptual
ms.assetid: e4d4fe39-0090-42a7-8405-6378370d11cb
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3ce8d425aeb1c1b66f198efb4b222dc94c6e24ff
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62627982"
---
# <a name="sql-server-native-client"></a>SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

SNAC oder SQL Server Native Client ist ein Begriff, der synonym verwendet wurde, ODBC- und OLE DB-Treiber für SQL Server zu verweisen.

**HINWEIS:**  Es wird nicht empfohlen, diese Treiber für die neue Entwicklung zu verwenden. Neue OLE DB-Anbieters wird aufgerufen, die [Microsoft OLE DB-Treiber für SQL Server](../../connect/oledb/oledb-driver-for-sql-server.md) (MSOLEDBSQL) wird die mit den neuesten Serverfunktionen, die in Zukunft aktualisiert.


**Weitere Informationen und das SNAC oder ODBC-Treiber herunterladen zu können, besuchen Sie [SNAC-Lebenszyklus erklärt](https://blogs.msdn.microsoft.com/sqlreleaseservices/snac-lifecycle-explained/).**

Weitere Informationen zum ODBC-Treiber für SQL Server finden Sie unter [Microsoft ODBC-Treiber für SQL Server unter Windows](https://msdn.microsoft.com/library/jj730314(v=sql.110).aspx).  Siehe auch [Einführung in die neuen Microsoft ODBC-Treiber für SQL Server](https://blogs.msdn.microsoft.com/sqlnativeclient/2013/01/23/introducing-the-new-microsoft-odbc-drivers-for-sql-server/), und [ODBC-Treiber 13.1 für SQL Server-Version](https://blogs.technet.microsoft.com/dataplatforminsider/2016/08/03/odbc-driver-13-1-for-sql-server-released/).  

 Informationen zu den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-Funktionen mit veröffentlicht [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], die letzte verfügbare Version von SQL Server native Client:

-   [SQL Server Native Client-Unterstützung für LocalDB](../../relational-databases/native-client/features/sql-server-native-client-support-for-localdb.md)  

-   [Metadatenermittlung](../../relational-databases/native-client/features/metadata-discovery.md)  

-   [Unterstützung für UTF-16 in SQL Server Native Client 11.0](../../relational-databases/native-client/features/utf-16-support-in-sql-server-native-client-11-0.md)  

-   [SQL Server Native Client-Unterstützung für hohe Verfügbarkeit, Notfallwiederherstellung](../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)  

-   [Zugreifen auf Diagnoseinformationen im Protokoll der erweiterten Ereignisse](../../relational-databases/native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md)  

ODBC im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client unterstützt drei Funktionen, die im Windows 7 SDK ODBC-Standardfunktionalität hinzugefügt wurden:  

-   Asynchrone Ausführung von Vorgängen mit Verbindungen. Weitere Informationen finden Sie unter [asynchrone Ausführung](https://go.microsoft.com/fwlink/?LinkID=191493).  

-   Erweiterbarkeit von C-Datentypen. Weitere Informationen finden Sie unter [C-Datentypen in ODBC](https://go.microsoft.com/fwlink/?LinkID=191495).  

     Zur Unterstützung dieser Funktion in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client SQLGetDescField kann zurückgeben **SQL_C_SS_TIME2** (für **Zeit** Typen) oder **SQL_C_SS_TIMESTAMPOFFSET** (für **Datetimeoffset**) anstelle von **SQL_C_BINARY**, wenn die Anwendung ODBC 3.8 verwendet. Weitere Informationen finden Sie unter [Datentypunterstützung für ODBC-Datum und Uhrzeit-Verbesserungen](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md).  

-   Aufrufen von **SQLGetData** mit einem kleinen Puffer mehrere Male auf, um einen großen Parameterwert abzurufen. Weitere Informationen finden Sie unter [Abrufen von Ausgabeparametern mit SQLGetData](https://go.microsoft.com/fwlink/?LinkID=191494).  

 In den folgenden Themen werden Änderungen des Verhaltens von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] beschrieben.  

-   Beim Aufrufen von **ICommandWithParameters:: SetParameterInfo**, der an übergebene Wert den *PwszName* Parameter muss ein gültiger Bezeichner sein. Weitere Informationen finden Sie unter [ICommandWithParameters](../../relational-databases/native-client-ole-db-interfaces/icommandwithparameters.md).  

-   **SQLDescribeParam** gibt stets einen ODBC-Spezifikation entsprechenden Wert zurück. Weitere Informationen finden Sie unter [SQLDescribeParam](../../relational-databases/native-client-odbc-api/sqldescribeparam.md).  

-   [Verhaltensänderungen des ODBC-Treibers bei der Behandlung von Zeichenkonvertierungen](../../relational-databases/native-client/features/odbc-driver-behavior-change-when-handling-character-conversions.md)  

## <a name="see-also"></a>Siehe auch  
[Installieren Sie SQL Server Native Client](../../relational-databases/native-client/applications/installing-sql-server-native-client.md)  
 [SQL Server Native Client-Features](../../relational-databases/native-client/features/sql-server-native-client-features.md)  
