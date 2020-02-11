---
title: sp_setdefaultdatatypemapping (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: 9f0dfadc3b2b990d999df1d66069c4b68df9e6cf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68104413"
---
# <a name="sp_setdefaultdatatypemapping-transact-sql"></a>sp_setdefaultdatatypemapping (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Markiert eine vorhandene Datentyp Zuordnung zwischen [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und einem nicht- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database Management System (DBMS) als Standardwert. Diese gespeicherte Prozedur wird auf dem Verteiler für jede Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
`[ @mapping_id = ] mapping_id`Identifiziert eine vorhandene Datentyp Zuordnung.  *mapping_id* ist vom Datentyp **int**und hat den Standardwert NULL. Wenn Sie *mapping_id*angeben, sind die verbleibenden Parameter nicht erforderlich.  
  
`[ @source_dbms = ] 'source_dbms'`Der Name des DBMS, von dem die Datentypen zugeordnet werden. *source_dbms* ist vom **Datentyp vom Datentyp sysname**. die folgenden Werte sind möglich:  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**MSSQLSERVER**|Die Quelle ist eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank.|  
|**Orakel**|Die Quelle ist eine Oracle-Datenbank.|  
|NULL (Standard)||  
  
 Sie müssen diesen Parameter angeben, wenn *mapping_id* NULL ist.  
  
`[ @source_version = ] 'source_version'`Die Versionsnummer des Quell-DBMS. *source_version* ist vom Datentyp **varchar (10)** und hat den Standardwert NULL.  
  
`[ @source_type = ] 'source_type'`Der Datentyp im Quell-DBMS. *source_type* ist vom **Datentyp vom Datentyp sysname**. Sie müssen diesen Parameter angeben, wenn *mapping_id* NULL ist.  
  
`[ @source_length_min = ] source_length_min`Die minimale Länge des Datentyps im Quell-DBMS. *source_length_min* ist vom Datentyp **bigint**und hat den Standardwert NULL.  
  
`[ @source_length_max = ] source_length_max`Die maximale Länge des Datentyps im Quell-DBMS. *source_length_max* ist vom Datentyp **bigint**und hat den Standardwert NULL.  
  
`[ @source_precision_min = ] source_precision_min`Die minimale Genauigkeit des Datentyps im Quell-DBMS. *source_precision_min* ist vom Datentyp **bigint**und hat den Standardwert NULL.  
  
`[ @source_precision_max = ] source_precision_max`Die maximale Genauigkeit des Datentyps im Quell-DBMS. *source_precision_max* ist vom Datentyp **bigint**und hat den Standardwert NULL.  
  
`[ @source_scale_min = ] source_scale_min`Die minimale Skala des Datentyps im Quell-DBMS. *source_scale_min* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @source_scale_max = ] source_scale_max`Die maximale Skalierung des Datentyps im Quell-DBMS. *source_scale_max* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @source_nullable = ] source_nullable`Gibt an, ob der Datentyp im Quell-DBMS den Wert NULL unterstützt. *source_nullable* ist vom Typ **Bit**und hat den Standardwert NULL. **1** bedeutet, dass NULL-Werte unterstützt werden.  
  
`[ @destination_dbms = ] 'destination_dbms'`Der Name des Ziel-DBMS. *destination_dbms* ist vom **Datentyp vom Datentyp sysname**. die folgenden Werte sind möglich:  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**MSSQLSERVER**|Das Ziel ist eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank.|  
|**Orakel**|Das Ziel ist eine Oracle-Datenbank.|  
|**DB2**|Das Ziel ist eine IBM DB2-Datenbank.|  
|**Sybase**|Das Ziel ist eine Sybase-Datenbank.|  
|NULL (Standard)||  
  
`[ @destination_version = ] 'destination_version'`Die Produktversion des Ziel-DBMS. *destination_version* ist vom Datentyp **varchar (10)** und hat den Standardwert NULL.  
  
`[ @destination_type = ] 'destination_type'`Der im Ziel-DBMS aufgelistete Datentyp. *destination_type* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @destination_length = ] destination_length`Die Länge des Datentyps im Ziel-DBMS. *destination_length* ist vom Datentyp **bigint**und hat den Standardwert NULL.  
  
`[ @destination_precision = ] destination_precision`Die Genauigkeit des Datentyps im Ziel-DBMS. *destination_precision* ist vom Datentyp **bigint**und hat den Standardwert NULL.  
  
`[ @destination_scale = ] destination_scale`Die Skala des Datentyps im Ziel-DBMS. *destination_scale* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @destination_nullable = ] destination_nullable`Gibt an, ob der Datentyp im Ziel-DBMS den Wert NULL unterstützt. *destination_nullable* ist vom Typ **Bit**und hat den Standardwert NULL. **1** bedeutet, dass NULL-Werte unterstützt werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_setdefaultdatatypemapping** wird bei allen Replikations Typen zwischen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und einem nicht- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -DBMS verwendet.  
  
 Die standardmäßigen Datentypzuordnungen gelten für alle Replikationstopologien, die das angegebene DBMS enthalten.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** können **sp_setdefaultdatatypemapping**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Angeben von Datentyp Zuordnungen für einen Oracle-Verleger](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [sp_getdefaultdatatypemapping &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql.md)   
 [sp_helpdatatypemap &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql.md)  
  
  
