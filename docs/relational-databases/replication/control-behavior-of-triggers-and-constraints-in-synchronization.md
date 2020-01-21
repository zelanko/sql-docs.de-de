---
title: Kontrollieren des Verhaltens von Triggern und Einschränkungen während der Synchronisierung
description: Erfahren Sie, wie Sie verhindern, dass während der Synchronisierung einer SQL Server-Replikationsveröffentlichung Trigger ausgeführt oder Einschränkungen erzwungen werden.
ms.custom: seo-lt-2019
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- identities [SQL Server replication]
- constraints [SQL Server], replication
- triggers [SQL Server], replication
- triggers [SQL Server replication]
- constraints [SQL Server replication]
- NOT FOR REPLICATION option
- NFR option
ms.assetid: 7c4e0f0e-cadc-4c99-98f4-69799b9b356b
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: 816bda09c547345f5d05cd511d51c72135f15029
ms.sourcegitcommit: 02d44167a1ee025ba925a6fefadeea966912954c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2019
ms.locfileid: "75321802"
---
# <a name="control-behavior-of-triggers-and-constraints-in-synchronization"></a>Kontrollieren des Verhaltens von Triggern und Einschränkungen während der Synchronisierung
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Während der Synchronisierung führen Replikation-Agents [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)-Anweisungen und [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md) sowie [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)-Anweisungen für replizierte Tabellen aus, was zur Ausführung von DML (Data Manipulation Language)-Triggern in diesen Tabellen führen kann. Es gibt Fälle, in denen Sie verhindern müssen, dass Trigger während der Synchronisierung ausgelöst werden oder Einschränkungen während der Synchronisierung erzwungen werden. Dieses Verhalten hängt davon ab, wie der Trigger oder die Einschränkung erstellt wird.  
  
### <a name="to-prevent-triggers-from-executing-during-synchronization"></a>So verhindern Sie, dass Trigger während der Synchronisierung ausgeführt werden  
  
1.  Geben Sie bei der Erstellung eines neuen Triggers die Option NOT FOR REPLICATION für [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md) an.  
  
2.  Für einen vorhandenen Trigger geben Sie die Option NOT FOR REPLICATION für [ALTER TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-trigger-transact-sql.md) an.  
  
### <a name="to-prevent-constraints-from-being-enforced-during-synchronization"></a>So verhindern Sie, dass Einschränkungen während der Synchronisierung erzwungen werden  
  
1.  Beim Erstellen einer neuen CHECK- oder FOREIGN KEY-Einschränkung geben Sie in der Einschränkungsdefinition von [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md) die Option CHECK NOT FOR REPLICATION an.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von Tabellen &#40;Datenbank-Engine&#41;](../../relational-databases/tables/create-tables-database-engine.md)  
  
  
