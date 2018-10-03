---
title: Sysdac_history_internal (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdac_history_internal
- sysdac_history_internal_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysdac_history_internal
ms.assetid: 774a1678-0b27-42be-8adc-a6d7a4a56510
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 40696085bc8eb9980d1150feade91a9edd627be0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47810387"
---
# <a name="data-tier-application-tables---sysdachistoryinternal"></a>Tabellen von Datenschichtanwendung: sysdac_history_internal
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enthält Informationen zu den Maßnahmen, die zur Verwaltung von Datenebenenanwendungen (DAC) ausgeführt werden. Diese Tabelle befindet sich in der **Dbo** Schema der **Msdb** Datenbank.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**action_id**|**int**|Bezeichner der Aktion|  
|**sequence_id**|**int**|Identifiziert einen Schritt innerhalb einer Aktion.|  
|**instance_id**|**uniqueidentifier**|Der Bezeichner der DAC-Instanz. Diese Spalte kann verknüpft werden, auf die **Instance_id** Spalte [dbo.sysdac_instances &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-tier-application-views-dbo-sysdac-instances.md).|  
|**action_type**|**tinyint**|Bezeichner des Aktionstyps:<br /><br /> **0** = bereitstellen<br /><br /> **1** = erstellen<br /><br /> **2** = umbenennen<br /><br /> **3** = trennen<br /><br /> **4** = löschen|  
|**action_type_name**|**h. varchar(19)**|Name des Aktionstyps:<br /><br /> **Bereitstellen**<br /><br /> **create**<br /><br /> **Umbenennen**<br /><br /> **Trennen**<br /><br /> **delete**|  
|**dac_object_type**|**tinyint**|Bezeichner des Typs des von der Aktion betroffenen Objekts:<br /><br /> **0** = DACPAC-Datei<br /><br /> **1** =-Anmeldung<br /><br /> **2** = Datenbank|  
|**dac_object_type_name**|**varchar(8)**|Name des Typs des von der Aktion betroffenen Objekts:<br /><br /> **DACPAC-Datei** = DAC-Instanz<br /><br /> **login**<br /><br /> **database**|  
|**action_status**|**tinyint**|Code, der den aktuellen Status der Aktion identifiziert:<br /><br /> **0** = ausstehend<br /><br /> **1** = Erfolg<br /><br /> **2** = Fehler|  
|**action_status_name**|**varchar(11)**|Aktueller Status der Aktion:<br /><br /> **Ausstehend**<br /><br /> **Erfolg**<br /><br /> **fail**|  
|**Erforderlich**|**bit**|Wird von [!INCLUDE[ssDE](../../includes/ssde-md.md)] verwendet, wenn das Rollback eines DAC-Vorgangs ausgeführt wird.|  
|**dac_object_name_pretran**|**sysname**|Name des Objekts, bevor ein Commit für die Transaktion ausgeführt wird, in der die Aktion enthalten ist. Wird nur für Datenbanken und Anmeldenamen verwendet.|  
|**dac_object_name_posttran**|**sysname**|Name des Objekts, nachdem ein Commit für die Transaktion ausgeführt wurde, in der die Aktion enthalten ist. Wird nur für Datenbanken und Anmeldenamen verwendet.|  
|**sqlscript**|**nvarchar(max)**|[!INCLUDE[tsql](../../includes/tsql-md.md)]-Skript, das eine Aktion für eine Datenbank oder einen Anmeldenamen implementiert.|  
|**Nutzlast**|**varbinary(max)**|DAC-Paketdefinition, die in einer binären codierten Zeichenfolge gespeichert ist.|  
|**Kommentare**|**varchar(max)**|Zeichnet die Anmeldung eines Benutzers auf, der potenziellen Datenverlust in einem DAC-Upgrade als akzeptabel angegeben hat.|  
|**error_string**|**nvarchar(max)**|Fehlermeldung, die im Fall eines Fehler generiert wird.|  
|**created_by**|**sysname**|Der Anmeldename, unter dem die Aktion, die diesen Eintrag erstellt hat, gestartet wurde.|  
|**date_created**|**datetime**|Datum und Uhrzeit, zu denen dieser Eintrag erstellt wurde.|  
|**date_modified**|**datetime**|Datum und Uhrzeit, zu denen der Eintrag zuletzt geändert wurde.|  
  
## <a name="remarks"></a>Hinweise  
 Durch DAC-Verwaltungsaktionen, z. B. das Bereitstellen oder Löschen einer DAC, werden mehrere Schritte generiert. Jeder Aktion wird ein Aktionsbezeichner zugewiesen. Jeder Schritt wird zugewiesen, eine Sequenznummer und eine Zeile in **Sysdac_history_internal**, wo der Status des Schritts aufgezeichnet wird. Die einzelnen Zeilen werden mit Beginn des Aktionsschritts erstellt und bei Bedarf aktualisiert, um dem Status des Vorgangs zu entsprechen. Beispielsweise kann ein DAC-Aktion "Bereitstellen" zugewiesen werden **Action_id** 12 und vier Zeilen in **Sysdac_history_internal**:  
  
|||||  
|-|-|-|-|  
|**action_id**|**sequence_id**|**action_type_name**|**dac_object_type_name**|  
|12|0|Erstellen|dacpac|  
|12|1|Erstellen|login|  
|12|2|Erstellen|Datenbank|  
|12|3|Umbenennen|Datenbank|  
  
 DAC-Vorgänge, z. B. löschen, entfernen Sie Zeilen aus nicht **Sysdac_history_internal**. Sie können die Zeilen für DACs, die nicht mehr in einer Instanz des [!INCLUDE[ssDE](../../includes/ssde-md.md)]s bereitgestellt werden, mithilfe der folgenden Abfrage manuell löschen:  
  
```sql  
DELETE FROM msdb.dbo.sysdac_history_internal  
WHERE instance_id NOT IN  
   (SELECT instance_id  
    FROM msdb.dbo.sysdac_instances_internal);  
```  
  
 Das Löschen von Zeilen für aktive DACs hat keinen Einfluss auf DAC-Vorgänge. Die einzige Auswirkung besteht darin, dass nicht der vollständige Verlauf für die DAC gemeldet werden kann.  
  
> [!NOTE]  
>  Derzeit steht kein Mechanismus zum Löschen von **Sysdac_history_internal** auf Zeilen [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Serverrolle sysadmin. Nur-Lese Zugriff auf diese Sicht ist für alle Benutzer mit Berechtigungen zum Verbinden mit der master-Datenbank verfügbar.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenebenenanwendungen](../../relational-databases/data-tier-applications/data-tier-applications.md)   
 [dbo.sysdac_instances &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-tier-application-views-dbo-sysdac-instances.md)   
 [sysdac_instances_internal &#40;Transact-SQL&#41;](../../relational-databases/system-tables/data-tier-application-tables-sysdac-instances-internal.md)  
  
  
