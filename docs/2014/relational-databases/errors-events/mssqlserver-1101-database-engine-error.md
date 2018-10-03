---
title: MSSQLSERVER_1101 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1101 (Database Engine error)
ms.assetid: d63b67d5-59f5-4f77-904e-5ba67f2dd850
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d4468e85f8170ecb6b23abf5af8ee3a114a6bef3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48152164"
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
  
  
