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
ms.openlocfilehash: 201098aadeb6bd091f0312532138f692ae8079b6
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85033237"
---
# <a name="mssqlserver_4064"></a>MSSQLSERVER_4064
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|4064|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DB_UFAIL_FATAL|  
|Meldungstext|Die Standarddatenbank des Benutzers kann nicht geöffnet werden. Fehler bei der Anmeldung.|  
  
## <a name="explanation"></a>Erklärung  
 Der SQL Server-Anmeldename konnte aufgrund eines Problems mit der Standarddatenbank keine Verbindung herstellen. Entweder ist die Datenbank ungültig, oder der Anmeldename besitzt keine CONNECT-Berechtigung für die Datenbank.  
  
## <a name="user-action"></a>Benutzeraktion  
 Ändern Sie mit ALTER LOGIN die Standarddatenbank für den Anmeldenamen. Gewähren Sie dem Anmeldenamen eine CONNECT-Berechtigung.  
  
  
