---
title: MSSQLSERVER_4064 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 4064 (Database Engine error)
ms.assetid: 32112b90-0a2f-4834-a027-756811732be7
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 69332b6d2830c53d5a3f9956443d123fd52485b3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48181478"
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
  
  
