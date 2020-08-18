---
description: MSSQLSERVER_21871
title: MSSQLSERVER_21871 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 21871 (Database Engine error)
ms.assetid: d3215378-9282-444f-a18b-00b96fd0133d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 52f82fbebc9f164152f6047a90bbb1238e1a2bb7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88332786"
---
# <a name="mssqlserver_21871"></a>MSSQLSERVER_21871
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|SQL Server|  
|Ereignis-ID|21871|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SQLErrorNum21871|  
|Meldungstext|Verleger %s der Datenbank %s wurde nicht umgeleitet.|  
  
## <a name="explanation"></a>Erklärung  
**sp_validate_replica_hosts_as_publishers** überprüft die Tabelle MSredirected_publishers in der Verteilungsdatenbank auf einen Eintrag für den identifizierten Verleger und die Verlegerdatenbank.  **sp_validate_replica_hosts_as_publishers** gibt den Fehler 21871 zurück, wenn kein Eintrag gefunden wird.  
  
## <a name="user-action"></a>Benutzeraktion  
**sp_validate_replica_hosts_as_publishers** ist nur für umgeleitete Verleger relevant. Wenn eine veröffentlichte Datenbank Mitglied einer Always On-Verfügbarkeitsgruppe ist, führen Sie die gespeicherte Prozedur **sp_redirect_publisher** aus, um den Verleger und die Verlegerdatenbank mit dem Verfügbarkeitsgruppen-Listener-Namen der Verfügbarkeitsgruppe zu verknüpfen.  
  
