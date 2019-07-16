---
title: Sys.fn_servershareddrives (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_servershareddrives
- fn_servershareddrives_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- fn_servershareddrives function
- shared drives [SQL Server]
- names [SQL Server], shared drives
- sys.fn_serversharedrives function
ms.assetid: ff01eff7-8cb6-460c-ba7a-6a52bda6d471
author: rothja
ms.author: jroth
ms.openlocfilehash: 71858ee3c57af8d94bdf4ef4addad720655942f4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68122556"
---
# <a name="sysfnservershareddrives-transact-sql"></a>sys.fn_servershareddrives (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt die Namen der freigegebenen Laufwerke zurück, die vom gruppierten Server verwendet werden.  
  
> [!IMPORTANT]  
>  Diese [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Systemfunktion wird aus Gründen der Abwärtskompatibilität bereitgestellt. Wir empfehlen die Verwendung [dm_io_cluster_valid_path_names &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-io-cluster-valid-path-names-transact-sql.md) stattdessen.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
fn_servershareddrives()  
```  
  
## <a name="tables-returned"></a>Zurückgegebene Tabellen  
 Wenn der aktuelle Server auf einem Clusterserver ist **Fn_servershareddrives** gibt Sie den Laufwerknamen der freigegebenen Laufwerke zurück.  
  
 Wenn die aktuelle Serverinstanz kein gruppierter Server, ist **Fn_servershareddrives** ein leeres Rowset zurück.  
  
## <a name="remarks"></a>Hinweise  
 `fn_servershareddrives` gibt eine Liste der freigegebenen Laufwerke zurück, die von diesem gruppierten Server verwendet werden. Diese freigegebenen Laufwerke gehören zu derselben Clustergruppe wie die [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Ressource. Außerdem ist die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Ressource von diesen Laufwerken abhängig.  
  
 Mit dieser Funktion lassen sich die Laufwerke ermitteln, die den Benutzern zur Verfügung stehen.  
  
## <a name="permissions"></a>Berechtigungen  
 Der Benutzer muss über die VIEW SERVER STATE-Berechtigung für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz verfügen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird `fn_servershareddrives` verwendet, um eine Abfrage auf einer Instanz eines gruppierten Servers auszuführen:  
  
```  
SELECT * FROM fn_servershareddrives();  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 DriveName  
  
 -------\-  
  
 m  
  
 n  
  
## <a name="see-also"></a>Siehe auch  
 [dm_io_cluster_valid_path_names &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-io-cluster-valid-path-names-transact-sql.md)   
 [sys.dm_io_cluster_shared_drives &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-io-cluster-shared-drives-transact-sql.md)   
 [sys.fn_virtualservernodes &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-virtualservernodes-transact-sql.md)  
  
  
