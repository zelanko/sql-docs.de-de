---
title: Aktivieren der Initialisierung mit einer Sicherung für Transaktions Veröffentlichungen (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- manual subscription initialization [SQL Server replication]
- subscriptions [SQL Server replication], initializing
- initializing subscriptions [SQL Server replication], without snapshots
- transactional replication, backup and restore
- backups [SQL Server replication], transactional replication
ms.assetid: 9df00514-aa9d-4ac6-9766-d226c9958175
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 046eb926391faff26bb3238dfd225619e9fec374
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/25/2020
ms.locfileid: "62721345"
---
# <a name="enable-initialization-with-a-backup-for-transactional-publications-sql-server-management-studio"></a>Aktivieren der Initialisierung von einer Sicherung für Transaktionsveröffentlichungen (SQL Server Management Studio)
  Wenn Sie ein Abonnement für eine Transaktionsveröffentlichung von einer Sicherung initialisieren möchten, aktivieren Sie die Veröffentlichung, um das Initialisieren von einer Sicherung zuzulassen. Geben Sie dann beim Erstellen des Abonnements die Sicherungsinformationen ein:  
  
-   Aktivieren Sie die Veröffentlichung im Dialogfeld **Veröffentlichungseigenschaften - \<Veröffentlichung>** auf der Seite **Abonnementoptionen**. Weitere Informationen zum Zugreifen auf dieses Dialogfeld finden Sie unter [View and Modify Publication Properties](publish/view-and-modify-publication-properties.md).  
  
-   Geben Sie mit der gespeicherten Prozedur [sp_addsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) Sicherungsinformationen an. Weitere Informationen zu den für **sp_addsubscription** erforderlichen Parametern finden Sie unter [Initialisieren eines Transaktionsabonnements von einer Sicherung &#40;Replikationsprogrammierung mit Transact-SQL&#41;](initialize-a-transactional-subscription-from-a-backup.md).  
  
### <a name="to-enable-initialization-with-a-backup"></a>So aktivieren Sie die Initialisierung mit einer Sicherung  
  
1.  Wählen Sie im Dialogfeld **Veröffentlichungseigenschaften - \<Veröffentlichung>** auf der Seite **Abonnementoptionen** für die Option **Initialisierung aus Sicherungsdateien zulassen** den Wert **TRUE** aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Initialisieren eines Transaktions Abonnements ohne Momentaufnahme](initialize-a-transactional-subscription-without-a-snapshot.md)  
  
  
