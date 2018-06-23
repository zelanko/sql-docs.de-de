---
title: 'Datenbankspiegelung: Interoperabilität und Koexistenz (SQL Server) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- high availability [SQL Server], interoperability and coexistence
- Database Engine [SQL Server], high availability
ms.assetid: 89fef397-e0cf-4e08-b598-25b8d4170523
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2ba2e5af89a4a9eabb420e0d75a8a90b4ef48540
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36160049"
---
# <a name="database-mirroring-interoperability-and-coexistence-sql-server"></a>Datenbankspiegelung: Interoperabilität und Koexistenz (SQL Server)
  Die Datenbankspiegelung kann mit den folgenden Funktionen oder Komponenten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwendet werden:  
  
-   [AlwaysOn-Failoverclusterinstanzen (SQL Server-Failoverclustering)](database-mirroring-and-sql-server-failover-cluster-instances.md)  
  
-   [Change Data Capture (und Änderungsnachverfolgung)](../../relational-databases/track-changes/change-data-capture-and-other-sql-server-features.md)  
  
-   [Datenbank-Momentaufnahmen](../../relational-databases/databases/database-snapshots-sql-server.md)  
  
-   [Volltextkataloge](database-mirroring-and-full-text-catalogs-sql-server.md)  
  
-   [Protokollversand](database-mirroring-and-log-shipping-sql-server.md)  
  
-   [Replikation](database-mirroring-and-replication-sql-server.md)  
  
 Die Datenbankspiegelung funktioniert nicht in Verbindung mit folgenden Elementen:  
  
-   Datenbankübergreifende Transaktionen/verteilte Transaktionen  
  
     Weitere Informationen dazu, warum solche Transaktionen nicht unterstützt werden, finden Sie unter [Datenbankübergreifende Transaktionen nicht unterstützt für Datenbankspiegelungs- oder AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md).  
  
-   [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankspiegelung &#40;SQL Server&#41;](database-mirroring-sql-server.md)  
  
  