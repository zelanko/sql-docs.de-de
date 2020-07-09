---
title: Verwenden eigenständiger Datenbanken mit Always On-Verfügbarkeitsgruppen
description: Verwenden eigenständiger Datenbanken mit einer Always On-Verfügbarkeitsgruppe
ms.custom: seodec18
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], interoperability
- contained database, AlwaysOnAvailabilityGroups
ms.assetid: cacce3ae-e940-4566-8298-6607c4268e74
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 58bbe0be8b2e139327605e674c580b7520b32af9
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85893196"
---
# <a name="use-contained-databases-with-always-on-availability-groups"></a>Verwenden eigenständiger Datenbanken mit Always On-Verfügbarkeitsgruppen 
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]

  Dieses Thema enthält Informationen zum Verwenden einer eigenständigen Datenbank in [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] mit [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a> Voraussetzungen  
  
-   Vor dem Hinzufügen einer enthaltenen Datenbank zu einer Verfügbarkeitsgruppe muss gewährleistet sein, dass die Serveroption **contained database authentication** auf jeder Serverinstanz, die ein Verfügbarkeitsreplikat für die Verfügbarkeitsgruppe hostet, auf **1** gesetzt ist. Weitere Informationen finden Sie unter [Contained Database Authentication (Serverkonfigurationsoption)](../../../database-engine/configure-windows/contained-database-authentication-server-configuration-option.md) und [Serverkonfigurationsoptionen &#40;SQL Server&#41;](../../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Serverkonfigurationsoptionen &#40;SQL Server&#41;](../../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Eigenständige Datenbanken](../../../relational-databases/databases/contained-databases.md)  
  
  
