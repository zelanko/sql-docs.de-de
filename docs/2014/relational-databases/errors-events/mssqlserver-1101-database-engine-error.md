---
title: MSSQLSERVER_1101 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 1101 (Database Engine error)
ms.assetid: d63b67d5-59f5-4f77-904e-5ba67f2dd850
caps.latest.revision: 18
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1043e24d95731faafa4dcd074bd5a6bb2257c47a
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37413139"
---
# <a name="mssqlserver1101"></a>MSSQLSERVER_1101
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|1101|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|NOALLOCPG|  
|Meldungstext|Eine neue Seite für die '%.*ls'-Datenbank konnte nicht zugeordnet werden, weil in der Dateigruppe '%.\*ls' nicht genügend Speicherplatz verfügbar ist. Speicherplatz kann durch Löschen von Objekten in der Dateigruppe, Hinzufügen von Dateien zur Dateigruppe oder Festlegen der automatischen Vergrößerung für vorhandene Dateien in der Dateigruppe gewonnen werden.|  
  
## <a name="explanation"></a>Erklärung  
 In einer Dateigruppe ist kein Speicherplatz verfügbar.  
  
## <a name="user-action"></a>Benutzeraktion  
 Durch die folgenden Aktionen kann Speicherplatz in der Dateigruppe verfügbar gemacht werden.  
  
-   Aktivieren Sie AUTOGROW.  
  
-   Fügen Sie der Dateigruppe weitere Dateien hinzu.  
  
-   Geben Sie Speicherplatz frei, indem sich nicht benötigte Indizes oder Tabellen in der Dateigruppe löschen.  
  
  
