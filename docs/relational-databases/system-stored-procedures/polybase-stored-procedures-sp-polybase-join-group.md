---
title: sp_polybase_join_group | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/24/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sp_polybase_join_group
helpviewer_keywords:
- PolyBase
ms.assetid: 48066431-fed2-4a8a-85af-ac704689e183
author: rothja
ms.author: jroth
ms.openlocfilehash: ba22ffe282e6b4248ed58bed850bc6ac08255df5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "72278110"
---
# <a name="sp_polybase_join_group-transact-sql"></a>sp_polybase_join_group (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Fügt einer polybase-Gruppe eine SQL Server Instanz als Computeknoten für die Berechnung der horizontalen Skalierung hinzu.  
  
 Auf der SQL Server Instanz muss das [polybase](../../relational-databases/polybase/polybase-guide.md) -Feature installiert sein.  Polybase ermöglicht die Integration von nicht SQL Server Datenquellen, z. b. Hadoop und Azure BLOB Storage. Siehe auch [sp_polybase_leave_group &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/polybase-stored-procedures-sp-polybase-leave-group.md).  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
sp_polybase_join_group (@head_node_address = N'head_node_address',  
    @dms_control_channel_port = dms_control_channel_port,  
    @head_node_sql_server_instance_name = head_node_sql_server_instance_name)  
[ ; ]          
```  
  
## <a name="arguments"></a>Argumente  
 head_node_address = N '*head_node_address*' * \@*  
 Der Name des Computers, der den SQL Server Head-Knoten der polybase-Erweiterungsgruppe hostet. head_node_address ist vom Datentyp nvarchar (255). * \@*  
  
 * \@dms_control_channel_port* = dms_control_channel_port  
 Der Port, an dem der Steuerungs Kanal für den Haupt Knoten PolyBase-Datenverschiebungsdienst Dienstanbieter ausgeführt wird. dms_control_channel_port ist eine nicht signierte __int16. * \@* Der Standardwert ist **16450**.  
  
 * \@head_node_sql_server_instance_name* = head_node_sql_server_instance_name  
 Der Name des Hauptknotens SQL Server Instanz in der polybase-Erweiterungsgruppe. head_node_sql_server_instance_name ist vom Datentyp nvarchar (16). * \@*  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die CONTROL SERVER-Berechtigung.  
  
## <a name="remarks"></a>Bemerkungen  
 Nachdem Sie die gespeicherte Prozedur ausgeführt haben, fahren Sie die polybase-Engine herunter, und starten Sie den PolyBase-Datenverschiebungsdienst-Dienst auf dem Computer neu. Um zu überprüfen, ob die folgende DMV auf dem Haupt Knoten ausgeführt wird: **sys. dm_exec_compute_nodes**.  
  
## <a name="example"></a>Beispiel  
 Das Beispiel verbindet den aktuellen Computer als Computeknoten mit einer polybase-Gruppe.  Der Name des Hauptknotens ist " **HST01** ", und der Name der SQL Server Instanz auf dem Haupt Knoten ist " **MSSQLSERVER**".  
  
```  
EXEC sp_polybase_join_group N'HST01', 16450, N'MSSQLSERVER'   
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Einstieg in polybase](../../relational-databases/polybase/get-started-with-polybase.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
