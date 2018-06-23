---
title: Verwenden einer Formatdatei zum Zuordnen von Tabellenspalten zu Datendateifeldern (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-bulk-import-export
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- mapping columns to fields during import [SQL Server]
- format files [SQL Server], mapping columns to fields
ms.assetid: e7ee4f7e-24c4-4eb7-84d2-41e57ccc1ef1
caps.latest.revision: 36
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f6afe2f0125b7f62f3b4a2b8f00bfba50a883442
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36059138"
---
# <a name="use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server"></a>Verwenden einer Formatdatei zum Zuordnen von Tabellenspalten zu Datendateifeldern (SQL Server)
  Eine Datendatei kann Felder in einer anderen Reihenfolge als die der entsprechenden Spalten in der Tabelle aufweisen. In diesem Thema werden Nicht-XML-Formatdateien und XML-Formatdateien dargestellt, die zum Anpassen an eine Datendatei, deren Felder eine andere Reihenfolge als die Tabellenspalten aufweisen, geändert wurden. Die geänderte Formatdatei ordnet die Datenfelder den entsprechenden Tabellenspalten zu.  
  
> [!NOTE]  
>  Mithilfe einer Nicht-XML- oder XML-Formatdatei kann der Massenimport einer Datendatei in die Tabelle ausgeführt werden. Hierzu kann ein **bcp**-Befehl, eine BULK INSERT- oder INSERT ... SELECT * FROM OPENROWSET(BULK...)-Anweisung verwendet werden. Weitere Informationen finden Sie unter [Massenimport von Daten mithilfe einer Formatdatei &#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md).  
  
## <a name="sample-table-and-data-file"></a>Beispieltabelle und Datendatei  
 Die in diesem Thema enthaltenen Beispiele über die geänderten Formatdateien basieren auf der folgenden Tabelle und Datendatei.  
  
### <a name="sample-table"></a>Beispieltabelle  
 Für die Beispiele in diesem Thema muss in der `myTestOrder` -Beispieldatenbank unter dem [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] -Schema eine Tabelle namens `dbo` erstellt werden. Führen Sie den folgenden Code aus, um diese Tabelle im [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] -Abfrage-Editor zu erstellen:  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE myTestOrder   
   (  
   Col1 smallint,  
   Col2 nvarchar(50) ,  
   Col3 nvarchar(50) ,   
   Col4 nvarchar(50)   
   );  
GO  
  
```  
  
### <a name="data-file"></a>Datendatei  
 Die Datendatei `myTestOrder-c.txt`enthält die folgenden Datensätze:  
  
```  
DataField3,DataField2,1,DataField4  
DataField3,DataField2,1,DataField4  
DataField3,DataField2,1,DataField4  
  
```  
  
 Zum Massenimportieren der Daten von `myTestSkipCol2-c.dat` in die Tabelle `myTestSkipCol` muss in der Formatdatei das erste Datenfeld der Spalte `Col3`, das zweite Datenfeld der Spalte `Col2`, das dritte Datenfeld der Spalte `Col1` und das vierte Datenfeld der Spalte `Col4` zugeordnet werden.  
  
## <a name="using-a-non-xml-format-file"></a>Verwenden einer Nicht-XML-Formatdatei  
 Sie können die Reihenfolge einer Spaltenzuordnung ändern, indem Sie zur Positionsangabe des entsprechenden Datenfelds den Reihenfolgenwert der Spalte ändern.  
  
 Die folgende Beispielformatdatei im Nicht-XML-Format, `myTestOrder.fmt`, ordnet die Felder in `myTestOrder-c.txt` den Spalten der `myTestOrder`-Tabelle zu. Informationen zum Erstellen der Datendatei und der Tabelle finden Sie unter "Beispieltabelle und Datendatei" weiter oben in diesem Thema. Die Formatdatei verwendet das Zeichendatenformat.  
  
 Die Formatdatei enthält die folgenden Informationen:  
  
```  
9.0  
4  
1       SQLCHAR       0       100     ","     3     Col3               SQL_Latin1_General_CP1_CI_AS  
2       SQLCHAR       0       100     ","     2     Col2               SQL_Latin1_General_CP1_CI_AS  
3       SQLCHAR       0       7       ","     1     Col1               ""  
4       SQLCHAR       0       100     "\r\n"  4     Col4               SQL_Latin1_General_CP1_CI_AS  
  
```  
  
> [!NOTE]  
>  Weitere Informationen zum Layout von Nicht-XML-Formatdateien finden Sie unter [Nicht-XML-Formatdateien &#40;SQL Server&#41;](xml-format-files-sql-server.md).  
  
### <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird eine `BULK INSERT`-Anweisung verwendet, um mithilfe der Nicht-XML-Formatdatei `myTestOrder-c.txt` einen Massenimport der Daten aus der Datendatei `myTestOrder` in die `myTestOrder.fmt`-Beispieltabelle auszuführen.  
  
 Führen Sie im [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]-Abfrage-Editor Folgendes aus:  
  
```  
USE AdventureWorks2012;  
GO  
BULK INSERT myTestOrder  
FROM 'C:\myTestOrder-c.txt'   
WITH (formatfile='C:\myTestOrder.fmt');  
GO  
  
```  
  
## <a name="using-an-xml-format-file"></a>Verwenden einer XML-Formatdatei  
 Die folgende Beispielformatdatei im Nicht-XML-Format, `myTestOrder.xml`, ordnet den Spalten der `myTestOrder-c.txt`-Tabelle die Felder in `myTestOrder` zu. Informationen zum Erstellen der Datendatei und der Tabelle finden Sie weiter oben in diesem Thema unter "Beispieltabelle und Datendatei".  
  
 Die Formatdatei `myTestOrder.xml` enthält die folgenden Informationen:  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT xmlns="http://schemas.microsoft.com/sqlserver/2004/bulkload/format"   
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
 <RECORD>  
  <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="7"/>  
  <FIELD ID="4" xsi:type="CharTerm" TERMINATOR="\r\n" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
 </RECORD>  
 <ROW>  
  <COLUMN SOURCE="3" NAME="Col1" xsi:type="SQLSMALLINT"/>  
  <COLUMN SOURCE="2" NAME="Col2" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="1" NAME="Col3" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="4" NAME="Col4" xsi:type="SQLNVARCHAR"/>  
 </ROW>  
</BCPFORMAT>  
  
```  
  
> [!NOTE]  
>  Informationen über die Syntax eines XML-Schemas und weitere Beispiele von XML-Formatdateien finden Sie unter [XML-Formatdateien &#40;SQL Server&#41;](xml-format-files-sql-server.md).  
  
### <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird der BULK-Rowsetanbieter `OPENROWSET` verwendet, um mithilfe der XML-Formatdatei `myTestOrder-c.txt` einen Datenimport aus der Datendatei `myTestOrder` in die `myTestOrder.xml` -Beispieltabelle auszuführen. Die `INSERT… SELECT` -Anweisung gibt die Spaltenliste in der Auswahlliste an.  
  
 Führen Sie im Abfrage-Editor von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] folgenden Code aus:  
  
```  
USE AdventureWorks2012;  
GO  
INSERT INTO myTestOrder   
  SELECT Col1, Col2, Col3, Col4  
      FROM  OPENROWSET(BULK  'C:\myTestOrder-c.txt',  
      FORMATFILE='C:\myTestOrder.Xml'    
       ) AS t1;  
GO  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Überspringen einer Tabellenspalte mithilfe einer Formatdatei &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md)   
 [Auslassen eines Datenfelds mithilfe einer Formatdatei &#40;SQL Server&#41;](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
  