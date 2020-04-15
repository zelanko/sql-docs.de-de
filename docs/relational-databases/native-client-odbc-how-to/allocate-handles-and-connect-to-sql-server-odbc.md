---
title: Zuweisen von Handles und Herstellen einer Verbindung mit SQL Server (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- handles [ODBC]
- handles [ODBC], connection
- handles [ODBC], about handles
ms.assetid: 6172cd52-9c9a-467d-992f-def07f3f3bb1
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5d26af711c07c4ea296d5351d0fcb0d1f9710706
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294503"
---
# <a name="allocate-handles-and-connect-to-sql-server-odbc"></a>Zuordnen von Handles und Herstellen einer Verbindung mit SQL Server (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

    
### <a name="to-allocate-handles-and-connect-to-sql-server"></a>So ordnen Sie Handles zu und stellen eine Verbindung mit SQL Server her  
  
1.  Schließen Sie die ODBC-Headerdateien Sql.h, Sqlext.h und Sqltypes.h ein.  
  
2.  Schließen Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-treiberspezifische Headerdatei Odbcss.h ein.  
  
3.  Rufen Sie [SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396) mit einem **HandleType** von SQL_HANDLE_ENV auf, um ODBC zu initialisieren und ein Umgebungshandle zuzuweisen.  
  
4.  Rufen Sie [SQLSetEnvAttr](../../relational-databases/native-client-odbc-api/sqlsetenvattr.md) **auf,** wobei das Attribut auf SQL_ATTR_ODBC_VERSION festgelegt ist und **ValuePtr** auf SQL_OV_ODBC3 festgelegt ist, um anzugeben, dass die Anwendung ODBC 3.x-Format-Funktionsaufrufe verwendet.  
  
5.  Rufen Sie optional [SQLSetEnvAttr](../../relational-databases/native-client-odbc-api/sqlsetenvattr.md) auf, um andere Umgebungsoptionen festzulegen, oder rufen Sie [SQLGetEnvAttr](https://go.microsoft.com/fwlink/?LinkId=58403) auf, um Umgebungsoptionen abzurufen.  
  
6.  Rufen Sie [SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396) mit einem **HandleType** von SQL_HANDLE_DBC auf, um ein Verbindungshandle zuzuweisen.  
  
7.  Rufen Sie optional [SQLSetConnectAttr auf,](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) um Verbindungsoptionen festzulegen, oder rufen Sie [SQLGetConnectAttr](../../relational-databases/native-client-odbc-api/sqlgetconnectattr.md) auf, um Verbindungsoptionen abzurufen.  
  
8.  Rufen Sie SQLConnect auf, um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]eine vorhandene Datenquelle zum Herstellen einer Verbindung mit zu verwenden.  
  
     oder  
  
     Rufen Sie [SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md) auf, um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]eine Verbindungszeichenfolge zum Herstellen einer Verbindung mit zu verwenden.  
  
     Eine minimale vollständige [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Verbindungszeichenfolge weist eine der beiden folgenden Formen auf:  
  
    ```  
    DSN=dsn_name;Trusted_connection=yes;  
    DRIVER={SQL Server Native Client 10.0};SERVER=server;Trusted_connection=yes;  
    ```  
  
     Wenn die Verbindungszeichenfolge nicht vollständig ist, kann **SQLDriverConnect** zur Eingabe der erforderlichen Informationen auffordern. Dies wird durch den für den *Parameter DriverCompletion* angegebenen Wert gesteuert.  
  
     \- oder -  
  
     Rufen Sie [SQLBrowseConnect](../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md) mehrmals iterativ auf, um die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Verbindungszeichenfolge zu erstellen und eine Verbindung mit herzustellen.  
  
9. Rufen Sie optional [SQLGetInfo](../../relational-databases/native-client-odbc-api/sqlgetinfo.md) auf, um Treiberattribute und -verhalten für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenquelle abzurufen.  
  
10. Ordnen Sie Anweisungen zu und verwenden Sie sie.  
  
11. Rufen Sie SQLDisconnect [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf, um die Verbindung zu trennen und das Verbindungshandle für eine neue Verbindung verfügbar zu machen.  
  
12. Rufen Sie [SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md) mit einem **HandleType** von SQL_HANDLE_DBC auf, um das Verbindungshandle freizugeben.  
  
13. Rufen Sie **SQLFreeHandle** mit einem **HandleType** von SQL_HANDLE_ENV auf, um das Umgebungshandle freizugeben.  
  
> [!IMPORTANT]  
>  Verwenden Sie nach Möglichkeit die Windows-Authentifizierung. Wenn die Windows-Authentifizierung nicht verfügbar ist, fordern Sie die Benutzer auf, ihre Anmeldeinformationen zur Laufzeit einzugeben. Die Anmeldeinformationen sollten nicht in einer Datei gespeichert werden. Wenn Sie Anmeldeinformationen beibehalten müssen, sollten Sie diese mit der [Win32-Krypto-API](https://go.microsoft.com/fwlink/?LinkId=64532)verschlüsseln.  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt einen Aufruf von **SQLDriverConnect** zum Herstellen einer Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ohne eine vorhandene ODBC-Datenquelle. Durch Übergeben einer unvollständigen Verbindungszeichenfolge an **SQLDriverConnect**bewirkt dies, dass der ODBC-Treiber den Benutzer auffordert, die fehlenden Informationen einzugeben.  
  
```  
#define MAXBUFLEN   255  
  
SQLHENV      henv = SQL_NULL_HENV;  
SQLHDBC      hdbc1 = SQL_NULL_HDBC;  
SQLHSTMT      hstmt1 = SQL_NULL_HSTMT;  
  
SQLCHAR      ConnStrIn[MAXBUFLEN] =  
         "DRIVER={SQL Server Native Client 10.0};SERVER=MyServer";  
  
SQLCHAR      ConnStrOut[MAXBUFLEN];  
SQLSMALLINT   cbConnStrOut = 0;  
  
// Make connection without data source. Ask that driver   
// prompt if insufficient information. Driver returns  
// SQL_ERROR and application prompts user  
// for missing information. Window handle not needed for  
// SQL_DRIVER_NOPROMPT.  
retcode = SQLDriverConnect(hdbc1,      // Connection handle  
                  NULL,         // Window handle  
                  ConnStrIn,      // Input connect string  
                  SQL_NTS,         // Null-terminated string  
                  ConnStrOut,      // Address of output buffer  
                  MAXBUFLEN,      // Size of output buffer  
                  &cbConnStrOut,   // Address of output length  
                  SQL_DRIVER_PROMPT);  
```  
  
  
