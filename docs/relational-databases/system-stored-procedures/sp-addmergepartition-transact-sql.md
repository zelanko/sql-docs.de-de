---
title: sp_addmergepartition (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addmergepartition
- sp_addmergepartition_TSQL
helpviewer_keywords:
- sp_addmergepartition
ms.assetid: 02a5f46b-e5ff-4932-a3ff-7f0fd82d0981
author: stevestein
ms.author: sstein
ms.openlocfilehash: 21e9d91978a01152f22d18f03fa54bf29b776b8a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68769172"
---
# <a name="sp_addmergepartition-transact-sql"></a>sp_addmergepartition (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Erstellt eine dynamisch gefilterte Partition für ein Abonnement, das nach den Werten [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) oder [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md) auf dem Abonnenten gefiltert wird. Diese gespeicherte Prozedur wird auf dem Verleger in der Datenbank ausgeführt, die veröffentlicht wird, und wird zum manuellen Generieren von Partitionen verwendet.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addmergepartition [ @publication = ] 'publication'  
        , [ @suser_sname = ] 'suser_sname'  
        , [ @host_name = ] 'host_name'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Die Mergeveröffentlichung, für die die Partition erstellt wird. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. Wenn *SUSER_SNAME* angegeben wird, muss der Wert von *Hostname* NULL sein.  
  
`[ @suser_sname = ] 'suser_sname'`Der Wert, der beim Erstellen der Partition für ein Abonnement verwendet wird, das nach dem Wert der [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md) -Funktion auf dem Abonnenten gefiltert wird. *SUSER_SNAME* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @host_name = ] 'host_name'`Der Wert, der beim Erstellen der Partition für ein Abonnement verwendet wird, das nach dem Wert der [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) -Funktion auf dem Abonnenten gefiltert wird. *HOST_NAME* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_addmergepartition** wird bei der Mergereplikation verwendet.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_MergeDynamicPubPlusPartition](../../relational-databases/replication/codesnippet/tsql/sp-addmergepartition-tra_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_addmergepartition**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen einer Momentaufnahme für eine Mergeveröffentlichung mit parametrisierten Filtern](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)   
 [Parametrisierte Zeilen Filter](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)  
  
  
