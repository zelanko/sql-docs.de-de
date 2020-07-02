---
title: sys. dm_os_child_instances (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_child_instances
- sys.dm_os_child_instances_TSQL
- dm_os_child_instances
- dm_os_child_instances_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- server state information [SQL Server]
- sys.dm_os_child_instances dynamic management view
- monitoring server health
ms.assetid: 1bef3074-0ccc-48fa-8f3d-14f3d99df86b
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0650278c0c0de78cf33b5b65b28bb00479f88f1e
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85754219"
---
# <a name="sysdm_os_child_instances-transact-sql"></a>sys.dm_os_child_instances (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Gibt eine Zeile für jede Benutzerinstanz zurück, die aus der übergeordneten Serverinstanz erstellt wurde.  
  
> **WICHTIG!** [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 Die von **sys. dm_os_child_instances** zurückgegebenen Informationen können verwendet werden, um den Status der einzelnen Benutzer Instanzen (heart_beat) zu bestimmen und um den Pipenamen (instance_pipe_name) abzurufen, der zum Erstellen einer Verbindung mit der Benutzer Instanz mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder sqlcmd verwendet werden kann. Die Verbindung zur Benutzerinstanz kann erst hergestellt werden, wenn die Benutzerinstanz von einem externen Vorgang, wie z. B. einer Clientanwendung, gestartet worden ist. Mit den SQL-Verwaltungstools selbst können keine Benutzerinstanzen gestartet werden.  
  
> **Hinweis:** Benutzer Instanzen sind nur eine Funktion von [!INCLUDE[ssExpressEd11](../../includes/ssexpressed11-md.md)] .  
> 
> **Hinweis** Um dies von oder aus aufzurufen [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] , verwenden Sie den Namen **sys. dm_pdw_nodes_os_child_instances**.  
  
|Column|Datentyp|BESCHREIBUNG|  
|------------|---------------|-----------------|  
|**owning_principal_name**|**nvarchar(256)**|Der Name des Benutzers, für den diese Benutzerinstanz erstellt wurde.|  
|owning_principal_sid|nvarchar(256)|Die SID (Sicherheits-ID) des Prinzipals, der Besitzer der Benutzerinstanz ist. Diese SID stimmt mit der Windows-SID überein.|  
|owning_principal_sid_binary|varbinary(85)|Die binäre SID-Version für den Benutzer, der die Benutzerinstanz besitzt.|  
|**instance_name**|**nvarchar(128)**|Der Name der Benutzerinstanz.|  
|**instance_pipe_name**|**nvarchar(260)**|Beim Erstellen einer Benutzerinstanz wird eine benannte Pipe für Verbindungen von Anwendungen erstellt. Dieser Name kann in einer Verbindungszeichenfolge für die Verbindung mit der Benutzerinstanz verwendet werden.|  
|**os_process_id**|**Int**|Die Prozessnummer des Windows-Prozesses für diese Benutzerinstanz.|  
|**os_process_creation_date**|**DateTime**|Datum und Uhrzeit des letzten Starts des Benutzerinstanzprozesses.|  
|**heart_beat**|**nvarchar (5)**|Aktueller Status der Benutzerinstanz – ALIVE oder DEAD.|  
|**pdw_node_id**|**int**|**Gilt für**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] ,[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Der Bezeichner für den Knoten, auf dem sich diese Distribution befindet.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen zur dynamischen Verwaltungs Sicht finden Sie unter [dynamische Verwaltungs Sichten und Funktionen &#40;Transact-SQL-&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md) in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Online Dokumentation.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Benutzerinstanzen für Nichtadministratoren](https://msdn.microsoft.com/85385aae-10fb-4f8b-9eeb-cce2ee7da019)  
  
  



