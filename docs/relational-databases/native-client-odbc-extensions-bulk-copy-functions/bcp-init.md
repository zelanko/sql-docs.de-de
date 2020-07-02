---
title: bcp_init | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- bcp_init
- bcp_initW
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_init function
ms.assetid: 6a25862c-7f31-4873-ab65-30f3abde89d2
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 19914bb99a2812035e6833b389a62e6ed3139463
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85774266"
---
# <a name="bcp_init"></a>bcp_init
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

Initialisiert den Massenkopiervorgang.  

## <a name="syntax"></a>Syntax  
  
```  
RETCODE bcp_init (  
        HDBC hdbc,  
        LPCTSTR szTable,  
        LPCTSTR szDataFile,  
        LPCTSTR szErrorFile,  
        INT eDirection);  
```  

Unicode-und ANSI-Namen:
- bcp_initA (ANSI)
- bcp_initW (Unicode)

## <a name="arguments"></a>Argumente  
 *hdbc*  
 Das für den Massenkopiervorgang aktivierte ODBC-Verbindungshandle.  
  
 *szTable*  
 Name der Datenbanktabelle, in die bzw. aus der kopiert werden soll. Dieser Name kann auch den Namen der Datenbank oder den Namen des Besitzers enthalten. Beispielsweise **Pubs. Gracie. Titeln**, **Pubs. Titel**, **Gracie. Titeln**und **Titel** sind alle gültigen Tabellennamen.  
  
 Wenn *eDirection* DB_OUT ist, kann *szTable* auch der Name einer Daten Bank Sicht sein.  
  
 Wenn *eDirection* DB_OUT ist und mithilfe [bcp_control](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) eine SELECT-Anweisung angegeben wird, bevor [bcp_exec](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md) aufgerufen wird, muss **bcp_init** *szTable* auf NULL festgelegt werden.  
  
 *szDataFile*  
 Name der Benutzerdatei, in die bzw. aus der kopiert werden soll. Wenn Daten mithilfe von [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)direkt aus Variablen kopiert werden, legen Sie *szDataFile* auf NULL fest.  
  
 *szErrorFile*  
 Der Name der Fehlerdatei, in die Statusmeldungen, Fehlermeldungen und Kopien von Zeilen geschrieben werden sollen, die aus einem bestimmten Grund nicht von einer Benutzerdatei in eine Tabelle kopiert werden konnten. Wenn NULL als *szErrorFile*übergeben wird, wird keine Fehler Datei verwendet.  
  
 *eDirection*  
 Die Richtung der Kopie, entweder DB_IN oder DB_OUT. DB_IN bedeutet eine Kopie aus Programmvariablen oder aus einer Benutzerdatei in eine Tabelle. DB_OUT bedeutet eine Kopie von einer Datenbanktabelle in eine Benutzerdatei an. Sie müssen einen Benutzerdateinamen mit DB_OUT angeben.  
  
## <a name="returns"></a>Gibt zurück  
 SUCCEED oder FAIL.  
  
## <a name="remarks"></a>Hinweise  
 Rufen Sie **bcp_init** auf, bevor Sie eine andere Massen Kopierfunktion aufrufen. **bcp_init** führt die erforderlichen Initialisierungen für einen Massen Kopiervorgang von Daten zwischen der Arbeitsstation und aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Die **bcp_init** -Funktion muss mit einem ODBC-Verbindungs Handle bereitgestellt werden, das für die Verwendung mit Massen Kopierfunktionen aktiviert ist. Um das Handle zu aktivieren, verwenden Sie [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) , wobei SQL_COPT_SS_BCP auf einem zugeordneten, aber nicht verbundenen Verbindungs Handle auf SQL_BCP_ON festgelegt ist. Wenn Sie versuchen, das Attribut einem bereits verbundenen Verbindungshandle zuzuweisen, tritt ein Fehler auf.  
  
 Wenn eine Datendatei angegeben wird, untersucht **bcp_init** die Struktur der Datenbankquelle oder der Ziel Tabelle, nicht die Datendatei. **bcp_init** gibt Datenformat Werte für die Datendatei basierend auf den einzelnen Spalten in der Datenbanktabelle, der Sicht oder dem SELECT-Resultset an. Diese Spezifikation enthält unter anderem den Datentyp jeder Spalte, das Vorhandensein bzw. Nichtvorhandensein eines Längen- oder NULL-Wertindikators und von Bytezeichenfolgen des Abschlusszeichens der Daten, sowie die Breite von Datentypen fester Länge. **bcp_init** legt diese Werte wie folgt fest:  
  
-   Der angegebene Datentyp entspricht dem Datentyp der Spalte in der Datenbanktabelle, der Sicht oder dem SELECT-Resultset. Der Datentyp wird von den in der Datei sqlncli.h angegebenen systemeigenen Datentypen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aufgelistet. Die Daten selbst werden in computereigenem Format dargestellt, Das heißt, dass Daten aus einer Spalte vom Datentyp **Integer** durch eine 4-Byte-Sequenz dargestellt werden, die auf dem Computer, auf dem die Datendatei erstellt wurde, Big-oder Little-Endian ist.  
  
-   Wenn ein Datenbankdatentyp eine feste Länge hat, haben auch die Daten der Datendatei eine feste Länge. Massen Kopierfunktionen, die Daten verarbeiten (z. b. [bcp_exec](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md)), analysieren Daten Zeilen, die erwarten, dass die Länge der Daten in der Datendatei mit der Länge der Daten identisch ist, die in der Datenbanktabelle, Sicht oder SELECT-Spaltenliste angegeben sind. Beispielsweise müssen Daten für eine als **char (13)** definierte Daten Bank Spalte für jede Daten Zeile in der Datei 13 Zeichen darstellen. Für Daten mit fester Länge kann ein NULL-Indikator verwendet werden, wenn die Datenbankspalte NULL-Werte zulässt.  
  
-   Wenn eine Bytesequenz für Abschlusszeichen definiert ist, wird deren Länge auf 0 festgelegt.  
  
-   Zum Kopieren von Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] muss die Datendatei für jede Spalte der Datenbanktabelle Daten aufweisen. Beim Kopieren aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden Daten aus allen Spalten in der Datenbanktabelle, Sicht oder SELECT-Resultset in die Datendatei kopiert.  
  
-   Beim Kopieren von Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] muss die Ordnungsposition einer Spalte in der Datendatei der Ordnungsposition einer Spalte in der Datenbanktabelle genau entsprechen. Beim Kopieren aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] platziert **bcp_exec** Daten auf der Grundlage der Ordnungsposition der Spalte in der Datenbanktabelle.  
  
-   Wenn ein Daten Bank Datentyp eine Variable Länge aufweist (z. b. **varbinary (22)**) oder wenn eine Daten Bank Spalte NULL-Werte enthalten kann, wird den Daten in der Datendatei ein Längen-/NULL-Indikator vorangestellt. Die Breite des Indikators ändert sich auf der Grundlage des Datentyps und der Version der Massenkopierfunktion.  
  
 Um die für eine Datendatei angegebenen Datenformat Werte zu ändern, müssen [bcp_columns](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md) und [bcp_colfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md)aufgerufen werden.  
  
 Massenkopiervorgänge in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] können für Tabellen, die keine Indizes enthalten, optimiert werden, indem das Datenbank-Wiederherstellungsmodul auf SIMPLE oder BULK_LOGGED festgelegt wird. Weitere Informationen finden Sie unter [Voraussetzungen für die minimale Protokollierung beim Massen Import](../../relational-databases/import-export/prerequisites-for-minimal-logging-in-bulk-import.md) und [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md).  
  
 Wenn keine Datendatei verwendet wird, müssen Sie [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) aufzurufen, um das Format und den Speicherort der Daten für jede Spalte anzugeben, und anschließend Daten Zeilen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)in die kopieren.  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt, wie die ODBC-Funktion bcp_init mit einer Formatdatei verwendet wird.  
  
 Bevor Sie den C++-Code kompilieren und ausführen, sind folgende Schritte erforderlich:  
  
-   Erstellen einer ODBC-Datenquelle mit dem Namen "Test". Sie können diese Datenquelle einer beliebigen Datenbank zuordnen.  
  
-   Führen Sie für die Datenbank die folgende [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung aus:  
  
    ```  
    CREATE TABLE BCPDate (cola int, colb datetime);  
    ```  
  
-   Fügen Sie dem Verzeichnis, in dem Sie die Anwendung ausführen, eine Datei namens Bcpfmt.fmt hinzu, und fügen Sie Folgendes in die Datei ein:  
  
    ```  
    8.0  
    2  
    1SQLCHAR04"\t"1colaSQL_Latin1_General_Cp437_Bin  
    2SQLCHAR08"\r\n"2colbSQL_Latin1_General_Cp437_Bin  
    ```  
  
-   Fügen Sie dem Verzeichnis, in dem Sie die Anwendung ausführen, eine Datei namens Bcpodbc.bcp hinzu, und fügen Sie Folgendes in die Datei ein:  
  
    ```  
    1  
    2  
    ```  
  
 Nun sind Sie bereit, C++-Code zu kompilieren und auszuführen.  
  
```  
// compile with: odbc32.lib sqlncli11.lib  
#include <stdio.h>  
#include <windows.h>  
#include <sql.h>  
#include <sqlext.h>  
#include <odbcss.h>  
  
SQLHENV henv = SQL_NULL_HENV;  
HDBC hdbc1 = SQL_NULL_HDBC;   
  
void Cleanup() {  
   if (hdbc1 != SQL_NULL_HDBC) {  
      SQLDisconnect(hdbc1);  
      SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   }  
  
   if (henv != SQL_NULL_HENV)  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
  
int main() {  
   RETCODE retcode;  
   SDWORD cRows;  
  
   // Allocate the ODBC environment and save handle.  
   retcode = SQLAllocHandle (SQL_HANDLE_ENV, NULL, &henv);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(Env) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Notify ODBC that this is an ODBC 3.0 app.  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER) SQL_OV_ODBC3, SQL_IS_INTEGER);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLSetEnvAttr(ODBC version) Failed\n\n");  
      Cleanup();  
      return(9);      
   }  
  
   // Allocate ODBC connection handle, set BCP mode, and connect.  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc1);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   retcode = SQLSetConnectAttr(hdbc1, SQL_COPT_SS_BCP, (void *)SQL_BCP_ON, SQL_IS_INTEGER);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLSetConnectAttr(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Sample uses Integrated Security. Create SQL Server DSN using Windows NT authentication.  
   retcode = SQLConnect(hdbc1, (UCHAR*)"Test", SQL_NTS, (UCHAR*)"", SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Initialize the bulk copy.  
   retcode = bcp_init(hdbc1, "BCPDate", "BCPODBC.bcp", NULL, DB_IN);  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_init(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Read the format file.  
   retcode = bcp_readfmt(hdbc1, "BCPFMT.fmt");  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_readfmt(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Execute the bulk copy.  
   retcode = bcp_exec(hdbc1, &cRows);  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_exec(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   printf("Number of rows bulk copied in = %d.\n", cRows);  
  
   // Cleanup  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
  
```  

## <a name="see-also"></a>Weitere Informationen  
 [Bulk Copy Functions](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
