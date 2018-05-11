---
title: MSSQLSERVER_945 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 945 (Database Engine error)
ms.assetid: ee501d13-0bd9-4627-896c-ed5b1bdb88b3
caps.latest.revision: 20
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4a1689953c7d91894df13e93503eda1bc1b4d0cb
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver945"></a>MSSQLSERVER_945
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|945|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DB_IS_SHUTDOWN|  
|Meldungstext|Die '%.*ls'-Datenbank kann nicht geöffnet werden, da auf einige Dateien nicht zugegriffen werden kann oder nicht genügend Platz im Arbeitsspeicher oder auf dem Datenträger zur Verfügung steht.  Ausführliche Informationen finden Sie im SQL Server-Fehlerprotokoll.|  
  
## <a name="explanation"></a>Erklärung  
Der Zugriff auf die Datenbank war nicht möglich, da Dateien oder andere Ressourcen fehlen.  
  
## <a name="user-action"></a>Benutzeraktion  
Zusätzliche Informationen zum Platz im Arbeitsspeicher, auf dem Datenträger und zum Berechtigungsfehler finden Sie im Fehlerprotokoll. Bestätigen Sie den Speicherort der MDF- und NDF-Dateien für die entsprechende Datenbank, und bestätigen Sie, dass das von [!INCLUDE[ssDE](../../includes/ssde-md.md)] verwendete Konto über eine Berechtigung für den Zugriff auf diese Dateien verfügt. Starten Sie die Datenbank neu, nachdem das Problem behoben wurde. Verwenden Sie dazu ALTER DATABASE, und legen Sie die Datenbank auf ONLINE fest.  
  
