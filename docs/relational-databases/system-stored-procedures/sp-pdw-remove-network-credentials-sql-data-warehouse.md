---
title: Sp_pdw_remove_network_credentials (SQL Data Warehouse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.service: sql-data-warehouse
ms.subservice: design
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: c12696a2-5939-402b-9866-8a837ca4c0a3
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 7a86459f8ea20b2596068093a2e24cb87aa788cb
ms.sourcegitcommit: 0a64d26f865a21f4bd967b2b72680fd8638770b8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/18/2019
ms.locfileid: "54395371"
---
# <a name="sppdwremovenetworkcredentials-sql-data-warehouse"></a>Sp_pdw_remove_network_credentials (SQL Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Dadurch wird in gespeicherten Anmeldeinformationen für das Netzwerk entfernt [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] auf eine Dateifreigabe im Netzwerk zugreifen. Verwenden Sie diese gespeicherte Prozedur z. B. beim Entfernen der Berechtigung für [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Sicherung durchführen und Wiederherstellungsvorgänge auf einem Server, die in Ihrem eigenen Netzwerk befinden.  
  
 ![Symbol zum Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol zum Themenlink") [Transact-SQL Syntax Conventions &#40;Transact-SQL&#41; (Transact-SQL-Syntaxkonventionen (Transact-SQL))](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_remove_network_credentials 'target_server_name'  
```  
  
## <a name="arguments"></a>Argumente  
 '*target_server_name*'  
 Gibt an, die Ziel-Serverhostnamen oder die IP-Adresse. Anmeldeinformationen für den Zugriff auf diesem Server aus entfernt [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. Dies nicht ändern oder entfernen Sie alle Berechtigungen auf dem tatsächlichen Zielserver, der von Ihrem eigenen Team verwaltet wird.  
  
 *Target_server_name* als nvarchar(337) definiert ist.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert **ALTER SERVER STATE** Berechtigung.  
  
## <a name="error-handling"></a>Fehlerbehandlung  
 Ein Fehler tritt auf, wenn das Entfernen von Anmeldeinformationen auf dem steuerknoten und alle Computeknoten nicht erfolgreich ist.  
  
## <a name="general-remarks"></a>Allgemeine Hinweise  
 Diese gespeicherte Prozedur entfernt die Anmeldeinformationen für das Netzwerk aus dem NetworkService-Konto für [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. Das Konto NetworkService ausgeführt wird, jede Instanz von SMP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf dem steuerknoten und den Compute-Knoten. Z. B. wenn ein Sicherungsvorgang ausgeführt wird, verwendet den Steuerelementknoten aus, und jeder Compute-Knoten die Anmeldeinformationen für das Konto NetworkService auf den Zielserver zugreifen.  
  
## <a name="metadata"></a>Metadaten  
 Verwenden Sie zum Auflisten aller Anmeldeinformationen und überprüfen die Anmeldeinformationen wurden entfernt [Sys. dm_pdw_network_credentials &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-network-credentials-transact-sql.md).  
  
 Verwenden Sie zum Hinzufügen von Anmeldeinformationen [Sp_pdw_add_network_credentials &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md).  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
### <a name="a-remove-credentials-for-performing-a-database-backup"></a>A. Entfernen der Anmeldeinformationen für das Ausführen einer datenbanksicherung  
 Im folgenden Beispiel wird die Benutzeranmeldeinformationen und das Kennwort für den Zugriff auf dem Zielserver, der IP-Adresse 10.192.147.63 verfügt.  
  
```  
EXEC sp_pdw_remove_network_credentials '10.192.147.63';  
```  
  
  

