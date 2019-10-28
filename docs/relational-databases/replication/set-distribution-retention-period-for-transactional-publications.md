---
title: Festlegen der Beibehaltungsdauer für die Verteilung von Transaktionsveröffentlichungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- transaction retention periods [SQL Server replication]
- retention periods [SQL Server replication]
ms.assetid: 9a98c53a-fea5-4235-b23d-6c69587c5676
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: 9092662f88410812bd6c1c2035e8d04cfa9dd434
ms.sourcegitcommit: 2a06c87aa195bc6743ebdc14b91eb71ab6b91298
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2019
ms.locfileid: "72907937"
---
# <a name="set-distribution-retention-period-for-transactional-publications"></a>Festlegen der Beibehaltungsdauer für die Verteilung von Transaktionsveröffentlichungen
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Geben Sie die Mindestbeibehaltungsdauer und die maximale Beibehaltungsdauer der Verteilung im Dialogfeld **Eigenschaften der Verteilungsdatenbank - \<Verteilungsdatenbank>** an. Dieses Dialogfeld ist über die Seite **Allgemein** des Dialogfelds **Verteilereigenschaften - \<Distributor>** verfügbar. Weitere Informationen zum Zugreifen auf dieses Dialogfeld finden Sie unter [Anzeigen und Ändern der Verteiler- und Verlegereigenschaften](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md).  
  
### <a name="to-specify-the-distribution-retention-period"></a>So geben Sie die Beibehaltungsdauer für die Verteilung an  
  
1.  Klicken Sie auf der Seite **Allgemein** des Dialogfelds **Verteilereigenschaften > \<Verteiler>** auf die Schaltfläche mit den Auslassungspunkten ( **…** ) für die Verteilungsdatenbank.  
  
2.  Zum Angeben der Mindestbeibehaltungsdauer geben Sie einen Wert in das Feld **Mindestens** ein; zum Angeben der maximalen Beibehaltungsdauer geben Sie einen Wert in das Feld **Aber nicht länger als** ein.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  

## <a name="see-also"></a>Weitere Informationen  
 [Verteilung konfigurieren](../../relational-databases/replication/configure-distribution.md)   
 [Abonnementablauf und -deaktivierung](../../relational-databases/replication/subscription-expiration-and-deactivation.md)  
  
  
