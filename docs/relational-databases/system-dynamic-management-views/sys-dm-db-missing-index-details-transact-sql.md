---
title: sys. dm_db_missing_index_details (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_db_missing_index_details
- dm_db_missing_index_details
- sys.dm_db_missing_index_details_TSQL
- dm_db_missing_index_details_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- missing indexes feature [SQL Server], sys.dm_db_missing_index_details dynamic management view
- sys.dm_db_missing_index_details dynamic management view
ms.assetid: ced484ae-7c17-4613-a3f9-6d8aba65a110
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 77b3faae57764a936e6115d22ac00ca855d3acb9
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82829435"
---
# <a name="sysdm_db_missing_index_details-transact-sql"></a>sys.dm_db_missing_index_details (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt detaillierte Informationen zu fehlenden Indizes, außer räumlichen Indizes, zurück.  
  
 In [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]können dynamische Verwaltungssichten keine Informationen verfügbar machen, die sich auf die Datenbankkapselung auswirken würden oder die sich auf andere Datenbanken beziehen, auf die der Benutzer Zugriff hat. Um zu vermeiden, dass diese Informationen verfügbar gemacht werden, wird jede Zeile, die Daten enthält, die nicht zum verbundenen Mandanten gehören, herausgefiltert.  

  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**index_handle**|**int**|Identifiziert einen bestimmten fehlenden Index. Der Bezeichner ist innerhalb des Servers eindeutig. **index_handle** ist der Schlüssel dieser Tabelle.|  
|**database_id**|**smallint**|Identifiziert die Datenbank, in der sich die Tabelle mit dem fehlenden Index befindet.|  
|**object_id**|**int**|Identifiziert die Tabelle, in der der Index fehlt.|  
|**equality_columns**|**nvarchar(4000)**|Durch Trennzeichen getrennte Liste von Spalten, die zu Gleichheitsprädikaten der folgenden Form beitragen:<br /><br /> *Table. Column*  = *constant_value*|  
|**inequality_columns**|**nvarchar(4000)**|Durch Trennzeichen getrennte Liste von Spalten, die zu Ungleichheitsprädikaten beispielsweise der folgenden Form beitragen:<br /><br /> *Table. Column*  >  *constant_value*<br /><br /> Jeder Vergleichsoperator außer "=" drückt Ungleichheit aus.|  
|**included_columns**|**nvarchar(4000)**|Durch Trennzeichen getrennte Liste von Spalten, die zur Abdeckung der Abfrage benötigt werden. Weitere Informationen zum abdecken oder einschließen von Spalten finden Sie unter [Erstellen von Indizes mit eingebundenen Spalten](../../relational-databases/indexes/create-indexes-with-included-columns.md).<br /><br /> Ignorieren Sie für Speicher optimierte Indizes (sowohl Hash als auch Speicher optimiertes Nonclustered) **included_columns**. Alle Spalten der Tabelle werden in jeden speicheroptimierten Index eingeschlossen.|  
|**statement**|**nvarchar(4000)**|Der Name der Tabelle, in der der Index fehlt.|  
  
## <a name="remarks"></a>Bemerkungen  
 Die von **sys.dm_db_missing_index_details** zurückgegebenen Informationen werden aktualisiert, wenn eine Abfrage vom Abfrageoptimierer optimiert wird, und sind nicht persistent. Informationen zu fehlenden Indizes werden nur bis zum Neustart von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aufbewahrt. Datenbankadministratoren sollten regelmäßig Sicherungskopien der Informationen zu fehlenden Indizes erstellen, wenn Sie sie nach dem Wiederverwenden des Servers beibehalten möchten.  
  
 Zum Bestimmen der Gruppen fehlender Indizes, denen ein bestimmter fehlender Index angehört, können Sie die dynamische Verwaltungssicht **sys.dm_db_missing_index_groups** abfragen, indem Sie sie in einem auf der **index_handle**-Spalte basierenden Gleichheitsjoin mit **sys.dm_db_missing_index_details** verknüpfen.  

  >[!NOTE]
  >Das Resultset für diese DMV ist auf 600 Zeilen beschränkt. Jede Zeile enthält einen fehlenden Index. Wenn Sie über mehr als 600 fehlende Indizes verfügen, sollten Sie die vorhandenen fehlenden Indizes ansprechen, damit Sie die neueren Indizes anzeigen können. 
  
## <a name="using-missing-index-information-in-create-index-statements"></a>Verwenden von Informationen zu fehlenden Indizes in CREATE INDEX-Anweisungen  
 Um die von **sys. dm_db_missing_index_details** zurückgegebenen Informationen in eine CREATE INDEX-Anweisung für Speicher optimierte und Datenträger basierte Indizes zu konvertieren, sollten Gleichheits Spalten vor die Ungleichheits Spalten eingefügt werden, und Sie sollten die Schlüssel des Indexes bilden. Eingeschlossene Spalten sollten der CREATE INDEX-Anweisung mithilfe der INCLUDE-Klausel hinzugefügt werden. Für eine effektive Reihenfolge der Gleichheitsspalten sortieren Sie sie nach ihrer Selektivität, wobei Sie die ausgewählten Spalten zuerst (am weitesten links in der Spaltenliste) aufführen.  
  
 Weitere Informationen zu Speicher optimierten Indizes finden Sie unter [Indizes für Speicher optimierte Tabellen](../../relational-databases/in-memory-oltp/indexes-for-memory-optimized-tables.md).  
  
## <a name="transaction-consistency"></a>Transaktionskonsistenz  
 Wenn durch eine Transaktion eine Tabelle erstellt oder gelöscht wird, werden die Zeilen mit Informationen zu fehlenden Indizes bezüglich der gelöschten Objekte aus diesem dynamischen Verwaltungsobjekt entfernt, damit die Transaktionskonsistenz erhalten bleibt.  
  
## <a name="permissions"></a>Berechtigungen

In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ist die- `VIEW SERVER STATE` Berechtigung erforderlich.   
Bei [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium-Tarifen ist die- `VIEW DATABASE STATE` Berechtigung in der Datenbank erforderlich. In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] den Tarifen "Standard" und "Basic" ist der **Server Administrator** oder ein **Azure Active Directory Administrator** Konto erforderlich.   

## <a name="see-also"></a>Weitere Informationen  
 [sys. dm_db_missing_index_columns &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-columns-transact-sql.md)   
 [sys. dm_db_missing_index_groups &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-groups-transact-sql.md)   
 [sys. dm_db_missing_index_group_stats &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-group-stats-transact-sql.md)  
  
  
