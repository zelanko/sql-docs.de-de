---
title: Angeben des standardmäßigen Momentaufnahmespeicherorts (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], default locations
- default snapshot locations
ms.assetid: 27c5d9ad-a915-4c59-a8b7-82e3af61ac4d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cd41dabe1554bc3f80adc4fdb6d8433f8aac9e7f
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52807332"
---
# <a name="specify-the-default-snapshot-location-sql-server-management-studio"></a>Angeben des standardmäßigen Momentaufnahmespeicherorts (SQL Server Management Studio)
  Geben Sie den standardmäßigen Momentaufnahmespeicherort im Verteilungskonfigurations-Assistenten auf der Seite **Snapshotordner** an. Weitere Informationen zum Verwenden dieses Assistenten finden Sie unter [Konfigurieren der Veröffentlichung und der Verteilung](configure-publishing-and-distribution.md). Wenn Sie eine Veröffentlichung auf einem Server erstellen, der nicht als Verteiler konfiguriert ist, geben Sie im Assistenten für neue Veröffentlichung auf der Seite **Momentaufnahmeordner** einen standardmäßigen Momentaufnahmespeicherort an. Weitere Informationen zum Zugreifen auf diesen Assistenten finden Sie unter [Erstellen einer Veröffentlichung](publish/create-a-publication.md).  
  
 Ändern Sie den standardmäßigen Momentaufnahmespeicherort im Dialogfeld **Verteilereigenschaften - \<Distributor>** auf der Seite **Verleger**. Weitere Informationen finden Sie unter [Anzeigen und Ändern der Verteiler- und Verlegereigenschaften](view-and-modify-distributor-and-publisher-properties.md). Bestimmen Sie den Momentaufnahmeordner für die einzelnen Veröffentlichungen im Dialogfeld **Veröffentlichungseigenschaften - \<Veröffentlichung>**. Weitere Informationen finden Sie unter [View and Modify Publication Properties](publish/view-and-modify-publication-properties.md).  
  
### <a name="to-modify-the-default-snapshot-location"></a>So ändern Sie den standardmäßigen Momentaufnahmespeicherort  
  
1.  Klicken Sie auf der Seite **Verleger** des Dialogfelds **Verteilereigenschaften – \<Verteiler>** auf die Schaltfläche mit den Auslassungspunkten (**...**) für den Verleger, dessen standardmäßiger Momentaufnahmespeicherort geändert werden soll.  
  
2.  Geben Sie im Dialogfeld **Verlegereigenschaften - \<Publisher>** einen Wert für die Eigenschaft **Standardmomentaufnahmeordner** ein.  
  
    > [!NOTE]  
    >  Der Momentaufnahme-Agent muss Schreibberechtigungen für das angegebene Verzeichnis und der Verteilungs-Agent oder Merge-Agent muss Leseberechtigungen besitzen. Bei Verwendung von Pullabonnements müssen Sie ein freigegebenes Verzeichnis als UNC-Pfad angeben, wie z.B. \\\Computername\Momentaufnahme. Weitere Informationen finden Sie unter [Schützen des Momentaufnahmeordners](security/secure-the-snapshot-folder.md).  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Alternative Speicherorte für Momentaufnahmeordner](alternate-snapshot-folder-locations.md)   
 [Initialisieren eines Abonnements mit einer Momentaufnahme](initialize-a-subscription-with-a-snapshot.md)  
  
  
