---
title: Eigenständige Datenbanken bei Always On-Verfügbarkeitsgruppen (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- contained database [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: cacce3ae-e940-4566-8298-6607c4268e74
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 74c8a0b41ee7224dad83fb41691a4898c15b7b38
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84936913"
---
# <a name="contained-databases-with-always-on-availability-groups-sql-server"></a>Eigenständige Datenbanken bei Always On-Verfügbarkeitsgruppen (SQL Server)
  Dieses Thema enthält Informationen zum Verwenden einer eigenständigen Datenbank in [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] mit [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
 **In diesem Thema:**  
  
-   [Voraussetzungen](#Prerequisites)  
  
-   [Verwandte Aufgaben](#RelatedTasks)  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a> Voraussetzungen  
  
-   Vor dem Hinzufügen einer enthaltenen Datenbank zu einer Verfügbarkeitsgruppe muss gewährleistet sein, dass die Serveroption `contained database authentication` auf jeder Serverinstanz, die ein Verfügbarkeitsreplikat für die Verfügbarkeitsgruppe hostet, auf `1` gesetzt ist. Weitere Informationen finden Sie unter [Contained Database Authentication (Serverkonfigurationsoption)](../../configure-windows/contained-database-authentication-server-configuration-option.md) und [Serverkonfigurationsoptionen &#40;SQL Server&#41;](../../configure-windows/server-configuration-options-sql-server.md).  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Serverkonfigurationsoptionen &#40;SQL Server&#41;](../../configure-windows/server-configuration-options-sql-server.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Eigenständige Datenbanken](../../../relational-databases/databases/contained-databases.md)  
  
  
