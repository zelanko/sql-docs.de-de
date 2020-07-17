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
ms.openlocfilehash: 0324c8424760ba10a7eae2c997cb5dfe3550e625
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85767663"
---
# <a name="set-distribution-retention-period-for-transactional-publications"></a>Festlegen der Beibehaltungsdauer für die Verteilung von Transaktionsveröffentlichungen
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
  Geben Sie die Mindestbeibehaltungsdauer und die maximale Beibehaltungsdauer der Verteilung im Dialogfeld **Eigenschaften der Verteilungsdatenbank - \<DistributionDatabase>** an. Dieses ist über die Seite **Allgemein** des Dialogfelds **Verteilereigenschaften - \<Distributor>** verfügbar. Weitere Informationen zum Zugreifen auf dieses Dialogfeld finden Sie unter [Anzeigen und Ändern der Verteiler- und Verlegereigenschaften](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md).  
  
### <a name="to-specify-the-distribution-retention-period"></a>So geben Sie die Beibehaltungsdauer für die Verteilung an  
  
1.  Klicken Sie auf der Seite **Allgemein** des Dialogfelds **Verteilereigenschaften - \<Distributor>** auf die Eigenschaftenschaltfläche ( **...** ) für die Verteilungsdatenbank.  
  
2.  Zum Angeben der Mindestbeibehaltungsdauer geben Sie einen Wert in das Feld **Mindestens** ein; zum Angeben der maximalen Beibehaltungsdauer geben Sie einen Wert in das Feld **Aber nicht länger als** ein.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  

## <a name="see-also"></a>Weitere Informationen  
 [Verteilung konfigurieren](../../relational-databases/replication/configure-distribution.md)   
 [Abonnementablauf und -deaktivierung](../../relational-databases/replication/subscription-expiration-and-deactivation.md)  
  
  
