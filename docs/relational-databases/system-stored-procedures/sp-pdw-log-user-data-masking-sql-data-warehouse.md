---
description: sp_pdw_log_user_data_masking (Azure-Synapse-Analyse)
title: sp_pdw_log_user_data_masking (Azure-Synapse-Analyse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.service: sql-data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 43c63b42-03cb-4fb5-8362-ec3b7e22a590
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: c014f76aac1544e16ec693277a034779f75883cd
ms.sourcegitcommit: ae474d21db4f724523e419622ce79f611e956a22
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/20/2020
ms.locfileid: "92255610"
---
# <a name="sp_pdw_log_user_data_masking-azure-synapse-analytics"></a>sp_pdw_log_user_data_masking (Azure-Synapse-Analyse)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Verwenden Sie **sp_pdw_log_user_data_masking** , um die Benutzerdaten Maskierung in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Aktivitäts Protokollen zu aktivieren. Die Maskierung von Benutzerdaten wirkt sich auf die Anweisungen für alle Datenbanken auf dem Gerät aus  
  
> [!IMPORTANT]  
>  Die [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Aktivitäts Protokolle, die von **sp_pdw_log_user_data_masking** betroffen sind, sind bestimmte [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Aktivitäts Protokolle. **sp_pdw_log_user_data_masking** wirkt sich nicht auf Daten Bank Transaktionsprotokolle oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Fehlerprotokolle aus.  
  
 **Hintergrund:** In den standardmäßigen Konfigurations [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Aktivitäts Protokollen sind vollständige [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisungen enthalten. in einigen Fällen können Benutzerdaten in Vorgängen wie **Insert**-, **Update**-und **Select** -Anweisungen enthalten sein. Im Falle eines Problems auf der Appliance können dadurch die Bedingungen, die das Problem verursacht haben, analysiert werden, ohne dass das Problem reproduziert werden muss. Um zu verhindern, dass die Benutzerdaten in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Aktivitäts Protokolle geschrieben werden, können Kunden die Benutzerdaten Maskierung mithilfe dieser gespeicherten Prozedur aktivieren. Die Anweisungen werden weiterhin in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Aktivitäts Protokolle geschrieben, aber alle Literale in Anweisungen, die möglicherweise Benutzerdaten enthalten, werden maskiert; durch einige vordefinierte Konstante Werte ersetzt.  
  
 Wenn die transparente Datenverschlüsselung auf dem Gerät aktiviert ist, wird die Maskierung der Benutzerdaten in den [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Aktivitäts Protokollen automatisch aktiviert.  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql  
-- Syntax for Azure Synapse Analytics and Parallel Data Warehouse  
  
sp_pdw_log_user_data_masking [ [ @masking_mode = ] value ] ;  
```

[!INCLUDE[synapse-analytics-od-unsupported-syntax](../../includes/synapse-analytics-od-unsupported-syntax.md)]

#### <a name="parameters"></a>Parameter  
`[ @masking_mode = ] masking_mode` Bestimmt, ob die Daten Maskierung für die transparente Datenverschlüsselung aktiviert ist. *masking_mode* ist vom Datentyp **int**und kann einen der folgenden Werte aufweisen:  
  
-   0 = deaktiviert, Benutzerdaten werden in den [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Aktivitäts Protokollen angezeigt.  
  
-   1 = aktiviert, Benutzerdaten Anweisungen werden in den [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Aktivitäts Protokollen angezeigt, aber die Benutzerdaten werden maskiert.  
  
-   2 = Anweisungen, die Benutzerdaten enthalten, werden nicht in die [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Aktivitäts Protokolle geschrieben.  
  
 Wenn **sp_pdw_ log_user_data_masking** ohne Parameter ausgeführt wird, wird der aktuelle Zustand der TDE-Protokoll Benutzerdaten Maskierung auf dem Gerät als skalares Resultset zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Maskierung von Benutzerdaten in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Aktivitäts Protokollen ermöglicht die Ersetzung von literalen mit vordefinierten Konstanten Werten in **Select** -und DML-Anweisungen, da Sie Benutzerdaten enthalten können. Wenn Sie *masking_mode* auf 1 festlegen, werden Metadaten nicht maskiert, wie z. b. Spaltennamen oder Tabellennamen. Wenn Sie *masking_mode* auf 2 festlegen, werden-Anweisungen mit Metadaten entfernt, z. b. Spaltennamen oder Tabellennamen.  
  
 Die Benutzerdaten Maskierung in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Aktivitäts Protokollen wird folgendermaßen implementiert:  
  
-   TDE und die Maskierung von Benutzerdaten in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Aktivitäts Protokollen sind standardmäßig deaktiviert. Die-Anweisungen werden nicht automatisch maskiert, wenn die Datenbankverschlüsselung auf dem Gerät nicht aktiviert ist.  
  
-   Durch das Aktivieren von TDE auf dem Gerät wird die Benutzerdaten Maskierung in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Aktivitäts Protokollen automatisch aktiviert.  
  
-   Die Deaktivierung von TDE wirkt sich nicht auf die Benutzerdaten Maskierung in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Aktivitäts Protokollen aus.  
  
-   [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]Mithilfe des **sp_pdw_log_user_data_masking** Verfahrens können Sie die Maskierung von Benutzerdaten in Aktivitäts Protokollen explizit aktivieren.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Daten Bank Rolle **sysadmin** oder die **Control Server** -Berechtigung.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die TDE-Protokollierung der Benutzerdaten auf dem Gerät aktiviert.  
  
```sql  
EXEC sp_pdw_log_user_data_masking 1;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_pdw_database_encryption &#40;Azure-Synapse-Analyse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)   
 [sp_pdw_database_encryption_regenerate_system_keys &#40;Azure-Synapse-Analyse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-regenerate-system-keys-sql-data-warehouse.md)  
  
  
