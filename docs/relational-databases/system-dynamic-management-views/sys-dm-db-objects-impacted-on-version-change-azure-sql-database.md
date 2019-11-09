---
title: sys. dm_db_objects_impacted_on_version_change
titleSuffix: Azure SQL Database
ms.date: 03/03/2017
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_db_objects_impacted_on_version_change_TSQL
- dm_db_objects_impacted_on_version_change
- dm_db_objects_impacted_on_version_change_TSQL
- sys.dm_db_objects_impacted_on_version_change
dev_langs:
- TSQL
helpviewer_keywords:
- dm_db_objects_impacted_on_version_change
- sys.dm_db_objects_impacted_on_version_change
ms.assetid: b94af834-c4f6-4a27-80a6-e8e71fa8793a
author: stevestein
ms.author: sstein
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.custom: seo-dt-2019
ms.openlocfilehash: 0255f7260044ee5c09d020f3ba6310d24bc8cb74
ms.sourcegitcommit: f688a37bb6deac2e5b7730344165bbe2c57f9b9c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/08/2019
ms.locfileid: "73843864"
---
# <a name="sysdm_db_objects_impacted_on_version_change-azure-sql-database"></a>sys.dm_db_objects_impacted_on_version_change (Azure SQL-Datenbank)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Diese datenbankbezogene Systemsicht wurde entworfen, um ein Frühwarnsystem bereitzustellen, mit dem Objekte ermittelt werden sollen, die von einem Upgrade der Hauptversion in [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] betroffen sein werden. Sie können die Sicht entweder vor oder nach dem Upgrade verwenden, um eine vollständige Enumeration der betroffenen Objekte abzurufen. Sie müssen diese Sicht in jeder Datenbank abfragen, damit der gesamte Server berücksichtigt wird.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|class|**int** nicht NULL|Die Klasse des Objekts, das betroffen sein wird:<br /><br /> **1** = Einschränkung<br /><br /> **7** = Indizes und Heaps|  
|class_desc|**nvarchar (60)** nicht NULL|Beschreibung der Klasse:<br /><br /> **OBJECT_OR_COLUMN**<br /><br /> **INDEX**|  
|major_id|**int** nicht NULL|Objekt-ID der Einschränkung oder Objekt-ID der Tabelle, die den Index oder Heap enthält.|  
|minor_id|**int** Normal|**Null** für Einschränkungen<br /><br /> Index_id für Indizes und Heaps|  
|Abhängigkeit|**nvarchar (60)** nicht NULL|Beschreibung der Abhängigkeit, die bewirkt, dass die Einschränkung oder der Index betroffen sind. Derselbe Wert wird auch für Warnungen verwendet, die während des Upgrades generiert werden.<br /><br /> Beispiele:<br /><br /> **Leerraum** (für intrinsisch)<br /><br /> **Geometrie** (für System-UDT)<br /><br /> **Geography::P Arse** (für System-UDT-Methode)|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW DATABASE STATE-Berechtigung.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt eine Abfrage für **sys. dm_db_objects_impacted_on_version_change** , um die Objekte zu finden, die von einem Upgrade auf die nächste Hauptserver Version betroffen sind.  
  
```  
SELECT * FROM sys.dm_db_objects_disabled_on_version_change;  
GO  
```  
  
```  
class  class_desc        major_id    minor_id    dependency                       
------ ----------------- ----------- ----------- ----------   
1      OBJECT_OR_COLUMN  181575685   NULL        geometry                        
7      INDEX             37575172    1           geometry                        
7      INDEX             2121058592  1           geometry                        
1      OBJECT_OR_COLUMN  101575400   NULL        geometry     
```  
  
## <a name="remarks"></a>Hinweise  
  
### <a name="how-to-update-impacted-objects"></a>Aktualisieren betroffener Objekte  
 Die folgenden Schritte beschreiben die Korrekturmaßnahmen, die Sie nach dem bevorstehenden Serviceupgrade im Juni durchführen sollten.  
  
|Order|Betroffenes Objekt|Korrekturmaßnahme|  
|-----------|---------------------|-----------------------|  
|1|**Indizes**|Erstellen Sie jeden durch **sys. dm_db_objects_impacted_on_version_change** identifizierten Index neu. Beispiel: `ALTER INDEX ALL ON <table> REBUILD`<br />\- oder<br />`ALTER TABLE <table> REBUILD`|  
|2|**Objekt**|Alle Einschränkungen, die von **sys. dm_db_objects_impacted_on_version_change** identifiziert werden, müssen erneut überprüft werden, nachdem die Geometry-und geography-Daten in der zugrunde liegenden Tabelle neu berechnet wurden. Führen Sie die erneute Überprüfung für Einschränkungen mithilfe von ALTER TABLE durch. <br />Beispiel: <br />`ALTER TABLE <tab> WITH CHECK CHECK CONSTRAINT <constraint name>`<br />\- oder<br />`ALTER TABLE <tab> WITH CHECK CONSTRAINT ALL`|  
  
  
