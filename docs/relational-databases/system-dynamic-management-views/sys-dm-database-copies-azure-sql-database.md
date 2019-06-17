---
title: Sys. dm_database_copies (Azure SQL-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- dm_database_copies_TSQL
- sys.dm_database_copies
- dm_database_copies
- sys.dm_database_copies_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dm_database_copies
- sys.dm_database_copies
ms.assetid: d03d4657-86d1-4496-97e6-cc3bc292e0b1
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 6b5a0a656693d66e701642c9c2202c2862136a54
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62741956"
---
# <a name="sysdmdatabasecopies-azure-sql-database"></a>sys.dm_database_copies (Azure SQL-Datenbank)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Gibt Informationen über das Kopieren der Datenbank zurück.  
  
Um Informationen zu georeplikationsverknüpfungen zurückzugeben, verwenden die [Sys. geo_replication_links](../../relational-databases/system-dynamic-management-views/sys-geo-replication-links-azure-sql-database.md) oder [dm_geo_replication_link_status](../../relational-databases/system-dynamic-management-views/sys-dm-geo-replication-link-status-azure-sql-database.md) Ansichten (in SQL-Datenbank V12 verfügbar).
  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|Die ID der aktuellen Datenbank in der `sys.databases`-Sicht.|  
|**start_date**|**datetimeoffset**|Die UTC-Zeit in einem regionalen [!INCLUDE[ssSDS](../../includes/sssds-md.md)]-Datencenter, zu der das Kopieren der Datenbank initiiert wurde.|  
|**modify_date**|**datetimeoffset**|Die UTC-Zeit im regionalen [!INCLUDE[ssSDS](../../includes/sssds-md.md)]-Datencenter, zu der das Kopieren der Datenbank abgeschlossen wurde. Die neue Datenbank ist ab diesem Zeitpunkt im Hinblick auf Transaktionen konsistent mit der primären Datenbank. Die Informationen über den Abschluss wird jede Minute aktualisiert.<br /><br />UTC-Zeit die letzte Aktualisierung des Felds Percent_complete widerspiegelt.|  
|**percent_complete**|**real**|Der Prozentsatz der kopierten Bytes. Werte zwischen 0 und 100 liegen. [!INCLUDE[ssSDS](../../includes/sssds-md.md)] wird nach einigen Fehlern wie Failovern u. U. automatisch weiter ausgeführt und startet das Kopieren der Datenbank erneut. In diesem Fall würde percent_complete bei 0 neu starten.|  
|**error_code**|**int**|Wenn der Wert größer als 0 ist, gibt der Code den Fehler an, der beim Kopieren aufgetreten ist. Der Wert ist gleich 0, wenn keine Fehler aufgetreten sind.|  
|**error_desc**|**nvarchar(4096)**|Beschreibung des Fehlers, der beim Kopieren aufgetreten ist.|  
|**error_severity**|**int**|Gibt 16 zurück, wenn das Kopieren der Datenbank fehlgeschlagen ist.|  
|**error_state**|**int**|Gibt 1 zurück, wenn der Kopiervorgang fehlgeschlagen ist.|  
|**copy_guid**|**uniqueidentifier**|Eindeutige ID des Vorgangs zum Kopieren.|  
|**partner_server**|**sysname**|Name der SQL-Datenbankserver, in dem die Kopie erstellt wird.|  
|**partner_database**|**sysname**|Der Name der Datenbankkopie auf dem Partnerserver.|  
|**replication_state**|**tinyint**|Der Status der fortlaufenden kopierbeziehung für diese Datenbank. Die Werte sind:<br /><br /> 0 = ausstehend. Erstellung der Datenbank geplant ist, aber die notwendigen Vorbereitungsschritte sind noch nicht abgeschlossen oder vorübergehend durch das seedingkontingent blockiert sind.<br /><br /> 1 = Seeding. Die Kopie der Datenbank das Seeding wird noch nicht vollständig mit der Quelldatenbank synchronisiert. In diesem Zustand können keine Sie mit der Kopie verbinden. Um den Seedingvorgang in Bearbeitung abbrechen, muss die Kopie der Datenbank gelöscht werden.|  
|**replication_state_desc**|**nvarchar(256)**|Beschreibung von replication_state. Folgende Werte sind möglich:<br /><br /> PENDING<br /><br /> SEEDING<br />|  
|**maximum_lag**|**int**|Reserviertes Feld.|  
|**is_continuous_copy**|**bit**|0 = gibt 0 zurück|  
|**is_target_role**|**bit**|0 = der Quelldatenbank<br /><br /> 1 = Datenbank kopieren|  
|**is_interlink_connected**|bit|Reserviertes Feld.|  
|**is_offline_secondary**|bit|Reserviertes Feld.|  
  
## <a name="permissions"></a>Berechtigungen  
 Diese Ansicht ist nur verfügbar, in der **master** Datenbank, um die prinzipalanmeldung auf Serverebene.  
  
## <a name="remarks"></a>Hinweise  
 Können Sie die **Sys. dm_database_copies** anzeigen in der **master** Datenbank Quelle oder Ziel [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Server. Beim Kopieren der Datenbank erfolgreich abgeschlossen wurde und die neue Datenbank ONLINE ist, wird die Zeile in der **Sys. dm_database_copies** -Sicht automatisch entfernt.  
  
  
