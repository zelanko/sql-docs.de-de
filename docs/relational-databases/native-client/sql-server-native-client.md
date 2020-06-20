---
title: Info
description: Erfahren Sie mehr über die Features von SQL Server Native Client (SNAC). SQL Server Native Client bezieht sich auf ODBC-und OLE DB Treiber für SQL Server.
ms.date: 04/14/2017
ms.prod: sql
ms.reviewer: ''
ms.custom: ''
ms.technology: native-client
ms.topic: conceptual
ms.assetid: e4d4fe39-0090-42a7-8405-6378370d11cb
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: eb9d7878f4edc9f81b7b17b5fdf44da5c9dcec48
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84948652"
---
# <a name="sql-server-native-client"></a>SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

SNAC (oder SQL Server Native Client) ist ein Begriff, der austauschbar verwendet wurde, um auf ODBC und OLE DB Treiber für SQL Server zu verweisen.

> [!IMPORTANT] 
> Die SQL Server Native Client (SQLNCLI) ist weiterhin veraltet, und es wird nicht empfohlen, Sie für neue Entwicklungsarbeiten zu verwenden. Verwenden Sie stattdessen den neuen [Microsoft OLE DB-Treiber für SQL Server](../../connect/oledb/oledb-driver-for-sql-server.md) (MSOLEDBSQL), der mit den aktuellsten Serverfeatures aktualisiert wird.

> [!NOTE]
> Weitere Informationen und das Herunterladen der SNAC-oder ODBC-Treiber finden Sie im [Blogbeitrag "SNAC Lifecycle: Blog](https://blogs.msdn.microsoft.com/sqlreleaseservices/snac-lifecycle-explained/)".
> Weitere Informationen zum ODBC-Treiber für SQL Server finden Sie unter [Microsoft ODBC Driver for SQL Server](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md).  

 Informationen zu den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-Funktionen [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] , die mit veröffentlicht wurden, der letzten verfügbaren Version von SQL Server Native Client:

-   [SQL Server Native Client-Unterstützung für LocalDB](../../relational-databases/native-client/features/sql-server-native-client-support-for-localdb.md)  

-   [Metadatenermittlung](../../relational-databases/native-client/features/metadata-discovery.md)  

-   [Unterstützung für UTF-16 in SQL Server Native Client 11.0](../../relational-databases/native-client/features/utf-16-support-in-sql-server-native-client-11-0.md)  

-   [SQL Server Native Client-Unterstützung für hohe Verfügbarkeit, Notfallwiederherstellung](../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)  

-   [Zugreifen auf Diagnoseinformationen im Protokoll für erweiterte Ereignisse](../../relational-databases/native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md)  

ODBC in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client unterstützt drei Features, die dem standardmäßigen ODBC im Windows 7-SDK hinzugefügt wurden:  

-   Asynchrone Ausführung von Vorgängen mit Verbindungen. Weitere Informationen finden Sie unter [asynchrone Ausführung](https://go.microsoft.com/fwlink/?LinkID=191493).  

-   Erweiterbarkeit von C-Datentypen. Weitere Informationen finden Sie unter [C-Datentypen in ODBC](https://go.microsoft.com/fwlink/?LinkID=191495).  

     Um dieses Feature in Native Client zu unterstützen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , kann SQLGetDescField **SQL_C_SS_TIME2** (bei **Zeit** Typen) oder **SQL_C_SS_TIMESTAMPOFFSET** (für **DateTimeOffset**) anstelle von **SQL_C_BINARY**zurückgeben, wenn die Anwendung ODBC 3,8 verwendet. Weitere Informationen finden Sie [unter Datentyp Unterstützung für ODBC-Datums-und Uhrzeit Verbesserungen](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md).  

-   Mehrmals aufrufen von **SQLGetData** mit einem kleinen Puffer, um einen großen Parameterwert abzurufen. Weitere Informationen finden Sie unter [Abrufen von Ausgabeparametern mit SQLGetData](https://go.microsoft.com/fwlink/?LinkID=191494).  

 In den folgenden Themen werden Änderungen des Verhaltens von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] beschrieben.  

-   Beim Aufrufen von **ICommandWithParameters:: SetParameterInfo**muss der an den *pwszName* -Parameter übergebenen Wert ein gültiger Bezeichner sein. Weitere Informationen finden Sie unter [ICommandWithParameters](../../relational-databases/native-client-ole-db-interfaces/icommandwithparameters.md).  

-   **SQLDescribeParam** gibt konsistent einen Wert zurück, der der ODBC-Spezifikation entspricht. Weitere Informationen finden Sie unter [SQLDescribeParam](../../relational-databases/native-client-odbc-api/sqldescribeparam.md).  

-   [Verhaltensänderungen des ODBC-Treibers bei der Behandlung von Zeichenkonvertierungen](../../relational-databases/native-client/features/odbc-driver-behavior-change-when-handling-character-conversions.md)  

## <a name="see-also"></a>Weitere Informationen  
[Installieren von SQL Server Native Client](../../relational-databases/native-client/applications/installing-sql-server-native-client.md)  
 [SQL Server Native Client-Funktionen](../../relational-databases/native-client/features/sql-server-native-client-features.md)  
