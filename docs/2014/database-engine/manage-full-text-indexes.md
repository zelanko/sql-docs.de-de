---
title: Verwalten von voll Text Indizes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
ms.assetid: 28ff17dc-172b-4ac4-853f-990b5dc02fd1
author: rothja
ms.author: jroth
ms.openlocfilehash: 92eb3669930407b359b8eeed4d3df2e802bdacdf
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84930937"
---
# <a name="manage-full-text-indexes"></a>Verwalten von Volltextindizes
     
##  <a name="viewing-and-changing-the-properties-of-a-full-text-index"></a><a name="view"></a>Anzeigen und Ändern der Eigenschaften eines voll Text Indexes  
  
#### <a name="to-view-or-change-the-properties-of-a-full-text-index-in-management-studio"></a>So zeigen Sie die Eigenschaften eines Volltextindexes in Management Studio an oder ändern sie  
  
1.  Erweitern Sie im Objekt-Explorer den Server.  
  
2.  Erweitern Sie **Datenbanken**, und erweitern Sie dann die Datenbank, die den Volltextindex enthält.  
  
3.  Erweitern Sie **Tabellen**.  
  
4.  Klicken Sie mit der rechten Maustaste auf die Tabelle, für die der Volltextindex definiert ist. Wählen Sie **Volltextindex**, und klicken Sie dann im Kontextmenü **Volltextindex** auf **Eigenschaften**. Das Dialogfeld **Volltextindexeigenschaften** wird geöffnet.  
  
5.  Im Bereich **Seite auswählen** können Sie eine der folgenden Seiten auswählen:  
  
    |Seite|BESCHREIBUNG|  
    |----------|-----------------|  
    |**Allgemein**|Ändert die grundlegenden Eigenschaften des Volltextindex. Beinhaltet mehrere änderbare Eigenschaften und eine Reihe von nicht änderbaren Eigenschaften, wie z. B. Datenbankname, Tabellenname und den Namen der Volltextschlüsselspalte. Die änderbaren Eigenschaften lauten:<br /><br /> **Volltextindex-Stoppliste**<br /><br /> **Volltextindizierung aktiviert**<br /><br /> **Änderungsnachverfolgung**<br /><br /> **Sucheigenschaftenliste**<br /><br /> <br /><br /> Weitere Informationen finden Sie unter [Volltextindex-Eigenschaften &#40;Seite 'Allgemein'&#41;](full-text-index-properties-general-page.md).|  
    |**Spalten**|Zeigt die Tabellenspalten an, die für die Volltextindizierung verfügbar sind. Die ausgewählte Spalte bzw. die Spalten werden volltextindiziert. Sie können beliebig viele verfügbare Spalten auswählen und in den Volltextindex aufnehmen. Weitere Informationen finden Sie unter [Volltextindex-Eigenschaften &#40;Seite "Spalten"&#41;](../../2014/database-engine/full-text-index-properties-columns-page.md).|  
    |**Zeitpläne**|Verwenden Sie diese Seite, um Zeitpläne für einen SQL Server-Agent-Auftrag zu erstellen oder zu verwalten, der eine inkrementelle Tabellenauffüllung für die Auffüllungen des Volltextindexes beginnt. Weitere Informationen finden Sie unter [Auffüllen von Volltextindizes](../relational-databases/indexes/indexes.md).<br /><br /> <strong> \* \* Wichtig \* Wenn \* </strong> Sie das Dialogfeld **voll Text Index Eigenschaften** schließen, werden alle neu erstellten Zeitpläne mit einem SQL Server-Agent Auftrag verknüpft (inkrementelle Tabellen Auffüllung starten *database_name*.* table_name*).|  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)] um vorgenommene Änderungen zu speichern und das Dialogfeld **Volltextindexeigenschaften** zu schließen.  
  
##  <a name="viewing-the-properties-of-indexed-tables-and-columns"></a><a name="props"></a>Anzeigen der Eigenschaften von indizierten Tabellen und Spalten  
 Mehrere [!INCLUDE[tsql](../includes/tsql-md.md)]-Funktionen, z. B. OBJECTPROPERTYEX, können verwendet werden, um den Wert verschiedener Eigenschaften der Volltextindizierung abzurufen. Diese Informationen sind für die Verwaltung und Problembehandlung der Volltextsuche hilfreich.  
  
 Die folgende Tabelle enthält die Volltexteigenschaften, die sich auf indizierte Tabellen und Spalten beziehen, sowie die zugehörigen [!INCLUDE[tsql](../includes/tsql-md.md)]-Funktionen.  
  
|Eigenschaft|Beschreibung|Funktion|  
|--------------|-----------------|--------------|  
|`FullTextTypeColumn`|TYPE COLUMN in der Tabelle, die die Dokumenttypinformationen der Spalte enthält.|[COLUMNPROPERTY](/sql/t-sql/functions/columnproperty-transact-sql)|  
|`IsFulltextIndexed`|Gibt an, ob eine Spalte für die Volltextindizierung aktiviert wurde.|COLUMNPROPERTY|  
|`IsFulltextKey`|Gibt an, ob der Index der Volltextschlüssel für eine Tabelle ist.|[INDEXPROPERTY](/sql/t-sql/functions/indexproperty-transact-sql)|  
|**TableFulltextBackgroundUpdateIndexOn**|Gibt an, ob für eine Tabelle das Update von Volltextindizes im Hintergrund aktiviert wurde.|[OBJECTPROPERTYEX](/sql/t-sql/functions/objectproperty-transact-sql)|  
|`TableFulltextCatalogId`|ID des Volltextkatalogs, in dem die Daten des Volltextindex für die Tabelle gespeichert sind.|OBJECTPROPERTYEX|  
|`TableFulltextChangeTrackingOn`|Gibt an, ob für eine Tabelle die Volltext-Änderungsnachverfolgung aktiviert ist.|OBJECTPROPERTYEX|  
|`TableFulltextDocsProcessed`|Die Anzahl der seit dem Start der Volltextindizierung verarbeiteten Zeilen.|OBJECTPROPERTYEX|  
|**TableFulltextFailCount**|Die Anzahl von Zeilen, für die die Volltextsuche keinen Index erstellt hat.|OBJECTPROPERTYEX|  
|**TableFulltextItemCount**|Die Anzahl von Zeilen, für die ein Volltextindex erfolgreich erstellt wurde.|OBJECTPROPERTYEX|  
|`TableFulltextKeyColumn`|Die Spalten-ID der Volltextspalte für den eindeutigen Schlüssel.|OBJECTPROPERTYEX|  
|`TableFullTextMergeStatus`|Gibt an, ob eine Tabelle über einen Volltextindex verfügt, der gerade zusammengeführt wird.|OBJECTPROPERTYEX|  
|**TableFulltextPendingChanges**|Anzahl der zu verarbeitenden ausstehenden Änderungsnachverfolgungseinträge.|OBJECTPROPERTYEX|  
|`TableFulltextPopulateStatus`|Der Auffüllungsstatus einer Volltexttabelle.|OBJECTPROPERTYEX|  
|`TableHasActiveFulltextIndex`|Gibt an, ob eine Tabelle über einen aktiven Volltextindex verfügt.|OBJECTPROPERTYEX|  
  
##  <a name="getting-information-about-the-full-text-key-column"></a><a name="key"></a>Informationen zur voll Text Schlüssel Spalte erhalten  
 Normalerweise müssen die Ergebnisse von CONTAINSTABLE- oder FREETEXTTABLE-Rowsetwertfunktionen mit der Basistabelle verknüpft werden. In solchen Fällen müssen Sie den Namen der eindeutigen Schlüsselspalte kennen. Sie können abfragen, ob ein bestimmter eindeutiger Index als Volltextschlüssel verwendet wird, und anschließend den Bezeichner der Volltextschlüsselspalte abrufen.  
  
#### <a name="to-inquire-whether-a-given-unique-index-is-used-as-the-full-text-key-column"></a>So überprüfen Sie, ob ein bestimmter eindeutiger Index als Volltextschlüsselspalte verwendet wird  
  
1.  Verwenden Sie eine [SELECT](/sql/t-sql/queries/select-transact-sql)-Anweisung, um die [INDEXPROPERTY](/sql/t-sql/functions/indexproperty-transact-sql)-Funktion aufzurufen. Verwenden Sie im Funktions aufrufdie OBJECT_ID-Funktion, um den Namen der Tabelle (*table_name*) in die Tabellen-ID zu konvertieren, den Namen eines eindeutigen Indexes für die Tabelle anzugeben und die `IsFulltextKey` Index-Eigenschaft wie folgt anzugeben:  
  
    ```  
    SELECT INDEXPROPERTY( OBJECT_ID('table_name'), 'index_name',  'IsFulltextKey' );  
    ```  
  
     Diese Anweisung gibt den Wert 1 zurück, wenn der Index verwendet wird, um die Eindeutigkeit für die Spalte des Volltextschlüssels zu erzwingen, oder den Wert 0, wenn dies nicht der Fall ist.  
  
 **Beispiel**  
  
 Im folgenden Beispiel wird abgefragt, ob der `PK_Document_DocumentID` -Index zum Erzwingen der Eindeutigkeit der Volltextschlüsselspalte verwendet wird:  
  
```  
USE AdventureWorks  
GO  
SELECT INDEXPROPERTY ( OBJECT_ID('Production.Document'), 'PK_Document_DocumentID',  'IsFulltextKey' )  
```  
  
 Dieses Beispiel gibt den Wert 1 zurück, wenn der `PK_Document_DocumentID` -Index verwendet wird, um die Eindeutigkeit der Volltextschlüsselspalte zu erzwingen. Andernfalls wird 0 oder NULL zurückgegeben. NULL impliziert, dass ein ungültiger Indexname verwendet wird, der Indexname der Tabelle nicht zugeordnet werden kann, die Tabelle nicht vorhanden ist oder eine andere Fehlerbedingung vorliegt.  
  
#### <a name="to-find-the-identifier-of-the-full-text-key-column"></a>So suchen Sie den Bezeichner der Volltextschlüsselspalte  
  
1.  Jede volltextfähige Tabelle beinhaltet eine Spalte, mit der die Eindeutigkeit aller Tabellenzeilen erzwungen wird (die *UNIQUE**KEY-Spalte*). Die `TableFulltextKeyColumn`-Eigenschaft, die mit der OBJECTPROPERTYEX-Funktion ermittelt werden kann, enthält die Spalten-ID der eindeutigen Schlüsselspalte.  
  
     Um diesen Bezeichner abzurufen, können Sie mit einer SELECT-Anweisung die OBJECTPROPERTYEX-Funktion aufrufen. Verwenden Sie die OBJECT_ID-Funktion, um den Namen der Tabelle (*table_name*) in die Tabellen-ID zu konvertieren und die- `TableFulltextKeyColumn` Eigenschaft wie folgt anzugeben:  
  
    ```  
    SELECT OBJECTPROPERTYEX(OBJECT_ID( 'table_name'), 'TableFulltextKeyColumn' ) AS 'Column Identifier';  
    ```  
  
 **Beispiele**  
  
 Im folgenden Beispiel wird der Bezeichner der Volltextschlüsselspalte oder NULL zurückgegeben. NULL impliziert, dass ein ungültiger Indexname verwendet wird, der Indexname der Tabelle nicht zugeordnet werden kann, die Tabelle nicht vorhanden ist oder eine andere Fehlerbedingung vorliegt.  
  
```  
USE AdventureWorks;  
GO  
SELECT OBJECTPROPERTYEX(OBJECT_ID('Production.Document'), 'TableFulltextKeyColumn');  
GO  
```  
  
 Das folgende Beispiel zeigt, wie der Bezeichner der eindeutigen Schlüsselspalte verwendet werden kann, um den Namen der Spalte zu ermitteln.  
  
```  
USE AdventureWorks;  
GO  
DECLARE @key_column sysname  
SET @key_column = Col_Name(Object_Id('Production.Document'),  
ObjectProperty(Object_id('Production.Document'),  
'TableFulltextKeyColumn')   
)  
SELECT @key_column AS 'Unique Key Column';  
GO  
```  
  
 Dieses Beispiel gibt eine Resultsetspalte mit dem Namen `Unique Key Column`zurück, die eine einzelne Zeile mit dem Namen der eindeutigen Schlüsselspalte (DocumentID) der Document-Tabelle enthält. Beachten Sie, dass diese Abfrage NULL zurückgibt, wenn ein ungültiger Indexname verwendet wird, der Indexname der Tabelle nicht zugeordnet werden kann, die Tabelle nicht vorhanden ist oder eine andere Fehlerbedingung vorliegt.  
  
##  <a name="disabling-or-re-enabling-a-table-for-full-text-indexing"></a><a name="disable"></a>Deaktivieren oder erneutes Aktivieren einer Tabelle für die voll Text Indizierung  
 In [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sind standardmäßig alle von Benutzern erstellten Datenbanken volltextfähig. Zudem wird eine einzelne Tabelle automatisch für die Volltextindizierung aktiviert, sobald ein Volltextindex für die Tabelle erstellt wird und dem Index eine Spalte hinzugefügt wird. Eine Tabelle wird für die Volltextindizierung automatisch deaktiviert, wenn die letzte Spalte aus dem Volltextindex der Tabelle entfernt wird.  
  
 Für eine Tabelle mit einem Volltextindex können Sie mit [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] eine Tabelle für die Volltextindizierung manuell deaktivieren und erneut aktivieren.  
  
#### <a name="to-enable-a-table-for-full-text-indexing"></a>So aktivieren Sie eine Tabelle für Volltextindizierung  
  
1.  Erweitern Sie die Servergruppe, erweitern Sie **Datenbanken**, und erweitern Sie die Datenbank, die die Tabelle enthält, die für Volltextindizierung aktiviert werden soll.  
  
2.  Erweitern Sie **Tabellen**, und klicken Sie mit der rechten Maustaste auf die Tabelle, die Sie deaktivieren oder für Volltextindizierung erneut aktivieren möchten.  
  
3.  Wählen Sie **Volltextindex**aus, und klicken Sie anschließend auf **Volltextindizierung deaktivieren** oder **Volltextindizierung aktivieren**.  
  
##  <a name="removing-a-full-text-index-from-a-table"></a><a name="remove"></a>Entfernen eines voll Text Indexes aus einer Tabelle  
  
#### <a name="to-remove-a-full-text-index-from-a-table"></a>So entfernen Sie einen Volltextindex einer Tabelle  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf die Tabelle mit dem Volltextindex, den Sie löschen möchten  
  
2.  Wählen Sie **Volltextindex löschen**aus.  
  
3.  Klicken Sie auf **OK** , wenn Sie aufgefordert werden, das Löschen des Volltextindexes zu bestätigen.  
  
  
