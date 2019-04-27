---
title: Volltextkatalog-Eigenschaften (Seite Tabellen und Sichten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.ftcatalogproperties.tablesviews.f1
ms.assetid: 2d45fcd2-0f0f-4167-9027-316d6696c106
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 78d7dc111bc0b6eb10e80f32785beeda710e52bd
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779191"
---
# <a name="full-text-catalog-properties-tables-and-views-page"></a>Volltextkatalog-Eigenschaften (Seite „Tabellen und Sichten“)
  In diesem Dialogfeld können Sie die Tabellen und Sichten anzeigen oder bearbeiten, die dem Volltextkatalog zugewiesen sind.  
  
## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente  
 **Alle geeigneten Tabellen-/Sichtobjekte in dieser Datenbank**  
 Listet alle Tabellen und Sichten auf, für die ein eindeutiger Index definiert ist, die jedoch noch nicht Bestandteil des Volltextkatalogs sind. Wählen Sie eine Tabelle oder Sicht aus, und weisen sie Sie den Katalog, wählen Sie die Elemente im Listenfeld aus, und klicken Sie auf die Schaltfläche "->".  
  
 **Dem Katalog zugewiesene Tabellen-/Sichtobjekte**  
 Listet die Tabellen und Sichten auf, die zurzeit dem Volltextkatalog zugewiesen sind.  
  
## <a name="selected-object-properties"></a>Ausgewählte Objekteigenschaften  
 **Ausgewählte Objekteigenschaften**  
 Zeigt die Eigenschaften des ausgewählten Objekts im Listenfeld der dem Katalog zugewiesenen Objekte an.  
  
 **Eindeutiger Index**  
 Listet die verfügbaren eindeutigen Indizes der Tabelle oder Sicht auf.  
  
 **Tabelle ist volltextfähig**  
 Aktivieren Sie dieses Kontrollkästchen, um den Volltextindex für die Tabelle zu aktivieren. Deaktivieren Sie das Kontrollkästchen, um den Volltextindex zu deaktivieren.  
  
## <a name="eligible-columns-grid"></a>Geeignetes Spaltenraster  
  
|||  
|-|-|  
|**Verfügbare Spalten**|Zeigt alle volltextindizierten Spalten an. Aktivieren Sie ein Kontrollkästchen, um eine Spalte zum Volltextindex hinzuzufügen.|  
|**Sprache für die Wörtertrennung**|Zeigt die Sprache des Worttrennmoduls an.|  
|**Datentypspalte**|Listet den Namen der Spalte in der Tabelle, die den Dokumenttyp aufgeführten Spalte enthält **verfügbaren Spalten** Wenn die Spalte ist eine `varbinary(max)` oder `image` Spalte.|  
|**Statistische Semantik**|Wählen Sie aus, ob die semantische Indizierung für die ausgewählte Spalte aktiviert werden soll. Weitere Informationen finden Sie unter [Semantische Suche &#40;SQL Server&#41;](../relational-databases/search/semantic-search-sql-server.md).<br /><br /> Wenn Sie eine **Sprache** vor der Option **Statistische Semantik**auswählen und die ausgewählte Sprache über kein zugeordnetes semantisches Sprachmodell verfügt, ist das Kontrollkästchen **Statistische Semantik** deaktiviert. Wenn Sie **Statistische Semantik** vor einer **Sprache**auswählen, werden im Dropdown-Kombinationsfeld nur die Sprachen angezeigt, für die das semantische Sprachmodell unterstützt wird.|  
  
## <a name="track-changes"></a>Nachverfolgen von Änderungen  
  
|||  
|-|-|  
|**Automatic**|Der Volltextindex wird automatisch aktualisiert, wenn in der zugrunde liegenden Tabelle Daten geändert, hinzugefügt oder gelöscht werden.|  
|**Manuell**|Wenn indizierte Daten geändert, hinzugefügt oder gelöscht werden, protokolliert [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] die Änderungen. Wenn für die Nachverfolgung von Änderungen die Option **Manuell** aktiviert ist, werden die Änderungen nicht automatisch in den Index übernommen. Stattdessen ein Administrator kann die Änderungen manuell anzuwenden mithilfe einer [ALTER FULLTEXT INDEX... START UPDATE POPULATION](/sql/t-sql/statements/alter-fulltext-index-transact-sql) Anweisung.|  
|**Änderungen nicht nachverfolgen**|Wenn diese Option aktiviert ist, werden Änderungen an den indizierten Daten im Katalog nicht aufgezeichnet. Ein Administrator muss den Index mithilfe von ALTER FULLTEXT INDEX mit FULL POPULATION oder INCREMENTAL POPULATION erstellen.|  
  
## <a name="see-also"></a>Siehe auch  
 [CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-catalog-transact-sql)   
 [ALTER FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-catalog-transact-sql)   
 [Auffüllen von Volltextindizes](../relational-databases/indexes/indexes.md)  
  
  
