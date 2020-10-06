---
title: sp_polybase_leave_group (Transact-SQL) | Microsoft-Dokumentation
description: Der sp_polybase_leave_group Transact-SQL-Befehl entfernt eine SQL Server Instanz aus einer polybase-Gruppe für die Berechnung der horizontalen Skalierung.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: polybase
ms.topic: conceptual
f1_keywords:
- sp_polybase_leave_group
- sp_polybase_leave_group_TSQL
helpviewer_keywords:
- sp_polybase_leave_group
ms.assetid: ef87a8f1-5407-47b5-b8bf-bd7d08c0f0fe
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 3d909da06b0f8cf4520d92a9ba8cb8652a6b2a5a
ms.sourcegitcommit: 968969b62bc158b9843aba5034c9d913519bc4a7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/06/2020
ms.locfileid: "91753887"
---
# <a name="sp_polybase_leave_group-transact-sql"></a>sp_polybase_leave_group (Transact-SQL)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Entfernt eine SQL Server Instanz aus einer polybase-Gruppe für die Berechnung der horizontalen Skalierung. 
 
 Auf der SQL Server Instanz muss das Feature  [polybase Guide](../../relational-databases/polybase/polybase-guide.md) installiert sein.  Polybase ermöglicht die Integration von nicht SQL Server Datenquellen, z. b. Hadoop und Azure BLOB Storage. Siehe auch [sp_polybase_join_group](../../relational-databases/system-stored-procedures/polybase-stored-procedures-sp-polybase-join-group.md).  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_polybase_leave_group;  
  
```  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Control Server-Berechtigung.  
  
## <a name="remarks"></a>Bemerkungen  
 Ein Computeknoten kann nur aus einer Gruppe entfernt werden.  
  
 Starten Sie nach dem Ausführen der gespeicherten Prozedur die polybase-Engine und PolyBase-Datenverschiebungsdienst-Dienst auf dem Computer neu. Um zu überprüfen, ob die folgende DMV auf dem Haupt Knoten ausgeführt wird: **sys.dm_exec_compute_nodes**.  
  
## <a name="example"></a>Beispiel  
 Im Beispiel wird der aktuelle Computer aus einer polybase-Gruppe entfernt.  
  
```sql  
EXEC sp_polybase_leave_group ;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Erste Schritte mit PolyBase](../polybase/polybase-guide.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
