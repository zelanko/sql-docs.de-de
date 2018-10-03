---
title: Sp_pdw_log_user_data_masking (SQL Data Warehouse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 43c63b42-03cb-4fb5-8362-ec3b7e22a590
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 23d7846bd72329a62579765679687204a8e14ec5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47630238"
---
# <a name="sppdwloguserdatamasking-sql-data-warehouse"></a>Sp_pdw_log_user_data_masking (SQL Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Verwendung **Sp_pdw_log_user_data_masking** Aktivieren von Benutzerdaten maskiert [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Aktivitätsprotokolle. Benutzer datenmaskierung wirkt sich auf die Anweisungen für alle Datenbanken auf dem Gerät.  
  
> [!IMPORTANT]  
>  Die [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Aktivitätsprotokolle betroffen **Sp_pdw_log_user_data_masking** sind bestimmte [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Aktivitätsprotokolle. **Sp_pdw_log_user_data_masking** wirkt sich nicht auf Datenbankprotokolle oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Fehlerprotokolle.  
  
 **Hintergrund:** In der Standardkonfiguration [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Aktivitätsprotokolle enthalten vollständige [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen, und es in einigen Fällen enthalten Benutzerdaten enthalten Vorgänge wie z. B. **einfügen**,  **UPDATE**, und **wählen** Anweisungen. Wenn auf dem Gerät ein Problem vorliegt können die Analyse der Bedingungen, die die Ursache des Problems, ohne das Problem reproduzieren. Um zu verhindern, dass die Benutzerdaten in geschriebenen [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] -Aktivitätsprotokollen, Kunden können auswählen, um die datenmaskierung Benutzer mit dieser gespeicherten Prozedur zu aktivieren. Die Anweisungen werden weiterhin in geschrieben [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Aktivitätsprotokolle, aber alle die Literale in Anweisungen, die Benutzerdaten enthalten unter Umständen werden maskiert werden; mit einigen vordefinierten Konstanten Werte ersetzt.  
  
 Wenn die transparente datenverschlüsselung auf dem Gerät aktiviert ist, maskieren Sie die Benutzerdaten in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Aktivitätsprotokolle wird automatisch aktiviert.  
  
## <a name="syntax"></a>Syntax  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_log_user_data_masking [ [ @masking_mode = ] value ] ;  
```  
  
#### <a name="parameters"></a>Parameter  
 [ **@masking_mode=** ] *masking_mode*  
 Bestimmt, ob transparent Data Encryption Log Maskieren von Benutzerdaten aktiviert ist. *Masking_mode* ist **Int**, und kann einen der folgenden Werte:  
  
-   0 = deaktiviert, Benutzer, die Daten, in angezeigt der [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Aktivitätsprotokolle.  
  
-   1 = Enabled "," User-Anweisungen Daten angezeigt, in werden der [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Aktivitätsprotokolle, aber die Benutzerdaten werden maskiert.  
  
-   2 = Anweisungen, die mit Benutzerdaten, die nicht, um geschrieben werden die [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Aktivitätsprotokolle.  
  
 Ausführen von **Sp_pdw_ Log_user_data_masking** ohne Parameter gibt den aktuellen Status der TDE Log Benutzer die datenmaskierung auf dem Gerät als skalare Resultset zurück.  
  
## <a name="remarks"></a>Hinweise  
 Benutzerdaten maskiert [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] aktiviert die Ersetzung von literalen-Aktivitätsprotokolle mit vordefinierten Konstanten Werten in **wählen** und DML-Anweisungen, wie sie Benutzerdaten enthalten können. Festlegen von *Masking_mode* 1 wird nicht maskiert Metadaten, z. B. Spaltennamen oder Tabellennamen. Festlegen von *Masking_mode* auf 2 entfernt-Anweisungen mit Metadaten, z. B. Spaltennamen oder Tabellennamen.  
  
 Benutzerdaten maskiert [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Aktivitätsprotokolle wird wie folgt implementiert:  
  
-   TDE und Benutzer datenmaskierung [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Aktivitätsprotokolle sind standardmäßig deaktiviert. Die Anweisungen werden nicht automatisch maskiert werden, wenn Verschlüsselung der Datenbank nicht auf dem Gerät aktiviert ist.  
  
-   Aktivieren von TDE automatisch auf dem Gerät aktiviert die datenmaskierung für die Benutzer im [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Aktivitätsprotokolle.  
  
-   Deaktivieren von TDE wirkt sich nicht auf Benutzerdaten im maskiert [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Aktivitätsprotokolle.  
  
-   Sie können explizit aktivieren, Benutzer datenmaskierung [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Aktivitätsprotokolle mit der **Sp_pdw_log_user_data_masking** Verfahren.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **Sysadmin** feste Datenbankrolle oder **CONTROL SERVER** Berechtigung.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die TDE-Log-Benutzerdaten, die auf dem Gerät maskiert.  
  
```  
EXEC sp_pdw_log_user_data_masking 1;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sp_pdw_database_encryption aktiviert werden &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)   
 [sp_pdw_database_encryption_regenerate_system_keys &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-regenerate-system-keys-sql-data-warehouse.md)  
  
  
