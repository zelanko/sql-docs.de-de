---
title: sp_helpdatatypemap (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpdatatypemap
- sp_helpdatatypemap_TSQL
helpviewer_keywords:
- sp_helpdatatypemap
ms.assetid: 800c9c65-723e-4961-a63d-327987f129f0
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 61229514cb837a40537b6a363d2ebba81a5cef5a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85786862"
---
# <a name="sp_helpdatatypemap-transact-sql"></a>sp_helpdatatypemap (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Gibt Informationen zu den definierten Datentyp Zuordnungen zwischen [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und nicht- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database Management Systems (DBMS) zurück. Diese gespeicherte Prozedur wird auf dem Verteiler für jede Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpdatatypemap [ @source_dbms = ] 'source_dbms'   
    [ , [ @source_version = ] 'source_version' ]  
    [ , [ @source_type = ] 'source_type' ]   
    [ , [ @destination_dbms = ] 'destination_dbms' ]  
    [ , [ @destination_version = ] 'destination_version' ]  
    [ , [ @destination_type = ] 'destination_type' ]  
    [ , [ @defaults_only = ] defaults_only ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @source_dbms = ] 'source_dbms'`Der Name des DBMS, von dem die Datentypen zugeordnet werden. *source_dbms* ist vom **Datentyp vom Datentyp sysname**. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**MSSQLSERVER**|Die Quelle ist eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank.|  
|**Orakel**|Die Quelle ist eine Oracle-Datenbank.|  
  
`[ @source_version = ] 'source_version'`Die Produktversion des Quell-DBMS. *source_version*ist vom Datentyp **varchar (10)**. Wenn kein Wert angegeben wird, werden die Datentyp Zuordnungen für alle Versionen des Quell-DBMS zurückgegeben. Ermöglicht das Filtern des Resultsets nach der Quellversion des DBMS.  
  
`[ @source_type = ] 'source_type'`Der im Quell-DBMS aufgelistete Datentyp. *source_type* ist vom **Datentyp vom Datentyp sysname**. Wenn kein Wert angegeben wird, werden die Zuordnungen für alle Datentypen im Quell-DBMS zurückgegeben. Ermöglicht das Filtern des Resultsets nach dem Datentyp im Quell-DBMS.  
  
`[ @destination_dbms = ] 'destination_dbms'`Der Name des Ziel-DBMS. *destination_dbms* ist vom **Datentyp vom Datentyp sysname**. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**MSSQLSERVER**|Das Ziel ist eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank.|  
|**Orakel**|Das Ziel ist eine Oracle-Datenbank.|  
|**DB2**|Das Ziel ist eine IBM DB2-Datenbank.|  
|**Sybase**|Das Ziel ist eine Sybase-Datenbank.|  
  
`[ @destination_version = ] 'destination_version'`Die Produktversion des Ziel-DBMS. *destination_version*ist vom Datentyp **varchar (10)**. Wenn kein Wert angegeben wird, werden die Zuordnungen für alle Versionen des Ziel-DBMS zurückgegeben. Ermöglicht das Filtern des Resultsets nach der Zielversion des DBMS.  
  
`[ @destination_type = ] 'destination_type'`Der im Ziel-DBMS aufgelistete Datentyp. *destination_type*ist vom **Datentyp vom Datentyp sysname**. Wenn kein Wert angegeben wird, werden die Zuordnungen für alle Datentypen im Ziel-DBMS zurückgegeben. Ermöglicht das Filtern des Resultsets nach dem Datentyp im Ziel-DBMS.  
  
`[ @defaults_only = ] defaults_only`Gibt an, ob nur die standardmäßigen Datentyp Zuordnungen zurückgegeben werden. *defaults_only* ist vom Typ **Bit**. der Standardwert ist **0**. **1** bedeutet, dass nur die standardmäßigen Datentyp Zuordnungen zurückgegeben werden. **0** bedeutet, dass die Standard-und alle benutzerdefinierten Datentyp Zuordnungen zurückgegeben werden.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|BESCHREIBUNG|  
|-----------------|-----------------|  
|**mapping_id**|Identifiziert eine Datentypzuordnung.|  
|**source_dbms**|Der Name und die Versionsnummer des Quell-DBMS.|  
|**source_type**|Der Datentyp im Quell-DBMS.|  
|**destination_dbms**|Der Name des Ziel-DBMS.|  
|**destination_type**|Der Datentyp im Ziel-DBMS.|  
|**is_default**|Gibt an, ob die Zuordnung eine Standardzuordnung oder eine alternative Zuordnung ist. Der Wert **0** gibt an, dass diese Zuordnung Benutzer definiert ist.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_helpdatatypemap** definiert Datentyp Zuordnungen sowohl von nicht SQL Server Verlegern als auch von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verlegern zu nicht-- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Abonnenten.  
  
 Wenn die angegebene Kombination aus Quell-und Ziel-DBMS nicht unterstützt wird, gibt **sp_helpdatatypemap** ein leeres Resultset zurück.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** auf dem Verteiler oder Mitglieder der festen Daten Bank Rolle **db_owner** in der Verteilungs Datenbank können **sp_helpdatatypemap**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_getdefaultdatatypemapping &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql.md)   
 [sp_setdefaultdatatypemapping &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-setdefaultdatatypemapping-transact-sql.md)  
  
  
