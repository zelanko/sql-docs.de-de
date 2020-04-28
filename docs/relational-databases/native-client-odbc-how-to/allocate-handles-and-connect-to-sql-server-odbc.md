---
title: Zuordnen von Handles und Herstellen einer Verbindung mit SQL Server (ODBC) | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81294503"
---
# <a name="allocate-handles-and-connect-to-sql-server-odbc"></a>Zuordnen von Handles und Herstellen einer Verbindung mit SQL Server (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

    
### <a name="to-allocate-handles-and-connect-to-sql-server"></a>So ordnen Sie Handles zu und stellen eine Verbindung mit SQL Server her  
  
1.  Schließen Sie die ODBC-Headerdateien Sql.h, Sqlext.h und Sqltypes.h ein.  
  
2.  Schließen Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-treiberspezifische Headerdatei Odbcss.h ein.  
  
3.  Nennen Sie [SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396) mit dem **Typ** "SQL_HANDLE_ENV", um ODBC zu initialisieren und ein Umgebungs Handle zuzuordnen.  
  
4.  Rufen Sie [SQLSetEnvAttr](../../relational-databases/native-client-odbc-api/sqlsetenvattr.md) auf, wobei **Attribute** auf SQL_ATTR_ODBC_VERSION und **ValuePtr** auf SQL_OV_ODBC3 festgelegt ist, um anzugeben, dass die Anwendung ODBC 3. x-formatfunktionsaufrufe verwendet.  
  
5.  Sie können optional auch [SQLSetEnvAttr](../../relational-databases/native-client-odbc-api/sqlsetenvattr.md) aufrufen, um andere Umgebungsoptionen festzulegen, oder [SQLGetEnvAttr](https://go.microsoft.com/fwlink/?LinkId=58403) aufrufen, um Umgebungsoptionen abzurufen.  
  
6.  Nennen Sie [SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396) mit dem **Handlertyp** SQL_HANDLE_DBC, um ein Verbindungs Handle zuzuordnen.  
  
7.  Sie können optional auch [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) aufrufen, um Verbindungsoptionen festzulegen, oder [SQLGetConnectAttr](../../relational-databases/native-client-odbc-api/sqlgetconnectattr.md) aufrufen, um die Verbindungsoptionen abzurufen.  
  
8.  Verwenden Sie SQLConnect, um eine vorhandene Datenquelle zum Herstellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]einer Verbindung mit zu verwenden.  
  
     Oder  
  
     Verwenden Sie [SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md) , um eine Verbindungs Zeichenfolge [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zum Herstellen einer Verbindung mit zu verwenden.  
  
     Eine minimale vollständige [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Verbindungszeichenfolge weist eine der beiden folgenden Formen auf:  
  
    ```  
    DSN=dsn_name;Trusted_connection=yes;  
    DRIVER={SQL Server Native Client 10.0};SERVER=server;Trusted_connection=yes;  
    ```  
  
     Wenn die Verbindungs Zeichenfolge nicht fertig ist, kann **SQLDriverConnect** zur Eingabe der erforderlichen Informationen aufgefordert werden. Dies wird durch den für den *DriverCompletion* -Parameter angegebenen Wert gesteuert.  
  
     \- oder -  
  
     Sie können [SQLBrowseConnect](../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md) mehrmals auf iterative Weise aufzurufen, um die Verbindungs Zeichenfolge [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu erstellen und eine Verbindung mit herzustellen.  
  
9. Optional können Sie [SQLGetInfo](../../relational-databases/native-client-odbc-api/sqlgetinfo.md) aufrufen, um Treiber Attribute und das Verhalten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für die Datenquelle abzurufen.  
  
10. Ordnen Sie Anweisungen zu und verwenden Sie sie.  
  
11. Führen Sie SQLDisconnect aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , um die Verbindung mit zu trennen und das Verbindungs Handle für eine neue Verbindung verfügbar zu machen.  
  
12. Nennen Sie [SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md) mit dem **Handlertyp** SQL_HANDLE_DBC, um das Verbindungs Handle freizugeben.  
  
13. Nennen Sie **SQLFreeHandle** mit dem **Handlertyp** SQL_HANDLE_ENV, um das Umgebungs Handle freizugeben.  
  
> [!IMPORTANT]  
>  Verwenden Sie nach Möglichkeit die Windows-Authentifizierung. Wenn die Windows-Authentifizierung nicht verfügbar ist, fordern Sie die Benutzer auf, ihre Anmeldeinformationen zur Laufzeit einzugeben. Die Anmeldeinformationen sollten nicht in einer Datei gespeichert werden. Wenn Sie Anmelde Informationen beibehalten müssen, sollten Sie diese mit der [Win32-kryptografieapi](https://go.microsoft.com/fwlink/?LinkId=64532)verschlüsseln.  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt einen **SQLDriverConnect** -Befehl, um eine Verbindung mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instanz von herzustellen, ohne dass eine vorhandene ODBC-Datenquelle erforderlich ist. Durch die Übergabe einer unvollständigen Verbindungs Zeichenfolge an **SQLDriverConnect**bewirkt dies, dass der ODBC-Treiber den Benutzer zur Eingabe der fehlenden Informationen auffordert.  
  
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
  
  
