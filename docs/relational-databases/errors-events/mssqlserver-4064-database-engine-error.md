---
title: MSSQLSERVER_4064 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 4064 (Database Engine error)
ms.assetid: 32112b90-0a2f-4834-a027-756811732be7
caps.latest.revision: 19
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c58d5a054999da21c3b2850e529a067df0edfb22
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2018
ms.locfileid: "34318761"
---
# <a name="mssqlserver4064"></a>MSSQLSERVER_4064
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
  
