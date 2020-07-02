---
title: sys. File Groups (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/24/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.filegroups_TSQL
- filegroups
- sys.filegroups
- filegroups_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.filegroups catalog view
ms.assetid: 9e851f72-1f8e-4515-a25d-152ebc12ed56
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6b676878f0e42e57d5a6081ce927ca9892e3e62c
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85754464"
---
# <a name="sysfilegroups-transact-sql"></a>sys.filegroups (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asdw-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  Enthält eine Zeile für jeden Datenspeicher, der einer Dateigruppe entspricht.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**\<inherited columns>**|--|Eine Liste der Spalten, die diese Sicht erbt, finden Sie unter [sys. data_spaces &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md).|  
|**filegroup_guid**|**uniqueidentifier**|GUID für die Dateigruppe.<br /><br /> NULL = PRIMARY-Dateigruppe|  
|**log_filegroup_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist der Wert NULL.|  
|**is_read_only**|**bit**|1 = Die Dateigruppe ist schreibgeschützt.<br /><br /> 0 = Auf die Dateigruppe besteht Lese-/Schreibzugriff.|  
|**is_autogrow_all_files**|**bit**|**Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ( [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis zur [aktuellen Version](https://go.microsoft.com/fwlink/p/?LinkId=299658)).<br /><br /> 1 = Wenn eine Datei in der Datei Gruppe den Schwellenwert für die automatische Vergrößerung erreicht, werden alle Dateien in der Datei Gruppe vergrößert.<br /><br /> 0 = wenn eine Datei in der Datei Gruppe den Schwellenwert für die automatische Vergrößerung erreicht, wird nur diese Datei vergrößert. Dies ist die Standardeinstellung.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle. Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Datenbereiche &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/data-spaces-transact-sql.md)  
  
  
