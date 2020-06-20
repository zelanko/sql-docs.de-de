---
title: Verwenden des nativen Unicode-Formats zum Importieren oder Exportieren von Daten (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- Unicode [SQL Server], bulk importing and exporting
- data formats [SQL Server], Unicode native
ms.assetid: a6213308-f3d5-406e-9029-19d8bb3367f3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: beae2f836de16dedf3be6d8c196910c53be02266
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85026291"
---
# <a name="use-unicode-native-format-to-import-or-export-data-sql-server"></a>Verwenden des systemeigenen Unicode-Formats zum Importieren oder Exportieren von Daten (SQL Server)
  Das native Unicode-Format ist hilfreich, wenn Informationen von einer Installation von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in eine andere kopiert werden müssen. Durch die Verwendung des systemeigenen Formats bei nicht auf Zeichen basierenden Daten kann Zeit eingespart werden, da die unnötige Konvertierung der Datentypen in und aus dem Zeichenformat entfällt. Die Verwendung des Unicode-Zeichenformats für alle Zeichendaten verhindert, dass es zum Verlust von erweiterten Zeichen beim Massenübertragen von Daten zwischen Servern mit unterschiedlichen Codepages kommt. Eine Datendatei im systemeigenen Unicode-Format kann von jeder Massenimportmethode gelesen werden.  
  
 Das systemeigene Unicode-Format wird für die Massenübertragung von Daten zwischen mehreren Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe einer Datendatei, die Sonderzeichen oder DBCS-Zeichen enthält, empfohlen. Für nicht auf Zeichen basierende Daten verwendet das systemeigene Unicode-Format systemeigene (Datenbank-)Datentypen. Für Zeichendaten, wie z. B. `char`, `nchar`, `varchar`, `nvarchar`, `text`, `varchar(max)`, `nvarchar(max)` und `ntext`, verwendet das systemeigene Unicode-Format das Unicode-Zeichendatenformat.  
  
 Die `sql_variant`-Daten, die in einer Datendatei im systemeigenen Unicode-Format als SQLVARIANT gespeichert werden, funktionieren auf die gleiche Weise wie in einer Datendatei im systemeigenen Format, mit der Ausnahme, dass Werte der Typen `char` und `varchar` in `nchar` und `nvarchar` konvertiert werden. Hierdurch verdoppelt sich der für die entsprechenden Spalten benötigte Speicherplatz. Die ursprünglichen Metadaten bleiben erhalten, und die Werte werden zurück in die ursprünglichen Datentypen `char` und `varchar` konvertiert, wenn sie in eine Tabellenspalte massenimportiert werden.  
  
## <a name="command-options-for-unicode-native-format"></a>Befehlsoptionen für das systemeigene Unicode-Format  
 Sie können Daten im nativen Unicode-Format in eine Tabelle importieren, indem Sie **bcp**, BULK INSERT oder INSERT... Select \* FROM OPENROWSET (BULK...). Bei einem **bcp** -Befehl oder einer BULK INSERT-Anweisung können Sie das Datenformat in der Befehlszeile angeben. Für eine INSERT ... SELECT * FROM OPENROWSET(BULK...)-Anweisung müssen Sie das Datenformat in einer Formatdatei angeben.  
  
 Das systemeigene Unicode-Format wird von den folgenden Optionen unterstützt:  
  
|Get-Help|Option|Beschreibung|  
|-------------|------------|-----------------|  
|**bcp**|**-N**|Bewirkt, dass das Hilfsprogramm **bcp** das Native Unicode-Format verwendet, das Native (Datenbank-) Datentypen für alle nicht-Zeichendaten und das Unicode-Zeichendaten Format für alle Zeichendaten (,,, `char` `nchar` `varchar` `nvarchar` , `text` und `ntext` ) verwendet.|  
|BULK INSERT|DataFileType **= '** widenative **'**|Gibt an, dass das systemeigene Unicode-Format beim Massenimportieren von Daten verwendet werden soll.|  
  
 Weitere Informationen finden Sie unter [bcp (Hilfsprogramm)](../../tools/bcp-utility.md), [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) oder [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).  
  
> [!NOTE]  
>  Alternativ können Sie die Formatierung pro Feld in einer Formatdatei angeben. Weitere Informationen finden Sie unter [Formatdateien zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md)erforderlich.  
  
## <a name="examples"></a>Beispiele  
 Die folgenden Beispiele zeigen, wie ein Massenexport nativer Daten mithilfe von **bcp** und wie ein Massenimport derselben Daten mithilfe von BULK INSERT ausgeführt wird.  
  
### <a name="sample-table"></a>Beispieltabelle  
 Für die Beispiele ist es erforderlich, dass eine Tabelle namens **myTestUniNativeData** in der **AdventureWorks**-Beispieldatenbank unter dem **dbo**-Schema erstellt wird. Vor dem Ausführen dieser Beispiele müssen Sie diese Tabelle erstellen. Führen Sie im [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] -Abfrage-Editor Folgendes aus:  
  
```  
USE AdventureWorks;  
GO  
CREATE TABLE myTestUniNativeData (  
   Col1 smallint,  
   Col2 nvarchar(50),  
   Col3 nvarchar(50)  
   );   
```  
  
 Führen Sie zum Auffüllen dieser Tabelle und zum Anzeigen der resultierenden Inhalte die folgenden Anweisungen aus:  
  
```  
INSERT INTO myTestUniNativeData(Col1,Col2,Col3)  
   VALUES(1,'DataField2','DataField3');  
INSERT INTO myTestUniNativeData(Col1,Col2,Col3)  
   VALUES(2,'DataField2','DataField3');  
GO  
SELECT Col1,Col2,Col3 FROM myTestUniNativeData  
  
```  
  
### <a name="using-bcp-to-bulk-export-native-data"></a>Verwenden von bcp für den Massenexport systemeigener Daten  
 Verwenden Sie zum Exportieren von Daten aus der Tabelle in die Datendatei **bcp** mit der Option **out** und den folgenden Qualifizierern:  
  
|Qualifizierer|BESCHREIBUNG|  
|----------------|-----------------|  
|**-N**|Gibt systemeigene Datentypen an.|  
|**-T**|Gibt an, dass das Hilfsprogramm **bcp** die Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe integrierter Sicherheit über eine vertrauenswürdige Verbindung herstellt. Wenn **-T** nicht angegeben wird, müssen Sie **-U** und **-P** angeben, um sich erfolgreich anzumelden.|  
  
 Das folgende Beispiel führt einen Massenexport von Daten im systemeigenen Format aus der `myTestUniNativeData`-Tabelle in eine neue Datendatei namens `myTestUniNativeData-N.Dat` aus. Geben Sie an der Eingabeaufforderung von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Folgendes ein:  
  
```  
bcp AdventureWorks..myTestUniNativeData out C:\myTestUniNativeData-N.Dat -N -T  
  
```  
  
### <a name="using-bulk-insert-to-bulk-import-native-data"></a>Verwenden von BULK INSERT für den Massenimport systemeigener Daten  
 Im folgenden Beispiel wird BULK INSERT verwendet, um die Daten in der Datendatei `myTestUniNativeData-N.Dat` in die `myTestUniNativeData` -Tabelle zu importieren. Führen Sie im [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] -Abfrage-Editor Folgendes aus:  
  
```  
USE AdventureWorks;  
GO  
BULK INSERT myTestUniNativeData   
    FROM 'C:\myTestUniNativeData-N.Dat'   
   WITH (DATAFILETYPE='widenative');   
GO  
SELECT Col1,Col2,Col3 FROM myTestUniNativeData;  
GO  
  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Verwandte Aufgaben  
 **So verwenden Sie Datenformate für Massenimport oder Massenexport**  
  
-   [Importieren von Daten aus früheren SQL Server-Versionen im nativen Format oder im Zeichenformat](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [Verwenden des Zeichenformats zum Importieren und Exportieren von Daten &#40;SQL Server&#41;](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Verwenden des nativen Formats zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Verwenden des Unicode-Zeichenformats zum Importieren und Exportieren von Daten &#40;SQL Server&#41;](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [bcp (Hilfsprogramm)](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)   
 [Datentypen &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)  
  
  
