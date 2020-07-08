---
title: sys. fn_virtualservernodes (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_virtualservernodes
- fn_virtualservernodes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- nodes [Faillover Clustering], virtual servers
- nodes [Faillover Clustering]
- virtual servers [Faillover Clustering]
- failover clustering [SQL Server], nodes
- fn_virtualservernodes function
- sys.fn_virtualservernodes function
ms.assetid: 257f3b8d-93c0-4444-87f1-ea211bd8cad0
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0ec290179cdbf3e61f0e5033acbf3156dbc6441a
ms.sourcegitcommit: 8515bb2021cfbc7791318527b8554654203db4ad
ms.contentlocale: de-DE
ms.lasthandoff: 07/08/2020
ms.locfileid: "86091664"
---
# <a name="sysfn_virtualservernodes-transact-sql"></a>sys.fn_virtualservernodes (Transact-SQL)
[!INCLUDE [sql-asdbmi-pdw](../../includes/applies-to-version/sql-asdbmi-pdw.md)]

  Gibt eine Liste der Failoverclusterinstanz-Knoten zurück, auf denen eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt werden kann. Diese Informationen sind in Umgebungen mit Failoverclustering hilfreich.  
  
> [!IMPORTANT]
>  Diese [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Systemfunktion ist aus Gründen der Abwärtskompatibilität enthalten. Es wird empfohlen, stattdessen [sys. dm_os_cluster_nodes &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-cluster-nodes-transact-sql.md) zu verwenden.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
fn_virtualservernodes()  
```  
  
## <a name="tables-returned"></a>Zurückgegebene Tabellen  
 Wenn es sich bei dem aktuellen Server um einen gruppierten Server handelt, gibt **fn_virtualservernodes** eine Liste der failoverclusterinstanzknoten zurück, auf denen diese Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] definiert wurde.  
  
 Wenn die aktuelle Serverinstanz kein gruppierter Server ist, gibt **fn_virtualservernodes** ein leeres Rowset zurück.  
  
## <a name="permissions"></a>Berechtigungen  
 Der Benutzer muss über die VIEW SERVER STATE-Berechtigung für die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verfügen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird `fn_virtualservernodes` verwendet, um eine Abfrage auf einer Instanz eines gruppierten Servers auszuführen:  
  
```  
SELECT * FROM fn_virtualservernodes();  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 NodeName  
  
 -------\-  
  
 SS3-CLUSN1  
  
 SS3-CLUSN2  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys. dm_os_cluster_nodes &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-cluster-nodes-transact-sql.md)   
 [sys.fn_servershareddrives &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-servershareddrives-transact-sql.md)  
  
  
