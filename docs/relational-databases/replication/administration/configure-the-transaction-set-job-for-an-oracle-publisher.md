---
title: Konfigurieren des Transaktionssatzauftrags (Oracle-Verleger)
description: In diesem Artikel erfahren Sie, wie Sie den Transaktionssatzauftrag für einen Oracle-Verleger konfigurieren, der Veröffentlichungen für einen SQL Server-Abonnenten ausführt.
ms.custom: seo-lt-2019
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
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
ms.openlocfilehash: 8f25f3d9c9a69d3a8f87e8a4eb1886f31092940f
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "75322052"
---
# <a name="configure-the-transaction-set-job-for-an-oracle-publisher"></a>Konfigurieren des Transaktionssatz-Auftrags für einen Oracle-Verleger
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Der **Xactset** -Auftrag ist ein Oracle-Datenbankauftrag, der bei der Replikation erstellt und auf einem Oracle-Verleger ausgeführt wird, um Transaktionssätze zu erstellen, wenn der Protokolllese-Agent nicht mit dem Verleger verbunden ist. Sie können diesen Auftrag auf dem Verteiler programmgesteuert mithilfe gespeicherter Replikationsprozeduren aktivieren und konfigurieren. Weitere Informationen finden Sie unter [Leistungsoptimierung für Oracle-Verleger](../../../relational-databases/replication/non-sql/performance-tuning-for-oracle-publishers.md).  
  
### <a name="to-enable-the-transaction-set-job"></a>So aktivieren Sie den Transaktionssatz-Auftrag  
  
1.  Legen Sie auf dem Oracle-Verleger den **job_queue_processes** -Initialisierungsparameter auf einen Wert fest, der die Ausführung des Xactset-Auftrags zulässt. Weitere Informationen zu diesem Parameter finden Sie in der Datenbankdokumentation für den Oracle-Verleger.  
  
2.  Führen Sie auf dem Verteiler [Sp_publisherproperty &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md) aus. Geben Sie für **\@publisher** den Namen des Oracle-Verlegers, für **\@propertyname** den Wert **xactsetbatching** und für **\@propertyvalue** den Wert **enabled** an.  
  
3.  Führen Sie auf dem Verteiler [Sp_publisherproperty &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md) aus. Geben Sie für **\@publisher** den Namen des Oracle-Verlegers, für **\@propertyname** den Wert **xactsetjobinterval** und für **\@propertyvalue** das Auftragsintervall in Minuten an.  
  
4.  Führen Sie auf dem Verteiler [Sp_publisherproperty &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md) aus. Geben Sie für **\@publisher** den Namen des Oracle-Verlegers, für **\@propertyname** den Wert **xactsetjob** und für **\@propertyvalue** den Wert **enabled** an.  
  
### <a name="to-configure-the-transaction-set-job"></a>So konfigurieren Sie den Transaktionssatz-Auftrag  
  
1.  (Optional) Führen Sie auf dem Verteiler [Sp_publisherproperty &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md) aus. Geben Sie für **\@publisher** den Namen des Oracle-Verlegers an. Dadurch werden die Eigenschaften des **Xactset** -Auftrags auf dem Verleger zurückgegeben.  
  
2.  Führen Sie auf dem Verteiler [Sp_publisherproperty &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md) aus. Geben Sie für **\@publisher** den Namen des Oracle-Verlegers, für **\@propertyname** den festgelegten Namen der Xactset-Auftragseigenschaft und für **\@propertyvalue** eine neue Einstellung an.  
  
3.  (Optional) Wiederholen Sie Schritt 2 für jede festgelegte Xactset-Auftragseigenschaft. Beim Ändern der **xactsetjobinterval** -Eigenschaft müssen Sie den Auftrag auf dem Oracle-Verleger neu starten, damit das neue Intervall wirksam wird.  
  
### <a name="to-view-properties-of-the-transaction-set-job"></a>So zeigen Sie die Eigenschaften des Transaktionssatz-Auftrags an  
  
1.  Führen Sie auf dem Verteiler [sp_helpxactsetjob](../../../relational-databases/system-stored-procedures/sp-helpxactsetjob-transact-sql.md)aus. Geben Sie für **\@publisher** den Namen des Oracle-Verlegers an.  
  
### <a name="to-disable-the-transaction-set-job"></a>So deaktivieren Sie den Transaktionssatz-Auftrag  
  
1.  Führen Sie auf dem Verteiler [Sp_publisherproperty &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md) aus. Geben Sie für **\@publisher** den Namen des Oracle-Verlegers, für **\@propertyname** den Wert **xactsetjob** und für **\@propertyvalue** den Wert **disabled** an.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird der `Xactset` -Auftrag aktiviert und ein Intervall von drei Minuten zwischen den Ausführungen festgelegt.  
  
 [!code-sql[HowTo#sp_enable_xactsetjob](../../../relational-databases/replication/codesnippet/tsql/configure-the-transactio_1.sql)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Leistungsoptimierung für Oracle-Verleger](../../../relational-databases/replication/non-sql/performance-tuning-for-oracle-publishers.md)   
 [Replication System Stored Procedures Concepts](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)  
  
  
