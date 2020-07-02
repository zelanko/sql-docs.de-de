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
ms.openlocfilehash: 9adc8ed5547691f693a88a5d468581022afd363e
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85783349"
---
# <a name="allocate-handles-and-connect-to-sql-server-odbc"></a>Zuordnen von Handles und Herstellen einer Verbindung mit SQL Server (ODBC)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

    
### <a name="to-allocate-handles-and-connect-to-sql-server"></a>So ordnen Sie Handles zu und stellen eine Verbindung mit SQL Server her  
  
1.  Schließen Sie die ODBC-Headerdateien Sql.h, Sqlext.h und Sqltypes.h ein.  
  
2.  Schließen Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-treiberspezifische Headerdatei Odbcss.h ein.  
  
3.  Nennen Sie [SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396) mit dem **Typ** "SQL_HANDLE_ENV", um ODBC zu initialisieren und ein Umgebungs Handle zuzuordnen.  
  
4.  Rufen Sie [SQLSetEnvAttr](../../relational-databases/native-client-odbc-api/sqlsetenvattr.md) auf, wobei **Attribute** auf SQL_ATTR_ODBC_VERSION und **ValuePtr** auf SQL_OV_ODBC3 festgelegt ist, um anzugeben, dass die Anwendung ODBC 3. x-formatfunktionsaufrufe verwendet.  
  
5.  Sie können optional auch [SQLSetEnvAttr](../../relational-databases/native-client-odbc-api/sqlsetenvattr.md) aufrufen, um andere Umgebungsoptionen festzulegen, oder [SQLGetEnvAttr](https://go.microsoft.com/fwlink/?LinkId=58403) aufrufen, um Umgebungsoptionen abzurufen.  
  
6.  Nennen Sie [SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396) mit dem **Handlertyp** SQL_HANDLE_DBC, um ein Verbindungs Handle zuzuordnen.  
  
7.  Sie können optional auch [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) aufrufen, um Verbindungsoptionen festzulegen, oder [SQLGetConnectAttr](../../relational-databases/native-client-odbc-api/sqlgetconnectattr.md) aufrufen, um die Verbindungsoptionen abzurufen.  
  
8.  Verwenden Sie SQLConnect, um eine vorhandene Datenquelle zum Herstellen einer Verbindung mit zu verwenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
     oder  
  
     Verwenden Sie [SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md) , um eine Verbindungs Zeichenfolge zum Herstellen einer Verbindung mit zu verwenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
     Eine minimale vollständige [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Verbindungszeichenfolge weist eine der beiden folgenden Formen auf:  
  
    ```  
    DSN=dsn_name;Trusted_connection=yes;  
    DRIVER={SQL Server Native Client 10.0};SERVER=server;Trusted_connection=yes;  
    ```  
  
     Wenn die Verbindungs Zeichenfolge nicht fertig ist, kann **SQLDriverConnect** zur Eingabe der erforderlichen Informationen aufgefordert werden. Dies wird durch den für den *DriverCompletion* -Parameter angegebenen Wert gesteuert.  
  
     \- oder -  
  
     Sie können [SQLBrowseConnect](../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md) mehrmals auf iterative Weise aufzurufen, um die Verbindungs Zeichenfolge zu erstellen und eine Verbindung mit herzustellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
9. Optional können Sie [SQLGetInfo](../../relational-databases/native-client-odbc-api/sqlgetinfo.md) aufrufen, um Treiber Attribute und das Verhalten für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenquelle abzurufen.  
  
10. Ordnen Sie Anweisungen zu und verwenden Sie sie.  
  
11. Führen Sie SQLDisconnect aus, um die Verbindung mit zu trennen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und das Verbindungs Handle für eine neue Verbindung verfügbar zu machen.  
  
12. Nennen Sie [SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md) mit dem **Handlertyp** SQL_HANDLE_DBC, um das Verbindungs Handle freizugeben.  
  
13. Nennen Sie **SQLFreeHandle** mit dem **Handlertyp** SQL_HANDLE_ENV, um das Umgebungs Handle freizugeben.  
  
> [!IMPORTANT]  
>  Verwenden Sie nach Möglichkeit die Windows-Authentifizierung. Wenn die Windows-Authentifizierung nicht verfügbar ist, fordern Sie die Benutzer auf, ihre Anmeldeinformationen zur Laufzeit einzugeben. Die Anmeldeinformationen sollten nicht in einer Datei gespeichert werden. Wenn Sie Anmelde Informationen beibehalten müssen, sollten Sie diese mit der [Win32-kryptografieapi](https://go.microsoft.com/fwlink/?LinkId=64532)verschlüsseln.  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt einen **SQLDriverConnect** -Befehl, um eine Verbindung mit einer Instanz von herzustellen, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ohne dass eine vorhandene ODBC-Datenquelle erforderlich ist. Durch die Übergabe einer unvollständigen Verbindungs Zeichenfolge an **SQLDriverConnect**bewirkt dies, dass der ODBC-Treiber den Benutzer zur Eingabe der fehlenden Informationen auffordert.  
  
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
  
  
