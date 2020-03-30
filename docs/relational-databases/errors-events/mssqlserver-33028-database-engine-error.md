---
title: MSSQLSERVER_33028 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 33028 (Database Engine error)
ms.assetid: c5cec0e4-0bcd-4907-826f-e7d835cfcb37
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cb42ae68df92466ab30cbb45f6ea526658143795
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "67908485"
---
# <a name="mssqlserver_33028"></a>MSSQLSERVER_33028
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|33028|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SEC_CRYPTOPROV_CANTOPENSESSION|  
|Meldungstext|Sitzung kann nicht für %S_MSG ‚%.*ls’ geöffnet werden. Anbieterfehlercode: %d.|  
  
## <a name="explanation"></a>Erklärung  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] konnte den in der Fehlermeldung aufgelisteten Kryptografieanbieter nicht öffnen. Der Kryptografieanbieter hat den aufgelisteten Fehlercode angegeben. Sie müssen möglicherweise den Kryptografieanbieter für weitere Informationen über den Fehler verständigen.  
  
|Fehlercode|BESCHREIBUNG|  
|--------------|---------------|  
|0|Erfolg. Kein Fehler.|  
|1|Fehler. Ein unbekannter oder unerwarteter Fehler ist aufgetreten. Es sind keine zusätzlichen Informationen verfügbar.|  
|2|Nicht genügend Pufferspeicher. Speicherplatz konnte nicht für den Kryptografieanbieter reserviert werden.|  
|3|Nicht unterstützt. Der Kryptografieanbieter wird nicht von dieser Version unterstützt. Wählen Sie einen anderen Kryptografieanbieter aus.|  
|4|Nicht gefunden. Der angegebene Kryptografieanbieter ist nicht vorhanden,oder Sie haben keine Autorisierung für den Zugriff auf die Dateien.|  
|5|Authorization Failure. Dies kann durch ein falsches Kennwort oder einen falschen Benutzernamen bei der Erstellung von Anmeldeinformationen verursacht werden. Dies kann verursacht werden, wenn die Anmeldeinformationen nicht vorhanden sind.|  
|6|Ungültiges Argument. Ein ungültiges Argument wurde an den Kryptografieanbieter übergeben.|  
  
## <a name="user-action"></a>Benutzeraktion  
Beheben Sie den Fehler oder wenden Sie sich an den Kryptografieanbieter, um weitere Informationen zu erhalten.  
  
