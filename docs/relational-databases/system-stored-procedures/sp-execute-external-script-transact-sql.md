---
title: sp_execute_external_script (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: machine-learning
ms.topic: language-reference
f1_keywords:
- sp_execute_external_script_TSQL
- sys.sp_execute_external_script
- sys.sp_execute_external_script_TSQL
- sp_execute_external_script
dev_langs:
- TSQL
helpviewer_keywords:
- sp_execute_external_script
ms.assetid: de4e1fcd-0e1a-4af3-97ee-d1becc7f04df
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions||=azuresqldb-mi-current'
ms.openlocfilehash: 8800df26e505f1fffe25e6f65218481e7a8158f0
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/04/2020
ms.locfileid: "80663014"
---
# <a name="sp_execute_external_script-transact-sql"></a>sp_execute_external_script (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
Die **sp_execute_external_script** gespeicherte Prozedur führt ein Skript aus, das als Eingabeargument für die Prozedur bereitgestellt wird, und wird mit [Machine Learning Services](../../machine-learning/index.yml) und Language [Extensions](../../language-extensions/language-extensions-overview.md)verwendet. 

Für Machine Learning Services werden [Python](../../machine-learning/concepts/extension-python.md) und [R](../../machine-learning/concepts/extension-r.md) unterstützt. Für Spracherweiterungen wird Java unterstützt, muss aber mit [CREATE EXTERNAL LANGUAGE](../../t-sql/statements/create-external-language-transact-sql.md)definiert werden.

Um **sp_execute_external_script**auszuführen, müssen Sie zuerst Machine Learning Services oder Language Extensions installieren. Weitere Informationen finden Sie unter [Installieren von SQL Server Machine Learning Services (Python und R) unter Windows](../../machine-learning/install/sql-machine-learning-services-windows-install.md) und [Linux](../../linux/sql-server-linux-setup-machine-learning.md)oder Installieren von [SQL Server-Spracherweiterungen unter Windows](../../language-extensions/install/install-sql-server-language-extensions-on-windows.md) und [Linux](../../linux/sql-server-linux-setup-language-extensions.md).
::: moniker-end

::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
Die **sp_execute_external_script** gespeicherte Prozedur führt ein Skript aus, das als Eingabeargument für die Prozedur bereitgestellt wird, und wird mit [Machine Learning Services](../../machine-learning/index.yml) auf SQL Server 2017 verwendet. 

Für Machine Learning Services werden [Python](../../machine-learning/concepts/extension-python.md) und [R](../../machine-learning/concepts/extension-r.md) unterstützt. 

Um **sp_execute_external_script**auszuführen, müssen Sie zuerst Machine Learning Services installieren. Weitere Informationen finden Sie unter [Installieren von SQL Server Machine Learning Services (Python und R) unter Windows](../../machine-learning/install/sql-machine-learning-services-windows-install.md).
::: moniker-end

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
Die **sp_execute_external_script** gespeicherte Prozedur führt ein Skript aus, das als Eingabeargument für die Prozedur bereitgestellt wird, und wird mit [R Services](../../machine-learning/r/sql-server-r-services.md) auf SQL Server 2016 verwendet.

Für R Services ist [R](../../machine-learning/concepts/extension-r.md) die unterstützte Sprache.

Um **sp_execute_external_script**auszuführen, müssen Sie zuerst R Services installieren. Weitere Informationen finden Sie unter [Installieren von SQL Server Machine Learning Services (Python und R) unter Windows](../../machine-learning/install/sql-r-services-windows-install.md).
::: moniker-end

 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
## <a name="syntax"></a>Syntax

```
sp_execute_external_script   
    @language = N'language',   
    @script = N'script'  
    [ , @input_data_1 = N'input_data_1' ]   
    [ , @input_data_1_name = N'input_data_1_name' ]  
    [ , @input_data_1_order_by_columns = N'input_data_1_order_by_columns' ]    
    [ , @input_data_1_partition_by_columns = N'input_data_1_partition_by_columns' ]  
    [ , @output_data_1_name = N'output_data_1_name' ]  
    [ , @parallel = 0 | 1 ]  
    [ , @params = N'@parameter_name data_type [ OUT | OUTPUT ] [ ,...n ]' ] 
    [ , @parameter1 = 'value1' [ OUT | OUTPUT ] [ ,...n ] ]
```
::: moniker-end
::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
## <a name="syntax-for-2017-and-earlier"></a>Syntax für 2017 und früher

```
sp_execute_external_script   
    @language = N'language',   
    @script = N'script'  
    [ , @input_data_1 = N'input_data_1' ]   
    [ , @input_data_1_name = N'input_data_1_name' ]  
    [ , @output_data_1_name = N'output_data_1_name' ]  
    [ , @parallel = 0 | 1 ]  
    [ , @params = N'@parameter_name data_type [ OUT | OUTPUT ] [ ,...n ]' ] 
    [ , @parameter1 = 'value1' [ OUT | OUTPUT ] [ ,...n ] ]
```
::: moniker-end

## <a name="arguments"></a>Argumente
 Sprache = N'*Sprache*' ** \@**  
::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
 Gibt die Skriptsprache an. *Sprache* ist **sysname**. Gültige Werte sind **R**, **Python**und jede Sprache, die mit [CREATE EXTERNAL LANGUAGE](../../t-sql/statements/create-external-language-transact-sql.md) definiert ist (z. B. Java).
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
 Gibt die Skriptsprache an. *Sprache* ist **sysname**. In SQL Server 2017 sind gültige Werte **R** und **Python**.
::: moniker-end
::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
 Gibt die Skriptsprache an. *Sprache* ist **sysname**. In SQL Server 2016 ist der einzige gültige Wert **R**.
::: moniker-end

 script = N'*script*' Externes Sprachskript, das als Literal- oder Variableneingabe angegeben ist. ** \@** *Skript* ist **nvarchar(max)**.  

`[ @input_data_1 =  N'input_data_1' ]`Gibt die Eingabedaten an, die vom externen [!INCLUDE[tsql](../../includes/tsql-md.md)] Skript in Form einer Abfrage verwendet werden. Der Datentyp von *input_data_1* ist **nvarchar(max)**.

`[ @input_data_1_name = N'input_data_1_name' ]`Gibt den Namen der Variablen an, die @input_data_1zur Darstellung der von definierten Abfrage verwendet wird. Der Datentyp der Variablen im externen Skript hängt von der Sprache ab. Bei R ist die Eingabevariable ein Datenrahmen. Im Fall von Python muss die Eingabe tabellarisch sein. *input_data_1_name* ist **sysname**.  Der Standardwert ist *InputDataSet*.  

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
`[ @input_data_1_order_by_columns = N'input_data_1_order_by_columns' ]`Wird zum Erstellen von Modellen pro Partition verwendet. Gibt den Namen der Spalte an, die zum Bestellen des Resultsets verwendet wird, z. B. nach Produktname. Der Datentyp der Variablen im externen Skript hängt von der Sprache ab. Bei R ist die Eingabevariable ein Datenrahmen. Im Fall von Python muss die Eingabe tabellarisch sein.

`[ @input_data_1_partition_by_columns = N'input_data_1_partition_by_columns' ]`Wird zum Erstellen von Modellen pro Partition verwendet. Gibt den Namen der Spalte an, die zum Segmentieren von Daten verwendet wird, z. B. geografische Region oder Datum. Der Datentyp der Variablen im externen Skript hängt von der Sprache ab. Bei R ist die Eingabevariable ein Datenrahmen. Im Fall von Python muss die Eingabe tabellarisch sein. 
::: moniker-end

`[ @output_data_1_name =  N'output_data_1_name' ]`Gibt den Namen der Variablen im externen Skript an, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die die Daten enthält, an die nach Abschluss des Aufrufs der gespeicherten Prozedur zurückgegeben werden soll. Der Datentyp der Variablen im externen Skript hängt von der Sprache ab. Für R muss die Ausgabe ein Datenrahmen sein. Für Python muss die Ausgabe ein Pandas-Datenrahmen sein. *output_data_1_name* ist **sysname**.  Der Standardwert ist *OutputDataSet*.  

`[ @parallel = 0 | 1 ]`Aktivieren Sie die parallele Ausführung `@parallel` von R-Skripten, indem Sie den Parameter auf 1 setzen. Der Standardwert für diesen Parameter ist 0 (keine Parallelität). Wenn `@parallel = 1` die Ausgabe direkt an den Clientcomputer gestreamt wird, ist die `WITH RESULT SETS` Klausel erforderlich, und es muss ein Ausgabeschema angegeben werden.  

 + Bei R-Skripts, die keine RevoScaleR-Funktionen verwenden, kann die Verwendung des `@parallel` Parameters für die Verarbeitung großer Datasets von Vorteil sein, vorausgesetzt, das Skript kann trivial parallelisiert werden. Wenn Sie z. `predict` B. die R-Funktion mit `@parallel = 1` einem Modell verwenden, um neue Vorhersagen zu generieren, legen Sie sie als Hinweis auf das Abfragemodul fest. Wenn die Abfrage parallelisiert werden kann, werden Zeilen entsprechend der **MAXDOP-Einstellung** verteilt.  
  
 + Bei R-Skripts, die RevoScaleR-Funktionen verwenden, wird die `@parallel = 1` parallele Verarbeitung automatisch verarbeitet, und Sie sollten nicht für den **sp_execute_external_script-Aufruf** angeben.  
  
`[ @params = N'@parameter_name data_type [ OUT | OUTPUT ] [ ,...n ]' ]`Eine Liste der Eingabeparameterdeklarationen, die im externen Skript verwendet werden.  
  
`[ @parameter1 = 'value1' [ OUT | OUTPUT ] [ ,...n ] ]`Eine Liste von Werten für die Eingabeparameter, die vom externen Skript verwendet werden.  

## <a name="remarks"></a>Hinweise

> [!IMPORTANT]
> Die Abfragestruktur wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von gesteuert, und Benutzer können keine beliebigen Vorgänge für die Abfrage ausführen. 

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
Verwenden Sie **sp_execute_external_script,** um Skripts auszuführen, die in einer unterstützten Sprache geschrieben wurden. Unterstützte Sprachen sind **Python** und **R,** die mit Machine Learning Services verwendet werden, und jede Sprache, die mit [CREATE EXTERNAL LANGUAGE](../../t-sql/statements/create-external-language-transact-sql.md) (z. B. Java) definiert ist, die mit Language Extensions verwendet wird.
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
Verwenden Sie **sp_execute_external_script,** um Skripts auszuführen, die in einer unterstützten Sprache geschrieben wurden. Unterstützte Sprachen sind **Python** und **R** in SQL Server 2017 Machine Learning Services.
::: moniker-end
::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
Verwenden Sie **sp_execute_external_script,** um Skripts auszuführen, die in einer unterstützten Sprache geschrieben wurden. Die einzige unterstützte Sprache ist **R** in SQL Server 2016 R Services.
::: moniker-end

Standardmäßig werden Resultsets, die von dieser gespeicherten Prozedur zurückgegeben werden, mit unbenannten Spalten ausgegeben. Spaltennamen, die in einem Skript verwendet werden, sind in der Skriptumgebung lokal und werden nicht im ausgegebenen Resultset widergespiegelt. Um Resultsetspalten zu `WITH RESULT SET` benennen, [`EXECUTE`](../../t-sql/language-elements/execute-transact-sql.md)verwenden Sie die Klausel von .

Zusätzlich zur Rückgabe eines Resultsets können Sie skalare Werte mithilfe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von OUTPUT-Parametern zurückgeben. 
  
Sie können die Ressourcen steuern, die von externen Skripts verwendet werden, indem Sie einen externen Ressourcenpool konfigurieren. Weitere Informationen finden Sie unter [CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md). Informationen über die Arbeitsauslastung erhalten Sie in den Katalogansichten des Ressourcen-Gouverneurs, dMS und Leistungsindikatoren. Weitere Informationen finden Sie unter [Resource Governor Catalog Views &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md), Resource Governor Related Dynamic Management Views &#40;[Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md)und SQL [Server, External Scripts Object](../../relational-databases/performance-monitor/sql-server-external-scripts-object.md).  

### <a name="monitor-script-execution"></a>Überwachen der Skriptausführung

Überwachen sie die Skriptausführung mit [sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md) und [sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md). 

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
### <a name="parameters-for-partition-modeling"></a>Parameter für die Partitionsmodellierung

Sie können zwei zusätzliche Parameter festlegen, die die Modellierung partitionierter Daten ermöglichen, wobei Partitionen auf einer oder mehreren Spalten basieren, die Sie bereitstellen und die natürlich einen Datensatz in logische Partitionen segmentieren, die nur während der Skriptausführung erstellt und verwendet werden. Spalten, die sich wiederholende Werte für Alter, Geschlecht, geografische Region, Datum oder Uhrzeit enthalten, sind einige Beispiele, die sich für partitionierte Datensätze eignen.
 
Die beiden Parameter sind **input_data_1_partition_by_columns** und **input_data_1_order_by_columns**, wobei der zweite Parameter verwendet wird, um das Resultset zu ordnen. Die Parameter werden als `sp_execute_external_script` Eingaben übergeben, wobei das externe Skript einmal für jede Partition ausgeführt wird. Weitere Informationen und Beispiele finden Sie unter [Tutorial: Erstellen partitionsbasierter Modelle](https://docs.microsoft.com/sql/machine-learning/tutorials/r-tutorial-create-models-per-partition).

Sie können Skript parallel ausführen, indem Sie `@parallel=1`angeben. Wenn die Eingabeabfrage parallelisiert werden `@parallel=1` kann, sollten Sie `sp_execute_external_script`als Teil Ihrer Argumente auf festlegen. Standardmäßig arbeitet der Abfrageoptimierer unter `@parallel=1` für Tabellen mit mehr als 256 Zeilen, aber wenn Sie dies explizit behandeln möchten, enthält dieses Skript den Parameter als Demonstration.

> [!Tip]
> Für Trainingsworkloads können Sie `@parallel` mit einem beliebigen arbiträren Trainingsskript verwenden, sogar solche, die nicht von Microsoft stammende RX-Algorithmen verwenden In der Regel bieten nur RevoScaleR-Algorithmen (mit dem RX-Präfix) Parallelität in Trainingsszenarios in SQL Server. Mit den neuen Parametern in SQL Server vNext können Sie jedoch ein Skript parallelisieren, das Funktionen aufruft, die nicht speziell für diese Funktion entwickelt wurden.
::: moniker-end

### <a name="streaming-execution-for-python-and-r-scripts"></a>Streaming-Ausführung für Python- und R-Skripte  

Streaming ermöglicht es dem Python- oder R-Skript, mit mehr Daten zu arbeiten, als in den Arbeitsspeicher passen. Um die Anzahl der zeilenzusteuern, die während des Streamings `@params` übergeben wurden, geben Sie in der Auflistung einen Ganzzahlwert für den Parameter `@r_rowsPerRead` an.  Wenn Sie z. B. ein Modell trainieren, das sehr breite Daten verwendet, können Sie den Wert so anpassen, dass weniger Zeilen gelesen werden, um sicherzustellen, dass alle Zeilen in einem Datenblock gesendet werden können. Sie können diesen Parameter auch verwenden, um die Anzahl der Zeilen zu verwalten, die gleichzeitig gelesen und verarbeitet werden, um Probleme mit der Serverleistung zu verringern. 
  
Sowohl `@r_rowsPerRead` der Parameter für `@parallel` Streaming als auch das Argument sollten als Hinweise betrachtet werden. Damit der Hinweis angewendet werden kann, muss es möglich sein, einen SQL-Abfrageplan zu generieren, der eine parallele Verarbeitung enthält. Wenn dies nicht möglich ist, kann die parallele Verarbeitung nicht aktiviert werden.  
  
> [!NOTE]  
> Streaming und parallele Verarbeitung werden nur in Enterprise Edition unterstützt. Sie können die Parameter in Ihre Abfragen in der Standard Edition einschließen, ohne einen Fehler zu verursachen, aber die Parameter haben keine Auswirkungen und R-Skripte werden in einem einzigen Prozess ausgeführt.  
  
## <a name="restrictions"></a>Beschränkungen  

### <a name="data-types"></a>Datentypen

Die folgenden Datentypen werden nicht unterstützt, wenn sie in der Eingabeabfrage oder in den Parametern **sp_execute_external_script** Prozedur verwendet werden, und geben einen nicht unterstützten Typfehler zurück.  

Als Problemumgehung **wird** die Spalte oder der [!INCLUDE[tsql](../../includes/tsql-md.md)] Wert in einen unterstützten Typ eingeschrieben, bevor Sie sie an das externe Skript senden.  
  
-   **Cursor**  
  
-   **timestamp**  
  
-   **datetime2**, **datetimeoffset**, **Uhrzeit**  
  
-   **Sql_variant**  
  
-   **Text**, **Bild**  
  
-   **xml**  
  
-   **hierarchyid**, **geometrie**, **geographie**  
  
-   Benutzerdefinierte CLR-Typen

Im Allgemeinen wird jedes Resultset, das [!INCLUDE[tsql](../../includes/tsql-md.md)] einem Datentyp nicht zugeordnet werden kann, als NULL ausgegeben.  

### <a name="restrictions-specific-to-r"></a>Für R spezifische Beschränkungen

Wenn die Eingabe **Datumszeitwerte** enthält, die nicht dem zulässigen Wertebereich in R entsprechen, werden Werte in **NA**konvertiert. Dies ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erforderlich, da ein größerer Wertebereich als in der R-Sprache unterstützt wird.

Float-Werte (z. `-Inf` `NaN`B. , [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , ) werden nicht unterstützt, `+Inf`obwohl beide Sprachen IEEE 754 verwenden. Aktuelles Verhalten sendet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Werte nur direkt an; Infolgedessen löst der SQL-Client in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] einen Fehler aus. Daher werden diese Werte in **NULL**konvertiert.

## <a name="permissions"></a>Berechtigungen

Erfordert **EXECUTE ANY EXTERNAL SCRIPT** Datenbankberechtigung.  

## <a name="examples"></a>Beispiele

Dieser Abschnitt enthält Beispiele dafür, wie diese gespeicherte Prozedur [!INCLUDE[tsql](../../includes/tsql-md.md)]zum Ausführen von R- oder Python-Skripten mit verwendet werden kann.

### <a name="a-return-an-r-data-set-to-sql-server"></a>A. Zurückgeben eines R-Datensatzes an SQL Server  

Im folgenden Beispiel wird eine **sp_execute_external_script** gespeicherte Prozedur erstellt, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]sp_execute_external_script verwendet, um das iris-Dataset zurückzugeben, das in R enthalten ist, an .  

```sql
DROP PROC IF EXISTS get_iris_dataset;  
go  
CREATE PROC get_iris_dataset
AS  
BEGIN  
 EXEC   sp_execute_external_script  
       @language = N'R'  
     , @script = N'iris_data <- iris;'
     , @input_data_1 = N''  
     , @output_data_1_name = N'iris_data'
     WITH RESULT SETS (("Sepal.Length" float not null,   
           "Sepal.Width" float not null,  
        "Petal.Length" float not null,   
        "Petal.Width" float not null, "Species" varchar(100)));  
END;
GO
```

### <a name="b-generate-an-r-model-based-on-data-from-sql-server"></a>B. Generieren eines R-Modells basierend auf Daten aus SQL Server  

Im folgenden Beispiel wird eine **sp_execute_external_script** gespeicherte Prozedur erstellt, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]sp_execute_external_script verwendet, um ein Irismodell zu generieren und das Modell an zurückzugeben.  

> [!NOTE]
>  Dieses Beispiel erfordert eine vorherige Installation des Pakets e1071. Weitere Informationen finden Sie unter [Installieren zusätzlicher R-Pakete auf SQL Server](../../machine-learning/package-management/install-additional-r-packages-on-sql-server.md).

```sql
DROP PROC IF EXISTS generate_iris_model;
GO
CREATE PROC generate_iris_model
AS
BEGIN
 EXEC sp_execute_external_script  
      @language = N'R'  
     , @script = N'  
          library(e1071);  
          irismodel <-naiveBayes(iris_data[,1:4], iris_data[,5]);  
          trained_model <- data.frame(payload = as.raw(serialize(irismodel, connection=NULL)));  
'  
     , @input_data_1 = N'select "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species" from iris_data'  
     , @input_data_1_name = N'iris_data'  
     , @output_data_1_name = N'trained_model'  
    WITH RESULT SETS ((model varbinary(max)));  
END;
GO
```

Um ein ähnliches Modell mithilfe von Python zu generieren, ändern Sie die Sprachen-ID von `@language=N'R'` zu `@language = N'Python'` und nehmen die notwendigen Änderungen im `@script`-Argument vor. Alle anderen Parameter funktionieren genauso wie bei R.

### <a name="c-create-a-python-model-and-generate-scores-from-it"></a>C. Erstellen eines Python-Modells und Generieren von Bewertungen daraus

Dieses Beispiel veranschaulicht, wie Sie „sp\_execute\_external\_script“ verwenden, um Bewertungen in einem einfachen Python-Modell zu generieren. 

```sql
CREATE PROCEDURE [dbo].[py_generate_customer_scores]
AS
BEGIN

-- Input query to generate the customer data
DECLARE @input_query NVARCHAR(MAX) = N'SELECT customer, orders, items, cost FROM dbo.Sales.Orders'

EXEC sp_execute_external_script @language = N'Python', @script = N'
import pandas as pd
from sklearn.cluster import KMeans

# Get data from input query
customer_data = my_input_data

# Define the model
n_clusters = 4
est = KMeans(n_clusters=n_clusters, random_state=111).fit(customer_data[["orders","items","cost"]])
clusters = est.labels_
customer_data["cluster"] = clusters

OutputDataSet = customer_data
'
, @input_data_1 = @input_query
, @input_data_1_name = N'my_input_data'
WITH RESULT SETS (("CustomerID" int, "Orders" float,"Items" float,"Cost" float,"ClusterResult" float));
END;
GO
```

Spaltenüberschriften, die im Python-Code verwendet werden, werden nicht an SQL Server ausgegeben. Verwenden Sie daher die WITH RESULT-Anweisung, um die Spaltennamen und Datentypen anzugeben, die SQL verwenden soll.

Zur Bewertung können Sie auch die native [PREDICT](../../t-sql/queries/predict-transact-sql.md)-Funktion verwenden, die in der Regel schneller ist, weil sie die Python- bzw. R-Laufzeit nicht aufrufen muss.

## <a name="see-also"></a>Siehe auch

+ [SQL Server Machine Learning-Dienste](../../machine-learning/index.yml)
+ [SQL Server-Spracherweiterungen](../../language-extensions/language-extensions-overview.md). 
+ [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
+ [Python-Bibliotheken und Datentypen](../../machine-learning/python/python-libraries-and-data-types.md)  
+ [R-Bibliotheken und R-Datentypen](../../machine-learning/r/r-libraries-and-data-types.md)  
+ [SQL Server R-Dienste](../../machine-learning/r/sql-server-r-services.md)   
+ [Bekannte Probleme für SQL Server Machine Learning Services](../../machine-learning/known-issues-for-sql-server-machine-learning-services.md)   
+ [CREATE EXTERNAL LIBRARY &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-library-transact-sql.md)  
+ [sp_prepare &#40;-Sql-&#41;](../../relational-databases/system-stored-procedures/sp-prepare-transact-sql.md)   
+ [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
+ [Externe Skripts aktiviert – Serverkonfigurationsoption](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)   
+ [SERVERPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/serverproperty-transact-sql.md)   
+ [SQL Server, Externes Skript-Objekt](../../relational-databases/performance-monitor/sql-server-external-scripts-object.md)  
+ [sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md)  
+ [sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md) 
