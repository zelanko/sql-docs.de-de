---
title: Verwenden des Zeichenformats zum Importieren und Exportieren von Daten (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- data formats [SQL Server], character
- character formats [SQL Server]
ms.assetid: d925e66a-1a73-43cd-bc06-1cbdf8174a4d
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e25c975dca01ee2787a598afbe1a67f09fbab0ce
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48078440"
---
# <a name="use-character-format-to-import-or-export-data-sql-server"></a>Verwenden des Zeichenformats zum Importieren und Exportieren von Daten (SQL Server)
  Das Zeichenformat wird für den Massenexport von Daten in eine Textdatei empfohlen, die in einem anderen Programm verwendet werden sollen, oder für den Massenimport von Daten aus einer Textdatei, die von einem anderen Programm generiert werden.  
  
> [!NOTE]  
>  Wenn Sie Daten zwischen Instanzen von [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] massenübertragen und die Datendatei Unicode-Zeichendaten, aber keine Sonderzeichen oder DBCS-Zeichen enthält, sollten Sie das Unicode-Zeichenformat verwenden. Weitere Informationen finden Sie unter [Verwenden des Unicode-Zeichenformats zum Importieren und Exportieren von Daten &#40;SQL Server&#41;](use-unicode-character-format-to-import-or-export-data-sql-server.md).  
  
 Das Zeichenformat verwendet das Zeichendatenformat für alle Spalten. Es ist nützlich, Informationen im Zeichenformat zu speichern, wenn Sie die Daten mit einem anderen Programm, z. B. als Kalkulationstabelle, verwenden, oder die Daten aus einer Datenbank eines anderen Herstellers wie z. B. Oracle in eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kopiert werden müssen.  
  
## <a name="considerations-for-using-character-format"></a>Überlegungen zum Verwenden des Zeichenformats  
 Beim Verwenden des Zeichenformats sollten Sie Folgendes berücksichtigen:  
  
-   Standardmäßig trennt das Hilfsprogramm **bcp** die Zeichendatenfelder mit einem Tabstoppzeichen und schließt den Datensatz mit einem Neue-Zeile-Zeichen ab. Weitere Informationen zum Angeben alternativer Abschlusszeichen finden Sie unter [Angeben von Feld- und Zeilenabschlusszeichen &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md).  
  
-   Standardmäßig werden vor einem Massenexport oder -import von Daten im Zeichenmodus die folgenden Konvertierungen ausgeführt:  
  
    |Richtung des Massenvorgangs|Konvertierung|  
    |---------------------------------|----------------|  
    |Exportieren|Konvertiert Daten in die Zeichendarstellung. Wenn dies explizit angefordert wird, werden die Daten in die angeforderte Codepage für Zeichenspalten konvertiert. Wenn keine Codepage angegeben wird, werden die Zeichendaten mithilfe der OEM-Codepage des Clientcomputers konvertiert.|  
    |Importieren|Konvertiert Zeichendaten bei Bedarf in die systemeigene Darstellung und übersetzt die Zeichendaten von der Codepage des Clients in die Codepage der Zielspalte(n).|  
  
-   Um den Verlust von Sonderzeichen zu verhindern, verwenden Sie das Unicode-Zeichenformat, oder geben Sie eine Codepage an.  
  
-   Alle `sql_variant`-Daten, die in einer Zeichenformatdatei gespeichert sind, werden ohne Metadaten gespeichert. Jedes Datenwerts wird in konvertiert `char` Format gemäß den Regeln der impliziten Datenkonvertierung. Beim Importieren in eine `sql_variant`-Spalte werden die Daten als `char`-Datentyp importiert. Beim Importieren in eine Spalte mit einem Datentyp außer `sql_variant`, die Daten werden von konvertiert `char` mithilfe der impliziten Konvertierung. Weitere Informationen zur Datenkonvertierung finden Sie unter [Datentypkonvertierung &amp;#40;Datenbank-Engine&amp;#41;](/sql/t-sql/data-types/data-type-conversion-database-engine).  
  
-   Die **Bcp** Hilfsprogramm Exporte `money` Werte wie Datendateien im Zeichenformat mit vier Stellen nach dem Dezimaltrennzeichen und ohne alle Symbole wie z. B. Kommas als Trennzeichen. So wird z. B. eine `money`-Spalte mit dem Wert 1,234,567.123456 beim Massenkopieren in eine Datendatei als die Zeichenfolge 1234567.1235 massenexportiert.  
  
## <a name="command-options-for-character-format"></a>Befehlsoptionen für das Zeichenformat  
 Sie können Daten im Zeichenformat in eine Tabelle importieren, indem Sie die folgenden Anweisungen verwenden: **bcp**, BULK INSERT oder INSERT ... SELECT \* FROM OPENROWSET(BULK...). Für einen **bcp**-Befehl oder eine BULK INSERT-Anweisung können Sie das Datenformat in der Befehlszeile angeben. Für eine INSERT ... SELECT * FROM OPENROWSET(BULK...)-Anweisung müssen Sie das Datenformat in einer Formatdatei angeben.  
  
 Das Zeichenformat wird von den folgenden Befehlszeilenoptionen unterstützt:  
  
|Befehl|Option|Description|  
|-------------|------------|-----------------|  
|**bcp**|**-c**|Bewirkt, dass die **Bcp** Dienstprogramm mit Zeichendaten enthalten sind.<sup> 1</sup>|  
|BULK INSERT|DATAFILETYPE **='char'**|Verwendet das Zeichenformat beim Massenimport von Daten.|  
  
 <sup>1</sup> zum Laden von Zeichen (**- C**) in ein Format, die kompatibel mit früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Clients verwenden die **-V** wechseln. Weitere Informationen finden Sie unter [Importieren von Daten aus früheren SQL Server-Versionen im nativen Format oder im Zeichenformat](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md).  
  
 Weitere Informationen finden Sie unter [bcp (Hilfsprogramm)](../../tools/bcp-utility.md), [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql), oder [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).  
  
> [!NOTE]  
>  Alternativ können Sie die Formatierung pro Feld in einer Formatdatei angeben. Weitere Informationen finden Sie unter [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).  
  
## <a name="examples"></a>Beispiele  
 Die folgenden Beispiele veranschaulichen, wie Zeichendaten mithilfe von **bcp** massenexportiert und die gleichen Daten mithilfe von BULK INSERT massenimportiert werden.  
  
### <a name="sample-table"></a>Beispieltabelle  
 Für diese Beispiele ist es erforderlich, dass eine Tabelle mit dem Namen **myTestCharData** in der Beispieldatenbank **AdventureWorks** im **dbo**-Schema erstellt wird. Vor dem Ausführen dieser Beispiele müssen Sie diese Tabelle erstellen. Zum Erstellen dieser Tabelle führen Sie im Abfrage-Editor von [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] folgende Schritte aus:  
  
```  
USE AdventureWorks;  
GO  
CREATE TABLE myTestCharData (  
   Col1 smallint,  
   Col2 nvarchar(50),  
   Col3 nvarchar(50)  
   );   
```  
  
 Führen Sie zum Auffüllen dieser Tabelle und zum Anzeigen der resultierenden Inhalte die folgenden Anweisungen aus:  
  
```  
INSERT INTO myTestCharData(Col1,Col2,Col3)  
   VALUES(1,'DataField2','DataField3');  
INSERT INTO myTestCharData(Col1,Col2,Col3)  
   VALUES(2,'DataField2','DataField3');  
GO  
SELECT Col1,Col2,Col3 FROM myTestCharData  
  
```  
  
### <a name="using-bcp-to-bulk-export-character-data"></a>Verwenden von bcp für den Massenexport von Zeichendaten  
 Verwenden Sie zum Exportieren von Daten aus der Tabelle in die Datendatei **bcp** mit der Option **out** und den folgenden Qualifizierern:  
  
|Qualifizierer|Description|  
|----------------|-----------------|  
|**-c**|Gibt das Zeichenformat an.|  
|**-t** `,`|Gibt ein Komma (`,`) als Feldabschlusszeichen an.<br /><br /> Hinweis: Das Standard-Feldabschlusszeichen ist das Tabstoppzeichen (\t). Weitere Informationen finden Sie unter [Specify Field and Row Terminators &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md).|  
|**-T**|Gibt an, dass das Hilfsprogramm **bcp** die Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe integrierter Sicherheit über eine vertrauenswürdige Verbindung herstellt. Wenn **-T** nicht angegeben wird, müssen Sie **-U** und **-P** angeben, um sich erfolgreich anzumelden.|  
  
 Im folgenden Beispiel wird ein Massenexport von Daten im Zeichenformat aus der `myTestCharData`-Tabelle in eine neue Datendatei ausgeführt. Diese Datendatei heißt `myTestCharData-c.Dat` und verwendet das Komma (,) als Feldabschlusszeichen. Geben Sie an der Eingabeaufforderung von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Folgendes ein:  
  
```  
bcp AdventureWorks..myTestCharData out C:\myTestCharData-c.Dat -c -t, -T  
  
```  
  
### <a name="using-bulk-insert-to-bulk-import-character-data"></a>Verwenden von BULK INSERT für den Massenimport von Zeichendaten  
 Im folgenden Beispiel wird BULK INSERT verwendet, um die Daten in der Datendatei `myTestCharData-c.Dat` in die `myTestCharData`-Tabelle zu importieren. Führen Sie im [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] -Abfrage-Editor Folgendes aus:  
  
```  
USE AdventureWorks;  
GO  
BULK INSERT myTestCharData   
   FROM 'C:\myTestCharData-c.Dat'   
   WITH (  
      DATAFILETYPE='char',  
      FIELDTERMINATOR=','  
   );   
GO  
SELECT Col1,Col2,Col3 FROM myTestCharData;  
GO  
  
```  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
 **So verwenden Sie Datenformate für Massenimport oder Massenexport**  
  
-   [Importieren von Daten aus früheren SQL Server-Versionen im nativen Format oder im Zeichenformat](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [Verwenden des nativen Formats zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Verwenden des Unicode-Zeichenformats zum Importieren und Exportieren von Daten &#40;SQL Server&#41;](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Verwenden des nativen Unicode-Formats zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
## <a name="see-also"></a>Siehe auch  
 [bcp Utility](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)   
 [Datentypen &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)   
 [Importieren von Daten aus früheren SQL Server-Versionen im nativen Format oder im Zeichenformat](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
  
