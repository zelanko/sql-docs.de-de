---
title: Sp_setdefaultdatatypemapping (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_setdefaultdatatypemapping
- sp_setdefaultdatatypemapping_TSQL
helpviewer_keywords:
- sp_setdefaultdatatypemapping
ms.assetid: 7394e8ca-4ce1-4e99-a784-205007c2c248
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e7d3ee86844f2b120c69e2cc2ddef55644cce8f2
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58538202"
---
# <a name="spsetdefaultdatatypemapping-transact-sql"></a>sp_setdefaultdatatypemapping (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Markiert eine vorhandene datentypzuordnung zwischen [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und einem nicht- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank-Managementsystem (DBMS) als Standardwert. Diese gespeicherte Prozedur wird auf dem Verteiler für jede Datenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_setdefaultdatatypemapping [ [ @mapping_id = ] mapping_id ]  
    [ , [ @source_dbms = ] 'source_dbms' ]  
    [ , [ @source_version = ] 'source_version' ]  
    [ , [ @source_type = ] 'source_type' ]   
    [ , [ @source_length_min = ] source_length_min ]  
    [ , [ @source_length_max = ] source_length_max ]  
    [ , [ @source_precision_min = ] source_precision_min ]  
    [ , [ @source_precision_max = ] source_precision_max ]  
    [ , [ @source_scale_min = ] source_scale_min ]  
    [ , [ @source_scale_max = ] source_scale_max ]  
    [ , [ @source_nullable = ] source_nullable ]  
    [ , [ @destination_dbms = ] 'destination_dbms' ]  
    [ , [ @destination_version = ] 'destination_version' ]  
    [ , [ @destination_type = ] 'destination_type' ]  
    [ , [ @destination_length = ] destination_length ]  
    [ , [ @destination_precision = ] destination_precision ]  
    [ , [ @destination_scale = ] destination_scale ]  
    [ , [ @destination_nullable = ] source_nullable ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @mapping_id = ] mapping_id` Identifiziert eine vorhandene datentypzuordnung.  *Mapping_id* ist **Int**, mit dem Standardwert NULL. Bei Angabe von *Mapping_id*, und klicken Sie dann die übrigen Parameter nicht erforderlich sind.  
  
`[ @source_dbms = ] 'source_dbms'` Ist der Name des DBMS aus dem die Datentypen zugeordnet werden. *Source_dbms* ist **Sysname**, und kann einen der folgenden Werte.  
  
|Wert|Description|  
|-----------|-----------------|  
|**MSSQLSERVER**|Die Quelle ist eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank.|  
|**ORACLE**|Die Quelle ist eine Oracle-Datenbank.|  
|NULL (Standard)||  
  
 Sie müssen diesen Parameter angeben, wenn *Mapping_id* ist NULL.  
  
`[ @source_version = ] 'source_version'` Ist die Versionsnummer des Quell-DBMS. *Source_version* ist **varchar(10)**, hat den Standardwert NULL.  
  
`[ @source_type = ] 'source_type'` Ist der Datentyp im Quell-DBMS. *Source_type* ist **Sysname**. Sie müssen diesen Parameter angeben, wenn *Mapping_id* ist NULL.  
  
`[ @source_length_min = ] source_length_min` Ist die minimale Länge des Datentyps im Quell-DBMS. *Source_length_min* ist **Bigint**, hat den Standardwert NULL.  
  
`[ @source_length_max = ] source_length_max` Ist die maximale Länge des Datentyps im Quell-DBMS. *Source_length_max* ist **Bigint**, hat den Standardwert NULL.  
  
`[ @source_precision_min = ] source_precision_min` Ist die minimale Genauigkeit des Datentyps im Quell-DBMS. *Source_precision_min* ist **Bigint**, hat den Standardwert NULL.  
  
`[ @source_precision_max = ] source_precision_max` Ist die maximale Genauigkeit des Datentyps im Quell-DBMS. *Source_precision_max* ist **Bigint**, hat den Standardwert NULL.  
  
`[ @source_scale_min = ] source_scale_min` Ist die minimale Dezimalstellen des Datentyps im Quell-DBMS. *Source_scale_min* ist **Int**, hat den Standardwert NULL.  
  
`[ @source_scale_max = ] source_scale_max` Ist die maximale Dezimalstellen des Datentyps im Quell-DBMS. *Source_scale_max* ist **Int**, hat den Standardwert NULL.  
  
`[ @source_nullable = ] source_nullable` Ist, wenn der Datentyp im Quell-DBMS einen NULL-Wert unterstützt. *Source_nullable* ist **Bit**, hat den Standardwert NULL. **1** bedeutet, dass NULL-Werte unterstützt werden.  
  
`[ @destination_dbms = ] 'destination_dbms'` Ist der Name des Ziel-DBMS. *Destination_dbms* ist **Sysname**, und kann einen der folgenden Werte.  
  
|Wert|Description|  
|-----------|-----------------|  
|**MSSQLSERVER**|Das Ziel ist eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank.|  
|**ORACLE**|Das Ziel ist eine Oracle-Datenbank.|  
|**DB2**|Das Ziel ist eine IBM DB2-Datenbank.|  
|**SYBASE**|Das Ziel ist eine Sybase-Datenbank.|  
|NULL (Standard)||  
  
`[ @destination_version = ] 'destination_version'` Ist die Produktversion des Ziel-DBMS. *Destination_version* ist **varchar(10)**, hat den Standardwert NULL.  
  
`[ @destination_type = ] 'destination_type'` Im Ziel-DBMS aufgelistete Datentyp. *Destination_type* ist **Sysname**, hat den Standardwert NULL.  
  
`[ @destination_length = ] destination_length` Ist die Länge des Datentyps im Ziel-DBMS. *Destination_length* ist **Bigint**, hat den Standardwert NULL.  
  
`[ @destination_precision = ] destination_precision` Ist die Genauigkeit des Datentyps im Ziel-DBMS. *Destination_precision* ist **Bigint**, hat den Standardwert NULL.  
  
`[ @destination_scale = ] destination_scale` Sind keine Dezimalstellen des Datentyps im Ziel-DBMS. *Destination_scale* ist **Int**, hat den Standardwert NULL.  
  
`[ @destination_nullable = ] destination_nullable` Ist, wenn der Datentyp im Ziel-DBMS einen NULL-Wert unterstützt. *Destination_nullable* ist **Bit**, hat den Standardwert NULL. **1** bedeutet, dass NULL-Werte unterstützt werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_setdefaultdatatypemapping** werden in allen Replikationstypen zwischen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und einem nicht- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DBMS.  
  
 Die standardmäßigen Datentypzuordnungen gelten für alle Replikationstopologien, die das angegebene DBMS enthalten.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Sysadmin** feste Serverrolle **Sp_setdefaultdatatypemapping**.  
  
## <a name="see-also"></a>Siehe auch  
 [Angeben von Datentypzuordnungen für einen Oracle-Verleger](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [sp_getdefaultdatatypemapping &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql.md)   
 [sp_helpdatatypemap &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql.md)  
  
  
