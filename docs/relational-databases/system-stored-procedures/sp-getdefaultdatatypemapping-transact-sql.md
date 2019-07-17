---
title: Sp_getdefaultdatatypemapping (Transact-SQL) | Microsoft-Dokumentation
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
author: stevestein
ms.author: sstein
ms.openlocfilehash: 32fe9edf5c3d8621046a27937d83f642b1689d1a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68123992"
---
# <a name="spgetdefaultdatatypemapping-transact-sql"></a>sp_getdefaultdatatypemapping (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Informationen zurück, auf die standardzuordnung für den angegebenen Datentyp zwischen [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und einem nicht- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank-Managementsystem (DBMS). Diese gespeicherte Prozedur wird auf dem Verteiler für jede Datenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
`[ @source_dbms = ] 'source_dbms'` Ist der Name des DBMS aus dem die Datentypen zugeordnet werden. *Source_dbms* ist **Sysname**, und kann einen der folgenden Werte:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**MSSQLSERVER**|Die Quelle ist eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank.|  
|**ORACLE**|Die Quelle ist eine Oracle-Datenbank.|  
  
 Sie müssen diesen Parameter festlegen.  
  
`[ @source_version = ] 'source_version'` Ist die Versionsnummer des Quell-DBMS. *Source_version* ist **varchar(10)** , hat den Standardwert NULL.  
  
`[ @source_type = ] 'source_type'` Ist der Datentyp im Quell-DBMS. *Source_type* ist **Sysname**, hat keinen Standardwert.  
  
`[ @source_length = ] source_length` Ist die Länge des Datentyps im Quell-DBMS. *Source_length* ist **Bigint**, hat den Standardwert NULL.  
  
`[ @source_precision = ] source_precision` Ist die Genauigkeit des Datentyps im Quell-DBMS. *Source_precision* ist **Bigint**, hat den Standardwert NULL.  
  
`[ @source_scale = ] source_scale` Sind keine Dezimalstellen des Datentyps im Quell-DBMS. *Source_scale* ist **Int**, hat den Standardwert NULL.  
  
`[ @source_nullable = ] source_nullable` Ist, wenn der Datentyp im Quell-DBMS einen NULL-Wert unterstützt. *Source_nullable* ist **Bit**, hat den Standardwert des **1**, was bedeutet, dass NULL-Werte unterstützt werden.  
  
`[ @destination_dbms = ] 'destination_dbms'` Ist der Name des Ziel-DBMS. *Destination_dbms* ist **Sysname**, und kann einen der folgenden Werte:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**MSSQLSERVER**|Das Ziel ist eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank.|  
|**ORACLE**|Das Ziel ist eine Oracle-Datenbank.|  
|**DB2**|Das Ziel ist eine IBM DB2-Datenbank.|  
|**SYBASE**|Das Ziel ist eine Sybase-Datenbank.|  
  
 Sie müssen diesen Parameter festlegen.  
  
`[ @destination_version = ] 'destination_version'` Ist die Produktversion des Ziel-DBMS. *Destination_version* ist **varchar(10)** , hat den Standardwert NULL.  
  
`[ @destination_type = ] 'destination_type' OUTPUT` Im Ziel-DBMS aufgelistete Datentyp. *Destination_type* ist **Sysname**, hat den Standardwert NULL.  
  
`[ @destination_length = ] destination_length OUTPUT` Ist die Länge des Datentyps im Ziel-DBMS. *Destination_length* ist **Bigint**, hat den Standardwert NULL.  
  
`[ @destination_precision = ] destination_precision OUTPUT` Ist die Genauigkeit des Datentyps im Ziel-DBMS. *Destination_precision* ist **Bigint**, hat den Standardwert NULL.  
  
`[ @destination_scale = ] _destination_scaleOUTPUT` Sind keine Dezimalstellen des Datentyps im Ziel-DBMS. *Destination_scale* ist **Int**, hat den Standardwert NULL.  
  
`[ @destination_nullable = ] _destination_nullableOUTPUT` Ist, wenn der Datentyp im Ziel-DBMS einen NULL-Wert unterstützt. *Destination_nullable* ist **Bit**, hat den Standardwert NULL. **1** bedeutet, dass NULL-Werte unterstützt werden.  
  
`[ @dataloss = ] _datalossOUTPUT` Ist, wenn die Zuordnung der potenzielle Datenverlust ist. *Datenverlust* ist **Bit**, hat den Standardwert NULL. **1** bedeutet, dass es besteht die Gefahr von Datenverlusten.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_getdefaultdatatypemapping** werden in allen Replikationstypen zwischen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und einem nicht- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DBMS.  
  
 **Sp_getdefaultdatatypemapping** gibt zurück, die Standarddaten für die Ziel-Typ, die bestmögliche Übereinstimmung in den Datentyp der angegebenen Quelle.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Sysadmin** feste Serverrolle **Sp_getdefaultdatatypemapping**.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_helpdatatypemap &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql.md)   
 [sp_setdefaultdatatypemapping &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-setdefaultdatatypemapping-transact-sql.md)   
 [Data Type Mapping for Oracle Publishers](../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md)   
 [IBM DB2 Subscribers](../../relational-databases/replication/non-sql/ibm-db2-subscribers.md)   
 [Oracle-Abonnenten](../../relational-databases/replication/non-sql/oracle-subscribers.md)  
  
  
