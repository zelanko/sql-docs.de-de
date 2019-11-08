---
title: Massen kopieren aus Programmvariablen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], program variables
- bcp_bind function
- mapping data types [ODBC]
- SQL Server Native Client ODBC driver, bulk copy
- data types [ODBC], bulk copying
- ODBC, bulk copy operations
- program variables [ODBC]
ms.assetid: e4284a1b-7534-4b34-8488-b8d05ed67b8c
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f88a966e2095f527f36c84498e026c1e23aaa2ab
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73785224"
---
# <a name="bulk-copying-from-program-variables"></a>Massenkopieren aus Programmvariablen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Sie können Massenkopiervorgänge direkt aus Programmvariablen durchführen. Nachdem Sie Variablen zugeordnet haben, die die Daten für eine Zeile enthalten, und [bcp_init](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) aufrufen, um das Massen kopieren zu starten, rufen Sie [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) für jede Spalte auf, um den Speicherort und das Format der Programmvariablen anzugeben, die der Spalte zugeordnet werden soll. Füllen Sie jede Variable mit Daten aus, und wenden Sie dann [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) an, um eine Daten Zeile an den Server zu senden. Wiederholen Sie den Vorgang zum Auffüllen der Variablen und zum Aufrufen von **bcp_sendrow** , bis alle Zeilen an den Server gesendet wurden. Rufen Sie dann [bcp_done](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-done.md) auf, um anzugeben, dass der Vorgang abgeschlossen ist.  
  
 Der **bcp_bind**_pData_ -Parameter enthält die Adresse der Variablen, die an die Spalte gebunden wird. Die Daten für die einzelnen Spalten können auf zweierlei Weise gespeichert werden:  
  
-   Zuordnen einer Variable für die Daten.  
  
-   Zuordnen einer Indikatorvariable, unmittelbar gefolgt von der Datenvariable.  
  
 Die Indikatorvariable gibt die Datenlänge für Spalten mit variabler Länge an und zeigt gegebenenfalls an, dass NULL-Werte für die Spalte zulässig sind. Wenn nur eine Daten Variable verwendet wird, wird die Adresse dieser Variablen im **bcp_bind**_pData_ -Parameter gespeichert. Wenn eine Indikator Variable verwendet wird, wird die Adresse der Indikator Variablen im **bcp_bind**_pData_ -Parameter gespeichert. Die Funktionen zum Massen kopieren berechnen den Speicherort der Daten Variablen, indem Sie die Parameter " **bcp_bind**_cbIndicator_ " und " *pData* " hinzufügen.  
  
 **bcp_bind** unterstützt drei Methoden für den Umgang mit Daten variabler Länge:  
  
-   Verwenden Sie *cbData* nur mit einer Daten Variablen. Legen Sie die Länge der Daten in *cbData*ab. Bei jeder Änderung der Länge der Daten, die Massen kopiert werden sollen, wird [bcp_collen](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md)aufgerufen, um *cbData*zurückzusetzen. Wenn eine der beiden anderen Methoden verwendet wird, geben Sie SQL_VARLEN_DATA für *cbData*an. Wenn alle Datenwerte, die für eine Spalte bereitgestellt werden, NULL sind, geben Sie SQL_NULL_DATA für *cbData*an.  
  
-   Verwenden von Indikatorvariablen. Speichern Sie beim Verschieben des jeweiligen neuen Datenwerts in die Datenvariable die Länge des Werts in der Indikatorvariable. Wenn eine der beiden anderen Methoden verwendet wird, geben Sie 0 für *cbIndicator*an.  
  
-   Verwenden von Abschlusszeichenzeigern. Laden Sie den **bcp_bind**_pterm_ -Parameter mit der Adresse des Bitmusters, von dem die Daten beendet werden. Wenn eine der beiden anderen Methoden verwendet wird, geben Sie für *pterm*den Wert NULL an.  
  
 Alle drei Methoden können für denselben **bcp_bind** -Befehl verwendet werden. in diesem Fall wird die Spezifikation verwendet, die dazu führt, dass die kleinste zu kopierende Datenmenge verwendet wird.  
  
 Der **bcp_bind**_Type_ -Parameter verwendet DB-Library-Datentyp Bezeichner, nicht ODBC-Datentyp Bezeichner. DB-Library-Datentyp Bezeichner werden in sqlncli. h für die Verwendung mit der ODBC- **bcp_bind** Funktion definiert.  
  
 Funktionen zum Massenkopieren unterstützen nicht alle ODBC C-Datentypen. Beispielsweise unterstützen die Massen Kopierfunktionen die ODBC-SQL_C_TYPE_TIMESTAMP Struktur nicht. verwenden Sie daher [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md) oder [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) , um ODBC-SQL_TYPE_TIMESTAMP Daten in eine SQL_C_CHAR Variable zu konvertieren. Wenn Sie dann **bcp_bind** mit einem *Typparameter* von SQLCHARACTER verwenden, um die Variable an eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **DateTime** -Spalte zu binden, konvertieren die Massen Kopierfunktionen die Zeitstempel-Escapesequenz in der Zeichen Variablen in das richtige DateTime-Format.  
  
 In der folgenden Tabelle werden die Datentypen aufgeführt, die für Zuordnungen eines ODBC SQL-Datentyps zu einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentyps empfohlen werden.  
  
|ODBC SQL-Datentyp|ODBC C-Datentyp|bcp_bind *Typparameter*|SQL Server-Datentyp|  
|-----------------------|----------------------|--------------------------------|--------------------------|  
|SQL_CHAR|SQL_C_CHAR|SQLCHARACTER|**character**<br /><br /> **char**|  
|SQL_VARCHAR|SQL_C_CHAR|SQLCHARACTER|**varchar**<br /><br /> **Zeichen variiert**<br /><br /> **char varying**<br /><br /> **sysname**|  
|SQL_LONGVARCHAR|SQL_C_CHAR|SQLCHARACTER|**text**|  
|SQL_WCHAR|SQL_C_WCHAR|SQLNCHAR|**nchar**|  
|SQL_WVARCHAR|SQL_C_WCHAR|SQLNVARCHAR|**nvarchar**|  
|SQL_WLONGVARCHAR|SQL_C_WCHAR|SQLNTEXT|**ntext**|  
|SQL_DECIMAL|SQL_C_CHAR|SQLCHARACTER|**decimal**<br /><br /> **31.12.2012**<br /><br /> **money**<br /><br /> **smallmoney**|  
|SQL_NUMERIC|SQL_C_NUMERIC|SQLNUMERICN|**numeric**|  
|SQL_BIT|SQL_C_BIT|SQLBIT|**bit**|  
|SQL_TINYINT (mit Vorzeichen)|SQL_C_SSHORT|SQLINT2|**smallint**|  
|SQL_TINYINT (ohne Vorzeichen)|SQL_C_UTINYINT|SQLINT1|**tinyint**|  
|SQL_SMALL_INT (mit Vorzeichen)|SQL_C_SSHORT|SQLINT2|**smallint**|  
|SQL_SMALL_INT (ohne Vorzeichen)|SQL_C_SLONG|SQLINT4|**int**<br /><br /> **integer**|  
|SQL_INTEGER (mit Vorzeichen)|SQL_C_SLONG|SQLINT4|**int**<br /><br /> **integer**|  
|SQL_INTEGER (ohne Vorzeichen)|SQL_C_CHAR|SQLCHARACTER|**decimal**<br /><br /> **31.12.2012**|  
|SQL_BIGINT (mit und ohne Vorzeichen)|SQL_C_CHAR|SQLCHARACTER|**bigint**|  
|SQL_REAL|SQL_C_FLOAT|SQLFLT4|**real**|  
|SQL_FLOAT|SQL_C_DOUBLE|SQLFLT8|**float**|  
|SQL_DOUBLE|SQL_C_DOUBLE|SQLFLT8|**float**|  
|SQL_BINARY|SQL_C_BINARY|SQLBINARY|**binary**<br /><br /> **timestamp**|  
|SQL_VARBINARY|SQL_C_BINARY|SQLBINARY|**varbinary**<br /><br /> **binäre unterschiedlichen**|  
|SQL_LONGVARBINARY|SQL_C_BINARY|SQLBINARY|**image**|  
|SQL_TYPE_DATE|SQL_C_CHAR|SQLCHARACTER|**datetime**<br /><br /> **smalldatetime**|  
|SQL_TYPE_TIME|SQL_C_CHAR|SQLCHARACTER|**datetime**<br /><br /> **smalldatetime**|  
|SQL_TYPE_TIMESTAMP|SQL_C_CHAR|SQLCHARACTER|**datetime**<br /><br /> **smalldatetime**|  
|SQL_GUID|SQL_C_GUID|SQLUNIQUEID|**uniqueidentifier**|  
|SQL_INTERVAL_|SQL_C_CHAR|SQLCHARACTER|**char**|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verfügt nicht über signierte Datentypen " **tinyint**", "Ganzzahl ohne Vorzeichen **smallint**" oder "Ganzzahl ohne Vorzeichen **int** ". Um den Verlust von Datenwerten beim Migrieren dieser Datentypen zu verhindern, erstellen Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabelle mit dem nächstgrößeren ganzzahligen Datentyp. Um zu verhindern, dass Benutzer später Werte außerhalb des für den ursprünglichen Datentyp zulässigen Bereichs hinzufügen, wenden Sie eine Regel auf die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Spalte an, mit der die zulässigen Werte entsprechend eingeschränkt werden:  
  
```  
CREATE TABLE Sample_Ints(STinyIntCol   SMALLINT,  
USmallIntCol INT)  
GO  
CREATE RULE STinyInt_Rule  
AS   
@range >= -128 AND @range <= 127  
GO  
CREATE RULE USmallInt_Rule  
AS   
@range >= 0 AND @range <= 65535  
GO  
sp_bindrule STinyInt_Rule, 'Sample_Ints.STinyIntCol'  
GO  
sp_bindrule USmallInt_Rule, 'Sample_Ints.USmallIntCol'  
GO  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt Intervalldatentypen nicht direkt. Eine Anwendung kann Intervallescapesequenzen jedoch als Zeichenfolgen in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Zeichenspalte speichern. Die Anwendung kann sie zur späteren Verwendung lesen, sie können aber nicht in [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen verwendet werden.  
  
 Mithilfe der Massenkopierfunktionen können aus einer ODBC-Datenquelle gelesene Daten schnell in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] geladen werden. Verwenden Sie [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md) , um die Spalten eines Resultsets an Programmvariablen zu binden, und verwenden Sie dann **bcp_bind** , um die gleichen Programmvariablen an einen Massen Kopiervorgang zu binden. Durch den Aufruf von [SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md) oder **SQLFetch** wird eine Daten Zeile aus der ODBC-Datenquelle in die Programmvariablen abgerufen. beim Aufrufen von [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) werden die Daten von den Programmvariablen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kopiert.  
  
 Eine Anwendung kann die [bcp_colptr](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-colptr.md) -Funktion immer dann verwenden, wenn Sie die Adresse der Daten Variablen ändern muss, die ursprünglich im **bcp_bind** _pData_ -Parameter angegeben wurde. Eine Anwendung kann die [bcp_collen](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md) -Funktion immer dann verwenden, wenn Sie die Daten Länge ändern muss, die ursprünglich im **bcp_bind**_cbData_ -Parameter angegeben wurde.  
  
 Sie können mit Massenkopiervorgängen keine Daten aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in Programmvariablen einlesen. Eine "bcp_readrow"-Funktion oder Ähnliches gibt es nicht. Sie können nur Daten aus der Anwendung an den Server senden.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von Massen Kopier &#40;Vorgängen (ODBC)&#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
  
