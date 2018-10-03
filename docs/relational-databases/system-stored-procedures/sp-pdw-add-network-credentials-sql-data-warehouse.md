---
title: Sp_pdw_add_network_credentials (SQL Data Warehouse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 0729eeff-ac7e-43f0-80fa-ff5346a75985
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 38111262840a7667a432422b996c666ddc0d0748
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47708228"
---
# <a name="sppdwaddnetworkcredentials-sql-data-warehouse"></a>Sp_pdw_add_network_credentials (SQL Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Dies speichert die Anmeldeinformationen für das Netzwerk in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] und ordnet diese mit einem Server. Verwenden Sie diese gespeicherte Prozedur z. B. gerne [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] geeignete Lese-/Schreibberechtigungen datenbanksicherung ausführen und Wiederherstellungsvorgänge auf einem Zielserver oder zum Erstellen einer Sicherung eines Zertifikats für TDE verwendet.  
  
 ![Symbol zum Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol zum Themenlink") [Transact-SQL Syntax Conventions &#40;Transact-SQL&#41; (Transact-SQL-Syntaxkonventionen (Transact-SQL))](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_add_network_credentials 'target_server_name',  'user_name', ꞌpasswordꞌ  
```  
  
## <a name="arguments"></a>Argumente  
 "*Target_server_name*"  
 Gibt an, die Ziel-Serverhostnamen oder die IP-Adresse. [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] wird für diesen Server erlauben mithilfe der Benutzername und Kennwort-Anmeldeinformationen, die an diese gespeicherte Prozedur übergeben wird.  
  
 Um über das InfiniBand-Netzwerk verbinden möchten, verwenden Sie die InfiniBand IP-Adresse des Zielservers ein.  
  
 *Target_server_name* als nvarchar(337) definiert ist.  
  
 '*user_name*'  
 Gibt an, der Benutzername, der Administratorberechtigungen auf dem Zielserver verfügt. Wenn die Anmeldeinformationen für den Zielserver bereits vorhanden sind, werden sie auf die neuen Anmeldeinformationen aktualisiert werden.  
  
 *USER_NAME* als Nvarchar (513) definiert ist.  
  
 "*Kennwort*Standardzeichen  
 Gibt das Kennwort für *User_name*.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert **ALTER SERVER STATE** Berechtigung.  
  
## <a name="error-handling"></a>Fehlerbehandlung  
 Hinzufügen von Anmeldeinformationen auf dem steuerknoten und alle Computeknoten nicht erfolgreich ist, tritt ein Fehler auf.  
  
## <a name="general-remarks"></a>Allgemeine Hinweise  
 Diese gespeicherte Prozedur fügt Anmeldeinformationen für das Netzwerk mit dem NetworkService-Konto für [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. Das Konto NetworkService ausgeführt wird, jede Instanz von SMP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf dem steuerknoten und den Compute-Knoten. Z. B. wenn ein Sicherungsvorgang ausgeführt wird, verwendet den Steuerelementknoten aus, und jeder Compute-Knoten die Anmeldeinformationen des NetworkService-Konto erhalten Sie lesen und Schreibberechtigungen für den Zielserver.  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
### <a name="a-add-credentials-for-performing-a-database-backup"></a>A. Hinzufügen von Anmeldeinformationen für das Ausführen einer datenbanksicherung  
 Im folgenden Beispiel wird die Anmeldeinformationen des Benutzers und das Kennwort für die Domäne Benutzer Seattle\david mit einem Zielserver, der über eine IP-Adresse des 10.172.63.255 verfügt. Der Benutzer Seattle\david verfügt über Lese-/Schreibberechtigungen auf dem Zielserver. [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Diese Anmeldeinformationen speichert und diese verwenden, um das Lesen und Schreiben in und aus dem Zielserver bei Bedarf für die Sicherung und Wiederherstellungsvorgänge.  
  
```  
EXEC sp_pdw_add_network_credentials '10.172.63.255', 'seattle\david', '********';  
```  
  
 Backup-Befehl erfordert, dass es sich bei den Namen des Servers als eine IP-Adresse eingegeben werden.  
  
> [!NOTE]  
>  Zum Durchführen der Sicherung über InfiniBand unbedingt die InfiniBand IP-Adresse des backup-Server verwenden.  
  
## <a name="see-also"></a>Siehe auch  
 [Sp_pdw_remove_network_credentials &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-remove-network-credentials-sql-data-warehouse.md)  
  
  

