---
title: sp_pdw_add_network_credentials
titleSuffix: Azure SQL Data Warehouse
ms.custom: seo-dt-2019
ms.date: 03/14/2017
ms.service: sql-data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 0729eeff-ac7e-43f0-80fa-ff5346a75985
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 88ddae78b3c866556edbd9e3026e3cb86c747f51
ms.sourcegitcommit: f688a37bb6deac2e5b7730344165bbe2c57f9b9c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/08/2019
ms.locfileid: "73844411"
---
# <a name="sp_pdw_add_network_credentials-sql-data-warehouse"></a>sp_pdw_add_network_credentials (SQL Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Dies speichert Netzwerk Anmelde Informationen in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] und ordnet diese einem Server zu. Verwenden Sie diese gespeicherte Prozedur z. b., um [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] geeignete Lese-/Schreibberechtigungen zum Ausführen von Daten Bank Sicherungs-und Wiederherstellungs Vorgängen auf einem Zielserver und zum Erstellen einer Sicherung eines Zertifikats zu erstellen, das für TDE verwendet wird.  
  
 ![Symbol zum Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Themenlink (Symbol)") [Transact-SQL-Syntaxkonventionen &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_add_network_credentials 'target_server_name',  'user_name', ꞌpasswordꞌ  
```  
  
## <a name="arguments"></a>Argumente  
 "*target_server_name*"  
 Gibt den Hostnamen oder die IP-Adresse des Zielservers an. [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] auf diesen Server mithilfe der Anmelde Informationen für Benutzername und Kennwort zugreifen, die an diese gespeicherte Prozedur übermittelt werden.  
  
 Verwenden Sie zum Herstellen einer Verbindung über das InfiniBand-Netzwerk die InfiniBand-IP-Adresse des Zielservers.  
  
 *target_server_name* ist als nvarchar (337) definiert.  
  
 '*user_name*'  
 Gibt den user_name an, der über Berechtigungen für den Zugriff auf den Zielserver verfügt. Wenn für den Zielserver bereits Anmelde Informationen vorhanden sind, werden Sie auf die neuen Anmelde Informationen aktualisiert.  
  
 *user_name* ist als nvarchar (513) definiert.  
  
 '*Password*ꞌ  
 Gibt das Kennwort für *user_name*an.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die **Alter Server State** -Berechtigung.  
  
## <a name="error-handling"></a>Fehlerbehandlung  
 Ein Fehler tritt auf, wenn das Hinzufügen von Anmelde Informationen auf dem Steuer Knoten und allen Computeknoten nicht erfolgreich ist.  
  
## <a name="general-remarks"></a>Allgemeine Hinweise  
 Diese gespeicherte Prozedur fügt dem Network Service-Konto für [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]Netzwerk Anmelde Informationen hinzu. Das Network Service-Konto führt jede Instanz von SMP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf dem Steuer Knoten und den Computeknoten aus. Wenn beispielsweise ein Sicherungs Vorgang ausgeführt wird, verwenden der Steuer Knoten und alle Computeknoten die Anmelde Informationen des Network Service-Kontos, um Lese-und Schreibberechtigungen für den Zielserver zu erhalten.  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
### <a name="a-add-credentials-for-performing-a-database-backup"></a>A. Hinzufügen von Anmelde Informationen zum Ausführen einer Datenbanksicherung  
 Im folgenden Beispiel werden die Anmelde Informationen für den Benutzernamen und das Kennwort für den Domänen Benutzer "tsattle\david" einem Zielserver mit der IP-Adresse 10.172.63.255 zugeordnet. Der Benutzer "einattle\david" verfügt über Lese-/Schreibberechtigungen für den Zielserver. in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] werden diese Anmelde Informationen gespeichert und zum Lesen und Schreiben auf dem Zielserver verwendet, sofern dies für Sicherungs-und Wiederherstellungs Vorgänge erforderlich ist.  
  
```  
EXEC sp_pdw_add_network_credentials '10.172.63.255', 'seattle\david', '********';  
```  
  
 Der Backup-Befehl erfordert, dass der Servername als IP-Adresse eingegeben wird.  
  
> [!NOTE]  
>  Um die Datenbanksicherung über InfiniBand auszuführen, achten Sie darauf, die InfiniBand-IP-Adresse des Sicherungs Servers zu verwenden.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_pdw_remove_network_credentials &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-remove-network-credentials-sql-data-warehouse.md)  
  
  

