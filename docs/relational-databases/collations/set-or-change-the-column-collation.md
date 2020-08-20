---
description: Festlegen oder Ändern der Spaltensortierung
title: Festlegen oder Ändern der Spaltensortierung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/05/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- tempdb database [SQL Server], collations
- collations [SQL Server], column
ms.assetid: d7a9638b-717c-4680-9b98-8849081e08be
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2c57021e300168a5e912dfce4ce1e0c62f728dfd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88465602"
---
# <a name="set-or-change-the-column-collation"></a>Festlegen oder Ändern der Spaltensortierung
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Sie können die Datenbanksortierung für **char**-, **varchar**-, **text**-, **nchar**-, **nvarchar**- und **ntext** -Daten überschreiben, indem Sie eine andere Sortierung für eine bestimmte Spalte einer Tabelle angeben und dann eine der folgenden Optionen verwenden:  
  
-   Die COLLATE-Klausel von [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md) und [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) (wie in den folgenden Beispielen) 

    -   **Direkte Konvertierung:** Orientieren Sie sich an einer der folgenden Tabellen:

        ```sql
        -- NVARCHAR column is encoded in UTF-16 because a supplementary character enabled collation is used
        CREATE TABLE dbo.MyTable (CharCol NVARCHAR(50) COLLATE Latin1_General_100_CI_AI_SC);

        -- VARCHAR column is encoded the Latin code page and therefore is not Unicode capable
        CREATE TABLE dbo.MyTable (CharCol VARCHAR(50) COLLATE Latin1_General_100_CI_AI);
        ```

        Sie können die Spalte direkt in UTF-8 konvertieren, indem Sie eine `ALTER COLUMN`-Anweisung ausführen, die den erforderlichen Datentyp und eine UTF-8-fähige Sortierung festlegt:

        ```sql 
        ALTER TABLE dbo.MyTable 
        ALTER COLUMN CharCol VARCHAR(50) COLLATE Latin1_General_100_CI_AI_SC_UTF8
        ```

        Diese Methode lässt sich leicht implementieren, es handelt sich jedoch um einen möglicherweise blockierenden Vorgang, der für große Tabellen und ausgelastete Anwendungen zum Problem werden kann.

    -   **Kopieren und ersetzen:** Orientieren Sie sich an einer der folgenden Tabellen:

        ```sql
        -- NVARCHAR column is encoded in UTF-16 because a supplementary character enabled collation is used
        CREATE TABLE dbo.MyTable (CharCol NVARCHAR(50) COLLATE Latin1_General_100_CI_AI_SC);
        GO

        -- VARCHAR column is encoded using the Latin code page and therefore is not Unicode capable
        CREATE TABLE dbo.MyTable (CharCol VARCHAR(50) COLLATE Latin1_General_100_CI_AI);
        GO
        ```

        Sie können die Spalte in UTF-8 konvertieren, indem Sie die Daten in eine neue Tabelle kopieren, in der für die Zielspalte bereits der erforderliche Datentyp und eine UTF-8-fähige Sortierung festgelegt sind. Anschließend können Sie die alte Tabelle ersetzen:

        ```sql
        CREATE TABLE dbo.MyTableNew (CharCol VARCHAR(50) COLLATE Latin1_General_100_CI_AI_SC_UTF8);
        GO
        INSERT INTO dbo.MyTableNew 
        SELECT * FROM dbo.MyTable;
        GO
        DROP TABLE dbo.MyTable;
        GO
        EXEC sp_rename 'dbo.MyTableNew', 'dbo.MyTable’;
        GO
        ```

        Diese Methode ist viel schneller als die direkte Konvertierung, aber die Verarbeitung komplexer Schemas mit vielen Abhängigkeiten (FS, PS, Trigger, DF) und das Synchronisieren des Tabellenendes (wenn die Datenbank gerade verwendet wird) erfordert mehr Planung.
        
    Weitere Informationen finden Sie unter [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Weitere Informationen finden Sie unter [Ändern von Spalten (Datenbank-Engine)](../../relational-databases/tables/modify-columns-database-engine.md#SSMSProcedure).  
  
-   Die **Column.Collation** -Eigenschaft in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO).  
  
 Sie können die Sortierung einer Spalte nicht ändern, wenn folgende Objekte aktuell auf die Spalte verweisen:  
  
-   Eine berechnete Spalte.  
-   Ein Index.  
-   Verteilungsstatistiken, die entweder automatisch oder mithilfe der `CREATE STATISTICS`-Anweisung generiert wurden  
-   Eine CHECK-Einschränkung.  
-   Eine FOREIGN KEY-Einschränkung.  
  
 Wenn Sie **tempdb**verwenden, enthält die [COLLATE](~/t-sql/statements/collations.md) -Klausel eine *database_defauls* -Option, mit der angegeben werden kann, dass für eine Spalte einer temporären Tabelle anstelle der Sortierung von **tempdb**die Standardsortierung der aktuellen Benutzerdatenbank für die Verbindung verwendet wird.  
  
## <a name="collations-and-text-columns"></a>Sortierungen und text-Spalten  
 Sie können Werte in einer **text** -Spalte einfügen und aktualisieren, deren Sortierung sich von der Codepage der Standardsortierung der Datenbank unterscheidet. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden die Werte implizit in die Sortierung der Spalte konvertiert.  
  
## <a name="collations-and-tempdb"></a>Sortierungen und tempdb  
 Die **tempdb** -Datenbank wird bei jedem Start von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellt und weist die gleiche Standardsortierung wie die **model** -Datenbank auf. Dabei handelt es sich normalerweise um die gleiche Sortierung wie die Standardsortierung der Instanz. Wenn Sie eine Benutzerdatenbank erstellen und eine andere Standardsortierung als für die **model**-Datenbank angeben, verwendet die Benutzerdatenbank eine andere Standardsortierung als die **tempdb**-Datenbank. Alle temporären gespeicherten Prozeduren oder temporären Tabellen werden in **tempdb**erstellt und gespeichert. Dies bedeutet, dass alle impliziten Spalten in temporären Tabellen und alle Konstanten, Variablen und Parameter mit erzwingbaren Standards in temporär gespeicherten Prozeduren andere Sortierungen aufweisen als die vergleichbaren Objekte, die in dauerhaften Tabellen und gespeicherten Prozeduren erstellt werden.  
  
 Dies kann zu Problemen hinsichtlich einer Nichtübereinstimmung in Sortierungen zwischen benutzerdefinierten Datenbanken und Systemdatenbankobjekten führen. Eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet z. B. die Latin1_General_CS_AS-Sortierung, und Sie führen die folgenden Anweisungen aus:  
  
```sql  
CREATE DATABASE TestDB COLLATE Estonian_CS_AS;  
USE TestDB;  
CREATE TABLE TestPermTab (PrimaryKey int PRIMARY KEY, Col1 nchar );  
```  
  
 In diesem System verwendet die **tempdb** -Datenbank die Latin1_General_CS_AS-Sortierung mit Codepage 1252, und `TestDB` und `TestPermTab.Col1` verwenden die `Estonian_CS_AS` -Sortierung mit Codepage 1257. Beispiel:  
  
```sql  
USE TestDB;  
GO  
-- Create a temporary table with the same column declarations  
-- as TestPermTab  
CREATE TABLE #TestTempTab (PrimaryKey int PRIMARY KEY, Col1 nchar );  
INSERT INTO #TestTempTab  
         SELECT * FROM TestPermTab;  
GO  
```  
  
 Im vorherigen Beispiel verwendet die **tempdb** -Datenbank die Latin1_General_CS_AS-Sortierung, und `TestDB` und `TestTab.Col1` verwenden die `Estonian_CS_AS` -Sortierung. Beispiel:  
  
```sql  
SELECT * FROM TestPermTab AS a INNER JOIN #TestTempTab on a.Col1 = #TestTempTab.Col1;  
```  
  
 Da **tempdb** die Standardserversortierung und `TestPermTab.Col1` eine andere Sortierung verwendet, wird in SQL Server der folgende Fehler zurückgegeben: „Ein Sortierungskonflikt zwischen ‚Latin1_General_CI_AS_KS_WS‘ und ‚Estonian_CS_AS‘ im Gleich-Vorgang kann nicht aufgelöst werden.“  
  
 Sie können den Fehler vermeiden, indem Sie stattdessen eine der folgenden Alternativen verwenden:  
  
-   Geben Sie an, dass für die Spalte der temporären Tabelle die Standardsortierung der Benutzerdatenbank und nicht die Standardsortierung von **tempdb**verwendet wird. Auf diese Weise kann die temporäre Tabelle mit ähnlich formatierten Tabellen in mehreren Datenbanken arbeiten, wenn dies in dem System erforderlich ist.  
  
    ```sql  
    CREATE TABLE #TestTempTab  
       (PrimaryKey int PRIMARY KEY,  
        Col1 nchar COLLATE database_default  
       );  
    ```  
  
-   Geben Sie die richtige Sortierung für die `#TestTempTab` -Spalte an:  
  
    ```sql  
    CREATE TABLE #TestTempTab  
       (PrimaryKey int PRIMARY KEY,  
        Col1 nchar COLLATE Estonian_CS_AS  
       );  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Festlegen oder Ändern der Serversortierung](../../relational-databases/collations/set-or-change-the-server-collation.md)   
 [Festlegen oder Ändern der Datenbanksortierung](../../relational-databases/collations/set-or-change-the-database-collation.md)   
 [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md)  
  
  
