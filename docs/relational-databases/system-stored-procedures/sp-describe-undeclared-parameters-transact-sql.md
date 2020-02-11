---
title: sp_describe_undeclared_parameters (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_describe_undeclared_parameters
- sp_describe_undeclared_parameters_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_describe_undeclared_parameters
ms.assetid: 6f016da6-dfee-4228-8b0d-7cd8e7d5a354
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1205572235b141709cd463476182d9b405446188
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "72908329"
---
# <a name="sp_describe_undeclared_parameters-transact-sql"></a>sp_describe_undeclared_parameters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Gibt ein Resultset zurück, das Metadaten zu nicht deklarierten Parametern in einem [!INCLUDE[tsql](../../includes/tsql-md.md)] Batch enthält. Berücksichtigt jeden Parameter, der ** \@im spql** -Batch verwendet wird, aber nicht in ** \@para**Metern deklariert ist. Ein Resultset wird zurückgegeben, das für jeden dieser Parameter eine Zeile mit den abgeleiteten Typinformationen für diesen Parameter enthält. Die Prozedur gibt ein leeres Resultset zurück, wenn der ** \@TQL** -Eingabe Batch über keine Parameter verfügt, ausgenommen der in ** \@para**Metern deklarierten Parameter.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```sql
  
sp_describe_undeclared_parameters   
    [ @tsql = ] 'Transact-SQL_batch'   
    [ , [ @params = ] N'parameters' data type ] [, ...n]  
```  
  
## <a name="arguments"></a>Argumente  
`[ \@tsql = ] 'Transact-SQL\_batch'`Eine oder mehrere [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen. *Transact-SQL_batch* kann vom Datentyp **nvarchar (**_n_**)** oder **nvarchar (max)** sein.  
  
`[ \@params = ] N'parameters'`\@Parameter stellen eine Deklarations Zeichenfolge für Parameter [!INCLUDE[tsql](../../includes/tsql-md.md)] für den Batch bereit, ähnlich wie sp_executesql funktioniert. *Parameter* können **nvarchar (**_n_**)** oder **nvarchar (max)** sein.  
  
 Ist eine Zeichenfolge, die die Definitionen aller Parameter enthält, die in *Transact-SQL_batch*eingebettet wurden. Die Zeichenfolge muss eine Unicode-Konstante oder eine Unicode-Variable sein. Jede Parameterdefinition besteht aus einem Parameternamen und einem Datentyp. Dabei ist n ein Platzhalter für zusätzlicher Parameterdefinitionen. Wenn die Transact-SQL-Anweisung oder der Batch in der Anweisung keine Parameter enthält \@, sind keine Parameter erforderlich. Der Standardwert für diesen Parameter ist NULL.  
  
 Datentyp  
 Der Datentyp des Parameters.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **sp_describe_undeclared_parameters** gibt bei Erfolg immer den Rückgabestatus 0 zurück. Wenn die Prozedur einen Fehler auslöst und die Prozedur als RPC aufgerufen wird, wird der Rückgabestatus vom Fehlertyp aufgefüllt, der in der error_type-Spalte von sys. dm_exec_describe_first_result_set beschrieben wird. Wenn die Prozedur von [!INCLUDE[tsql](../../includes/tsql-md.md)] aufgerufen wird, ist der Rückgabewert immer 0, auch bei Fehlern.  
  
## <a name="result-sets"></a>Resultsets  
 **sp_describe_undeclared_parameters** gibt das folgende Resultset zurück.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**parameter_ordinal**|**int NOT NULL**|Enthält die Ordnungsposition des Parameters im Resultset. Die Position des ersten Parameters wird mit 1 angegeben.|  
|**name**|**vom Datentyp sysname ist nicht NULL.**|Enthält den Namen des Parameters.|  
|**suggested_system_type_id**|**int NOT NULL**|Enthält die **system_type_id** des Datentyps des Parameters, wie in sys. types angegeben.<br /><br /> Bei CLR-Typen wird von dieser Spalte der Wert 240 zurückgegeben, obwohl die **system_type_name** Spalte NULL zurückgibt.|  
|**suggested_system_type_name**|**nvarchar (256) NULL**|Enthält den Namen des Datentyps. Enthält für den Datentyp des Parameters angegebene Argumente (z. B. Länge, Genauigkeit, Skala). Wenn der Datentyp ein benutzerdefinierter Aliastyp ist, wird der zugrunde liegende Systemtyp hier angegeben. Wenn es sich um einen benutzerdefinierten CLR-Datentyp handelt, wird in dieser Spalte NULL zurückgegeben. Wenn der Typ des Parameters nicht abgeleitet werden kann, wird NULL zurückgegeben.|  
|**suggested_max_length**|**smallint not NULL**|Siehe sys. Columns. für **max_length** Spalten Beschreibung.|  
|**suggested_precision**|**tinyint not NULL**|Siehe sys. Columns. enthält eine Beschreibung der Genauigkeitsspalte.|  
|**suggested_scale**|**tinyint not NULL**|Siehe sys. Columns. enthält eine Beschreibung der Skalierungsspalte.|  
|**suggested_user_type_id**|**int NULL**|Enthält bei CLR- und Aliastypen die user_type_id des Datentyps der Spalte, wie in sys.types angegeben. Andernfalls NULL.|  
|**suggested_user_type_database**|**vom Datentyp sysname NULL**|Enthält bei CLR- und Aliastypen den Namen der Datenbank, in der der Typ definiert wurde. Andernfalls NULL.|  
|**suggested_user_type_schema**|**vom Datentyp sysname NULL**|Enthält bei CLR- und Aliastypen den Namen des Schemas, in dem der Typ definiert wurde. Andernfalls NULL.|  
|**suggested_user_type_name**|**vom Datentyp sysname NULL**|Enthält bei CLR- und Aliastypen den Namen des Typs. Andernfalls NULL.|  
|**suggested_assembly_qualified_type_name**|**nvarchar (4000) NULL**|Gibt für CLR-Typen den Namen der Assembly und der Klasse zurück, die den Typ definiert. Andernfalls NULL.|  
|**suggested_xml_collection_id**|**int NULL**|Enthält die xml_collection_id des Datentyps des Parameters, wie in sys. Columns angegeben. Diese Spalte gibt NULL zurück, wenn der zurückgegebene Typ keiner XML-Schemaauflistung zugeordnet ist.|  
|**suggested_xml_collection_database**|**vom Datentyp sysname NULL**|Enthält die Datenbank, in der die XML-Schemaauflistung definiert ist, die diesem Typ zugeordnet wurde. Diese Spalte gibt NULL zurück, wenn der zurückgegebene Typ keiner XML-Schemaauflistung zugeordnet ist.|  
|**suggested_xml_collection_schema**|**vom Datentyp sysname NULL**|Enthält das Schema, in dem die XML-Schemaauflistung definiert ist, die diesem Typ zugeordnet wurde. Diese Spalte gibt NULL zurück, wenn der zurückgegebene Typ keiner XML-Schemaauflistung zugeordnet ist.|  
|**suggested_xml_collection_name**|**vom Datentyp sysname NULL**|Enthält den Namen der XML-Schemaauflistung, die diesem Typ zugeordnet wurde. Diese Spalte gibt NULL zurück, wenn der zurückgegebene Typ keiner XML-Schemaauflistung zugeordnet ist.|  
|**suggested_is_xml_document**|**Bit not NULL**|Gibt 1 zurück, wenn als Typ XML zurückgegeben wird und sichergestellt ist, dass es sich um ein XML-Dokument handelt. Andernfalls wird 0 zurückgegeben.|  
|**suggested_is_case_sensitive**|**Bit not NULL**|Gibt 1 zurück, wenn die Spalte von einem Zeichenfolgentyp ist, bei dem die Groß-/Kleinschreibung beachtet wird, andernfalls 0.|  
|**suggested_is_fixed_length_clr_type**|**Bit not NULL**|Gibt 1 zurück, wenn die Spalte von einem CLR-Typ mit fester Länge ist, andernfalls 0.|  
|**suggested_is_input**|**Bit not NULL**|Gibt 1 zurück, wenn der Parameter an anderer Stelle verwendet wird als links einer Zuweisung. Andernfalls wird 0 zurückgegeben.|  
|**suggested_is_output**|**Bit not NULL**|Gibt 1 zurück, wenn der Parameter auf der linken Seite einer Zuweisung verwendet wird oder an einen Ausgabeparameter einer gespeicherten Prozedur übergeben wird. Andernfalls wird 0 zurückgegeben.|  
|**formal_parameter_name**|**vom Datentyp sysname NULL**|Wenn es sich bei dem Parameter um ein Argument für eine gespeicherte Prozedur oder eine benutzerdefinierte Funktion handelt, wird der Name des entsprechenden formalen Parameters zurückgegeben. Andernfalls wird NULL zurückgegeben.|  
|**suggested_tds_type_id**|**int NOT NULL**|Zur internen Verwendung.|  
|**suggested_tds_length**|**int NOT NULL**|Zur internen Verwendung.|  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_describe_undeclared_parameters** gibt immer den Rückgabestatus 0 (null) zurück.  
  
 Die häufigste Verwendung besteht darin, dass für eine Anwendung eine [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung ausgeführt wird, die möglicherweise Parameter enthält und von dieser verarbeitet werden muss. Dies gilt beispielsweise für eine Benutzeroberfläche (z. B. ODBCTest oder RowsetViewer), bei der der Benutzer eine Abfrage mit ODBC-Parametersyntax eingibt. Die Anwendung muss die Anzahl der Parameter dynamisch ermitteln und bei jedem den Benutzer auffordern.  
  
 Ein weiteres Beispiel liegt vor, wenn eine Anwendung ohne Benutzereingabe eine Schleife in den Parametern ausführen und die Daten für diese von einem anderen Speicherort (z. B. einer Tabelle) abrufen muss. In diesem Fall muss die Anwendung nicht alle Parameterinformationen zusammen übergeben. Stattdessen kann die Anwendung alle Parameterinformationen vom Anbieter und die Daten selbst aus der Tabelle abrufen. Code, der **sp_describe_undeclared_parameters** verwendet, ist allgemeinerer und erfordert weniger wahrscheinlich Änderungen, wenn sich die Datenstruktur zu einem späteren Zeitpunkt ändert.  
  
 **sp_describe_undeclared_parameters** gibt einen Fehler in einem der folgenden Fälle zurück.  
  
-   , Wenn die \@Eingabe-zql kein gültiger [!INCLUDE[tsql](../../includes/tsql-md.md)] Batch ist. Die Gültigkeit wird durch analysieren und Analysieren des [!INCLUDE[tsql](../../includes/tsql-md.md)] Batches bestimmt. Fehler, die durch den Batch während der Abfrageoptimierung oder während der Ausführung verursacht werden, werden nicht [!INCLUDE[tsql](../../includes/tsql-md.md)] berücksichtigt, wenn bestimmt wird, ob der Batch gültig ist.  
  
-   , \@Wenn Parameter nicht NULL sind und eine Zeichenfolge enthält, die keine syntaktisch gültige Deklarations Zeichenfolge für Parameter ist, oder, wenn Sie eine Zeichenfolge enthält, die einen Parameter mehrmals deklariert.  
  
-   , Wenn der [!INCLUDE[tsql](../../includes/tsql-md.md)] Eingabe Batch eine lokale Variable mit demselben Namen wie ein in \@Parametern deklarierter Parameter deklariert.  
  
- , Wenn die Anweisung auf temporäre Tabellen verweist.

- Die Abfrage umfasst die Erstellung einer dauerhaften Tabelle, die dann abgefragt wird.
  
 Wenn \@"TQL" keine Parameter aufweist, die nicht in \@"Parser" deklariert sind, gibt die Prozedur ein leeres Resultset zurück.  
  
## <a name="parameter-selection-algorithm"></a>Algorithmus für die Parameterauswahl  
 Bei einer Abfrage mit nicht deklarierten Parametern erfolgt die Datentypableitung für nicht deklarierte Parameter in drei Schritten.  
  
 **Schritt 1**  
  
 Der erste Schritt der Datentypableitung für eine Abfrage mit nicht deklarierten Parametern besteht darin, die Datentypen aller Teilausdrücke zu ermitteln, deren Datentypen nicht von den nicht deklarierten Parametern abhängen. Der Typ kann für die folgenden Ausdrücke ermittelt werden:  
  
-   Spalten, Konstanten, Variablen und deklarierte Parameter.  
  
-   Ergebnisse eines Aufrufs einer benutzerdefinierten Funktion (User-Defined Function, UDF).  
  
-   Ein Ausdruck mit Datentypen, die nicht für alle Eingaben von den nicht deklarierten Parametern abhängen.  
  
 Sehen Sie sich dies beispielsweise für die Abfrage `SELECT dbo.tbl(@p1) + c1 FROM t1 WHERE c2 = @p2 + 2` an. Die Ausdrücke dbo. tbl (\@P1) + C1 und C2 verfügen über Datentypen, und \@der Ausdruck \@P1 und P2 + 2 nicht.  
  
 Wenn nach diesem Schritt ein anderer Ausdruck als ein UDF-Aufruf über zwei Argumente ohne Datentypen verfügt, tritt bei der Typableitung ein Fehler auf. Beispielsweise führen alle folgenden Ausdrücke zu Fehlern:  
  
```sql
SELECT * FROM t1 WHERE @p1 = @p2  
SELECT * FROM t1 WHERE c1 = @p1 + @p2  
SELECT * FROM t1 WHERE @p1 = SUBSTRING(@p2, 2, 3)  
```  
  
 Im folgenden Beispiel wird kein Fehler erzeugt:  
  
```sql
SELECT * FROM t1 WHERE @p1 = dbo.tbl(c1, @p2, @p3)  
```
  
 **Schritt 2**  
  
 Für einen angegebenen nicht deklarierten Parameter \@p findet der typableitungs Algorithmus den innersten Ausdruck\@E (p) \@, der p enthält und eine der folgenden ist:  
  
-   Ein Argument für einen Vergleich oder ein Zuweisungsoperator.  
  
-   Ein Argument für eine benutzerdefinierte Funktion (einschließlich Tabellenwert-UDFs), Prozedur oder Methode.  
  
-   Ein Argument für eine **Values** -Klausel einer **Insert** -Anweisung.  
  
-   Ein Argument für eine **Cast** -oder **Convert-Konvertierung**.  
  
 Der typableitungs Algorithmus findet einen Ziel Datentyp TT\@(p) für E\@(p). Für die vorherigen Beispiele sind die folgenden Zieldatentypen möglich:  
  
-   Der Datentyp der anderen Seite des Vergleichs oder der Zuweisung.  
  
-   Der deklarierte Datentyp des Parameters, an den dieses Argument übergeben wird.  
  
-   Der Datentyp der Spalte, in der dieser Wert eingefügt wird.  
  
-   Der Datentyp, in den die Anweisung umgewandelt oder konvertiert wird.  
  
 Sehen Sie sich dies beispielsweise für die Abfrage `SELECT * FROM t WHERE @p1 = dbo.tbl(@p2 + c1)` an. Anschließend ist e\@(P1) \@= P1, E\@(P2) \@= P2 + C1, TT\@(P1) der deklarierte Rückgabe Datentyp von dbo. tbl, und TT\@(P2) ist der deklarierte Parameter Datentyp für dbo. tbl.  
  
 Wenn \@p in keinem Ausdruck enthalten ist, der am Anfang des Schritts 2 aufgelistet ist, bestimmt der typableitungs Algorithmus,\@dass E (p) der größte Skalarausdruck \@ist, der p enthält, und der typableitungs Algorithmus berechnet nicht den Ziel Datentyp TT (\@p)\@für E (p). Wenn die Abfrage beispielsweise `@p + 2` ausgewählt ist, dann ist E\@(p) \@= p + 2, und es ist kein TT\@(p) vorhanden.  
  
 **Schritt 3**  
  
 Nachdem nun E (\@p) und TT (\@p) identifiziert wurden, leitet der typableitungs Algorithmus einen Datentyp für \@p auf eine der beiden folgenden Weisen ab:  
  
-   Einfache Ableitung  
  
     Wenn E (\@p) = \@p und TT (\@p) vorhanden ist, d. h \@., wenn p direkt ein Argument für einen der am Anfang von Schritt 2 aufgeführten Ausdrücke ist, leitet der typableitungs Algorithmus den Datentyp \@von p in TT (\@p) ab. Beispiel:  
  
    ```sql
    SELECT * FROM t WHERE c1 = @p1 AND @p2 = dbo.tbl(@p3)  
    ```  
  
     Der Datentyp für \@P1, \@P2 und \@P3 ist der Datentyp von C1, der Rückgabe Datentyp von dbo. tbl und der Parameter Datentyp für dbo. tbl.  
  
     Wenn \@p ein Argument für einen \<-, >-, \<=-oder >=-Operator ist, gelten als Sonderfall keine einfachen ABLEITUNGS Regeln. Der Typableitungsalgorithmus verwendet die allgemeinen, im nächsten Abschnitt erklärten Ableitungsregeln. Betrachten Sie beispielsweise die folgenden beiden Abfragen für Fälle, in denen c1 eine Spalte vom Datentyp char(30) ist:  
  
    ```sql
    SELECT * FROM t WHERE c1 = @p  
    SELECT * FROM t WHERE c1 > @p  
    ```  
  
     Im ersten Fall leitet der typableitungs Algorithmus **char (30)** als Datentyp für \@p gemäß den Regeln weiter oben in diesem Thema ab. Im zweiten Fall leitet der typableitungs Algorithmus **varchar (8000)** gemäß den allgemeinen ABLEITUNGS Regeln im nächsten Abschnitt ab.  
  
-   Allgemeine Ableitung  
  
     Wenn keine einfache Ableitung möglich ist, kommen für nicht deklarierte Parameter die folgenden Datentypen infrage:  
  
    -   Ganzzahlige Datentypen (**Bit**, **tinyint**, **smallint**, **int**, **bigint**)  
  
    -   Money-Datentypen (**smallmoney**, **Money**)  
  
    -   Gleit Komma Datentypen (**float**, **Real**)  
  
    -   **numeric (38, 19)** : andere numerische oder Dezimal Datentypen werden nicht berücksichtigt.  
  
    -   **varchar (8000)**, **varchar (max)**, **nvarchar (4000)** und **nvarchar (max)** -andere Zeichen folgen Datentypen (z. b. **Text**, **char (8000)**, **nvarchar (30)** usw.) werden nicht berücksichtigt.  
  
    -   **varbinary (8000)** und **varbinary (max)** -andere binäre Datentypen werden nicht berücksichtigt (z. b. **Image**, **Binary (8000)**, **varbinary (30)** usw.).  
  
    -   **Date**, **time (7)**, **smalldatetime**, **DateTime**, **datetime2 (7)**, **DateTimeOffset (7)** -andere Datums-und Uhrzeit Typen, wie z. b. **time (4)**, werden nicht berücksichtigt.  
  
    -   **sql_variant**  
  
    -   **basi**  
  
    -   System definierte CLR-Typen (**hierarchyid**, **Geometry**, **geography**)  
  
    -   Benutzerdefinierte CLR-Typen  
  
### <a name="selection-criteria"></a>Auswahlkriterien  
 Von den infrage kommenden Datentypen wird jeder Datentyp abgelehnt, durch den die Abfrage ungültig gemacht würde. Von den verbleibenden infrage kommenden Datentypen wählt der Typableitungsalgorithmus anhand der folgenden Regeln einen aus.  
  
1.  Der Datentyp, der die kleinste Anzahl impliziter Konvertierungen in\@E (p) erzeugt, wird ausgewählt. Wenn ein bestimmter Datentyp einen Datentyp\@für E (p) erzeugt, der nicht mit TT (\@p) identisch ist, betrachtet der typableitungs Algorithmus dies als zusätzliche implizite Konvertierung des Datentyps e\@(p) in TT\@(p).  
  
     Beispiel:  
  
    ```sql
    SELECT * FROM t WHERE Col_Int = Col_Int + @p  
    ```  
  
     In diesem Fall ist E (\@p) Col_Int + \@p, und TT (\@p) ist **int**. **int** wird für \@p ausgewählt, da es keine impliziten Konvertierungen erzeugt. Jeder andere ausgewählte Datentyp erzeugt mindestens eine implizite Konvertierung.  
  
2.  Wenn mehrere Datentypen gleich wenige Konvertierungen erzeugen, wird der Datentyp mit dem höheren Rang verwendet. Beispiel:  
  
    ```sql
    SELECT * FROM t WHERE Col_Int = Col_smallint + @p  
    ```  
  
     In diesem Fall wird mit **int** und **smallint** eine Konvertierung erzeugt. Jeder andere Datentyp erzeugt mehr als eine Konvertierung. Da **int** Vorrang vor **smallint**hat, wird **int** für \@p verwendet. Weitere Informationen zur Rangfolge von Datentypen finden Sie unter [Rangfolge der Datentypen &#40;Transact-SQL-&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
     Diese Regel gilt nur, wenn zwischen jedem Datentyp, der nach Regel 1 genauso wenige Konvertierungen wie ein anderer erzeugt, und dem Datentyp mit dem höchsten Rang eine implizite Konvertierung erfolgt. Wenn keine implizite Konvertierung erfolgt, tritt bei der Datentypableitung ein Fehler auf. Beispielsweise kann die Datentyp Ableitung in der Abfrage `SELECT @p FROM t`nicht ausgeführt werden, da \@jeder Datentyp für p gleichermaßen gut wäre. Beispielsweise gibt es keine implizite Konvertierung von **int** in **XML**.  
  
3.  Wenn zwei ähnliche Datentypen mit Regel 1 verknüpft sind, z. b. **varchar (8000)** und **varchar (max)**, wird der kleinere Datentyp (**varchar (8000)**) ausgewählt. Das gleiche Prinzip gilt für die Datentypen **nvarchar** und **varbinary** .  
  
4.  Für die Zwecke der Regel 1 bevorzugt der Typableitungsalgorithmus bestimmte Konvertierungen gegenüber anderen. Die Konvertierungen werden in der folgenden Reihenfolge bevorzugt (beste bis schlechteste):  

    1.  Konvertierung zwischen gleichem Basisdatentyp mit unterschiedlicher Länge.  
  
    2.  Konvertierung zwischen einer Version mit fester Länge und derselben Datentyp Version (z. b. **char** in **varchar**).  
  
    3.  Konvertierung zwischen **null** und **int**.  
  
    4.  Jede andere Konvertierung.  
  
 Für die Abfrage `SELECT * FROM t WHERE [Col_varchar(30)] > @p`wird z. b. **varchar (8000)** ausgewählt, da die Konvertierung (a) am besten ist. Bei der Abfrage `SELECT * FROM t WHERE [Col_char(30)] > @p`wird auch **varchar (8000)** ausgewählt, weil eine Typkonvertierung (b) verursacht wird und da eine andere Auswahl (z. b. **varchar (4000)**) eine Typkonvertierung (d) verursachen würde.  
  
 Als letztes Beispiel wird bei einer Abfrage `SELECT NULL + @p` **int** für p ausgewählt, da \@dies zu einer Typkonvertierung (c) führt.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Berechtigung zum Ausführen \@des "parql"-Arguments.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden bestimmte Informationen zurückgegeben, z. B. der erwartete Datentyp für den nicht deklarierten `@id`-Parameter und den nicht deklarierten `@name`-Parameter.  
  
```sql
sp_describe_undeclared_parameters @tsql =   
N'SELECT object_id, name, type_desc   
FROM sys.indexes  
WHERE object_id = @id OR name = @name'  
  
```  
  
 Wenn der `@id`-Parameter als `@params`-Verweis bereitgestellt wird, wird der `@id`-Parameter im Resultset ausgelassen, und nur der `@name`-Parameter wird beschrieben.  
  
```sql
sp_describe_undeclared_parameters @tsql =   
N'SELECT object_id, name, type_desc   
FROM sys.indexes  
WHERE object_id = @id OR NAME = @name',  
@params = N'@id int'  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_describe_first_result_set &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md)   
 [sys. dm_exec_describe_first_result_set &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-transact-sql.md)   
 [sys. dm_exec_describe_first_result_set_for_object &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-for-object-transact-sql.md)
