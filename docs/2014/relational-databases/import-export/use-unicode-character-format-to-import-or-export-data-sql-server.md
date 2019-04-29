---
title: Verwenden des Unicode-Zeichenformats zum Importieren und Exportieren von Daten (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- data formats [SQL Server], Unicode character
- Unicode [SQL Server], bulk importing and exporting
ms.assetid: 74342a11-c1c0-4746-b482-7f3537744a70
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 85df40b07542e1af144796d4e8b5f9fb33cdc7c9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63065762"
---
# <a name="use-unicode-character-format-to-import-or-export-data-sql-server"></a>Verwenden des Unicode-Zeichenformats zum Importieren und Exportieren von Daten (SQL Server)
  Es wird empfohlen, für die Massenübertragung von Daten zwischen mehreren Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe einer Datendatei, die Sonderzeichen oder Zeichen aus dem Doppelbyte-Zeichensatz (Double-Byte Character Set, DBCS) enthält, das Unicode-Zeichenformat zu verwenden. Mit dem Unicode-Zeichenformat können Daten von einem Server mithilfe einer Codepage exportiert werden, wenn sich diese Codepage von der Codepage unterscheidet, die der Client verwendet, der den Vorgang ausführt. In solchen Fällen bietet die Verwendung des Unicode-Zeichenformats folgende Vorteile:  
  
-   Wenn es sich bei den Quell- und Zieldaten um Unicode-Datentypen handelt, bleiben bei Verwendung des Unicode-Zeichenformats alle Zeichendaten erhalten.  
  
-   Wenn es sich bei den Quell- und Zieldaten nicht um Unicode-Datentypen handelt, wird durch die Verwendung des Unicode-Datenformats der Verlust von Sonderzeichen in Bezug auf die Quelldaten minimiert, die am Ziel nicht dargestellt werden können.  
  
 Datendateien im Unicode-Zeichenformat folgen den Konventionen für Unicode-Dateien. Die ersten zwei Bytes der Datei sind Hexadezimalzahlen (0xFFFE). Diese Bytes dienen als Markierungen für die Bytereihenfolge, in der angegeben wird, ob in der Datei das höherwertige Byte zuerst oder zuletzt gespeichert wird.  
  
> [!IMPORTANT]  
>  Damit eine Formatdatei mit einer Datendatei mit Unicode-Zeichen verwendet werden kann, müssen alle Eingabefelder Unicode-Textzeichenfolgen sein (d. h., entweder Unicode-Zeichenfolgen einer festen Länge oder Unicode-Zeichenfolgen mit Abschlusszeichen).  
  
 Die `sql_variant`-Daten, die in einer Datendatei im Unicode-Zeichenformat gespeichert sind, verhalten sich wie Daten in einer Datendatei im Zeichenformat, außer dass die Daten als `nchar`-Daten und nicht als `char`-Daten gespeichert sind. Weitere Informationen zum Zeichenformat finden Sie unter [Sortierung und Unicode-Unterstützung](../collations/collation-and-unicode-support.md).  
  
 Wenn Sie andere Feld- und Zeilenabschlusszeichen als die standardmäßig durch das Unicode-Zeichenformat vorgegebenen verwenden möchten, informieren Sie sich unter [Angeben von Feld- und Zeilenabschlusszeichen &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md).  
  
## <a name="command-options-for-unicode-character-format"></a>Befehlsoptionen für das Unicode-Zeichenformat  
 Sie können Daten im Unicode-Zeichenformat in eine Tabelle importieren, indem Sie **bcp**, BULK INSERT oder INSERT ... SELECT \* FROM OPENROWSET(BULK...). Für einen **bcp**-Befehl oder eine BULK INSERT-Anweisung können Sie das Datenformat in der Befehlszeile angeben. Für eine INSERT ... SELECT * FROM OPENROWSET(BULK...)-Anweisung müssen Sie das Datenformat in einer Formatdatei angeben.  
  
 Das Unicode-Zeichenformat wird von den folgenden Befehlszeilenoptionen unterstützt:  
  
|Befehl|Option|Description|  
|-------------|------------|-----------------|  
|**bcp**|**-w**|Verwendet das Unicode-Zeichenformat|  
|BULK INSERT|DATAFILETYPE **='** widechar **'**|Verwendet das Unicode-Zeichenformat beim Massenimport von Daten|  
  
 Weitere Informationen finden Sie unter [bcp (Hilfsprogramm](../../tools/bcp-utility.md), [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql), oder [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).  
  
> [!NOTE]  
>  Alternativ können Sie die Formatierung pro Feld in einer Formatdatei angeben. Weitere Informationen finden Sie unter [Formatdateien zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).  
  
## <a name="examples"></a>Beispiele  
 Die folgenden Beispiele veranschaulichen den Massenexport von Unicode-Zeichendaten mithilfe von **bcp** und den Massenimport derselben Daten mithilfe von BULK INSERT.  
  
### <a name="sample-table"></a>Beispieltabelle  
 Für die Beispiele muss in der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]-Beispieldatenbank unter dem `myTestUniCharData`-Schema eine Tabelle namens `dbo` erstellt werden. Vor dem Ausführen dieser Beispiele müssen Sie diese Tabelle erstellen. Führen Sie Folgendes aus, um diese Tabelle im [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]-Abfrage-Editor zu erstellen:  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE myTestUniCharData (  
   Col1 smallint,  
   Col2 nvarchar(50),  
   Col3 nvarchar(50)  
   );   
```  
  
 Führen Sie zum Auffüllen dieser Tabelle und zum Anzeigen der resultierenden Inhalte die folgenden Anweisungen aus:  
  
```  
INSERT INTO myTestUniCharData(Col1,Col2,Col3)  
   VALUES(1,'DataField2','DataField3')   
        ,(2,'DataField2','DataField3');  
GO  
SELECT Col1,Col2,Col3 FROM myTestUniCharData;  
  
```  
  
### <a name="using-bcp-to-bulk-export-unicode-character-data"></a>Verwenden von "bcp" für den Massenexport von Unicode-Zeichendaten  
 Verwenden Sie zum Exportieren von Daten aus der Tabelle in die Datendatei **bcp** mit der Option **out** und den folgenden Qualifizierern:  
  
|Qualifizierer|Description|  
|----------------|-----------------|  
|**-w**|Gibt das Unicode-Zeichenformat an|  
|**-t** `,`|Gibt ein Komma (`,`) als Feldabschlusszeichen an.<br /><br /> Hinweis: Das standardmäßige Feldabschlusszeichen ist das Unicode-Zeichen (\t). Weitere Informationen finden Sie unter [Angeben von Feld- und Zeilenabschlusszeichen &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md).|  
|**-T**|Gibt an, dass das Hilfsprogramm **bcp** die Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe integrierter Sicherheit über eine vertrauenswürdige Verbindung herstellt. Wenn **-T** nicht angegeben wird, müssen Sie **-U** und **-P** angeben, um sich erfolgreich anzumelden.|  
  
 Im folgenden Beispiel wird ein Massenexport von Daten im Unicode-Zeichenformat aus der `myTestUniCharData`-Tabelle in eine neue Datendatei ausgeführt. Diese Datendatei heißt `myTestUniCharData-w.Dat` und verwendet das Komma (`,`) als Feldabschlusszeichen. Geben Sie an der Eingabeaufforderung von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Folgendes ein:  
  
```  
bcp AdventureWorks2012..myTestUniCharData out C:\myTestUniCharData-w.Dat -w -t, -T  
  
```  
  
### <a name="using-bulk-insert-to-bulk-import-unicode-character-data"></a>Verwenden von BULK INSERT für den Massenimport von Unicode-Zeichendaten  
 Im folgenden Beispiel wird `BULK INSERT` zum Importieren der Daten aus der Datendatei `myTestUniCharData-w.Dat` in die `myTestUniCharData`-Tabelle verwendet. Das nicht standardmäßige Feldabschlusszeichen (`,`) muss in der Anweisung deklariert werden. Führen Sie im [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] -Abfrage-Editor Folgendes aus:  
  
```  
USE AdventureWorks2012;  
GO  
BULK INSERT myTestUniCharData   
   FROM 'C:\myTestUniCharData-w.Dat'   
   WITH (  
      DATAFILETYPE='widechar',  
      FIELDTERMINATOR=','  
   );   
GO  
SELECT Col1,Col2,Col3 FROM myTestUniCharData;  
GO  
  
```  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
 **So verwenden Sie Datenformate für Massenimport oder Massenexport**  
  
-   [Importieren von Daten aus früheren SQL Server-Versionen im systemeigenen Format oder im Zeichenformat](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [Verwenden des Zeichenformats zum Importieren und Exportieren von Daten &#40;SQL Server&#41;](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Verwenden des nativen Formats zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Verwenden des nativen Unicode-Formats zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
## <a name="see-also"></a>Siehe auch  
 [bcp Utility](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)   
 [Datentypen &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)   
 [Sortierung und Unicode-Unterstützung](../collations/collation-and-unicode-support.md)  
  
  
