---
title: 'T-SQL-Tutorial: Erstellen und Abfragen von Datenbankobjekten | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 07/30/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
ms.assetid: 9fb8656b-0e4e-4ada-b404-4db4d3eea995
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 874bedd5e6f8eec03941fa3d3fc957351166500b
ms.sourcegitcommit: a13256f484eee2f52c812646cc989eb0ce6cf6aa
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/25/2019
ms.locfileid: "56801144"
---
# <a name="lesson-1-create-and-query-database-objects"></a>Lektion 1: Erstellen und Abfragen von Datenbankobjekten
[!INCLUDE[tsql-appliesto-ss2008-all-md](../includes/tsql-appliesto-ss2008-all-md.md)]

In dieser Lektion erfahren Sie, wie Sie eine Datenbank erstellen, eine Tabelle in der Datenbank erstellen und dann auf die Daten in der Tabelle zugreifen und diese ändern können. Weil diese Lektion eine Einführung in die Verwendung von [!INCLUDE[tsql](../includes/tsql-md.md)]darstellt, werden viele der für diese Anweisungen verfügbaren Optionen nicht verwendet bzw. beschrieben.  
  
[!INCLUDE[tsql](../includes/tsql-md.md)] -Anweisungen können wie folgt geschrieben und an die [!INCLUDE[ssDE](../includes/ssde-md.md)] übertragen werden:  
  
-   Mithilfe von [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. In diesem Lernprogramm wird vorausgesetzt, dass Sie [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]verwenden. Sie können jedoch auch [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] Express verwenden, das als kostenloser Download im [Microsoft Download Center](https://go.microsoft.com/fwlink/?linkid=67359)zur Verfügung steht.  
  
-   Mithilfe des [Hilfsprogramms sqlcmd](../tools/sqlcmd-utility.md).  
  
-   Durch Herstellen der Verbindung über eine von Ihnen erstellte Anwendung.  
  
Der Code wird in der [!INCLUDE[ssDE](../includes/ssde-md.md)] immer auf gleiche Weise und mit denselben Berechtigungen ausgeführt, unabhängig davon, wie Sie die Codeanweisungen übermitteln.  
  
Damit Sie [!INCLUDE[tsql](../includes/tsql-md.md)] -Anweisungen in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]ausführen können, öffnen Sie [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] und stellen eine Verbindung mit einer Instanz von [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]her.  

## <a name="prerequisites"></a>Voraussetzungen
Zur Durchführung dieses Tutorials benötigen Sie SQL Server Management Studio und Zugriff auf eine SQL Server-Instanz. 

- Installieren Sie [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

Wenn Sie über keinen Zugriff auf eine SQL Server-Instanz verfügen, wählen Sie Ihre Plattform aus den folgenden Links aus. Wenn Sie die SQL-Authentifizierung wählen, verwenden Sie Ihre SQL Server-Anmeldeinformationen.
- **Windows**: [Herunterladen von Microsoft SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads)
- **macOS**: [Herunterladen von SQL Server 2017 für Docker](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker)

## <a name="create-a-database"></a>Erstellen einer Datenbank
Wie viele [!INCLUDE[tsql](../includes/tsql-md.md)] -Anweisungen verfügt auch die CREATE DATABASE-Anweisung über einen erforderlichen Parameter: den Namen der Datenbank. CREATE DATABASE verfügt auch über viele optionale Parameter wie den Speicherort auf dem Datenträger, an den Sie die Datenbankdateien kopieren möchten. Wenn Sie CREATE DATABASE ohne optionale Parameter ausführen, werden von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Standardwerte für viele dieser Parameter verwendet. In diesem Lernprogramm werden nur wenige der optionalen Syntaxparameter verwendet.   

1.  Geben Sie in einem Fenster des Abfrage-Editors den folgenden Code ein, aber führen Sie ihn nicht aus:  
  
    ```sql  
    CREATE DATABASE TestData  
    GO  
    ```  
  
2.  Verwenden Sie den Zeiger, um die Wörter `CREATE DATABASE`auszuwählen, und drücken Sie dann **F1**. Das CREATE DATABASE-Thema in der SQL Server-Onlinedokumentation sollte geöffnet werden. Sie können dieses Verfahren verwenden, um die vollständige Syntax für CREATE DATABASE und für die anderen in diesem Lernprogramm verwendeten Anweisungen zu finden.  
  
3.  Drücken Sie im Abfrage-Editor **F5** , um die Anweisung auszuführen und eine Datenbank mit Namen `TestData`zu erstellen.  
  
Wenn Sie eine Datenbank erstellen, wird von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] eine Kopie der **model** -Datenbank erstellt und die Kopie in den Namen der Datenbank umbenannt. Dieser Vorgang dauert nur einige Sekunden, es sei denn, Sie geben eine große Anfangsgröße der Datenbank als optionalen Parameter an.  
  
> [!NOTE]  
> Das GO-Schlüsselwort trennt Anweisungen, wenn mehrere Anweisungen in einem einzelnen Batch gesendet werden. GO ist optional, wenn der Batch nur eine Anweisung enthält.  

## <a name="create-a-table"></a>Erstellen einer Tabelle
[!INCLUDE[tsql-appliesto-ss2008-all-md](../includes/tsql-appliesto-ss2008-all-md.md)]

Zum Erstellen einer Tabelle müssen Sie einen Tabellennamen sowie die Namen und Datentypen jeder Spalte in der Tabelle angeben. Außerdem empfiehlt es sich, anzugeben, ob NULL-Werte in den einzelnen Spalten zulässig sind. Zum Erstellen der Tabelle müssen Sie über die Berechtigung `CREATE TABLE` verfügen sowie über die Berechtigung `ALTER SCHEMA` für das Schema, das die Tabelle enthalten wird. Die feste Datenbankrolle [`db_ddladmin`](../relational-databases/security/authentication-access/database-level-roles.md) verfügt über folgende Berechtigungen.  
  
Die meisten Tabellen verfügen über einen Primärschlüssel, der sich aus einer oder mehreren Spalten der Tabelle zusammensetzt. Ein Primärschlüssel ist immer eindeutig. [!INCLUDE[ssDE](../includes/ssde-md.md)] erzwingt die Einschränkung, dass ein Primärschlüsselwert in der Tabelle nicht wiederholt werden kann.  
  
Eine Liste der Datentypen sowie Links zu Beschreibungen der einzelnen Datentypen finden Sie unter [Datentypen &#40;Transact-SQL&#41;](../t-sql/data-types/data-types-transact-sql.md).  
  
> [!NOTE]  
> [!INCLUDE[ssDE](../includes/ssde-md.md)] kann mit oder ohne Beachtung der Groß-/Kleinschreibung installiert werden. Wurde [!INCLUDE[ssDE](../includes/ssde-md.md)] so installiert, dass die Groß-/Kleinschreibung beachtet wird, müssen Objektnamen immer die gleiche Groß-/Kleinschreibung aufweisen. Beispielsweise unterscheidet sich eine Tabelle namens OrderData von einer Tabelle namens ORDERDATA. Wurde [!INCLUDE[ssDE](../includes/ssde-md.md)] so installiert, dass die Groß-/Kleinschreibung nicht beachtet wird, bezeichnen diese beiden Tabellennamen die gleiche Tabelle, und der Name kann nur einmal verwendet werden.  
  
  
### <a name="switch-the-query-editor-connection-to-the-testdata-database"></a>Ändern der Verbindung des Abfrage-Editors in die Datenbank TestData  
Geben Sie in einem Abfrage-Editorfenster den folgenden Code ein, und führen Sie ihn aus, um die Verbindung in die `TestData` -Datenbank zu ändern.  
  
  ```sql  
  USE TestData  
  GO  
  ```  
  
### <a name="create-the-table"></a>Erstellen der Tabelle
Geben Sie in einem Abfrage-Editorfenster den folgenden Code ein, und führen Sie ihn aus, um eine einfache Tabelle namens `Products`zu erstellen. Die Spalten in der Tabelle heißen `ProductID`, `ProductName`, `Price`und `ProductDescription`. Die `ProductID` -Spalte ist der Primärschlüssel der Tabelle. `int`, `varchar(25)`, `money`und `text` sind Datentypen. Nur die Spalten `Price` und `ProductionDescription` dürfen keine Daten enthalten, wenn eine Zeile eingefügt oder geändert wird. Diese Anweisung enthält ein optionales Element (`dbo.`), das als Schema bezeichnet wird. Das Schema ist das Datenbankobjekt, das die Tabelle besitzt. Wenn Sie Administrator sind, ist `dbo` das Standardschema. `dbo` steht für Datenbankbesitzer (database owner, dbo).  
  
  ```sql  
  CREATE TABLE dbo.Products  
     (ProductID int PRIMARY KEY NOT NULL,  
     ProductName varchar(25) NOT NULL,  
     Price money NULL,  
     ProductDescription text NULL)  
  GO  
 ```  

## <a name="insert-and-update-data-in-a-table"></a>Einfügen und Aktualisieren von Daten in einer Tabelle
Nachdem Sie nun die **Products** -Tabelle erstellt haben, können Sie Daten mithilfe der INSERT-Anweisung in die Tabelle einfügen. Nach dem Einfügen der Daten ändern Sie den Inhalt einer Zeile mithilfe einer UPDATE-Anweisung. Mithilfe der WHERE-Klausel der UPDATE-Anweisung schränken Sie das Update auf eine einzelne Zeile ein. Durch die vier Anweisungen werden die folgenden Daten eingegeben.  
  
|ProductID|ProductName|Price|ProductDescription|  
|-------------|---------------|---------|----------------------|  
|1|Clamp|12.48|Workbench clamp|  
|50|Screwdriver|3.17|Flat head|  
|75|Tire Bar||Tool for changing tires.|  
|3000|3mm Bracket|.52||  
  
Die grundlegende Syntax lautet: INSERT, Tabellenname, Spaltenliste, VALUES und dann eine Liste der einzufügenden Werte. Die beiden Bindestriche vor einer Zeile geben an, dass es sich bei der Zeile um einen Kommentar handelt, der vom Compiler ignoriert wird. In diesem Fall wird im Kommentar eine zulässige Variante der Syntax beschrieben.  
  
### <a name="insert-data-into-a-table"></a>Einfügen von Daten in eine Tabelle  
  
1.  Führen Sie die folgende Anweisung aus, um eine Zeile in die in der vorhergehenden Aufgabe erstellte `Products` -Tabelle einzufügen. Dies ist die grundlegende Syntax.  
  
   ```sql 
   -- Standard syntax  
   INSERT dbo.Products (ProductID, ProductName, Price, ProductDescription)  
       VALUES (1, 'Clamp', 12.48, 'Workbench clamp')  
   GO   
   ```  
  
2.  In der folgenden Anweisung sehen Sie, wie die Reihenfolge, in der die Parameter bereitgestellt werden, durch Wechseln der Position von `ProductID` und `ProductName` sowohl in der Liste der Felder (in Klammern) als auch in der Liste der Werte geändert werden kann.  
  
   ```sql  
   -- Changing the order of the columns  
   INSERT dbo.Products (ProductName, ProductID, Price, ProductDescription)  
       VALUES ('Screwdriver', 50, 3.17, 'Flat head')  
   GO    
   ```  
  
3.  Die folgende Anweisung veranschaulicht, dass die Namen der Spalten optional sind, solange die Werte in der richtigen Reihenfolge aufgelistet werden. Obwohl diese Syntax gängig ist, wird ihre Verwendung nicht empfohlen, da sie das Verständnis des Codes durch Dritte erschweren könnte. `NULL` wird für die `Price` -Spalte angegeben, da der Preis für dieses Produkt noch nicht bekannt ist.  
  
   ```sql  
   -- Skipping the column list, but keeping the values in order  
   INSERT dbo.Products  
       VALUES (75, 'Tire Bar', NULL, 'Tool for changing tires.')  
   GO  
  ```  
  
4.  Der Schemaname ist optional, solange Sie auf eine Tabelle im Standardschema zugreifen und diese ändern. Da die `ProductDescription` -Spalte NULL-Werte zulässt und kein Wert bereitgestellt wird, können Name und Wert der `ProductDescription` -Spalte vollständig aus der Anweisung gelöscht werden.  
  
   ```sql  
   -- Dropping the optional dbo and dropping the ProductDescription column  
   INSERT Products (ProductID, ProductName, Price)  
       VALUES (3000, '3mm Bracket', .52)  
   GO  
   ```  
  
### <a name="update-the-products-table"></a>Aktualisieren der Products-Tabelle  
Geben Sie die folgende `UPDATE` -Anweisung zum Ändern von `ProductName` des zweiten Produkts von `Screwdriver`in `Flat Head Screwdriver`ein, und führen Sie sie aus.  
  
  ```sql  
  UPDATE dbo.Products  
      SET ProductName = 'Flat Head Screwdriver'  
      WHERE ProductID = 50  
  GO  
  ```  

## <a name="read-data-from-a-table"></a>Lesen von Daten aus einer Tabelle
Daten in einer Tabelle können mithilfe der SELECT-Anweisung gelesen werden. Die SELECT-Anweisung gehört zu den wichtigsten [!INCLUDE[tsql](../includes/tsql-md.md)] -Anweisungen. Ihre Syntax zeichnet sich durch unzählige Variationen aus. In diesem Lernprogramm arbeiten Sie mit fünf einfachen Versionen.  
  
### <a name="read-the-data-in-a-table"></a>Lesen der Daten in einer Tabelle  
  
1.  Geben Sie die folgenden Anweisungen zum Lesen der Daten in der `Products` -Tabelle ein, und führen Sie sie aus.  
  
  ```sql 
  -- The basic syntax for reading data from a single table  
  SELECT ProductID, ProductName, Price, ProductDescription  
      FROM dbo.Products  
  GO  
  ```  
  
2.  Sie können alle Spalten in der Tabelle mithilfe eines Sternchens auswählen. Dies wird häufig bei Ad-hoc-Abfragen verwendet. Sie sollten die Spaltenliste im dauerhaften Code bereitstellen, sodass die Anweisung die vorhergesagten Spalten zurückgibt, selbst wenn der Tabelle später eine neue Spalte hinzugefügt wird.  
  
  ```sql  
  -- Returns all columns in the table  
  -- Does not use the optional schema, dbo  
  SELECT * FROM Products  
  GO   
  ```  
  
3.  Sie können Spalten auslassen, die nicht zurückgegeben werden sollen. Die Spalten werden in der Reihenfolge zurückgegeben, in der sie aufgelistet sind.  
  
  ```sql  
  -- Returns only two of the columns from the table  
  SELECT ProductName, Price  
      FROM dbo.Products  
  GO    
  ```  
  
4.  Mithilfe einer `WHERE` -Klausel können Sie die an den Benutzer zurückgegebenen Zeilen beschränken.  
  
  ``` sql 
  -- Returns only two of the records in the table  
  SELECT ProductID, ProductName, Price, ProductDescription  
      FROM dbo.Products  
      WHERE ProductID < 60  
  GO    
  ```  
  
5.  Sie können die Werte in den Spalten direkt nach ihrer Rückgabe bearbeiten. Im folgenden Beispiel wird eine mathematische Operation für die `Price` -Spalte ausgeführt. Spalten, die auf diese Weise geändert wurden, weisen keinen Namen auf, es sei denn, Sie geben einen Namen mithilfe des `AS` -Schlüsselworts an.  
  
  ```sql  
  -- Returns ProductName and the Price including a 7% tax  
  -- Provides the name CustomerPays for the calculated column  
  SELECT ProductName, Price * 1.07 AS CustomerPays  
      FROM dbo.Products  
  GO  
  ```  
  
### <a name="useful-functions-in-a-select-statement"></a>Nützliche Funktionen in einer SELECT-Anweisung  
Weitere Informationen zu bestimmten Funktionen, die zum Bearbeiten von Daten in SELECT-Anweisungen verwendet werden können, finden Sie in den folgenden Themen:  
  
|||  
|-|-|  
|[Zeichenfolgenfunktionen &#40;Transact-SQL&#41;](../t-sql/functions/string-functions-transact-sql.md)|[Datums- und Uhrzeitdatentypen und zugehörige Funktionen &#40;Transact-SQL&#41;](../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)|  
|[Mathematische Funktionen &#40;Transact-SQL&#41;](../t-sql/functions/mathematical-functions-transact-sql.md)|[Text- und Bildfunktionen &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/b9c70488-1bf5-4068-a003-e548ccbc5199)|  

## <a name="create-views-and-stored-procedures"></a>Erstellen von Ansichten und gespeicherten Prozeduren
Bei einer Sicht handelt es sich um eine gespeicherte SELECT-Anweisung, und eine gespeicherte Prozedur setzt sich aus einer oder mehreren [!INCLUDE[tsql](../includes/tsql-md.md)] -Anweisungen zusammen, die als Batch ausgeführt werden.  
  
Sichten werden wie Tabellen abgefragt und nehmen keine Parameter an. Gespeicherte Prozeduren sind komplexer als Sichten. Gespeicherte Prozeduren können sowohl Eingabe- als auch Ausgabeparameter aufweisen und Anweisungen enthalten, die den Ablauf des Codes steuern, wie z. B. IF- und WHILE-Anweisungen. Als eine der Grundregeln guter Programmierung gilt die Verwendung gespeicherter Prozeduren für alle Aktionen, die sich in der Datenbank wiederholen.  
  
In diesem Beispiel erstellen Sie mithilfe von CREATE VIEW eine Sicht, die nur zwei der Spalten in der **Products** -Tabelle auswählt. Sie erstellen dann mithilfe von CREATE PROCEDURE eine gespeicherte Prozedur, die einen Parameter für den Preis akzeptiert und nur die Produkte zurückgibt, deren Preis unter dem angegebenen Parameterwert liegt.  
  
### <a name="create-a-view"></a>Erstellen einer Ansicht  
  
Führen Sie die folgende Anweisung aus, um eine sehr einfache Sicht zu erstellen, die eine SELECT-Anweisung ausführt und die Namen und Preise der Produkte an den Benutzer zurückgibt.  
  
  ```sql  
  CREATE VIEW vw_Names  
     AS  
     SELECT ProductName, Price FROM Products;  
  GO    
  ```  
  
### <a name="test-the-view"></a>Testen der Sicht  
  
Sichten werden genau wie Tabellen behandelt. Greifen Sie mithilfe einer `SELECT` -Anweisung auf eine Sicht zu.  
  
  ```sql  
  SELECT * FROM vw_Names;  
  GO   
  ```  
  
### <a name="create-a-stored-procedure"></a>Erstellen einer gespeicherten Prozedur  
  
Die folgende Anweisung erstellt eine gespeicherte Prozedur namens `pr_Names`, die einen Eingabeparameter mit der Bezeichnung `@VarPrice` vom Datentyp `money`akzeptiert. Die gespeicherte Prozedur druckt die mit dem Eingabeparameter verkettete `Products less than` -Anweisung. Dieser Parameter wird vom `money` -Datentyp in den `varchar(10)` -Zeichendatentyp geändert. Dann führt die Prozedur eine `SELECT` -Anweisung für die Sicht aus und übergibt dabei den Eingabeparameter als Teil der `WHERE` -Klausel. Dadurch werden alle Produkte zurückgegeben, deren Preis unter dem Wert des Eingabeparameters liegt.  
  
  ```sql  
  CREATE PROCEDURE pr_Names @VarPrice money  
     AS  
     BEGIN  
        -- The print statement returns text to the user  
        PRINT 'Products less than ' + CAST(@VarPrice AS varchar(10));  
        -- A second statement starts here  
        SELECT ProductName, Price FROM vw_Names  
              WHERE Price < @varPrice;  
     END  
  GO    
  ```  
  
### <a name="test-the-stored-procedure"></a>Testen der gespeicherten Prozedur.  
  
Wenn Sie die gespeicherte Prozedur testen möchten, geben Sie die folgende Anweisung ein, und führen Sie sie aus. Die Prozedur sollte die Namen der beiden Produkte zurückgeben, die Sie in Lektion 1 mit einem Preis unter `Products` in die `10.00`-Tabelle eingegeben haben.  
  
  ```sql  
  EXECUTE pr_Names 10.00;  
  GO  
  ```  

## <a name="next-steps"></a>Nächste Schritte
Im nächsten Artikel erfahren Sie, wie Sie Berechtigungen für Datenbankobjekte konfigurieren. Die Objekte, die in Lektion 1 erstellt wurden, werden in Lektion 2 ebenfalls verwendet. 

Zum nächsten Artikel wechseln, um mehr zu erfahren:
> [!div class="nextstepaction"]
> [Nächste Schritte](../t-sql/lesson-2-configuring-permissions-on-database-objects.md)
  
  
  
