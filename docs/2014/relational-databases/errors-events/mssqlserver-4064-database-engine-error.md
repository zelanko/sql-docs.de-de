---
title: MSSQLSERVER_4064 | Microsoft-Dokumentation
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
- 4064 (Database Engine error)
ms.assetid: 32112b90-0a2f-4834-a027-756811732be7
caps.latest.revision: 19
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 38494142ea13c7e756c3d856c8828b5dbe03bf9b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36162038"
---
# <a name="mssqlserver4064"></a>MSSQLSERVER_4064
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|4064|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DB_UFAIL_FATAL|  
|Meldungstext|Die Standarddatenbank des Benutzers kann nicht geöffnet werden. Fehler bei der Anmeldung.|  
  
## <a name="explanation"></a>Erklärung  
 Der SQL Server-Anmeldename konnte aufgrund eines Problems mit der Standarddatenbank keine Verbindung herstellen. Entweder ist die Datenbank ungültig, oder der Anmeldename besitzt keine CONNECT-Berechtigung für die Datenbank.  
  
## <a name="user-action"></a>Benutzeraktion  
 Ändern Sie mit ALTER LOGIN die Standarddatenbank für den Anmeldenamen. Gewähren Sie dem Anmeldenamen eine CONNECT-Berechtigung.  
  
  