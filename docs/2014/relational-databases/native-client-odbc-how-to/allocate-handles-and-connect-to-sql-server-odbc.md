---
title: Reservieren von Handles und Herstellen einer Verbindung mit SQLServer (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- handles [ODBC]
- handles [ODBC], connection
- handles [ODBC], about handles
ms.assetid: 6172cd52-9c9a-467d-992f-def07f3f3bb1
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: adf51bdb9181030079d8b3f94628a1280299c856
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048492"
---
# <a name="allocate-handles-and-connect-to-sql-server-odbc"></a>Zuordnen von Handles und Herstellen einer Verbindung mit SQL Server (ODBC)
    
### <a name="to-allocate-handles-and-connect-to-sql-server"></a>So ordnen Sie Handles zu und stellen eine Verbindung mit SQL Server her  
  
1.  Schließen Sie die ODBC-Headerdateien Sql.h, Sqlext.h und Sqltypes.h ein.  
  
2.  Schließen Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-treiberspezifische Headerdatei Odbcss.h ein.  
  
3.  Rufen Sie [SQLAllocHandle](http://go.microsoft.com/fwlink/?LinkId=58396) mit einem `HandleType` SQL_HANDLE_ENV auf, um ODBC zu initialisieren und ein Umgebungshandle zuzuordnen.  
  
4.  Rufen Sie [SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md) mit `Attribute` festgelegt auf SQL_ATTR_ODBC_VERSION und `ValuePtr` auf SQL_OV_ODBC3 festgelegt ist, um anzugeben, die Anwendung Funktionsaufrufe für ODBC 3.x-Format verwenden.  
  
5.  Rufen Sie optional [SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md) um andere Umgebungsoptionen festzulegen, oder rufen [SQLGetEnvAttr](http://go.microsoft.com/fwlink/?LinkId=58403) um Umgebungsoptionen abzurufen.  
  
6.  Rufen Sie [SQLAllocHandle](http://go.microsoft.com/fwlink/?LinkId=58396) mit einem `HandleType` SQL_HANDLE_DBC auf, um ein Verbindungshandle zuzuordnen.  
  
7.  Rufen Sie optional [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) um Verbindungsoptionen festzulegen, oder rufen [SQLGetConnectAttr](../native-client-odbc-api/sqlgetconnectattr.md) Verbindungsoptionen abgerufen.  
  
8.  Rufen Sie SQLConnect um eine vorhandene Datenquelle zu verwenden, für die Verbindung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     oder  
  
     Rufen Sie [SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md) eine Verbindungszeichenfolge zu verwenden, für die Verbindung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Eine minimale vollständige [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Verbindungszeichenfolge weist eine der beiden folgenden Formen auf:  
  
    ```  
    DSN=dsn_name;Trusted_connection=yes;  
    DRIVER={SQL Server Native Client 10.0};SERVER=server;Trusted_connection=yes;  
    ```  
  
     Wenn die Verbindungszeichenfolge nicht vollständig ist, kann `SQLDriverConnect` den Benutzer auffordern, die erforderlichen Informationen einzugeben. Dies wird gesteuert, indem der angegebene Wert für die *DriverCompletion* Parameter.  
  
     \- oder –  
  
     Rufen Sie [SQLBrowseConnect](../native-client-odbc-api/sqlbrowseconnect.md) mehrere Male in einer iterativen Weise erstellen die Verbindungszeichenfolge und Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
9. Rufen Sie optional [SQLGetInfo](../native-client-odbc-api/sqlgetinfo.md) abzurufenden Treiberattribute und-Verhalten für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenquelle.  
  
10. Ordnen Sie Anweisungen zu und verwenden Sie sie.  
  
11. Rufen Sie SQLDisconnect trennen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und das Verbindungshandle für eine neue Verbindung verfügbar zu machen.  
  
12. Rufen Sie [SQLFreeHandle](../native-client-odbc-api/sqlfreehandle.md) mit einem `HandleType` SQL_HANDLE_DBC auf, um das Verbindungshandle freizugeben.  
  
13. Rufen Sie `SQLFreeHandle` mit dem `HandleType` SQL_HANDLE_ENV auf, um das Umgebungshandle wieder freizugeben.  
  
> [!IMPORTANT]  
>  Verwenden Sie nach Möglichkeit die Windows-Authentifizierung. Wenn die Windows-Authentifizierung nicht verfügbar ist, fordern Sie die Benutzer auf, ihre Anmeldeinformationen zur Laufzeit einzugeben. Die Anmeldeinformationen sollten nicht in einer Datei gespeichert werden. Wenn Sie die Anmeldeinformationen permanent speichern müssen, verschlüsseln Sie sie mit der [Win32 Crypto-API](http://go.microsoft.com/fwlink/?LinkId=64532).  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird ein Aufruf von `SQLDriverConnect` zum Herstellen einer Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gezeigt, bei der keine vorhandene ODBC-Datenquelle erforderlich ist. Die Übergabe einer unvollständigen Verbindungszeichenfolge an `SQLDriverConnect` führt dazu, dass der ODBC-Treiber den Benutzer dazu auffordert, die fehlenden Informationen einzugeben.  
  
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
  
  