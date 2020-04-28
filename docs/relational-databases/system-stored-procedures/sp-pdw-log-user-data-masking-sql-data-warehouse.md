---
title: sp_pdw_log_user_data_masking (SQL Data Warehouse) | Microsoft-Dokumentation
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
ms.openlocfilehash: 18798dece1c801ad0cc4854b7fccc15529a56d5c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68056447"
---
# <a name="sp_pdw_log_user_data_masking-sql-data-warehouse"></a>sp_pdw_log_user_data_masking (SQL Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Verwenden Sie **sp_pdw_log_user_data_masking** , um die Benutzerdaten [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Maskierung in Aktivitäts Protokollen zu aktivieren. Die Maskierung von Benutzerdaten wirkt sich auf die Anweisungen für alle Datenbanken auf dem Gerät aus  
  
> [!IMPORTANT]  
>  Die [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Aktivitäts Protokolle, die von **sp_pdw_log_user_data_masking** betroffen [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] sind, sind bestimmte Aktivitäts Protokolle. **sp_pdw_log_user_data_masking** wirkt sich nicht auf Daten Bank Transaktionsprotokolle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Fehlerprotokolle aus.  
  
 **Hintergrund:** In den standardmäßigen [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Konfigurations Aktivitäts Protokollen sind [!INCLUDE[tsql](../../includes/tsql-md.md)] vollständige Anweisungen enthalten. in einigen Fällen können Benutzerdaten in Vorgängen wie **Insert**-, **Update**-und **Select** -Anweisungen enthalten sein. Im Falle eines Problems auf der Appliance können dadurch die Bedingungen, die das Problem verursacht haben, analysiert werden, ohne dass das Problem reproduziert werden muss. Um zu verhindern, dass die Benutzerdaten in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Aktivitäts Protokolle geschrieben werden, können Kunden die Benutzerdaten Maskierung mithilfe dieser gespeicherten Prozedur aktivieren. Die-Anweisungen werden weiterhin in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Aktivitäts Protokolle geschrieben, aber alle Literale in-Anweisungen, die möglicherweise Benutzerdaten enthalten, werden maskiert. ersetzt durch einige vordefinierte Konstante Werte.  
  
 Wenn die transparente Datenverschlüsselung auf dem Gerät aktiviert ist, wird die Maskierung der [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Benutzerdaten in den Aktivitäts Protokollen automatisch aktiviert.  
  
## <a name="syntax"></a>Syntax  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_log_user_data_masking [ [ @masking_mode = ] value ] ;  
```  
  
#### <a name="parameters"></a>Parameter  
`[ @masking_mode = ] masking_mode`Bestimmt, ob die Daten Maskierung für die transparente Datenverschlüsselung aktiviert ist. *masking_mode* ist vom Datentyp **int**und kann einen der folgenden Werte aufweisen:  
  
-   0 = deaktiviert, Benutzerdaten werden in den [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Aktivitäts Protokollen angezeigt.  
  
-   1 = aktiviert, Benutzerdaten Anweisungen werden in den [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Aktivitäts Protokollen angezeigt, aber die Benutzerdaten werden maskiert.  
  
-   2 = Anweisungen, die Benutzerdaten enthalten, werden nicht [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] in die Aktivitäts Protokolle geschrieben.  
  
 Wenn **sp_pdw_ log_user_data_masking** ohne Parameter ausgeführt wird, wird der aktuelle Zustand der TDE-Protokoll Benutzerdaten Maskierung auf dem Gerät als skalares Resultset zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Maskierung von [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Benutzerdaten in Aktivitäts Protokollen ermöglicht die Ersetzung von literalen mit vordefinierten Konstanten Werten in **Select** -und DML-Anweisungen, da Sie Benutzerdaten enthalten können. Wenn Sie *masking_mode* auf 1 festlegen, werden Metadaten nicht maskiert, wie z. b. Spaltennamen oder Tabellennamen. Wenn Sie *masking_mode* auf 2 festlegen, werden-Anweisungen mit Metadaten entfernt, z. b. Spaltennamen oder Tabellennamen.  
  
 Die Benutzerdaten Maskierung in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Aktivitäts Protokollen wird folgendermaßen implementiert:  
  
-   TDE und die Maskierung von [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Benutzerdaten in Aktivitäts Protokollen sind standardmäßig deaktiviert. Die-Anweisungen werden nicht automatisch maskiert, wenn die Datenbankverschlüsselung auf dem Gerät nicht aktiviert ist.  
  
-   Durch das Aktivieren von TDE auf dem Gerät wird die Benutzerdaten Maskierung in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Aktivitäts Protokollen automatisch aktiviert.  
  
-   Die Deaktivierung von TDE wirkt sich nicht auf die [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Benutzerdaten Maskierung in Aktivitäts Protokollen aus.  
  
-   Mithilfe des [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] **sp_pdw_log_user_data_masking** Verfahrens können Sie die Maskierung von Benutzerdaten in Aktivitäts Protokollen explizit aktivieren.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Daten Bank Rolle **sysadmin** oder die **Control Server** -Berechtigung.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die TDE-Protokollierung der Benutzerdaten auf dem Gerät aktiviert.  
  
```  
EXEC sp_pdw_log_user_data_masking 1;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_pdw_database_encryption &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)   
 [sp_pdw_database_encryption_regenerate_system_keys &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-regenerate-system-keys-sql-data-warehouse.md)  
  
  
