---
title: Konfigurieren des Transaktionssatz-Auftrags für einen Oracle-Verleger (Replikationsprogrammierung mit Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_publisherproperty
- Oracle publishing [SQL Server replication], configuring
ms.assetid: beea1a5c-0053-4971-a68f-0da53063fcbb
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: bfa83609f4040fc9875a63217b0e86d6a3ff99bc
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63187019"
---
# <a name="configure-the-transaction-set-job-for-an-oracle-publisher-replication-transact-sql-programming"></a>Konfigurieren des Transaktionssatz-Auftrags für einen Oracle-Verleger (Replikationsprogrammierung mit Transact-SQL)
  Der **Xactset** -Auftrag ist ein Oracle-Datenbankauftrag, der bei der Replikation erstellt und auf einem Oracle-Verleger ausgeführt wird, um Transaktionssätze zu erstellen, wenn der Protokolllese-Agent nicht mit dem Verleger verbunden ist. Sie können diesen Auftrag auf dem Verteiler programmgesteuert mithilfe gespeicherter Replikationsprozeduren aktivieren und konfigurieren. Weitere Informationen finden Sie unter [Leistungsoptimierung für Oracle-Verleger](../non-sql/performance-tuning-for-oracle-publishers.md).  
  
### <a name="to-enable-the-transaction-set-job"></a>So aktivieren Sie den Transaktionssatz-Auftrag  
  
1.  Legen Sie auf dem Oracle-Verleger den **job_queue_processes** -Initialisierungsparameter auf einen Wert fest, der die Ausführung des Xactset-Auftrags zulässt. Weitere Informationen zu diesem Parameter finden Sie in der Datenbankdokumentation für den Oracle-Verleger.  
  
2.  Führen Sie auf dem Verteiler [Sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql) aus. Geben Sie den Namen des Oracle-Verlegers für **@publisher**, einen Wert von `xactsetbatching` für **@propertyname**, und den Wert `enabled` für **@propertyvalue**.  
  
3.  Führen Sie auf dem Verteiler [Sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql) aus. Geben Sie den Namen des Oracle-Verlegers für **@publisher**, einen Wert von `xactsetjobinterval` für **@propertyname**, und das Auftragsintervall in Minuten an, für die **@propertyvalue**.  
  
4.  Führen Sie auf dem Verteiler [Sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql) aus. Geben Sie den Namen des Oracle-Verlegers für **@publisher**, einen Wert von `xactsetjob` für **@propertyname**, und den Wert `enabled` für **@propertyvalue**.  
  
### <a name="to-configure-the-transaction-set-job"></a>So konfigurieren Sie den Transaktionssatz-Auftrag  
  
1.  (Optional) Führen Sie auf dem Verteiler [Sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql) aus. Geben Sie den Namen des Oracle-Verlegers für **@publisher**. Dadurch werden die Eigenschaften des **Xactset** -Auftrags auf dem Verleger zurückgegeben.  
  
2.  Führen Sie auf dem Verteiler [Sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql) aus. Geben Sie den Namen des Oracle-Verlegers für **@publisher**, den Namen der Xactset-Auftragseigenschaft, die für **@propertyname**festgelegt ist, und eine neue Einstellung für **@propertyvalue**.  
  
3.  (Optional) Wiederholen Sie Schritt 2 für jede festgelegte Xactset-Auftragseigenschaft. Beim Ändern der `xactsetjobinterval` -Eigenschaft, Sie müssen den Auftrag neu starten auf dem Oracle-Verleger für das neue Intervall wirksam wird.  
  
### <a name="to-view-properties-of-the-transaction-set-job"></a>So zeigen Sie die Eigenschaften des Transaktionssatz-Auftrags an  
  
1.  Führen Sie auf dem Verteiler [sp_helpxactsetjob](/sql/relational-databases/system-stored-procedures/sp-helpxactsetjob-transact-sql)aus. Geben Sie den Namen des Oracle-Verlegers für **@publisher**.  
  
### <a name="to-disable-the-transaction-set-job"></a>So deaktivieren Sie den Transaktionssatz-Auftrag  
  
1.  Führen Sie auf dem Verteiler [Sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql) aus. Geben Sie den Namen des Oracle-Verlegers für **@publisher**, einen Wert von `xactsetjob` für **@propertyname**, und den Wert `disabled` für **@propertyvalue**.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird der `Xactset` -Auftrag aktiviert und ein Intervall von drei Minuten zwischen den Ausführungen festgelegt.  
  
 [!code-sql[HowTo#sp_enable_xactsetjob](../../../snippets/tsql/SQL15/replication/howto/tsql/enablexactsetjob.sql#sp_enable_xactsetjob)]  
  
## <a name="see-also"></a>Siehe auch  
 [Leistungsoptimierung für Oracle-Verleger](../non-sql/performance-tuning-for-oracle-publishers.md)   
 [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md)  
  
  
