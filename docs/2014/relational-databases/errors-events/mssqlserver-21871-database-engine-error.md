---
title: MSSQLSERVER_21871 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21871 (Database Engine error)
ms.assetid: d3215378-9282-444f-a18b-00b96fd0133d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 832ee3caa23a034f1c228d01ff8ec2ceda32de06
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48151013"
---
# <a name="mssqlserver21871"></a>MSSQLSERVER_21871
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|21871|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SQLErrorNum21871|  
|Meldungstext|Verleger %s der Datenbank %s wurde nicht umgeleitet.|  
  
## <a name="explanation"></a>Erklärung  
 `sp_validate_replica_hosts_as_publishers` überprüft die Tabelle MSredirected_publishers in der Verteilungsdatenbank für einen Eintrag für den identifizierten Verleger und die Publisher-Datenbank.  `sp_validate_replica_hosts_as_publishers` gibt den Fehler 21871 zurück, wenn kein Eintrag gefunden wird.  
  
## <a name="user-action"></a>Benutzeraktion  
 `sp_validate_replica_hosts_as_publishers` ist nur für umgeleitete Verleger relevant. Wenn eine veröffentlichte Datenbank Mitglied einer AlwaysOn-Verfügbarkeitsgruppe ist, führen Sie die gespeicherte Prozedur `sp_redirect_publisher` aus, um den Verleger und die Verlegerdatenbank mit dem Verfügbarkeitsgruppenlistenernamen der Verfügbarkeitsgruppe zu verknüpfen.  
  
  
