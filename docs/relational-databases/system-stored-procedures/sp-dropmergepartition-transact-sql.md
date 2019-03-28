---
title: Sp_dropmergepartition (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropmergepartition_TSQL
- sp_dropmergepartition
helpviewer_keywords:
- sp_dropmergepartition
ms.assetid: 1be511c1-79ff-4947-9379-78d83b7b8945
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 74837390afe358d4f9a12d4f98ea9d2e4166e146
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58536092"
---
# <a name="spdropmergepartition-transact-sql"></a>sp_dropmergepartition (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Entfernt eine Partition für einen parametrisierten Zeilenfilter aus einer Veröffentlichung. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt. Mit dieser gespeicherten Prozedur werden zudem der entsprechende Momentaufnahmeauftrag und die Momentaufnahmedateien für die Partition entfernt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_dropmergepartition [ @publication = ] 'publication'  
        , [ @suser_sname = ] 'suser_sname'  
        , [ @host_name = ] 'host_name'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication] = 'publication'` Ist der Name der Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
`[ @suser_sname = ] 'suser_sname'` Ist der Wert der [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md) -Funktion auf dem Abonnenten verwendet wird, um die Partition zu definieren. *SUSER_SNAME* ist **Sysname**, hat keinen Standardwert.  
  
`[ @host_name = ] 'host_name'` Ist der Wert der [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) -Funktion auf dem Abonnenten verwendet wird, um die Partition zu definieren. *HOST_NAME* ist **Sysname**, hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_dropmergepartition** wird bei der Mergereplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder **Db_owner** feste Datenbankrolle können ausführen **Sp_dropmergepartition**.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Partitionen für eine Mergeveröffentlichung mit parametrisierten Filtern](../../relational-databases/replication/publish/manage-partitions-for-a-merge-publication-with-parameterized-filters.md)  
  
  
