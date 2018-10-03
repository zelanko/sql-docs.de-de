---
title: Sp_polybase_join_group | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 878afb5f16c988ee98908030695e0f03c7e2f7d5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47722648"
---
# <a name="sppolybasejoingroup-transact-sql"></a>Sp_polybase_join_group (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Eine PolyBase-Gruppe für die Berechnung für horizontales Skalieren hinzugefügt eine SQL Server-Instanz als Compute-Knoten.  
  
 SQL Server-Instanz benötigen den [PolyBase](../../relational-databases/polybase/polybase-guide.md) Feature installiert.  PolyBase ermöglicht die Integration von nicht - SQL Server-Datenquellen wie Hadoop und Azure-Blob-Speicher. Siehe auch [Sp_polybase_leave_group &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/polybase-stored-procedures-sp-polybase-leave-group.md).  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
sp_polybase_join_group (@head_node_address = N'head_node_address',  
    @dms_control_channel_port = dms_control_channel_port,  
    @head_node_sql_server_instance_name = head_node_sql_server_instance_name)  
[ ; ]          
```  
  
## <a name="arguments"></a>Argumente  
 *@head_node_address* = N'*Head_node_address*"  
 Der Name des Computers, den SQL Server-Hauptknoten des PolyBase-Erweiterungsgruppe hostet. *@head_node_address* ist vom Datentyp nvarchar(255) an.  
  
 *@dms_control_channel_port* Dms_control_channel_port =  
 Der Port, an dem der Steuerungskanal für den Hauptknoten PolyBase-Datenverschiebungsdienst ausgeführt wird. *@dms_control_channel_port* ist eine nicht signierte __int16 an. Der Standardwert ist **16450**.  
  
 *@head_node_sql_server_instance_name* Head_node_sql_server_instance_name =  
 Der Name der SQL Server-Instanz Head-Knoten in der PolyBase-Erweiterungsgruppe. *@head_node_sql_server_instance_name* ist nvarchar(16) an.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die CONTROL SERVER-Berechtigung.  
  
## <a name="remarks"></a>Hinweise  
 Nach dem Ausführen der gespeicherten Prozedur, fahren Sie die PolyBase-Engine herunter, und starten Sie die PolyBase-Datenverschiebungsdienst auf den Computer neu. So überprüfen die folgende DMV auf dem Hauptknoten ausführen: **dm_exec_compute_nodes**.  
  
## <a name="example"></a>Beispiel  
 Im Beispiel werden den aktuellen Computer als Compute-Knoten zu einer PolyBase-Gruppe verknüpft.  Der Name des Head-Knotens ist **HST01** und der Name der SQL Server-Instanz auf dem Hauptknoten **MSSQLSERVER**.  
  
```  
EXEC sp_polybase_join_group N'HST01', 16450, N'MSSQLSERVER'   
```  
  
## <a name="see-also"></a>Siehe auch  
 [Erste Schritte mit PolyBase](../../relational-databases/polybase/get-started-with-polybase.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
