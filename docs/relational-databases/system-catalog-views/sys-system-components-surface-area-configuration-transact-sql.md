---
title: sys. system_components_surface_area_configuration (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.system_components_surface_area_configuration_TSQL
- system_components_surface_area_configuration
- system_components_surface_area_configuration_TSQL
- sys.system_components_surface_area_configuration
dev_langs:
- TSQL
helpviewer_keywords:
- sys.system_components_surface_area_configuration catalog view
ms.assetid: d9920008-3387-4f9e-8f21-47473f2ba04f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 665e73b3cd072bfffc214c518d75d96af3591f94
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68108875"
---
# <a name="syssystem_components_surface_area_configuration-transact-sql"></a>sys.system_components_surface_area_configuration (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt eine Zeile für jedes ausführbare Systemobjekt zurück, das von einer Komponente der Oberflächenkonfiguration aktiviert oder deaktiviert werden kann. Weitere Informationen finden Sie unter [Oberflächenkonfiguration](../../relational-databases/security/surface-area-configuration.md).  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**component_name**|**sysname**|Der Komponenten Name. Hierfür wird die Schlüsselwortsortierung Latin1_General_CI_AS_KS_WS verwendet. Lässt keine NULL-Werte zu.|  
|**database_name**|**sysname**|Die Datenbank, die das Objekt enthält. Hierfür wird die Schlüsselwortsortierung Latin1_General_CI_AS_KS_WS verwendet. Dies muss eine der folgenden Ressourcen sein:<br /><br /> **master**<br /><br /> **msdb**<br /><br /> **mssqlsystemresource**|  
|**schema_name**|**sysname**|Das Schema, das das Objekt enthält. Hierfür wird die Schlüsselwortsortierung Latin1_General_CI_AS_KS_WS verwendet. Lässt keine NULL-Werte zu.|  
|**object_name**|**sysname**|Name des Objekts. Hierfür wird die Schlüsselwortsortierung Latin1_General_CI_AS_KS_WS verwendet. Lässt keine NULL-Werte zu.|  
|**state**|**tinyint**|0 = Deaktiviert<br /><br /> 1 = Aktiviert|  
|**type**|**char (2)**|Objekttyp. Kann eines der folgenden Elemente sein:<br /><br /> P = SQL_STORED_PROCEDURE<br /><br /> PC = CLR_STORED_PROCEDURE<br /><br /> FN = SQL_SCALAR_FUNCTION<br /><br /> FS = CLR_SCALAR_FUNCTION<br /><br /> FT = CLR_TABLE_VALUED_FUNCTION<br /><br /> IF = SQL_INLINE_TABLE_VALUED_FUNCTION<br /><br /> TF = SQL_TABLE_VALUED_FUNCTION<br /><br /> X = EXTENDED_STORED_PROCEDURE|  
|**type_desc**|**nvarchar(60)**|Die Beschreibung für den Anzeigenamen des Objekttyps.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Sicherheits Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
