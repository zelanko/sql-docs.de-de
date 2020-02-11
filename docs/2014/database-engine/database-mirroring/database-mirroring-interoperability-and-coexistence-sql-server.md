---
title: 'Datenbankspiegelung: Interoperabilität und Koexistenz (SQL Server) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- high availability [SQL Server], interoperability and coexistence
- Database Engine [SQL Server], high availability
ms.assetid: 89fef397-e0cf-4e08-b598-25b8d4170523
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 2f38e7bac91c4d65e9c6209d693a598466096069
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62807306"
---
# <a name="database-mirroring-interoperability-and-coexistence-sql-server"></a>Datenbankspiegelung: Interoperabilität und Koexistenz (SQL Server)
  Die Datenbankspiegelung kann mit den folgenden Funktionen oder Komponenten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwendet werden:  
  
-   [AlwaysOn-Failoverclusterinstanzen (SQL Server-Failoverclustering)](database-mirroring-and-sql-server-failover-cluster-instances.md)  
  
-   [Change Data Capture (und Änderungs Nachverfolgung)](../../relational-databases/track-changes/change-data-capture-and-other-sql-server-features.md)  
  
-   [Datenbank-Momentaufnahmen](../../relational-databases/databases/database-snapshots-sql-server.md)  
  
-   [Voll Text Kataloge](database-mirroring-and-full-text-catalogs-sql-server.md)  
  
-   [Protokoll Versand](database-mirroring-and-log-shipping-sql-server.md)  
  
-   [Replikation](database-mirroring-and-replication-sql-server.md)  
  
 Die Datenbankspiegelung funktioniert nicht in Verbindung mit folgenden Elementen:  
  
-   Datenbankübergreifende Transaktionen/verteilte Transaktionen  
  
     Weitere Informationen dazu, warum solche Transaktionen nicht unterstützt werden, finden Sie unter [Datenbankübergreifende Transaktionen nicht unterstützt für Datenbankspiegelungs- oder AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md).  
  
-   [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbankspiegelung &#40;SQL Server&#41;](database-mirroring-sql-server.md)  
  
  
