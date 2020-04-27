---
title: Abonnementablauf und -deaktivierung | Microsoft Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Distributors [SQL Server replication], distribution retention period
- subscriptions [SQL Server replication], expiration
- publications [SQL Server replication], publication retention periods
- expiration [SQL Server replication]
- retention periods [SQL Server replication]
- publication retention periods
- distribution retention period
- subscriptions [SQL Server replication], deactivation
- deactivating subscriptions
ms.assetid: 4d03f5ab-e721-4f56-aebc-60f6a56c1e07
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 89818f172ee9af09a44654dffc800bf6adc35de4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62630380"
---
# <a name="subscription-expiration-and-deactivation"></a>Abonnementablauf und -deaktivierung
  Abonnements können deaktiviert werden oder ablaufen, wenn sie nicht innerhalb einer angegebenen *Beibehaltungsdauer*synchronisiert werden. Die stattfindende Aktion hängt vom Typ der Replikation und der überschrittenen Beibehaltungsdauer ab.  
  
 Weitere Informationen zum Festlegen von Beibehaltungsdauern finden Sie unter [Festlegen des Ablaufdatums für Abonnements](publish/set-the-expiration-period-for-subscriptions.md), [Festlegen der Beibehaltungsdauer für die Verteilung bei Transaktionsveröffentlichungen &#40;SQL Server Management Studio&#41;](set-distribution-retention-period-for-transactional-publications.md), und [Verleger- und Verteilereigenschaften](configure-publishing-and-distribution.md).  
  
## <a name="transactional-replication"></a>Transaktionsreplikation  
 Die Transaktions Replikation verwendet die maximale Beibehaltungs Dauer für die **@max_distretention** Verteilung (der-Parameter von [sp_adddistributiondb &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql)) und die **@retention** Beibehaltungs Dauer der Veröffentlichung (der-Parameter von [sp_addpublication &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql)):  
  
-   Falls ein Abonnement nicht innerhalb der maximalen Beibehaltungsdauer für die Verteilung (standardmäßig 72 Stunden) synchronisiert wird und Änderungen in der Verteilungsdatenbank vorliegen, die noch nicht an den Abonnenten übermittelt wurden, wird das Abonnement vom Auftrag **Verteilungscleanup** , der auf dem Verteiler ausgeführt wird, als deaktiviert gekennzeichnet. Das Abonnement muss erneut initialisiert werden.  
  
-   Falls ein Abonnement nicht innerhalb der Beibehaltungsdauer für die Veröffentlichung (standardmäßig 336 Stunden) synchronisiert wird, läuft das Abonnement ab und wird vom Auftrag **Cleanup abgelaufener Abonnements** gelöscht, der auf dem Verleger ausgeführt wird. Das Abonnement muss neu erstellt und synchronisiert werden.  
  
     Wenn ein Pushabonnement abläuft, wird es vollständig entfernt. Bei Pullabonnements ist dies nicht der Fall. Sie müssen einen Cleanup der Pullabonnements auf dem Abonnenten ausführen. Weitere Informationen finden Sie unter [Delete a Pull Subscription](delete-a-pull-subscription.md).  
  
## <a name="merge-replication"></a>Mergereplikation  
 Bei der Mergereplikation wird die Beibehaltungs Dauer der Veröffentlichung verwendet (die **@retention** Parameter und von **@retention_period_unit** [sp_addmergepublication &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)). Wenn ein Abonnement abläuft, muss es erneut initialisiert werden, da Metadaten für das Abonnement entfernt werden. Abonnements, die nicht erneut initialisiert werden, werden vom Auftrag **Cleanup abgelaufener Abonnements** gelöscht, der auf dem Verleger ausgeführt wird. Dieser Auftrag wird standardmäßig einmal pro Tag ausgeführt, und es werden dabei alle Pushabonnements gelöscht, die seit einem Zeitraum, der der doppelten Beibehaltungsdauer der Veröffentlichung entspricht, nicht synchronisiert wurden. Beispiel:  
  
-   Wenn eine Veröffentlichung eine Beibehaltungsdauer von 14 Tagen aufweist, kann ein Abonnement ablaufen, wenn es nicht innerhalb von 14 Tagen synchronisiert wurde.  
  
     Wenn auf dem Verleger [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder eine höhere Version ausgeführt wird und der Agent für das Abonnement aus [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder einer höheren Version stammt, läuft ein Abonnement nur ab, wenn Änderungen an den Daten in der Partition dieses Abonnements vorgenommen wurden. Nehmen wir beispielsweise an, dass ein Abonnent Kundendaten nur für Kunden in Deutschland empfängt. Falls die Beibehaltungsdauer auf 14 Tage festgelegt wurde, läuft das Abonnement nur dann am Tag 14 ab, wenn während der letzten 14 Tage Änderungen an den deutschen Kundendaten vorgenommen wurden.  
  
-   14 bis 27 Tage nach der letzten Synchronisierung kann das Abonnement erneut initialisiert werden.  
  
-   28 Tage nach der letzten Synchronisierung wird das Abonnement vom Auftrag **Cleanup abgelaufener Abonnements** gelöscht. Wenn ein Pushabonnement abläuft, wird es vollständig entfernt. Bei Pullabonnements ist dies nicht der Fall. Sie müssen einen Cleanup der Pullabonnements auf dem Abonnenten ausführen. Weitere Informationen finden Sie unter [Delete a Pull Subscription](delete-a-pull-subscription.md).  
  
### <a name="considerations-for-setting-the-publication-retention-period-for-merge-publications"></a>Überlegungen für das Festlegen der Beibehaltungsdauer der Veröffentlichung für Mergeveröffentlichungen  
 Beachten Sie bei der Festlegung der Beibehaltungsdauer für Mergeveröffentlichungen Folgendes:  
  
-   Die Beibehaltungsdauer für Mergeveröffentlichungen weist eine 24-stündige Kulanzfrist auf, um Abonnenten in unterschiedlichen Zeitzonen aufzunehmen. Wenn Sie beispielsweise eine Beibehaltungsdauer von einem Tag festgelegt haben, beträgt die tatsächliche Beibehaltungsdauer 48 Stunden.  
  
-   Der Cleanup der Metadaten für die Mergereplikation hängt von der Beibehaltungsdauer der Veröffentlichung ab:  
  
    -   Die Replikation kann der Cleanup von Metadaten aus den Veröffentlichungs- und Abonnementdatenbanken erst ausführen, wenn das Ablaufdatum erreicht ist. Geben Sie keinen zu hohen Wert für die Beibehaltungsdauer an, da dies zu einer Beeinträchtigung der Replikationsleistung führen kann. Es wird empfohlen, eine niedrigere Einstellung zu verwenden, wenn Sie zuverlässig einschätzen können, dass alle Abonnenten innerhalb dieser Zeitspanne regelmäßig synchronisiert werden.  
  
    -   Es ist möglich, anzugeben, dass Abonnements nie ablaufen (der Wert 0 für **@retention**). es wird jedoch dringend empfohlen, diesen Wert nicht zu verwenden, da die Metadaten nicht bereinigt werden können.  
  
-   Die Beibehaltungsdauer für alle Wiederveröffentlichungen muss auf einen Wert festgelegt werden, der gleich oder niedriger ist als die auf dem ursprünglichen Verleger festgelegte Beibehaltungsdauer. Verwenden Sie zudem dieselben Beibehaltungsdauerwerte für Veröffentlichungen für alle Verleger und ihre alternativen Synchronisierungspartner. Das Verwenden unterschiedlicher Werte kann zu mangelnder Konvergenz der Daten führen. Wenn Sie die Beibehaltungsdauer der Veröffentlichung ändern müssen, sollten Sie den Abonnenten erneut initialisieren, um sicherzustellen, dass die Daten konvergieren.  
  
-   Wenn die Beibehaltungsdauer der Veröffentlichung nach einem Cleanup erhöht wird und für ein Abonnement ein Mergevorgang mit dem Verleger versucht wird (auf dem die Metadaten bereits gelöscht wurden), dann läuft das Abonnement nicht ab, weil die Beibehaltungsdauer erhöht wurde. Allerdings verfügt der Verleger nicht über ausreichende Metadaten zum Herunterladen der Änderungen auf den Abonnenten. Dies führt zu mangelnder Konvergenz der Daten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erneutes Initialisieren von Abonnements](reinitialize-subscriptions.md)   
 [Verwaltung des Replikations-Agents](agents/replication-agent-administration.md)   
 [Abonnieren von Veröffentlichungen](subscribe-to-publications.md)  
  
  
