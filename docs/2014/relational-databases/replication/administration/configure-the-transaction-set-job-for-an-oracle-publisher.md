---
title: Konfigurieren des Transaktions Satz-Auftrags für einen Oracle-Verleger (Replikations Programmierung mit Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: 43a25ce755a505f0efd7c25243b8969a962ea701
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85065974"
---
# <a name="configure-the-transaction-set-job-for-an-oracle-publisher-replication-transact-sql-programming"></a>Konfigurieren des Transaktionssatz-Auftrags für einen Oracle-Verleger (Replikationsprogrammierung mit Transact-SQL)
  Der **Xactset** -Auftrag ist ein Oracle-Datenbankauftrag, der bei der Replikation erstellt und auf einem Oracle-Verleger ausgeführt wird, um Transaktionssätze zu erstellen, wenn der Protokolllese-Agent nicht mit dem Verleger verbunden ist. Sie können diesen Auftrag auf dem Verteiler programmgesteuert mithilfe gespeicherter Replikationsprozeduren aktivieren und konfigurieren. Weitere Informationen finden Sie unter [Leistungsoptimierung für Oracle-Verleger](../non-sql/performance-tuning-for-oracle-publishers.md).  
  
### <a name="to-enable-the-transaction-set-job"></a>So aktivieren Sie den Transaktionssatz-Auftrag  
  
1.  Legen Sie auf dem Oracle-Verleger den **job_queue_processes** -Initialisierungsparameter auf einen Wert fest, der die Ausführung des Xactset-Auftrags zulässt. Weitere Informationen zu diesem Parameter finden Sie in der Datenbankdokumentation für den Oracle-Verleger.  
  
2.  Führen Sie auf dem Verteiler [Sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql) aus. Geben Sie den Namen des Oracle-Verlegers für ** \@ Publisher**, den Wert `xactsetbatching` für ** \@ propertyName**und den Wert `enabled` für ** \@ PropertyValue**an.  
  
3.  Führen Sie auf dem Verteiler [Sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql) aus. Geben Sie den Namen des Oracle-Verlegers für den ** \@ Verleger**, den Wert `xactsetjobinterval` für ** \@ propertyName**und das Auftrags Intervall in Minuten für ** \@ PropertyValue**an.  
  
4.  Führen Sie auf dem Verteiler [Sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql) aus. Geben Sie den Namen des Oracle-Verlegers für ** \@ Publisher**, den Wert `xactsetjob` für ** \@ propertyName**und den Wert `enabled` für ** \@ PropertyValue**an.  
  
### <a name="to-configure-the-transaction-set-job"></a>So konfigurieren Sie den Transaktionssatz-Auftrag  
  
1.  (Optional) Führen Sie auf dem Verteiler [Sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql) aus. Geben Sie den Namen des Oracle-Verlegers für den ** \@ Verleger**an. Dadurch werden die Eigenschaften des **Xactset** -Auftrags auf dem Verleger zurückgegeben.  
  
2.  Führen Sie auf dem Verteiler [Sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql) aus. Geben Sie den Namen des Oracle-Verlegers für ** \@ Publisher**, den Namen der Xactset-Auftrags Eigenschaft, die für ** \@ propertyName**festgelegt wird, und eine neue Einstellung für ** \@ PropertyValue**an.  
  
3.  (Optional) Wiederholen Sie Schritt 2 für jede festgelegte Xactset-Auftragseigenschaft. Wenn Sie die- `xactsetjobinterval` Eigenschaft ändern, müssen Sie den Auftrag auf dem Oracle-Verleger neu starten, damit das neue Intervall wirksam wird.  
  
### <a name="to-view-properties-of-the-transaction-set-job"></a>So zeigen Sie die Eigenschaften des Transaktionssatz-Auftrags an  
  
1.  Führen Sie auf dem Verteiler [sp_helpxactsetjob](/sql/relational-databases/system-stored-procedures/sp-helpxactsetjob-transact-sql)aus. Geben Sie den Namen des Oracle-Verlegers für den ** \@ Verleger**an.  
  
### <a name="to-disable-the-transaction-set-job"></a>So deaktivieren Sie den Transaktionssatz-Auftrag  
  
1.  Führen Sie auf dem Verteiler [Sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql) aus. Geben Sie den Namen des Oracle-Verlegers für ** \@ Publisher**, den Wert `xactsetjob` für ** \@ propertyName**und den Wert `disabled` für ** \@ PropertyValue**an.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird der `Xactset` -Auftrag aktiviert und ein Intervall von drei Minuten zwischen den Ausführungen festgelegt.  
  
 [!code-sql[HowTo#sp_enable_xactsetjob](../../../snippets/tsql/SQL15/replication/howto/tsql/enablexactsetjob.sql#sp_enable_xactsetjob)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Leistungsoptimierung für Oracle-Verleger](../non-sql/performance-tuning-for-oracle-publishers.md)   
 [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md)  
  
  
