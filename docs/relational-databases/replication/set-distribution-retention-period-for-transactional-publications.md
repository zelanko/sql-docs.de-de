---
title: Festlegen der Beibehaltungsdauer für die Verteilung
description: Erfahren Sie, wie Sie in SQL Server Management Studio (SSMS) die Beibehaltungsdauer für Daten in der Verteilungsdatenbank festlegen.
ms.custom: seo-lt-2019
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
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: d699eb502d99818926e92ff07a8fc16248aeee3d
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "76287207"
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
  
  
