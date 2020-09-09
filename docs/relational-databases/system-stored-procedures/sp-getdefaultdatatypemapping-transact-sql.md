---
description: sp_getdefaultdatatypemapping (Transact-SQL)
title: sp_getdefaultdatatypemapping (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_getdefaultdatatypemapping_TSQL
- sp_getdefaultdatatypemapping
helpviewer_keywords:
- sp_getdefaultdatatypemapping
ms.assetid: b8401de1-f135-41d0-ba79-ce8fe1f48c00
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 6d7737d0c4d8d44901da52bad6ad6867d7080554
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89543337"
---
# <a name="sp_getdefaultdatatypemapping-transact-sql"></a>sp_getdefaultdatatypemapping (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt Informationen zur Standard Zuordnung für den angegebenen Datentyp zwischen [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und einem nicht- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database Management System (DBMS) zurück. Diese gespeicherte Prozedur wird auf dem Verteiler für jede Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_getdefaultdatatypemapping [ @source_dbms = ] 'source_dbms'   
    [ , [ @source_version = ] 'source_version' ]  
        , [ @source_type = ] 'source_type'    
    [ , [ @source_length = ] source_length ]  
    [ , [ @source_precision = ] source_precision ]  
    [ , [ @source_scale = ] source_scale ]  
    [ , [ @source_nullable = ] source_nullable ]  
        , [ @destination_dbms = ] 'destination_dbms'   
    [ , [ @destination_version = ] 'destination_version' ]  
    [ , [ @destination_type = ] 'destination_type' OUTPUT ]  
    [ , [ @destination_length = ] destination_length OUTPUT ]  
    [ , [ @destination_precision = ] destination_precision OUTPUT ]  
    [ , [ @destination_scale = ] destination_scale OUTPUT ]  
    [ , [ @destination_nullable = ] source_nullable OUTPUT ]  
    [ , [ @dataloss = ] dataloss OUTPUT ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @source_dbms = ] 'source_dbms'` Der Name des DBMS, von dem die Datentypen zugeordnet werden. *source_dbms* ist vom **Datentyp vom Datentyp sysname**. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**MSSQLSERVER**|Die Quelle ist eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank.|  
|**Orakel**|Die Quelle ist eine Oracle-Datenbank.|  
  
 Sie müssen diesen Parameter festlegen.  
  
`[ @source_version = ] 'source_version'` Die Versionsnummer des Quell-DBMS. *source_version* ist vom Datentyp **varchar (10)** und hat den Standardwert NULL.  
  
`[ @source_type = ] 'source_type'` Der Datentyp im Quell-DBMS. *source_type* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @source_length = ] source_length` Die Länge des Datentyps im Quell-DBMS. *source_length* ist vom Datentyp **bigint**und hat den Standardwert NULL.  
  
`[ @source_precision = ] source_precision` Die Genauigkeit des Datentyps im Quell-DBMS. *source_precision* ist vom Datentyp **bigint**und hat den Standardwert NULL.  
  
`[ @source_scale = ] source_scale` Die Skala des Datentyps im Quell-DBMS. *source_scale* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @source_nullable = ] source_nullable` Gibt an, ob der Datentyp im Quell-DBMS den Wert NULL unterstützt. *source_nullable* ist vom Typ **Bit**und hat den Standardwert **1**. Dies bedeutet, dass NULL-Werte unterstützt werden.  
  
`[ @destination_dbms = ] 'destination_dbms'` Der Name des Ziel-DBMS. *destination_dbms* ist vom **Datentyp vom Datentyp sysname**. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**MSSQLSERVER**|Das Ziel ist eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank.|  
|**Orakel**|Das Ziel ist eine Oracle-Datenbank.|  
|**DB2**|Das Ziel ist eine IBM DB2-Datenbank.|  
|**Sybase**|Das Ziel ist eine Sybase-Datenbank.|  
  
 Sie müssen diesen Parameter festlegen.  
  
`[ @destination_version = ] 'destination_version'` Die Produktversion des Ziel-DBMS. *destination_version* ist vom Datentyp **varchar (10)** und hat den Standardwert NULL.  
  
`[ @destination_type = ] 'destination_type' OUTPUT` Der im Ziel-DBMS aufgelistete Datentyp. *destination_type* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @destination_length = ] destination_length OUTPUT` Die Länge des Datentyps im Ziel-DBMS. *destination_length* ist vom Datentyp **bigint**und hat den Standardwert NULL.  
  
`[ @destination_precision = ] destination_precision OUTPUT` Die Genauigkeit des Datentyps im Ziel-DBMS. *destination_precision* ist vom Datentyp **bigint**und hat den Standardwert NULL.  
  
`[ @destination_scale = ] _destination_scaleOUTPUT` Die Skala des Datentyps im Ziel-DBMS. *destination_scale* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @destination_nullable = ] _destination_nullableOUTPUT` Gibt an, ob der Datentyp im Ziel-DBMS den Wert NULL unterstützt. *destination_nullable* ist vom Typ **Bit**und hat den Standardwert NULL. **1** bedeutet, dass NULL-Werte unterstützt werden.  
  
`[ @dataloss = ] _datalossOUTPUT` Gibt an, ob die Zuordnung das Potenzial eines Daten Verlusts hat. *Datenverlust ist vom Datenverlust* **Bit**und hat den Standardwert NULL. **1** bedeutet, dass ein Datenverlust möglich ist.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_getdefaultdatatypemapping** wird bei allen Replikations Typen zwischen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und einem nicht-- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DBMS verwendet.  
  
 **sp_getdefaultdatatypemapping** gibt den standardmäßigen Ziel Datentyp zurück, der dem angegebenen Quell Datentyp am ehesten entspricht.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** können **sp_getdefaultdatatypemapping**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_helpdatatypemap &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql.md)   
 [sp_setdefaultdatatypemapping &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-setdefaultdatatypemapping-transact-sql.md)   
 [Data Type Mapping for Oracle Publishers](../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md)   
 [IBM DB2 Subscribers](../../relational-databases/replication/non-sql/ibm-db2-subscribers.md)   
 [Oracle Subscribers](../../relational-databases/replication/non-sql/oracle-subscribers.md)  
  
  
