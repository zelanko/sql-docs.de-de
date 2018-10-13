---
title: Sp_describe_first_result_set (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_describe_first_result_set
- sp_describe_first_result_set_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_describe_first_result_set
ms.assetid: f2355a75-3a8e-43e6-96ad-4f41038f6d22
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 317defb8c3efd99274421f169424cc09ec4caf58
ms.sourcegitcommit: 5d6e1c827752c3aa2d02c4c7653aefb2736fffc3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/10/2018
ms.locfileid: "49072064"
---
# <a name="spdescribefirstresultset-transact-sql"></a>sp_describe_first_result_set (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Gibt die Metadaten zurück, für die erste mögliche des Resultset der [!INCLUDE[tsql](../../includes/tsql-md.md)] Batch. Gibt ein leeres Resultset zurück, wenn vom Batch keine Ergebnisse zurückgegeben werden. Löst einen Fehler aus, wenn die [!INCLUDE[ssDE](../../includes/ssde-md.md)] kann nicht bestimmt werden die Metadaten für die erste Abfrage, die von einer statischen Analyse ausgeführt wird. Die dynamische verwaltungssicht [Sys. dm_exec_describe_first_result_set &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-transact-sql.md) gibt die gleichen Informationen zurück.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_describe_first_result_set [ @tsql = ] N'Transact-SQL_batch'   
    [ , [ @params = ] N'parameters' ]   
    [ , [ @browse_information_mode = ] <tinyint> ] ]  
```  
  
## <a name="arguments"></a>Argumente  
 [  **\@Tsql =** ] **"***Transact-SQL_batch***"**  
 Eine oder mehrere [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen. *Transact-SQL_batch* möglicherweise **Nvarchar (***n***)** oder **nvarchar(max)**.  
  
 [  **\@Params =** ] **N'***Parameter***"**  
 \@Params stellt eine deklarationszeichenfolge für Parameter für die [!INCLUDE[tsql](../../includes/tsql-md.md)] Batch, die analog zu Sp_executesql ist. Parameter können ggf. werden **nvarchar (n)** oder **nvarchar(max)**.  
  
 Eine Zeichenfolge, die die Definitionen aller Parameter enthält, die in eingebettet wurden die [!INCLUDE[tsql](../../includes/tsql-md.md)] *_batch*. Die Zeichenfolge muss eine Unicode-Konstante oder eine Unicode-Variable sein. Jede Parameterdefinition besteht aus einem Parameternamen und einem Datentyp. *n* ist ein Platzhalter, der zusätzliche Parameterdefinitionen. Jeder in Parameter in der Anweisung muss definiert werden, \@Params. Wenn die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung oder der Batch in der Anweisung keine Parameter, \@"Params" ist nicht erforderlich. NULL, ist der Standardwert für diesen Parameter.  
  
 [  **\@Browse_information_mode =** ] *Tinyint*  
 Gibt an, ob zusätzliche Schlüsselspalten und Quelltabelleninformationen zurückgegeben werden. Wenn der Wert gleich 1, jede Abfrage analysiert, als ob es sich um eine FOR BROWSE-Option für die Abfrage enthält. Zusätzliche Schlüsselspalten und Quelltabelleninformationen werden zurückgegeben.  
  
-   Bei 0 werden keine Informationen zurückgegeben.  
  
-   Wenn der Wert gleich 1, jede Abfrage analysiert, als ob es sich um eine FOR BROWSE-Option für die Abfrage enthält. Damit werden Basistabellennamen als Quellspalteninformationen zurückgegeben.  
  
-   Bei 2 wird jede Abfrage analysiert, als würde sie beim Vorbereiten oder Ausführen eines Cursors verwendet. Damit werden Sichtnamen als Quellspalteninformationen zurückgegeben.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **Sp_describe_first_result_set** immer den Status bei Erfolg NULL zurück. Wenn die Prozedur löst einen Fehler aus, und die Prozedur als RPC aufgerufen wird, wird der Rückgabestatus durch den Typ des Fehlers in der Error_type-Spalte der Sys. dm_exec_describe_first_result_set beschrieben aufgefüllt. Wenn die Prozedur von [!INCLUDE[tsql](../../includes/tsql-md.md)] aufgerufen wird, ist der Rückgabewert immer 0; dies gilt auch bei einem Fehler.  
  
## <a name="result-sets"></a>Resultsets  
 Diese allgemeinen Metadaten werden in den Ergebnismetadaten als Resultset mit einer Zeile für jede Spalte zurückgegeben. Jede Zeile beschreibt den Typ und die NULL-Zulässigkeit der Spalte in dem Format, das im folgenden Abschnitt beschriebenen wird. Wenn die erste Anweisung nicht für alle Steuerelementpfade vorhanden ist, wird ein Resultset mit 0 Zeilen zurückgegeben.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**is_hidden**|**Bit nicht NULL**|Gibt an, dass es sich bei der Spalte um eine zusätzliche Spalte zum Suchen von Informationen handelt, die nicht im Resultset angezeigt wird.|  
|**column_ordinal**|**Int nicht NULL**|Enthält die Ordnungsposition der Spalte im Resultset. Die Position der ersten Spalte wird mit 1 angegeben.|  
|**name**|**Sysname NULL**|Enthält den Namen der Spalte, wenn ein Name bestimmt werden kann. Andernfalls enthält er NULL.|  
|**is_nullable**|**Bit nicht NULL**|Enthält den Wert 1, wenn die Spalte NULL-Werte zulässt, 0, wenn die Spalte keinen NULL-Werte zulässt, und 1, wenn nicht ermittelt werden kann, ob die Spalte NULL-Werte zulässt.|  
|**system_type_id**|**Int nicht NULL**|Enthält die System_type_id des Datentyps der Spalte, wie in sys.types angegeben. Bei CLR-Typen wird von dieser Spalte der Wert 240 zurückgegeben, obwohl von der system_type_name-Spalte NULL zurückgegeben wird.|  
|**system_type_name**|**nvarchar(256) NULL**|Enthält den Namen und die Argumente (z. B. Länge, Genauigkeit oder Skala), die für den Datentyp der Spalte angegeben wurden. Wenn der Datentyp ein benutzerdefinierter Aliastyp ist, wird der zugrunde liegende Systemtyp hier angegeben. Bei einem benutzerdefinierten CLR-Typ wird NULL in dieser Spalte zurückgegeben.|  
|**max_length**|**Smallint nicht NULL**|Maximale Länge (in Byte) für die Spalte.<br /><br /> -1 = Spaltendatentyp ist **varchar(max)**, **nvarchar(max)**, **'varbinary(max)'**, oder **Xml**.<br /><br /> Für **Text** Spalten, die **Max_length** Wert werden 16- oder den Wert festlegen, indem **Sp_tableoption 'Text in Row'**.|  
|**precision**|**Tinyint nicht NULL**|Die Genauigkeit der Spalte, wenn sie auf numerischen Werten basiert. Andernfalls wird 0 zurückgegeben.|  
|**scale**|**Tinyint nicht NULL**|Die Skalierung der Spalte, wenn sie auf numerischen Werten basiert. Andernfalls wird 0 zurückgegeben.|  
|**collation_name**|**Sysname NULL**|Name der Sortierung der Spalte, wenn diese zeichenbasiert ist. Andernfalls wird NULL zurückgegeben.|  
|**user_type_id**|**Int NULL**|Enthält bei CLR- und Aliastypen die user_type_id des Datentyps der Spalte, wie in sys.types angegeben. Andernfalls NULL.|  
|**user_type_database**|**Sysname NULL**|Enthält bei CLR- und Aliastypen den Namen der Datenbank, in der der Typ definiert wurde. Andernfalls NULL.|  
|**user_type_schema**|**Sysname NULL**|Enthält bei CLR- und Aliastypen den Namen des Schemas, in dem der Typ definiert wurde. Andernfalls NULL.|  
|**user_type_name**|**Sysname NULL**|Enthält bei CLR- und Aliastypen den Namen des Typs. Andernfalls NULL.|  
|**assembly_qualified_type_name**|**nvarchar(4000)**|Gibt bei CLR-Typen den Namen der Assembly und der Klasse zurück, die den Typ definieren. Andernfalls NULL.|  
|**xml_collection_id**|**Int NULL**|Enthält die xml_collection_id des Datentyps für die Spalte, wie in sys.columns angegeben. Diese Spalte gibt NULL zurück, wenn der Rückgabetyp nicht mit einer XML-schemaauflistung verknüpft ist.|  
|**xml_collection_database**|**Sysname NULL**|Enthält die Datenbank, in der die XML-Schemaauflistung definiert ist, die diesem Typ zugeordnet wurde. Diese Spalte gibt NULL zurück, wenn der Rückgabetyp nicht mit einer XML-schemaauflistung verknüpft ist.|  
|**xml_collection_schema**|**Sysname NULL**|Enthält das Schema, in dem die XML-Schemaauflistung definiert ist, die diesem Typ zugeordnet wurde. Diese Spalte gibt NULL zurück, wenn der Rückgabetyp nicht mit einer XML-schemaauflistung verknüpft ist.|  
|**xml_collection_name**|**Sysname NULL**|Enthält den Namen der XML-Schemaauflistung, die diesem Typ zugeordnet wurde. Diese Spalte gibt NULL zurück, wenn der Rückgabetyp nicht mit einer XML-schemaauflistung verknüpft ist.|  
|**is_xml_document**|**Bit nicht NULL**|Gibt 1 zurück, wenn der zurückgegebene Datentyp XML ist und für diesen Typ garantiert ist, dass es sich um ein vollständiges XML-Dokument (einschließlich eines Stammknotens) handelt, nicht um ein XML-Fragment. Andernfalls wird 0 zurückgegeben.|  
|**is_case_sensitive**|**Bit nicht NULL**|Gibt 1 zurück, wenn die Spalte einen Zeichenfolgentyp darstellt, bei dem die Groß-/Kleinschreibung beachtet wird, andernfalls 0.|  
|**is_fixed_length_clr_type**|**Bit nicht NULL**|Gibt 1 zurück, wenn die Spalte ein CLR-Typ mit fester Länge ist, andernfalls 0.|  
|**source_server**|**sysname**|Der Name des ursprünglichen Servers, der von der Spalte in diesem Ergebnis zurückgegeben wurde (bei einem Remoteserver). Der Name angegeben wird, wie er in der sys.servers angezeigt wird. Gibt NULL zurück, wenn die Spalte vom lokalen Server stammt oder der ursprüngliche Server nicht ermittelt werden konnte. Wird nur aufgefüllt, wenn die Suche nach Informationen erforderlich ist.|  
|**source_database**|**sysname**|Der Name der ursprünglichen Datenbank, die von der Spalte in diesem Ergebnis zurückgegeben wird. Gibt NULL zurück, wenn die Datenbank nicht ermittelt werden kann. Wird nur aufgefüllt, wenn die Suche nach Informationen erforderlich ist.|  
|**source_schema**|**sysname**|Der Name des ursprünglichen Schemas, das von der Spalte in diesem Ergebnis zurückgegeben wird. Gibt NULL zurück, wenn das Schema nicht bestimmt werden kann. Wird nur aufgefüllt, wenn die Suche nach Informationen erforderlich ist.|  
|**source_table**|**sysname**|Der Name der ursprünglichen Tabelle, die von der Spalte in diesem Ergebnis zurückgegeben wird. Gibt NULL zurück, wenn die Tabelle nicht bestimmt werden kann. Wird nur aufgefüllt, wenn die Suche nach Informationen erforderlich ist.|  
|**source_column**|**sysname**|Der Name der ursprünglichen Spalte, die von der Ergebnisspalte zurückgegeben wird. Gibt NULL zurück, wenn die Spalte nicht bestimmt werden kann. Wird nur aufgefüllt, wenn die Suche nach Informationen erforderlich ist.|  
|**is_identity_column**|**NULL-Bit**|Gibt 1 zurück, wenn die Spalte eine Identitätsspalte ist, andernfalls 0. Gibt NULL zurück, wenn nicht ermittelt werden kann, ob die Spalte eine Identitätsspalte ist.|  
|**is_part_of_unique_key**|**NULL-Bit**|Gibt 1 zurück, wenn die Spalte Teil eines eindeutigen Index (einschließlich UNIQUE- und PRIMARY-Einschränkung) ist, andernfalls 0. Gibt NULL zurück, wenn nicht ermittelt werden kann, ob die Spalte Teil eines eindeutigen Indexes ist. Wird nur aufgefüllt, wenn die Suche nach Informationen erforderlich ist.|  
|**is_updateable**|**NULL-Bit**|Gibt 1 zurück, wenn die Spalte aktualisiert werden kann, andernfalls 0. Gibt NULL zurück, wenn nicht ermittelt werden kann, ob die Spalte aktualisiert werden kann.|  
|**is_computed_column**|**NULL-Bit**|Gibt 1 zurück, wenn die Spalte eine berechnete Spalte, andernfalls 0. Gibt NULL zurück, wenn nicht ermittelt werden kann, ob die Spalte eine berechnete Spalte ist.|  
|**is_sparse_column_set**|**NULL-Bit**|Gibt 1 zurück, wenn die Spalte eine Sparsespalte ist, andernfalls 0. Gibt NULL zurück, wenn nicht ermittelt werden kann, dass die Spalte Teil eines sparsespaltensatzes ist.|  
|**ordinal_in_order_by_list**|**Smallint NULL**|Die Position dieser Spalte in der ORDER BY-Liste. Gibt NULL zurück, wenn die Spalte in der ORDER BY-Liste nicht angezeigt wird, oder wenn ORDER BY-Liste nicht eindeutig bestimmt werden kann.|  
|**order_by_list_length**|**Smallint NULL**|Länge der ORDER BY-Liste. Gibt NULL zurück, wenn keine ORDER BY-Liste vorhanden ist oder die ORDER BY-Liste nicht eindeutig bestimmt werden kann. Beachten Sie, dass dieser Wert für alle von zurückgegebenen Zeilen gleich **Sp_describe_first_result_set.**|  
|**order_by_is_descending**|**Smallint NULL**|Wenn Ordinal_in_order_by_list nicht NULL ist, ist die **Order_by_is_descending** -Spalte meldet die Richtung der ORDER BY-Klausel für diese Spalte. Andernfalls wird NULL gemeldet.|  
|**tds_type_id**|**Int nicht NULL**|Für die interne Verwendung.|  
|**tds_length**|**Int nicht NULL**|Für die interne Verwendung.|  
|**tds_collation_id**|**Int NULL**|Für die interne Verwendung.|  
|**tds_collation_sort_id**|**Tinyint NULL**|Für die interne Verwendung.|  
  
## <a name="remarks"></a>Hinweise  
 **Sp_describe_first_result_set** wird sichergestellt, dass wenn die Prozedur die ersten Resultset-Metadaten für (eine hypothetische) zurückgibt Batch ein und dieser Batch (A) anschließend klicken Sie dann den Batch ausgeführt werden, entweder (1) löst einen Fehler aus – Zeitpunkt der Optimierung, (2) Löst einen Laufzeitfehler, (3) gibt kein Ergebnis festgelegt ist, oder (4) zurück, die einen ersten mit den gleichen Metadaten beschriebenen Resultset **Sp_describe_first_result_set**.  
  
 Der Name, die NULL-Zulässigkeit und der Datentyp können abweichen. Wenn **Sp_describe_first_result_set** gibt ein leeres Resultset, die Garantie, dass die Batchausführung keine Resultsets zurückgeben.  
  
 Dabei wird vorausgesetzt, dass keine relevanten schemaänderungen auf dem Server vorhanden sind. Relevanten schemaänderungen auf dem Server nicht einschließen, Erstellen von temporären Tabellen oder Tabellenvariablen im Batch zwischen dem Zeitpunkt, **Sp_describe_first_result_set** aufgerufen wird und die Uhrzeit, die während der das Resultset zurückgegeben wird Ausführung wie schemaänderungen durch Batch b  
  
 **Sp_describe_first_result_set** gibt Sie in den folgenden Fällen einen Fehler zurück.  
  
-   Wenn die Eingabe \@Tsql ist kein gültiger [!INCLUDE[tsql](../../includes/tsql-md.md)] Batch. Gültigkeit wird bestimmt durch Analysieren der [!INCLUDE[tsql](../../includes/tsql-md.md)] Batch. Alle Fehler, die durch den Batch verursacht während der abfrageoptimierung oder-Ausführung werden nicht berücksichtigt, wenn bestimmt wird, ob die [!INCLUDE[tsql](../../includes/tsql-md.md)] Batch gültig ist.  
  
-   Wenn \@Params ist nicht NULL und enthält eine Zeichenfolge, die nicht auf einen syntaktisch gültige deklarationszeichenfolge für Parameter ist, oder wenn es sich um eine Zeichenfolge enthält, deklariert einen beliebigen Parameter mehr als einmal.  
  
-   Wenn die Eingabe [!INCLUDE[tsql](../../includes/tsql-md.md)] eingabebatch deklariert eine lokale Variable mit dem gleichen Namen wie ein Parameter in deklariert \@Params.  
  
-   Die Anweisung verwendet eine temporäre Tabelle.  
  
-   Die Abfrage umfasst die Erstellung einer dauerhaften Tabelle, die dann abgefragt wird.  
  
 Wenn alle anderen Überprüfungen erfolgreich sind, werden alle möglichen Ablaufsteuerungspfade im Eingabebatch berücksichtigt. Diese berücksichtigt alle ablaufsteuerungsanweisungen (GOTO, IF/ELSE, WHILE, und [!INCLUDE[tsql](../../includes/tsql-md.md)] TRY/CATCH-Blöcke) sowie alle Prozeduren, dynamische [!INCLUDE[tsql](../../includes/tsql-md.md)] Batches oder Trigger, die vom eingabebatch durch eine EXEC-Anweisung eine DDL-Anweisung, die bewirkt, dass aufgerufen DDL-Trigger ausgelöst werden, oder eine DML-Anweisung, die bewirkt, dass Trigger ausgelöst wird, werden in einer Zieltabelle oder für eine Tabelle, die aufgrund von kaskadierenden Aktion auf einer foreign Key-Einschränkung geändert wird. Bei einer Vielzahl möglicher Steuerelementpfade wird der Algorithmus irgendwann beendet.  
  
 Für jede-ablaufsteuerungspfads, die erste Anweisung (sofern vorhanden), die gibt ein Resultset richtet sich nach **Sp_describe_first_result_set**.  
  
 Bei mehreren möglichen ersten Anweisungen in einem Batch kann sich das jeweilige Ergebnis im Hinblick auf die Anzahl der Spalten, die Spaltennamen, die NULL-Zulässigkeit und den Datentyp unterscheiden. Im Folgenden wird ausführlicher erläutert, wie diese Unterschiede gehandhabt werden:  
  
-   Wenn sich die Anzahl der Spalten unterscheidet, wird ein Fehler ausgelöst, und es wird kein Ergebnis zurückgegeben.  
  
-   Wenn der Spaltenname abweicht, wird der zurückgegebene Spaltenname auf NULL festgelegt.  
  
-   Wenn die NULL-Zulässigkeit abweicht, sind NULL-Werte in der zurückgegebenen NULL-Zulässigkeit zulässig.  
  
-   Wenn der Datentyp abweicht, wird ein Fehler ausgelöst, und nur in folgenden Fällen wird ein Ergebnis zurückgegeben:  
  
    -   **varchar(a)** zu **varchar(a')** , in denen ein "> ein.  
  
    -   **varchar(a)** zu **varchar(max)**  
  
    -   **nvarchar(a)** zu **nvarchar(a')** , in denen ein "> ein.  
  
    -   **nvarchar(a)** zu **nvarchar(max)**  
  
    -   **varbinary(a)** zu **varbinary(a')** , in denen ein "> ein.  
  
    -   **varbinary(a)** zu **varbinary(max)**  
  
 **Sp_describe_first_result_set** unterstützt keine Indirekte Rekursion.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Berechtigung zum Ausführen der \@Tsql-Argument.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="typical-examples"></a>Typische Beispiele  
  
#### <a name="a-simple-example"></a>A. Einfaches Beispiel  
 Im folgenden Beispiel wird das von einer einzelnen Abfrage zurückgegebene Resultset beschrieben.  
  
```  
sp_describe_first_result_set @tsql = N'SELECT object_id, name, type_desc FROM sys.indexes'  
```  
  
 Im folgenden Beispiel wird das von einer einzelnen Abfrage mit einem Parameter zurückgegebene Resultset veranschaulicht.  
  
```  
sp_describe_first_result_set @tsql =   
N'SELECT object_id, name, type_desc   
FROM sys.indexes   
WHERE object_id = @id1'  
, @params = N'@id1 int'  
```  
  
#### <a name="b-browse-mode-examples"></a>B. Beispielen für Durchsuchenmodi  
 In den folgenden drei Beispielen wird der Hauptunterschied zwischen den unterschiedlichen Modi für die Informationssuche veranschaulicht. In den Abfrageergebnissen waren nur die relevanten Spalten enthalten.  
  
 Beispiel mit dem Wert 0, der angibt, dass keine Informationen zurückgegeben werden.  
  
```sql  
CREATE TABLE dbo.t (a int PRIMARY KEY, b1 int);  
GO  
CREATE VIEW dbo.v AS SELECT b1 AS b2 FROM dbo.t;  
GO  
EXEC sp_describe_first_result_set N'SELECT b2 AS b3 FROM dbo.v', null, 0;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
|is_hidden|column_ordinal|NAME|source_schema|source_table|source_column|is_part_of_unique_key|  
|----------------|---------------------|----------|--------------------|-------------------|--------------------|-------------------------------|  
|0|1|b3|NULL|NULL|NULL|NULL|  
  
 Beispiel mit dem Wert 1, der angibt, dass Informationen so zurückgegeben werden, als ob in der Abfrage eine FOR BROWSE-Option eingeschlossen wäre.  
  
```sql  
EXEC sp_describe_first_result_set N'SELECT b2 AS b3 FROM v', null, 1  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
|is_hidden|column_ordinal|NAME|source_schema|source_table|source_column|is_part_of_unique_key|  
|----------------|---------------------|----------|--------------------|-------------------|--------------------|-------------------------------|  
|0|1|b3|dbo|t|B1|0|  
|1|2|a|dbo|t|a|1|  
  
 Beispiel mit dem Wert 2, der angibt, dass die Analyse erfolgt, als ob Sie einen Cursor vorbereiteten.  
  
```sql  
EXEC sp_describe_first_result_set N'SELECT b2 AS b3 FROM v', null, 2  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
|is_hidden|column_ordinal|NAME|source_schema|source_table|source_column|is_part_of_unique_key|  
|----------------|---------------------|----------|--------------------|-------------------|--------------------|-------------------------------|  
|0|1|B3|dbo|v|B2|0|  
|1|2|ROWSTAT|NULL|NULL|NULL|0|  
  
### <a name="examples-of-problems"></a>Beispiele für Probleme  
 In den folgenden Beispielen werden zwei Tabellen für alle Beispiele verwendet. Führen Sie die folgenden Anweisungen aus, um die Beispieltabellen zu erstellen.  
  
```  
CREATE TABLE dbo.t1 (a int NULL, b varchar(10) NULL, c nvarchar(10) NULL);  
CREATE TABLE dbo.t2 (a smallint NOT NULL, d varchar(20) NOT NULL, e int NOT NULL);  
```  
  
#### <a name="error-because-the-number-of-columns-differ"></a>Fehler aufgrund unterschiedlicher Spaltenanzahl  
 Die Anzahl der Spalten in möglichen ersten Resultsets weicht in diesem Beispiel ab.  
  
```  
sp_describe_first_result_set @tsql =   
N'  
IF(1=1)  
    SELECT a FROM t1;  
ELSE  
    SELECT a, b FROM t1;  
SELECT * FROM t; -- Ignored, not a possible first result set.'  
  
```  
  
#### <a name="error-because-the-data-types-differ"></a>Fehler aufgrund abweichender Datentypen  
 Die Spaltentypen unterscheiden sich in verschiedenen möglichen ersten Resultsets.  
  
```  
sp_describe_first_result_set @tsql =   
N'  
IF(1=1)  
    SELECT a FROM t1;  
ELSE  
    SELECT a FROM t2;  
```  
  
 Ergebnis: Fehler, die nicht übereinstimmende Typen (**Int** im Vergleich zu **Smallint**).  
  
#### <a name="column-name-cannot-be-determined"></a>Spaltenname kann nicht bestimmt werden  
 Die Spalten in möglichen ersten Resultsets unterscheiden sich hinsichtlich der Länge für identische Typen mit variabler Länge, NULL-Zulässigkeiten und Spaltennamen:  
  
```  
sp_describe_first_result_set @tsql =   
N'  
IF(1=1)  
    SELECT b FROM t1;  
ELSE  
    SELECT d FROM t2; '  
```  
  
 Ergebnis: \<Unbekannter Spaltenname > **varchar(20) NULL**  
  
#### <a name="column-name-forced-to-be-identical-through-aliasing"></a>Spaltenname mit durch Aliasing erzwungenem identischem Spaltennamen  
 Analog zum vorherigen, die Namen der Spalten sind jedoch aufgrund von Spaltenaliasing identisch.  
  
```  
sp_describe_first_result_set @tsql =   
N'  
IF(1=1)  
    SELECT b FROM t1;  
ELSE  
    SELECT d AS b FROM t2;'  
```  
  
 Ergebnis: b **Varchar (20) NULL**  
  
#### <a name="error-because-column-types-cannot-be-matched"></a>Fehler aufgrund nicht zuzuordnender Spaltentypen  
 Die Spaltentypen unterscheiden sich in verschiedenen möglichen ersten Resultsets.  
  
```  
sp_describe_first_result_set @tsql =   
N'  
IF(1=1)  
    SELECT b FROM t1;  
ELSE  
    SELECT c FROM t1;'  
```  
  
 Ergebnis: Fehler, die nicht übereinstimmende Typen (**varchar(10)** im Vergleich zu **nvarchar(10)**).  
  
#### <a name="result-set-can-return-an-error"></a>Resultset kann einen Fehler zurückgeben  
 Das erste Resultset ist Fehler oder Resultset.  
  
```  
sp_describe_first_result_set @tsql =   
N'  
IF(1=1)  
    RAISERROR(''Some Error'', 16, 1);  
  
ELSE  
    SELECT a FROM t1;  
SELECT e FROM t2; -- Ignored, not a possible first result set.;'  
```  
  
 Ergebnis: eine **IntNULL**  
  
#### <a name="some-code-paths-return-no-results"></a>Einige Codepfade geben keine Ergebnisse zurück  
 Der erste Resultset ist NULL oder ein Resultset.  
  
```  
sp_describe_first_result_set @tsql =   
N'  
IF(1=1)  
    RETURN;  
SELECT a FROM t1;'  
```  
  
 Ergebnis: eine **IntNULL**  
  
#### <a name="result-from-dynamic-sql"></a>Ergebnis von dynamischem SQL  
 Das erste Resultset ist dynamisches SQL, das ermittelt werden kann, da es sich um eine Literalzeichenfolge handelt.  
  
```  
sp_describe_first_result_set @tsql =   
N'EXEC(N''SELECT a FROM t1'');'  
```  
  
 Ergebnis: eine **INT NULL**  
  
#### <a name="result-failure-from-dynamic-sql"></a>Ergebnisfehler von dynamischem SQL  
 Das erste Resultset ist aufgrund von dynamischem SQL nicht definiert.  
  
```  
sp_describe_first_result_set @tsql =   
N'  
DECLARE @SQL NVARCHAR(max);  
SET @SQL = N''SELECT a FROM t1 WHERE 1 = 1 '';  
IF(1=1)  
    SET @SQL += N'' AND e > 10 '';  
EXEC(@SQL); '  
```  
  
 Ergebnis: Fehler. Das Ergebnis kann aufgrund von dynamischem SQL nicht ermittelt werden.  
  
#### <a name="result-set-specified-by-user"></a>Vom Benutzer angegebenes Resultset  
 Das erste Resultset wird manuell vom Benutzer angegeben.  
  
```  
sp_describe_first_result_set @tsql =   
N'  
DECLARE @SQL NVARCHAR(max);  
SET @SQL = N''SELECT a FROM t1 WHERE 1 = 1 '';  
IF(1=1)  
    SET @SQL += N'' AND e > 10 '';  
EXEC(@SQL)  
    WITH RESULT SETS(  
        (Column1 BIGINT NOT NULL)  
    ); '  
```  
  
 Ergebnis: Column1 **Bigint nicht NULL**  
  
#### <a name="error-caused-by-a-ambiguous-result-set"></a>Von einem mehrdeutigen Resultset verursachter Fehler  
 In diesem Beispiel wird davon ausgegangen, dass ein anderer Benutzer, die mit dem Namen "user1" eine Tabelle mit dem Namen t1 im Standardschema s1 mit Spalten hat (eine **Int NULL nicht**).  
  
```  
sp_describe_first_result_set @tsql =   
N'  
    IF(@p > 0)  
    EXECUTE AS USER = ''user1'';  
    SELECT * FROM t1;'  
, @params = N'@p int'  
```  
  
 Ergebnis: Fehler. T1 kann entweder "T1" oder "s1.t1, jeweils eine andere Anzahl von Spalten sein.  
  
#### <a name="result-even-with-ambiguous-result-set"></a>Ergebnis auch bei mehrdeutigem Resultset  
 Verwenden Sie die gleichen Annahmen wie im vorherigen Beispiel.  
  
```  
sp_describe_first_result_set @tsql =   
N'  
    IF(@p > 0)  
    EXECUTE AS USER = ''user1'';  
    SELECT a FROM t1;'  
```  
  
 Ergebnis: eine **Int NULL** da sowohl dbo.t1.a und s1.t1.a den Typ aufweisen **Int** NULL- Zulässigkeit unterscheidet.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_describe_undeclared_parameters &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql.md)   
 [sys.dm_exec_describe_first_result_set &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-transact-sql.md)   
 [sys.dm_exec_describe_first_result_set_for_object &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-for-object-transact-sql.md)  
 
