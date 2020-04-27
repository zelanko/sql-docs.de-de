---
title: Beibehalten von Identitätswerten beim Massenimport von Daten (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- identity values [SQL Server], bulk imports
- data formats [SQL Server], identity values
- bulk importing [SQL Server], identity values
ms.assetid: 45894a3f-2d8a-4edd-9568-afa7d0d3061f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5bb2fbd3129475c5d712cd4d1fce8bbe29ea096f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66011909"
---
# <a name="keep-identity-values-when-bulk-importing-data-sql-server"></a>Beibehalten von Identitätswerten beim Massenimport von Daten (SQL Server)
  Datendateien, die Identitäts Werte enthalten, können per Massen Import in eine [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Instanz von importiert werden. Standardmäßig werden die Werte für die Identitätsspalte in der importierten Datendatei ignoriert, und von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden automatisch eindeutige Werte zugewiesen. Die eindeutigen Werte basieren auf dem Ausgangswert und den inkrementellen Werten, die bei der Tabellenerstellung angegeben werden.  
  
 Wenn die Datendatei keine Werte für die Bezeichnerspalte in der Tabelle enthält, sollten Sie eine Formatdatei verwenden, um anzugeben, dass die Bezeichnerspalte beim Importieren von Daten ausgelassen werden soll. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] weist der Spalte automatisch eindeutige Werte zu.  
  
 Um zu verhindern, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] beim Massenimport von Datenzeilen in eine Tabelle Identitätswerte zuweist, verwenden Sie den entsprechenden Qualifizierer für den Befehl zur Identitätsbeibehaltung (keepidentity). Wenn Sie einen Qualifizierer zur Identitätsbeibehaltung angeben, verwendet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Identitätswerte in der Datendatei. Nachfolgend sind diese Qualifizierer aufgeführt:  
  
|Get-Help|Qualifizierer zur Identitätsbeibehaltung|Qualifizierertyp|  
|-------------|------------------------------|--------------------|  
|`bcp`|**-E**|Schalter|  
|BULK INSERT|KEEPIDENTITY|Argument|  
|INSERT ... SELECT * FROM OPENROWSET(BULK...)|KEEPIDENTITY|Tabellenhinweis|  
  
 Weitere Informationen finden Sie unter [bcp (Hilfsprogramm)](../../tools/bcp-utility.md), [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql), [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql), [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql), [SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) und [Tabellenhinweise &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table).  
  
> [!NOTE]  
>  Weitere Informationen zu einer automatisch inkrementierten Zahl, die in mehreren Tabellen verwendet oder aus Anwendungen aufgerufen werden kann, ohne dass auf eine Tabelle verwiesen wird, finden Sie unter [Sequenznummern](../sequence-numbers/sequence-numbers.md).  
  
## <a name="examples"></a>Beispiele  
 In den Beispielen in diesem Thema wird der Massen Import von Daten mithilfe von INSERT... Wählen Sie * FROM OPENROWSET (BULK...) aus, und behalten Sie die Standardwerte bei.  
  
### <a name="sample-table"></a>Beispieltabelle  
 Für den Massenimport muss eine Tabelle namens **myTestKeepNulls** erstellt werden, und zwar in der **AdventureWorks**-Beispieldatenbank unter dem **dbo**-Schema. Führen Sie zum Erstellen dieser Tabelle im [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]-Abfrage-Editor Folgendes aus:  
  
```  
USE AdventureWorks;  
GO  
SELECT * INTO HumanResources.myDepartment   
   FROM HumanResources.Department  
      WHERE 1=0;  
GO  
SELECT * FROM HumanResources.myDepartment;  
```  
  
 Für die **Department**-Tabelle, auf der `myDepartment` basiert, ist IDENTITY_INSERT auf OFF festgelegt. Wenn Sie also Daten in eine Identitätsspalte importieren möchten, müssen Sie KEEPIDENTITY oder **-E** angeben.  
  
### <a name="sample-data-file"></a>Beispieldatendatei  
 Die in den Beispielen zum Massenimport verwendete Datendatei enthält massenkopierte Daten, die im systemeigenen Format aus der `HumanResources.Department`-Tabelle exportiert wurden. Geben Sie zur Erstellung der Datendatei an der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Eingabeaufforderung Folgendes ein:  
  
```  
bcp AdventureWorks.HumanResources.Department out myDepartment-n.Dat -n -T  
```  
  
### <a name="sample-format-file"></a>Beispielformatdatei  
 In diesen Beispielen für den Massenimport wird eine Datei im XML-Format verwendet (`myDepartment-f-x-n.Xml`), von der wiederum systemeigene Datenformate verwendet werden. In diesem Beispiel wird diese Formatdatei mit `bcp` mithilfe der `HumanResources.Department`-Tabelle der `AdventureWorks`-Datenbank generiert. Geben Sie an der Windows-Eingabeaufforderung Folgendes ein:  
  
```  
bcp AdventureWorks.HumanResources.Department format nul -n -x -f myDepartment-f-n-x.Xml -T  
```  
  
 Weitere Informationen zum Erstellen einer Formatdatei finden Sie unter [Erstellen einer Formatdatei &#40;SQL Server&#41;](create-a-format-file-sql-server.md).  
  
### <a name="a-using-bcp-and-keeping-identity-values"></a>A. Mit "bcp" und unter Beibehaltung der Identitätswerte  
 Anhand des nachfolgenden Beispiels wird veranschaulicht, wie Identitätswerte beibehalten werden können, wenn `bcp` für den Massenimport von Daten verwendet wird. Der Befehl `bcp` verwendet die Formatdatei `myDepartment-f-n-x.Xml` und enthält folgende Schalter:  
  
|Qualifizierer|BESCHREIBUNG|  
|----------------|-----------------|  
|**-E**|Gibt an, dass Identitätswerte in der Datendatei für die Identitätsspalte verwendet werden sollen.|  
|**-T**|Gibt an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , `bcp` dass das Hilfsprogramm eine vertrauenswürdige Verbindung mit herstellt.|  
  
 Geben Sie an der Windows-Eingabeaufforderung Folgendes ein.  
  
```  
bcp AdventureWorks.HumanResources.myDepartment in C:\myDepartment-n.Dat -f C:\myDepartment-f-n-x.Xml -E -T  
  
```  
  
### <a name="b-using-bulk-insert-and-keeping-identity-values"></a>B. Mit BULK INSERT und unter Beibehaltung der Identitätswerte  
 Im nachfolgenden Beispiel wird BULK INSERT für den Massenimport von Daten aus der `myDepartment-c.Dat`-Datei in die `AdventureWorks.HumanResources.myDepartment`-Tabelle verwendet. Die Anweisung verwendet die `myDepartment-f-n-x.Xml`-Formatdatei und nimmt die Option KEEPIDENTITY auf, um sicherzustellen, dass sämtliche Identitätswerte in der Datendatei beibehalten werden.  
  
 Führen Sie im [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]-Abfrage-Editor Folgendes aus:  
  
```  
USE AdventureWorks;  
GO  
DELETE HumanResources.myDepartment;  
GO  
BULK INSERT HumanResources.myDepartment  
   FROM 'C:\myDepartment-n.Dat'  
   WITH (  
      KEEPIDENTITY,  
      FORMATFILE='C:\myDepartment-f-n-x.Xml'  
   );  
GO  
SELECT * FROM HumanResources.myDepartment;  
  
```  
  
### <a name="c-using-openrowset-and-keeping-identity-values"></a>C. Mit OPENROWSET und unter Beibehaltung der Identitätswerte  
 Im nachfolgenden Beispiel wird der OPENROWSET-Massen-Rowset-Anbieter zum Massenimport von Daten aus der `myDepartment-c.Dat`-Datei in die `AdventureWorks.HumanResources.myDepartment`-Tabelle verwendet. Die Anweisung verwendet die `myDepartment-f-n-x.Xml`-Formatdatei und nimmt den KEEPIDENTITY-Hinweis auf, um sicherzustellen, dass sämtliche Identitätswerte in der Datendatei beibehalten werden.  
  
 Führen Sie im [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]-Abfrage-Editor Folgendes aus:  
  
```  
USE AdventureWorks;  
GO  
DELETE HumanResources.myDepartment;  
GO  
  
INSERT INTO HumanResources.myDepartment  
   with (KEEPIDENTITY)  
   (DepartmentID, Name, GroupName, ModifiedDate)  
   SELECT *  
      FROM  OPENROWSET(BULK 'C:\myDepartment-n.Dat',  
      FORMATFILE='C:\myDepartment-f-n-x.Xml') as t1;  
GO  
  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Beibehalten von NULL-Werten oder Verwenden von Standardwerten während des Massenimports &#40;SQL Server&#41;](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [Vorbereiten von Daten für den Massenexport oder -import &#40;SQL Server&#41;](prepare-data-for-bulk-export-or-import-sql-server.md)  
  
 **So verwenden Sie eine Formatdatei**  
  
-   [Erstellen einer Formatdatei &#40;SQL Server&#41;](create-a-format-file-sql-server.md)  
  
-   [Massenimport von Daten mithilfe einer Formatdatei &#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [Verwenden einer Formatdatei zum Zuordnen von Tabellenspalten zu Datendateifeldern &#40;SQL Server&#41;](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
-   [Auslassen eines Datenfelds mithilfe einer Formatdatei &#40;SQL Server&#41;](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [Überspringen einer Tabellenspalte mithilfe einer Formatdatei &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
 **So verwenden Sie Datenformate für Massenimport oder Massenexport**  
  
-   [Importieren von Daten aus früheren SQL Server-Versionen im nativen Format oder im Zeichenformat](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [Verwenden des Zeichenformats zum Importieren und Exportieren von Daten &#40;SQL Server&#41;](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Verwenden des nativen Formats zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Verwenden des Unicode-Zeichenformats zum Importieren und Exportieren von Daten &#40;SQL Server&#41;](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Verwenden des nativen Unicode-Formats zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
 **So geben Sie Datenformate für die Kompatibilität bei Verwendung von bcp an**  
  
1.  [Angeben von Feld- und Zeilenabschlusszeichen &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md)  
  
2.  [Angeben der Präfixlänge in Datendateien mittels bcp &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
3.  [Angeben des Dateispeichertyps mithilfe von bcp &#40;SQL Server&#41;](specify-file-storage-type-by-using-bcp-sql-server.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [bcp (Hilfsprogramm)](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)   
 [Tabellenhinweise &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table)  
  
  
