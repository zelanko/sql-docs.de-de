---
title: Massenimport von Daten mithilfe einer Formatdatei (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk importing [SQL Server], format files
- format files [SQL Server], importing data using
ms.assetid: 2956df78-833f-45fa-8a10-41d6522562b9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c6d9779209b3ffb317658243c168d74740f6731b
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85026450"
---
# <a name="use-a-format-file-to-bulk-import-data-sql-server"></a>Massenimport von Daten mithilfe einer Formatdatei (SQL Server)
  In diesem Thema wird die Verwendung einer Formatdatei bei Massenimportvorgängen beschrieben. Durch die Formatdatei werden die Felder der Datendatei den Spalten der Tabelle zugeordnet.  Sie können eine nicht-XML-oder XML-Format Datei für den Massen Import von Daten verwenden, wenn Sie einen **bcp** -Befehl oder eine BULK INSERT-oder INSERT... SELECT * FROM OPENROWSET (BULK...) [!INCLUDE[tsql](../../includes/tsql-md.md)] s.  
  
> [!IMPORTANT]  
>  Damit eine Formatdatei mit einer Datendatei mit Unicode-Zeichen verwendet werden kann, müssen alle Eingabefelder Unicode-Textzeichenfolgen sein (d. h., entweder Unicode-Zeichenfolgen einer festen Länge oder Unicode-Zeichenfolgen mit Abschlusszeichen).  
  
> [!NOTE]  
>  Wenn Sie mit Format Dateien nicht vertraut sind, finden Sie weitere Informationen unter [nicht-XML-Format Dateien &#40;SQL Server&#41;](xml-format-files-sql-server.md) und [XML-Format Dateien &#40;SQL Server&#41;](xml-format-files-sql-server.md).  
  
## <a name="format-file-options-for-bulk-import-commands"></a>Formatdateioptionen für Massenimportbefehle  
 In der folgenden Tabelle sind die Formatdateioptionen für die einzelnen Massenimportbefehle zusammengefasst.  
  
|Massenladebefehle|Verwenden der Formatdateioption|  
|------------------------|-----------------------------------|  
|BULK INSERT|FORMATFILE = '*format_file_path*'|  
|INSERT ... SELECT * FROM OPENROWSET(BULK...)|FORMATFILE = '*format_file_path*'|  
|**bcp** ... **in**|**-f** *format_file*|  
  
 Weitere Informationen finden Sie unter [bcp (Hilfsprogramm)](../../tools/bcp-utility.md), [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) oder [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).  
  
> [!NOTE]  
>  Verwenden Sie in der Formatdatei einen der folgenden Datentypen für den Massenexport oder -import von SQLXML-Daten: SQLCHAR oder SQLVARYCHAR (die Daten werden in der Clientcodepage oder in der Codepage, die durch die Sortierung impliziert wird, gesendet), SQLNCHAR oder SQLNVARCHAR (die Daten werden als Unicode gesendet) oder SQLBINARY oder SQLVARYBIN (die Daten werden ohne Konvertierung gesendet).  
  
## <a name="examples"></a>Beispiele  
 Die Beispiele in diesem Abschnitt veranschaulichen die Verwendung von Format Dateien für den Massen Import von Daten mithilfe des **bcp** -Befehls und des BULK INSERT und einfügen... SELECT * FROM OPENROWSET (BULK...)-Anweisungen. Bevor Sie eines der Beispiele für den Massenimport nachvollziehen können, müssen Sie eine entsprechende Tabelle, eine Datendatei und eine Formatdatei für das Beispiel erstellen.  
  
### <a name="sample-table"></a>Beispieltabelle  
 Damit die Beispiele nachvollzogen werden können, muss im **dbo**-Schema in der [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)]-Beispieldatenbank eine Tabelle mit der Bezeichnung **myTestFormatFiles** erstellt werden. Führen Sie Folgendes aus, um diese Tabelle im [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]-Abfrage-Editor zu erstellen:  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE myTestFormatFiles (  
   Col1 smallint,  
   Col2 nvarchar(50),  
   Col3 nvarchar(50),  
   Col4 nvarchar(50)  
   );  
GO  
```  
  
### <a name="sample-data-file"></a>Beispieldatendatei  
 Für die Beispiele wird eine Beispieldatendatei `myTestFormatFiles-c.Dat` verwendet, die die folgenden Datensätze enthält. Geben Sie zur Erstellung der Datendatei an der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Eingabeaufforderung Folgendes ein:  
  
```  
10,Field2,Field3,Field4  
15,Field2,Field3,Field4  
46,Field2,Field3,Field4  
58,Field2,Field3,Field4  
```  
  
### <a name="sample-format-files"></a>Beispielformatdateien  
 Bei einigen Beispielen in diesem Abschnitt werden XML-Formatdateien, `myTestFormatFiles-f-x-c.Xml`, verwendet, während in anderen Beispielen Dateien in einem anderen Format verwendet werden. Beide Formatdateitypen verwenden Zeichendatenformate und ein Feldabschlusszeichen (,), das nicht dem Standard entspricht.  
  
#### <a name="the-sample-non-xml-format-file"></a>Beispieldatei – Nicht im XML-Format  
 Im folgenden Beispiel wird zur Generierung einer XML-Formatdatei aus der `myTestFormatFiles`-Tabelle der Befehl **bcp** verwendet. Die Datei `myTestFormatFiles.Fmt` enthält die folgenden Informationen:  
  
```  
9.0  
4  
1       SQLCHAR       0       7       ","      1     Col1         ""  
2       SQLCHAR       0       100     ","      2     Col2         SQL_Latin1_General_CP1_CI_AS  
3       SQLCHAR       0       100     ","      3     Col3         SQL_Latin1_General_CP1_CI_AS  
4       SQLCHAR       0       100     "\r\n"   4     Col4         SQL_Latin1_General_CP1_CI_AS  
```  
  
 Wenn zur Erstellung dieser Formatdatei der **bcp**-Befehl mit der Option **format** verwendet werden soll, geben Sie an der Windows-Eingabeaufforderung Folgendes ein:  
  
```  
bcp AdventureWorks2012..MyTestFormatFiles format nul -c -t, -f myTestFormatFiles.Fmt -T  
  
```  
  
 Weitere Informationen zum Erstellen einer Formatdatei finden Sie unter [Erstellen einer Formatdatei &#40;SQL Server&#41;](create-a-format-file-sql-server.md).  
  
#### <a name="the-sample-xml-format-file"></a>Beispieldatei – Im XML-Format  
 Im folgenden Beispiel wird zur Erstellung einer XML-Formatdatei aus der `myTestFormatFiles`-Tabelle der Befehl **bcp** verwendet. Die Datei `myTestFormatFiles.Xml` enthält die folgenden Informationen:  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
 <RECORD>  
  <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="7"/>  
  <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="4" xsi:type="CharTerm" TERMINATOR="\r\n" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
 </RECORD>  
 <ROW>  
  <COLUMN SOURCE="1" NAME="Col1" xsi:type="SQLSMALLINT"/>  
  <COLUMN SOURCE="2" NAME="Col2" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="3" NAME="Col3" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="4" NAME="Col4" xsi:type="SQLNVARCHAR"/>  
 </ROW>  
</BCPFORMAT>  
```  
  
 Wenn zur Erstellung dieser Formatdatei der **bcp**-Befehl mit der Option **format** verwendet werden soll, geben Sie an der Windows-Eingabeaufforderung Folgendes ein:  
  
```  
bcp AdventureWorks2012..MyTestFormatFiles format nul -c -t, -x -f myTestFormatFiles.Xml -T  
```  
  
### <a name="using-bcp"></a>Verwenden von "bcp"  
 Im nachfolgenden Beispiel wird der Befehl **bcp** für den Massenimport von Daten aus der `myTestFormatFiles-c.Dat`-Datendatei in die `HumanResources.myTestFormatFiles`-Tabelle der Beispieldatenbank verwendet. In diesem Beispiel wird die XML-Formatdatei `MyTestFormatFiles.Xml` verwendet. Vorhandene Tabellenzeilen werden in diesem Beispiel vor dem Import der Datendatei gelöscht.  
  
 Geben Sie an der Windows-Eingabeaufforderung Folgendes ein:  
  
```  
bcp AdventureWorks2012..myTestFormatFiles in C:\myTestFormatFiles-c.Dat -f C:\myTestFormatFiles.Xml -T  
```  
  
> [!NOTE]  
>  Weitere Informationen zu diesem Befehl finden Sie unter [bcp (Hilfsprogramm)](../../tools/bcp-utility.md).  
  
### <a name="using-bulk-insert"></a>Verwenden von BULK INSERT  
 Im nachfolgenden Beispiel wird BULK INSERT für den Massenimport von Daten aus der `myTestFormatFiles-c.Dat`-Datendatei in die `HumanResources.myTestFormatFiles`-Tabelle in der [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)]-Beispieldatenbank verwendet. Im Beispiel wird die XML-Formatdatei `MyTestFormatFiles.Fmt` verwendet. Vorhandene Tabellenzeilen werden in diesem Beispiel vor dem Import der Datendatei gelöscht.  
  
 Führen Sie im [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] -Abfrage-Editor Folgendes aus:  
  
```  
USE AdventureWorks2012;  
GO  
DELETE myTestFormatFiles;  
GO  
BULK INSERT myTestFormatFiles   
   FROM 'C:\myTestFormatFiles-c.Dat'   
   WITH (FORMATFILE = 'C:\myTestFormatFiles.Fmt');  
GO  
SELECT * FROM myTestFormatFiles;  
GO  
```  
  
> [!NOTE]  
>  Weitere Informationen zu dieser Anweisung finden Sie unter [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).  
  
### <a name="using-the-openrowset-bulk-rowset-provider"></a>Verwenden des OPENROWSET-Bulk-Rowsetanbieters  
 Im nachfolgenden Beispiel wird `INSERT ... SELECT * FROM OPENROWSET(BULK...)` für den Massenimport von Daten aus der `myTestFormatFiles-c.Dat`-Datendatei in die `HumanResources.myTestFormatFiles`-Tabelle in der `AdventureWorks`-Beispieldatenbank verwendet. In diesem Beispiel wird die XML-Formatdatei `MyTestFormatFiles.Xml` verwendet. Vorhandene Tabellenzeilen werden in diesem Beispiel vor dem Import der Datendatei gelöscht.  
  
 Führen Sie im [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] -Abfrage-Editor Folgendes aus:  
  
```  
USE AdventureWorks2012;  
DELETE myTestFormatFiles;  
GO  
INSERT INTO myTestFormatFiles  
    SELECT *  
      FROM  OPENROWSET(BULK  'C:\myTestFormatFiles-c.Dat',  
      FORMATFILE='C:\myTestFormatFiles.Xml'       
      ) as t1 ;  
GO  
SELECT * FROM myTestFormatFiles;  
GO  
```  
  
 Wenn Sie die Beispieltabelle nicht mehr benötigen, können Sie sie mit der folgenden Anweisung löschen:  
  
```  
DROP TABLE myTestFormatFiles  
```  
  
> [!NOTE]  
>  Weitere Informationen zur OPENROWSET BULK-Klausel finden Sie unter [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)zu markieren.  
  
## <a name="additional-examples"></a>Zusätzliche Beispiele  
 [Erstellen einer Formatdatei &#40;SQL Server&#41;](create-a-format-file-sql-server.md)  
  
 [Überspringen einer Tabellenspalte mithilfe einer Formatdatei &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
 [Auslassen eines Datenfelds mithilfe einer Formatdatei &#40;SQL Server&#41;](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
 [Verwenden einer Formatdatei zum Zuordnen von Tabellenspalten zu Datendateifeldern &#40;SQL Server&#41;](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [bcp (Hilfsprogramm)](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)   
 [Nicht-XML-Formatdateien &#40;SQL Server&#41;](xml-format-files-sql-server.md)   
 [XML-Formatdateien &#40;SQL Server&#41;](xml-format-files-sql-server.md)  
  
  
