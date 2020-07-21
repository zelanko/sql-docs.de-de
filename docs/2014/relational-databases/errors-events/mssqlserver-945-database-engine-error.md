---
title: MSSQLSERVER_945 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 945 (Database Engine error)
ms.assetid: ee501d13-0bd9-4627-896c-ed5b1bdb88b3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 913778fc4c40a76cb3a7f5aca07b981567428253
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86553065"
---
# <a name="mssqlserver_945"></a>MSSQLSERVER_945
    
## <a name="details"></a>Details  
  
|attribute|Wert|  
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
  
  
