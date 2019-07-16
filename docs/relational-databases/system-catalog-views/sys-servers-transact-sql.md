---
title: Sys.Servers (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/07/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- servers_TSQL
- sys.servers_TSQL
- servers
- sys.servers
dev_langs:
- TSQL
helpviewer_keywords:
- sys.servers catalog view
ms.assetid: 4e774ed9-4e83-4726-9f1d-8efde8f9feff
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: b17296d558c078d3f580e63bf662bb975615ad94
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68132948"
---
# <a name="sysservers-transact-sql"></a>sys.servers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Enthält eine Zeile für jeden registrierten Verbindungs- oder Remoteserver sowie eine Zeile für den lokalen Server, bei dem **server_id** = 0 ist.  

|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|Lokale ID des Verbindungsservers.|  
|**name**|**sysname**|Wenn **Server_id** = 0, der zurückgegebene Wert ist, den Namen des Servers.<br /><br /> Wenn **Server_id** > 0 ist, der zurückgegebene Wert wird der lokale Name des Verbindungsservers.|  
|**product**|**sysname**|Der Produktname des Verbindungsservers. Der Wert "SQL Server" gibt an, eine andere Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Anbieter**|**sysname**|Der Name des OLE DB-Anbieters zum Herstellen einer Verbindung mit Verbindungsservern.|  
|**data_source**|**nvarchar(4000)**|Die Verbindungseigenschaft der OLE DB-Datenquelle.|  
|**location**|**nvarchar(4000)**|Die Verbindungseigenschaft des OLE DB-Standortes. Ist NULL, wenn nichts angegeben wird.|  
|**provider_string**|**nvarchar(4000)**|Die Verbindungseigenschaft der OLE DB-Anbieterzeichenfolge.<br /><br /> Besitzt den Wert NULL, wenn der Aufrufer nicht über die ALTER ANY LINKED SERVER-Berechtigung verfügt.|  
|**catalog**|**sysname**|Die Verbindungseigenschaft des OLE DB-Katalogs. Ist NULL, wenn nichts angegeben wird.|  
|**connect_timeout**|**int**|Das Verbindungstimeout in Sekunden. Ist 0, wenn nichts angegeben wird.|  
|**query_timeout**|**int**|Abfragetimeout in Sekunden. Ist 0, wenn nichts angegeben wird.|  
|**is_linked**|**bit**|0 = Ist ein Server im alten Format, der mithilfe von **sp_addserver**hinzugefügt wurde und ein anderes Verhalten hinsichtlich RPC und verteilter Transaktionen aufweist.<br /><br /> 1 = Standardverbindungsserver.|  
|**is_remote_login_enabled**|**bit**|RPC-Option ist so festgelegt, dass eingehende Remoteanmeldungen für diesen Server möglich sind.|  
|**is_rpc_out_enabled**|**bit**|Ausgehendes RPC (von diesem Server) wurde aktiviert.|  
|**is_data_access_enabled**|**bit**|Server wurde für verteilte Abfragen aktiviert.|  
|**is_collation_compatible**|**bit**|Wenn keine Sortierungsinformationen verfügbar sind, wird davon ausgegangen, dass die Sortierung von Remotedaten mit der von lokalen Daten kompatibel ist.|  
|**uses_remote_collation**|**bit**|Bei 1 verwenden Sie die vom Remoteserver gemeldete Sortierung; verwenden Sie andernfalls die von der nächsten Spalte angegebene Sortierung.|  
|**collation_name**|**sysname**|Name der zu verwendenden Sortierung, oder NULL bei Verwendung der lokalen Sortierung.|  
|**lazy_schema_validation**|**bit**|Bei 1 wird die Schemaüberprüfung zu Beginn der Abfrage nicht überprüft.|  
|**is_system**|**bit**|Auf diesen Server kann nur vom internen System zugegriffen werden.|  
|**is_publisher**|**bit**|Der Server ist ein Replikationsverleger.|  
|**is_subscriber**|**bit**|Der Server ist ein Replikationsabonnent.|  
|**is_distributor**|**bit**|Der Server ist ein Replikationsverteiler.|  
|**is_nonsql_subscriber**|**bit**|Der Server ist ein Replikationsabonnent ohne SQL Server.|  
|**is_remote_proc_transaction_promotion_enabled**|**bit**|Wenn diese Option auf 1 festgelegt ist und eine remote gespeicherte Prozedur aufgerufen wird, wird eine verteilte Transaktion gestartet und bei MS DTC eingetragen. Weitere Informationen finden Sie unter [sp_serveroption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-serveroption-transact-sql.md)erläutert.|  
|**modify_date**|**datetime**|Datum, an dem die Serverinformationen zuletzt geändert wurden.|  
  
## <a name="permissions"></a>Berechtigungen  
 Der Wert in **provider_string** ist immer NULL, wenn der Aufrufer nicht über die ALTER ANY LINKED SERVER-Berechtigung verfügt.  
  
 Zum Anzeigen des lokalen Servers (**server_id** = 0) sind keine Berechtigungen erforderlich.  
  
 Wenn Sie einen Verbindungs- oder Remoteserver erstellen, wird von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine standardmäßige Anmeldenamenzuordnung zur **public** -Serverrolle erstellt. Standardmäßige anmeldenamenzuordnung bedeutet, dass alle Anmeldungen alle Verbindungs- und Remoteserver angezeigt werden können. Wenn Sie die Sichtbarkeit auf diese Server beschränken möchten, entfernen Sie die standardmäßige Anmeldenamenzuordnung, indem Sie [sp_droplinkedsrvlogin](../../relational-databases/system-stored-procedures/sp-droplinkedsrvlogin-transact-sql.md) ausführen und NULL für den *locallogin* -Parameter angeben.  
  
 Wenn die standardmäßige Anmeldenamenzuordnung gelöscht wird, können die Verbindungs- bzw. Remoteserver nur von den explizit als verknüpfte Anmeldung oder Remoteanmeldung hinzugefügten Benutzern angezeigt werden, die auch über einen Anmeldenamen dafür verfügen.  Die folgenden Berechtigungen sind erforderlich, um alle Verbindungs- und Remoteserver-Server nach der die standardmäßige anmeldenamenzuordnung anzuzeigen:  
  
- `ALTER ANY LINKED SERVER` oder `ALTER ANY LOGIN ON SERVER`  
- Mitgliedschaft in den festen Serverrollen **setupadmin** oder **sysadmin**  
  
## <a name="see-also"></a>Siehe auch  
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Verbindungsserver-Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/linked-servers-catalog-views-transact-sql.md)   
 [sp_addlinkedsrvlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)   
 [sp_addremotelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addremotelogin-transact-sql.md)  
  
  
