---
title: MSSQLSERVER_945 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 945 (Database Engine error)
ms.assetid: ee501d13-0bd9-4627-896c-ed5b1bdb88b3
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f8c2cf1abfb41f4a49fccfe1befad11e429037da
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62761745"
---
# <a name="mssqlserver945"></a>MSSQLSERVER_945
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|945|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DB_IS_SHUTDOWN|  
|Meldungstext|Die '%.*ls'-Datenbank kann nicht geöffnet werden, da auf einige Dateien nicht zugegriffen werden kann oder nicht genügend Platz im Arbeitsspeicher oder auf dem Datenträger zur Verfügung steht.  Ausführliche Informationen finden Sie im SQL Server-Fehlerprotokoll.|  
  
## <a name="explanation"></a>Erklärung  
Der Zugriff auf die Datenbank war nicht möglich, da Dateien oder andere Ressourcen fehlen.  
  
## <a name="user-action"></a>Benutzeraktion  
Zusätzliche Informationen zum Platz im Arbeitsspeicher, auf dem Datenträger und zum Berechtigungsfehler finden Sie im Fehlerprotokoll. Bestätigen Sie den Speicherort der MDF- und NDF-Dateien für die entsprechende Datenbank, und bestätigen Sie, dass das von [!INCLUDE[ssDE](../../includes/ssde-md.md)] verwendete Konto über eine Berechtigung für den Zugriff auf diese Dateien verfügt. Starten Sie die Datenbank neu, nachdem das Problem behoben wurde. Verwenden Sie dazu ALTER DATABASE, und legen Sie die Datenbank auf ONLINE fest.  
  
