---
title: Auslassen eines Datenfelds mithilfe einer Formatdatei (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- format files [SQL Server], skipping data fields
- skipping data fields when importing
ms.assetid: 6a76517e-983b-47a1-8f02-661b99859a8b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f880dcacbd4571c188d0368a0378a89c45787af2
ms.sourcegitcommit: 45a9d7ffc99502c73f08cb937cbe9e89d9412397
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2019
ms.locfileid: "66011715"
---
# <a name="use-a-format-file-to-skip-a-data-field-sql-server"></a>Auslassen eines Datenfelds mithilfe einer Formatdatei (SQL Server)
  Eine Datendatei kann mehr Felder enthalten, als Spalten in der Tabelle vorhanden sind. In diesem Thema wird beschrieben, wie Nicht-XML- und XML-Formatdateien an eine Datendatei mit mehr Feldern angepasst werden können, indem die Tabellenspalten den entsprechenden Datenfeldern zugeordnet und die übrigen Felder ignoriert werden.  
  
> [!NOTE]  
>  Mit einer Nicht-XML- oder XML-Formatdatei kann eine Datendatei mithilfe eines **bcp**-Befehls, einer BULK INSERT-Anweisung oder einer INSERT ... SELECT * FROM OPENROWSET(BULK...)-Anweisung verwendet werden. Weitere Informationen finden Sie unter [Massenimport von Daten mithilfe einer Formatdatei &#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md).  
  
## <a name="sample-data-file-and-table"></a>Beispiel für Datendatei und Tabelle  
 Die in diesem Thema enthaltenen Beispiele über die geänderten Formatdateien basieren auf der folgenden Tabelle und Datendatei.  
  
### <a name="sample-table"></a>Beispieltabelle  
 Für die Beispiele muss in der `myTestSkipField` -Beispieldatenbank unter dem [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] -Schema eine Tabelle mit dem Namen `dbo` erstellt werden. Wenn Sie diese Tabelle erstellen möchten, führen Sie im [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] -Abfrage-Editor folgenden Code aus:  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE myTestSkipField   
   (  
   PersonID smallint,  
   FirstName nvarchar(50) ,  
   LastName nvarchar(50)   
   );  
GO  
```  
  
### <a name="sample-data-file"></a>Beispieldatendatei  
 Die Datendatei `myTestSkipField-c.dat`enthält die folgenden Datensätze:  
  
```  
1,Skipme,DataField3,DataField4  
1,Skipme,DataField3,DataField4  
1,Skipme,DataField3,DataField4  
```  
  
 Wenn ein Massenimport für Daten aus `myTestSkipField-c.dat` in die `myTestSkipField` -Tabelle ausgeführt werden soll, muss die Formatdatei folgende Funktionen ausführen:  
  
-   Der ersten Spalte ( `PersonID`) das erste Datenfeld zuordnen.  
  
-   Das zweite Datenfeld auslassen.  
  
-   Der zweiten Spalte ( `FirstName`) das dritte Datenfeld zuordnen.  
  
-   Der dritten Spalte (`LastName`) das vierte Datenfeld zuordnen.  
  
## <a name="non-xml-format-file-for-more-data-fields"></a>Nicht-XML-Formatdatei für weitere Datenfelder  
 Die Formatdatei `myTestSkipField.fmt` ordnet die Felder in `myTestSkipField-c.dat` den Spalten der `myTestSkipField`-Tabelle zu. Die Formatdatei verwendet das Zeichendatenformat. Damit eine Spaltenzuordnung ausgelassen werden kann, muss der Wert für die Spaltenreihenfolge auf 0 festgelegt werden, wie für die `ExtraField` -Spalte in der Formatdatei veranschaulicht.  
  
 Die Formatdatei `myTestSkipField.fmt` enthält die folgenden Informationen:  
  
```  
9.0  
4  
1       SQLCHAR       0       7       ","      1     PersonID               ""  
2       SQLCHAR       0       100       ","    0     ExtraField             SQL_Latin1_General_CP1_CI_AS  
3       SQLCHAR       0       100     ","      2     FirstName              SQL_Latin1_General_CP1_CI_AS  
4       SQLCHAR       0       100     "\r\n"   3     LastName               SQL_Latin1_General_CP1_CI_AS  
  
```  
  
> [!NOTE]  
>  Informationen zur Syntax von Nicht-XML-Formatdateien finden Sie unter [Nicht-XML-Formatdateien &#40;SQL Server&#41;](xml-format-files-sql-server.md).  
  
### <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird `INSERT ... SELECT * FROM OPENROWSET(BULK...)` mithilfe der Formatdatei `myTestSkipField.fmt` verwendet. Die Datendatei `myTestSkipField-c.dat` wird per Massenimport in die `myTestSkipField` -Tabelle übertragen. Hinweise zum Erstellen der Beispieltabelle und Datendatei finden Sie unter "Beispiel für Datendatei und Tabelle" in diesem Thema.  
  
 Führen Sie im [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]-Abfrage-Editor den folgenden Code aus:  
  
```  
USE AdventureWorks2012;  
GO  
INSERT INTO myTestSkipField   
   SELECT *  
      FROM  OPENROWSET(BULK  'C:\myTestSkipField-c.dat',  
      FORMATFILE='C:\myTestSkipField.fmt'    
       ) AS t1;  
GO   
```  
  
## <a name="xml-format-file-for-more-data-fields"></a>XML-Formatdatei für weitere Datenfelder  
 Die in diesem Beispiel verwendete Formatdatei basiert auf einer anderen Formatdatei, `myTestSkipField.xml`, in der durchgängig das Zeichendatenformat verwendet wird und deren Felder der Anzahl und Reihenfolge der Spalten in der `myTestSkipField`-Tabelle entsprechen. Informationen, wie Sie den Inhalt dieser Formatdatei anzeigen, finden Sie unter [Erstellen einer Formatdatei &#40;SQL Server&#41;](create-a-format-file-sql-server.md).  
  
 Die Formatdatei `myTestSkipField.xml` ordnet die Felder in `myTestSkipField-c.dat` den Spalten der `myTestSkipField`-Tabelle zu. Die Formatdatei verwendet das Zeichendatenformat.  
  
 Die Formatdatei `myTestSkipField.xml` enthält die folgenden Informationen:  
  
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
  <COLUMN SOURCE="1" NAME="PersonID" xsi:type="SQLSMALLINT"/>  
  <COLUMN SOURCE="3" NAME="FirstName" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="4" NAME="LastName" xsi:type="SQLNVARCHAR"/>  
 </ROW>  
</BCPFORMAT>  
```  
  
### <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird `INSERT ... SELECT * FROM OPENROWSET(BULK...)` mithilfe der Formatdatei `myTestSkipField.Xml` verwendet. Die Datendatei `myTestSkipField-c.dat` wird per Massenimport in die `myTestSkipField` -Tabelle übertragen. Hinweise zum Erstellen der Beispieltabelle und Datendatei finden Sie unter "Beispiel für Datendatei und Tabelle" in diesem Thema.  
  
 Führen Sie im [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]-Abfrage-Editor den folgenden Code aus:  
  
```  
USE AdventureWorks2012;  
GO  
INSERT INTO myTestSkipField   
  SELECT *  
      FROM  OPENROWSET(BULK  'C:\myTestSkipField-c.dat',  
      FORMATFILE='C:\myTestSkipField.xml'    
       ) AS t1;  
GO  
  
```  
  
> [!NOTE]  
>  Informationen über die Syntax eines XML-Schemas und weitere Beispiele von XML-Formatdateien finden Sie unter [XML-Formatdateien &#40;SQL Server&#41;](xml-format-files-sql-server.md).  
  
## <a name="see-also"></a>Siehe auch  
 [bcp Utility](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)   
 [Überspringen einer Tabellenspalte mithilfe einer Formatdatei &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md)   
 [Verwenden einer Formatdatei zum Zuordnen von Tabellenspalten zu Datendateifeldern &#40;SQL Server&#41;](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
  
