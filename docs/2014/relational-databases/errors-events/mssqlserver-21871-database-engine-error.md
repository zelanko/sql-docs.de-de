---
title: MSSQLSERVER_21871 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 21871 (Database Engine error)
ms.assetid: d3215378-9282-444f-a18b-00b96fd0133d
caps.latest.revision: 7
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 910fc06aac87eb846c0db76956eb45377fa3ecdb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36058302"
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
 `sp_validate_replica_hosts_as_publishers` überprüft die Tabelle MSredirected_publishers in der Verteilungsdatenbank für einen Eintrag für den identifizierten Verleger und der Verlegerdatenbank.  `sp_validate_replica_hosts_as_publishers` gibt den Fehler 21871 zurück, wenn kein Eintrag gefunden wird.  
  
## <a name="user-action"></a>Benutzeraktion  
 `sp_validate_replica_hosts_as_publishers` ist nur für umgeleitete Verleger relevant. Wenn eine veröffentlichte Datenbank Mitglied einer AlwaysOn-Verfügbarkeitsgruppe ist, führen Sie die gespeicherte Prozedur `sp_redirect_publisher` aus, um den Verleger und die Verlegerdatenbank mit dem Verfügbarkeitsgruppenlistenernamen der Verfügbarkeitsgruppe zu verknüpfen.  
  
  