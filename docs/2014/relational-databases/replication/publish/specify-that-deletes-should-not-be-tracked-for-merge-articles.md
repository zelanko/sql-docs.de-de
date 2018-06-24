---
title: Gibt an, dass Löschvorgänge nicht sollen, können Sie für Mergeartikel (Replikationsprogrammierung mit Transact-SQL nachverfolgt werden) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- TSQL
helpviewer_keywords:
- conditional delete tracking [SQL Server replication]
- merge replication [SQL Server replication], conditional delete tracking
ms.assetid: 0fe330ca-5fb5-422e-ad6f-92fb5d6a3b6c
caps.latest.revision: 34
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 7ab89664d39f6dbe8a929b7bd1280f39e97e2414
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36056906"
---
# <a name="specify-that-deletes-should-not-be-tracked-for-merge-articles-replication-transact-sql-programming"></a>Angeben, dass Löschvorgänge für Mergeartikel nicht nachverfolgt werden sollen (Replikationsprogrammierung mit Transact-SQL)
    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 Standardmäßig synchronisiert die Mergereplikation DELETE-Befehle zwischen dem Verleger und dem Abonnenten. Die Mergereplikation ermöglicht Ihnen, Zeilen in der Abonnementdatenbank auch dann beizubehalten, wenn sie aus der Veröffentlichung gelöscht wurden und umgekehrt. Sie können bei der Erstellung eines neuen Artikels programmgesteuert festlegen, dass der DELETE-Befehl ignoriert wird, oder Sie können diese Funktionalität zu einem späteren Zeitpunkt mithilfe von gespeicherten Replikationsprozeduren aktivieren.  
  
> [!IMPORTANT]  
>  Die Aktivierung dieser Funktionalität führt zu Nichtkonvergenz, was bedeutet, dass die dem Abonnenten verfügbaren Daten nicht genau den Daten des Verlegers entsprechen. Sie müssen einen eigenen Mechanismus implementieren, um die gelöschten Zeilen zu entfernen.  
  
### <a name="to-specify-that-deletes-be-ignored-for-a-new-merge-article"></a>So geben Sie an, dass Löschvorgänge für Mergeartikel ignoriert werden sollen  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) aus. Geben Sie den Wert `false` für **@delete_tracking**. Weitere Informationen finden Sie unter [Define an Article](define-an-article.md).  
  
    > [!NOTE]  
    >  Wenn die Quelltabelle eines Artikels bereits in einer anderen Veröffentlichung veröffentlicht wurde, muss der Wert von **delete_tracking** für beide Artikel gleich sein.  
  
### <a name="to-specify-that-deletes-be-ignored-for-an-existing-merge-article"></a>So geben Sie an, dass Löschvorgänge für einen vorhandenen Mergeartikel ignoriert werden sollen  
  
1.  Führen Sie [sp_helpmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql) aus, um zu ermitteln, ob die Fehlerkompensierung für einen Artikel aktiviert ist, und achten Sie im Resultset auf den Wert von **delete_tracking**. Ist dieser Wert **0**, werden Löschvorgänge bereits ignoriert.  
  
2.  Ist der in Schritt 1 ermittelte Wert **1** ist, führen Sie [sp_changemergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql) auf dem Verleger für die Veröffentlichungsdatenbank aus. Geben Sie den Wert **Delete_tracking** für **@property**, und der Wert `false` für **@value**.  
  
    > [!NOTE]  
    >  Wenn die Quelltabelle eines Artikels bereits in einer anderen Veröffentlichung veröffentlicht wurde, muss der Wert von **delete_tracking** für beide Artikel gleich sein.  
  
## <a name="see-also"></a>Siehe auch  
 [Optimieren der Mergereplikationsleistung durch bedingtes Nachverfolgen von Löschvorgängen](../merge/optimize-merge-replication-performance-with-conditional-delete-tracking.md)  
  
  
