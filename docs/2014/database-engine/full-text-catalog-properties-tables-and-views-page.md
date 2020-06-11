---
title: Voll Text Katalog-Eigenschaften (Seite "Tabellen und Sichten") | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.ftcatalogproperties.tablesviews.f1
ms.assetid: 2d45fcd2-0f0f-4167-9027-316d6696c106
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 205ee5d7c316c9a81e82edc0b2b6d132ed5c0ae1
ms.sourcegitcommit: 18a7c77be31f9af92ad9d0d3ac5eecebe8eec959
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/26/2020
ms.locfileid: "83858678"
---
# <a name="full-text-catalog-properties-tables-and-views-page"></a>Volltextkatalog-Eigenschaften (Seite „Tabellen und Sichten“)
  In diesem Dialogfeld können Sie die Tabellen und Sichten anzeigen oder bearbeiten, die dem Volltextkatalog zugewiesen sind.  
  
## <a name="ui-element-list"></a>Liste der Benutzeroberflächen Elemente  
 **Alle geeigneten Tabellen-/Sichtobjekte in dieser Datenbank**  
 Listet alle Tabellen und Sichten auf, für die ein eindeutiger Index definiert ist, die jedoch noch nicht Bestandteil des Volltextkatalogs sind. Wenn Sie eine Tabelle oder Sicht auswählen und dem Katalog zuweisen möchten, wählen Sie die Elemente im Listenfeld aus, und klicken Sie auf die Schaltfläche "->".  
  
 **Dem Katalog zugewiesene Tabellen-/Sichtobjekte**  
 Listet die Tabellen und Sichten auf, die zurzeit dem Volltextkatalog zugewiesen sind.  
  
## <a name="selected-object-properties"></a>Ausgewählte Objekteigenschaften  
 **Eigenschaften des ausgewählten Objekts**  
 Zeigt die Eigenschaften des ausgewählten Objekts im Listenfeld der dem Katalog zugewiesenen Objekte an.  
  
 **Eindeutiger Index**  
 Listet die verfügbaren eindeutigen Indizes der Tabelle oder Sicht auf.  
  
 **Die Tabelle ist volltextfähig.**  
 Aktivieren Sie dieses Kontrollkästchen, um den Volltextindex für die Tabelle zu aktivieren. Deaktivieren Sie das Kontrollkästchen, um den Volltextindex zu deaktivieren.  
  
## <a name="eligible-columns-grid"></a>Geeignetes Spaltenraster  
  
|||  
|-|-|  
|**Verfügbare Spalten**|Zeigt alle volltextindizierten Spalten an. Aktivieren Sie ein Kontrollkästchen, um eine Spalte zum Volltextindex hinzuzufügen.|  
|**Sprache für die Wörtertrennung**|Zeigt die Sprache des Worttrennmoduls an.|  
|**Datentypspalte**|Listet den Namen der Spalte in der Tabelle auf, die den Dokumenttyp der Spalte enthält, die in **Verfügbare Spalten** aufgelistet ist, wenn die Spalte eine- `varbinary(max)` oder-Spalte ist `image` .|  
|**Statistische Semantik**|Wählen Sie aus, ob die semantische Indizierung für die ausgewählte Spalte aktiviert werden soll. Weitere Informationen finden Sie unter [Semantische Suche &#40;SQL Server&#41;](../relational-databases/search/semantic-search-sql-server.md).<br /><br /> Wenn Sie eine **Sprache** vor der Option **Statistische Semantik**auswählen und die ausgewählte Sprache über kein zugeordnetes semantisches Sprachmodell verfügt, ist das Kontrollkästchen **Statistische Semantik** deaktiviert. Wenn Sie **Statistische Semantik** vor einer **Sprache**auswählen, werden im Dropdown-Kombinationsfeld nur die Sprachen angezeigt, für die das semantische Sprachmodell unterstützt wird.|  
  
## <a name="track-changes"></a>Nachverfolgen von Änderungen  
  
|||  
|-|-|  
|**Automatisch**|Der Volltextindex wird automatisch aktualisiert, wenn in der zugrunde liegenden Tabelle Daten geändert, hinzugefügt oder gelöscht werden.|  
|**Manuell**|Wenn indizierte Daten geändert, hinzugefügt oder gelöscht werden, protokolliert [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] die Änderungen. Wenn für die Nachverfolgung von Änderungen die Option **Manuell** aktiviert ist, werden die Änderungen nicht automatisch in den Index übernommen. Stattdessen kann ein Administrator die Änderungen manuell mithilfe einer [ALTER FULLTEXT INDEX ... START UPDATE POPULATION](/sql/t-sql/statements/alter-fulltext-index-transact-sql) -Anweisung anwenden.|  
|**Änderungen nicht nachverfolgen**|Wenn diese Option aktiviert ist, werden Änderungen an den indizierten Daten im Katalog nicht aufgezeichnet. Ein Administrator muss den Index mithilfe von ALTER FULLTEXT INDEX mit FULL POPULATION oder INCREMENTAL POPULATION erstellen.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-catalog-transact-sql)   
 [ALTER FULLTEXT CATALOG &#40;Transact-SQL-&#41;](/sql/t-sql/statements/alter-fulltext-catalog-transact-sql)   
 [Auffüllen von Volltextindizes](../relational-databases/indexes/indexes.md)  
  
  
