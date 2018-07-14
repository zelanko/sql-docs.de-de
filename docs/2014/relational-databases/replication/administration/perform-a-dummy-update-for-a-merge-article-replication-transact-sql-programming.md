---
title: Ausführen eines Pseudoupdates für einen Mergeartikel (Replikationsprogrammierung mit Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_mergedummyupdate
- dummy updates [SQL Server replication]
ms.assetid: 2f339210-4d85-4843-bd94-e86f7100d3ef
caps.latest.revision: 30
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 13f72453ec5981120997d024493da2609fb2a092
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37227060"
---
# <a name="perform-a-dummy-update-for-a-merge-article-replication-transact-sql-programming"></a>Ausführen eines Pseudoupdates für einen Mergeartikel (Replikationsprogrammierung mit Transact-SQL)
  Bei der Mergereplikation kommen im Rahmen des Replikationsvorgangs Trigger zum Einsatz: Beim Aktualisieren einer veröffentlichten Tabelle wird ein Update-Trigger ausgelöst. In manchen Fällen können Daten aktualisiert werden, ohne dass der Trigger ausgelöst wird, z. B. bei WRITETEXT- und UPDATETEXT-Vorgängen. In diesen Fällen müssen Sie explizit eine UPDATE-Pseudoanweisung hinzufügen, um die Änderung zu replizieren. Sie können eine UPDATE-Pseudoanweisung mithilfe gespeicherter Replikationsprozeduren hinzufügen.  
  
### <a name="to-add-a-dummy-update-statement"></a>So fügen Sie eine UPDATE-Pseudoanweisung hinzu  
  
1.  Führen Sie den Vorgang (z. B. UPDATETEXT) für eine Zeile in einer veröffentlichten Tabelle für einen Mergevorgang aus, für die ein Pseudoupdate erforderlich ist.  
  
2.  Führen Sie auf dem Server (Verleger oder Abonnent) auf der Datenbank, auf dem die Änderung vorgenommen wurde, [sp_mergedummyupdate &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-mergedummyupdate-transact-sql) aus. Geben Sie die Tabelle, in der die Änderung für **@source_object**vorgenommen wurde, und den eindeutigen Bezeichner der geänderten Zeile für **@rowguid**aus.  
  
3.  Synchronisieren Sie das Abonnement, um die geänderte Zeile zu replizieren.  
  
  
