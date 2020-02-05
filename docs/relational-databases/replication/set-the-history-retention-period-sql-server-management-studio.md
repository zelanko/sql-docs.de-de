---
title: Festlegen der Beibehaltungsdauer für den Verlauf (SSMS)
description: Erfahren Sie, wie Sie in SQL Server Management Studio (SSMS) die Beibehaltungsdauer für den Verlauf der Verteilungsdatenbank festlegen.
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- history retention periods [SQL Server replication]
- retention periods [SQL Server replication]
ms.assetid: c288daab-5181-4d4b-ba2a-8a147098e758
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 6f9ada00c3166637ca1c5721b17ed950df58a4e2
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "76287197"
---
# <a name="set-the-history-retention-period-sql-server-management-studio"></a>Festlegen der Beibehaltungsdauer für den Verlauf (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Die Beibehaltungsdauer für den Verlauf wird auf der Seite **General** des Dialogfelds **Distribution Database Properties - \<DistributionDatabase>** angegeben. Mit dieser Einstellung wird angegeben, wie lange der Replikations-Agentverlauf gespeichert werden soll. Diese Seite ist über die Seite **General** des Dialogfelds **Verteilereigenschaften - \<Distributor>** verfügbar. Weitere Informationen zum Zugreifen auf dieses Dialogfeld finden Sie unter [Anzeigen und Ändern der Verteiler- und Verlegereigenschaften](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md).  
  
### <a name="to-specify-the-history-retention-period"></a>So geben Sie die Beibehaltungsdauer für den Verlauf an  
  
1.  Klicken Sie auf der Seite **Allgemein** des Dialogfelds **Verteilereigenschaften - \<Distributor>** auf die Schaltfläche mit den drei Punkten ( **…** ) für die Verteilungsdatenbank.  
  
2.  Geben Sie im Feld **Replikationsleistungsverlauf speichern** einen Wert ein.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verteilung konfigurieren](../../relational-databases/replication/configure-distribution.md)  
  
  
