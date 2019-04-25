---
title: Überwachen von Paketausführungen und anderen Vorgängen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: cbbcd79f-ab9b-46ec-84cb-4821c1d16b99
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 6f6a4e147c90fe7c4f25f5c8b821b4787ec3be71
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62766982"
---
# <a name="monitoring-for-package-executions-and-other-operations"></a>Überwachen von Paketausführungen und anderen Vorgängen
  Sie können [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Paketausführungen, Projektüberprüfungen und andere Vorgänge mit einem oder mehreren der folgenden Tools überwachen. Bestimmte Tools, z. B. Datenabzweigungen, sind nur für Projekte verfügbar, die auf dem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Server bereitgestellt werden.  
  
-   Protokolle  
  
     Weitere Informationen finden Sie unter [Integration Services-Protokollierung &#40;SSIS&#41;](integration-services-ssis-logging.md).  
  
-   Berichte  
  
     Weitere Informationen finden Sie unter [Berichte für den Integration Services-Server](../reports-for-the-integration-services-server.md).  
  
-   Ansichten  
  
     Weitere Informationen finden Sie unter [Sichten &#40;Integration Services-Katalog&#41;](/sql/integration-services/system-views/views-integration-services-catalog).  
  
-   Leistungsindikatoren  
  
     Weitere Informationen finden Sie unter [Performance Counters](performance-counters.md).  
  
-   Datenabzweigungen  
  
## <a name="operation-types"></a>Vorgangstypen  
 Mehrere verschiedene Typen von Vorgängen werden im `SSISDB`-Katalog auf dem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Server überwacht. Jeder Vorgang kann mehrere ihm zugeordnete Meldungen aufweisen. Jede Meldung kann einem von mehreren Typklassen zugeordnet werden. Eine Meldung kann z. B. vom Typ Information, Warnung oder Fehler sein. Die vollständige Liste von Meldungstypen finden Sie in der Dokumentation zur Transact-SQL-Sicht [catalog.operation_messages &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-views/catalog-operation-messages-ssisdb-database). Eine vollständige Liste der Vorgangstypen finden Sie unter [catalog.operations &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-views/catalog-operations-ssisdb-database).  
  
 Neun verschiedene Statustypen werden verwendet, um den Status eines Vorgangs anzugeben. Eine vollständige Liste der Statustypen finden Sie in der Sicht [catalog.operations &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-views/catalog-operations-ssisdb-database).  
  
## <a name="related-content"></a>Verwandte Inhalte  
 Blogeintrag [SSIS T-SQL API Overview](https://go.microsoft.com/fwlink/?LinkId=249051)(Übersicht über die SSIS-T-SQL-API) auf blogs.msdn.com.  
  
  
