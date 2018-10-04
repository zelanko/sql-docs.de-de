---
title: Verwenden des nativen Formats zum Importieren oder Exportieren von Daten (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- native data format [SQL Server]
- data formats [SQL Server], native
ms.assetid: eb279b2f-0f1f-428f-9b8f-2a7fc495b79f
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2dee0f6a337cab7713862e662e06bb94a0b34a5d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48124300"
---
# <a name="use-native-format-to-import-or-export-data-sql-server"></a>Verwenden des systemeigenen Formats zum Importieren oder Exportieren von Daten (SQL Server)
  Das systemeigene Format wird für die Massenübertragung von Daten zwischen mehreren Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe einer Datendatei empfohlen, die keinen erweiterten oder Doppelbyte-Zeichensatz (Double-Byte Character Set, DBCS) enthält.  
  
> [!NOTE]  
>  Für die Massenübertragung von Daten zwischen mehreren Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe einer Datendatei, die erweiterte Zeichen oder DBCS-Zeichen enthält, sollten Sie das systemeigene Unicode-Format verwenden. Weitere Informationen finden Sie unter [Verwenden des nativen Unicode-Formats zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](use-unicode-native-format-to-import-or-export-data-sql-server.md).  
  
 Das systemeigene Format erhält die systemeigenen Datentypen einer Datenbank. Das systemeigene Format ist für die Hochgeschwindigkeitsübertragung von Daten zwischen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabellen konzipiert. Wenn Sie eine Formatdatei verwenden, müssen Quell- und Zieltabelle nicht identisch sein. Die Datenübertragung besteht aus zwei Schritten:  
  
1.  Massenexportieren der Daten aus einer Quelltabelle in eine Datendatei  
  
2.  Massenimportieren der Daten aus der Datendatei in die Zieltabelle  
  
 Durch die Verwendung des systemeigenen Formats zwischen identischen Tabellen wird die unnötige Konvertierung von Datentypen in das und aus dem Zeichenformat vermieden und somit Zeit und Speicherplatz gespart. Um eine optimale Übertragungsrate zu erreichen, werden jedoch wenige Überprüfungen der Datenformatierung vorgenommen. Berücksichtigen Sie, um Probleme mit den geladenen Daten zu verhindern, die folgende Einschränkungsliste.  
  
## <a name="restrictions"></a>Restrictions  
 Um Daten im systemeigenen Format erfolgreich zu importieren, müssen folgende Punkte sichergestellt sein:  
  
-   Die Datendatei liegt im systemeigenen Format vor.  
  
-   Die Zieltabelle muss mit der Datendatei kompatibel sein (Spaltenanzahl, Datentyp, Länge, NULL-Status usw. müssen richtig sein), oder Sie müssen eine Formatdatei verwenden, um jedes Feld den entsprechenden Spalten zuzuordnen.  
  
    > [!NOTE]  
    >  Wenn Sie Daten aus einer Datei importieren, die nicht mit der Zieltabelle übereinstimmt, kann der Importvorgang zwar erfolgreich sein, aber die in die Zieltabelle eingefügten Datenwerte sind wahrscheinlich falsch. Das liegt daran, dass die Daten aus der Datei mithilfe des Formats der Zieltabelle interpretiert werden. Daher hat jede fehlende Übereinstimmung die Einfügung falscher Werte zur Folge. Eine derartige fehlende Übereinstimmung kann jedoch unter keinen Umständen logische oder physische Inkonsistenzen in der Datenbank verursachen.  
  
     Weitere Informationen zur Verwendung von Formatdateien finden Sie unter [Formatdateien zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).  
  
 Ein erfolgreicher Import beschädigt die Zieltabelle nicht.  
  
## <a name="how-bcp-handles-data-in-native-format"></a>Behandlung von Daten im systemeigenen Format durch bcp  
 Dieser Abschnitt enthält spezielle Überlegungen zum Exportieren und Importieren von Daten im systemeigenen Format durch das Hilfsprogramm **bcp** .  
  
-   Nicht auf Zeichen basierende Daten  
  
     Das Hilfsprogramm bcp verwendet das interne binäre Datenformat von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , um nicht auf Zeichen basierende Daten aus einer Tabelle in eine Datendatei zu schreiben.  
  
-   Daten vom Typ `char` oder `varchar`  
  
     Am Anfang jedes `char` oder `varchar` Feld **Bcp** fügt die Präfixlänge.  
  
    > [!IMPORTANT]  
    >  Wenn der einheitliche Modus verwendet wird, konvertiert das Hilfsprogramm **bcp** standardmäßig Zeichen aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in OEM-Zeichen, bevor sie in eine Datendatei kopiert werden. Das Hilfsprogramm **bcp** konvertiert Zeichen aus einer Datendatei in ANSI-Zeichen, bevor der Massenimport der Zeichen in eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabelle ausgeführt wird. Während dieser Konvertierungen kann es zum Verlust von Daten mit erweiterten Zeichen kommen. Verwenden Sie für erweiterte Zeichen entweder das systemeigene Unicode-Format, oder geben Sie eine Codepage an.  
  
-   `sql_variant` Daten  
  
     Wenn `sql_variant` Daten als SQLVARIANT in einer Datendatei mit systemeigenen Format gespeichert, die Daten alle Merkmale. Die Metadaten, die den Datentyp jedes Datenwerts aufzeichnen, werden zusammen mit dem Datenwert gespeichert. Diese Metadaten werden verwendet, um den Datenwert mit dem gleichen Datentyp im Ziel neu zu erstellen `sql_variant` Spalte.  
  
     Ist der Datentyp der Zielspalte nicht `sql_variant`, alle Datenwerte in den Datentyp der Zielspalte, Einhaltung der üblichen Regeln der impliziten Datenkonvertierung konvertiert wird. Wenn während der Datenkonvertierung ein Fehler auftritt, wird für den aktuellen Batch ein Rollback ausgeführt. Bei Werten vom Typ `char` und `varchar`, die zwischen `sql_variant`-Spalten übertragen werden, treten möglicherweise Probleme bei der Codepagekonvertierung auf.  
  
     Weitere Informationen zur Datenkonvertierung finden Sie unter [Datentypkonvertierung &amp;#40;Datenbank-Engine&amp;#41;](/sql/t-sql/data-types/data-type-conversion-database-engine).  
  
## <a name="command-options-for-native-format"></a>Befehlsoptionen für das systemeigene Format  
 Sie können Daten im nativen Format unter Verwendung von **bcp**, BULK INSERT oder INSERT ... SELECT \* FROM OPENROWSET(BULK...). Für einen **bcp**-Befehl oder eine BULK INSERT-Anweisung können Sie das Datenformat in der Befehlszeile angeben. Für eine INSERT ... SELECT * FROM OPENROWSET(BULK...)-Anweisung müssen Sie das Datenformat in einer Formatdatei angeben.  
  
 Das systemeigene Format wird durch die folgenden Befehlszeilenoptionen unterstützt:  
  
|Befehl|Option|Description|  
|-------------|------------|-----------------|  
|**bcp**|**-n**|Bewirkt, dass die **Bcp** Hilfsprogramm, um die nativen Datentypen der Daten verwenden.<sup> 1</sup>|  
|BULK INSERT|DATAFILETYPE **='** native **'**|Verwendet die systemeigenen Datentypen (native oder widenative) der Daten. Beachten Sie, dass DATAFILETYPE nicht erforderlich ist, wenn eine Formatdatei die Datentypen angibt.|  
  
 <sup>1</sup> zum Laden nativer (**- n**) in ein Format, die kompatibel mit früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Clients verwenden die **-V** wechseln. Weitere Informationen finden Sie unter [Importieren von Daten aus früheren SQL Server-Versionen im nativen Format oder im Zeichenformat](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md).  
  
 Weitere Informationen finden Sie unter [bcp (Hilfsprogramm)](../../tools/bcp-utility.md), [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql), oder [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).  
  
> [!NOTE]  
>  Alternativ können Sie die Formatierung pro Feld in einer Formatdatei angeben. Weitere Informationen finden Sie unter [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).  
  
## <a name="examples"></a>Beispiele  
 Die folgenden Beispiele zeigen, wie ein Massenexport nativer Daten mithilfe von **bcp** und wie ein Massenimport derselben Daten mithilfe von BULK INSERT ausgeführt wird.  
  
### <a name="sample-table"></a>Beispieltabelle  
 Die Beispiele erfordern, dass eine Tabelle mit dem Namen **myTestNativeData** in der **AdventureWorks** -Beispieldatenbank unter dem Schema **dbo** erstellt wird. Vor dem Ausführen dieser Beispiele müssen Sie diese Tabelle erstellen. Führen Sie im [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] -Abfrage-Editor Folgendes aus:  
  
```  
USE AdventureWorks;  
GO  
CREATE TABLE myTestNativeData (  
   Col1 smallint,  
   Col2 nvarchar(50),  
   Col3 nvarchar(50)  
   );   
```  
  
 Führen Sie zum Auffüllen dieser Tabelle und zum Anzeigen der resultierenden Inhalte die folgenden Anweisungen aus:  
  
```  
INSERT INTO myTestNativeData(Col1,Col2,Col3)  
   VALUES(1,'DataField2','DataField3');  
INSERT INTO myTestNativeData(Col1,Col2,Col3)  
   VALUES(2,'DataField2','DataField3');  
GO  
SELECT Col1,Col2,Col3 FROM myTestNativeData  
  
```  
  
### <a name="using-bcp-to-bulk-export-native-data"></a>Verwenden von bcp für den Massenexport systemeigener Daten  
 Verwenden Sie zum Exportieren von Daten aus der Tabelle in die Datendatei **bcp** mit der Option **out** und den folgenden Qualifizierern:  
  
|Qualifizierer|Description|  
|----------------|-----------------|  
|**-n**|Gibt systemeigene Datentypen an.|  
|**-T**|Gibt an, dass das Hilfsprogramm **bcp** die Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe integrierter Sicherheit über eine vertrauenswürdige Verbindung herstellt. Wenn **-T** nicht angegeben wird, müssen Sie **-U** und **-P** angeben, um sich erfolgreich anzumelden.|  
  
 Das folgende Beispiel führt einen Massenexport von Daten im systemeigenen Format aus der `myTestNativeData`-Tabelle in eine neue Datendatei namens `myTestNativeData-n.Dat` aus. Geben Sie an der Eingabeaufforderung von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Folgendes ein:  
  
```  
bcp AdventureWorks..myTestNativeData out C:\myTestNativeData-n.Dat -n -T  
  
```  
  
### <a name="using-bulk-insert-to-bulk-import-native-data"></a>Verwenden von BULK INSERT für den Massenimport systemeigener Daten  
 Im folgenden Beispiel wird BULK INSERT verwendet, um die Daten in der Datendatei `myTestNativeData-n.Dat` in die `myTestNativeData` -Tabelle zu importieren. Führen Sie im [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] -Abfrage-Editor Folgendes aus:  
  
```  
USE AdventureWorks;  
GO  
BULK INSERT myTestNativeData   
    FROM 'C:\myTestNativeData-n.Dat'   
   WITH (DATAFILETYPE='native');   
GO  
SELECT Col1,Col2,Col3 FROM myTestNativeData  
GO  
  
```  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
 **So verwenden Sie Datenformate für Massenimport oder Massenexport**  
  
-   [Importieren von Daten aus früheren SQL Server-Versionen im systemeigenen Format oder im Zeichenformat](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [Verwenden des Zeichenformats zum Importieren und Exportieren von Daten &#40;SQL Server&#41;](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Verwenden des Unicode-Zeichenformats zum Importieren und Exportieren von Daten &#40;SQL Server&#41;](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Verwenden des nativen Unicode-Formats zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
## <a name="see-also"></a>Siehe auch  
 [bcp Utility](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [Datentypen &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)   
 [sql_variant &#40;Transact-SQL&#41;](/sql/t-sql/data-types/sql-variant-transact-sql)   
 [Importieren von Daten aus früheren SQL Server-Versionen im nativen Format oder im Zeichenformat](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)   
 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)   
 [Verwenden des nativen Unicode-Formats zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
  
