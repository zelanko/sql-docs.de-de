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
ms.openlocfilehash: ae11fbccaa4f577815e503d9a0dffaa34c7c04ed
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85723613"
---
# <a name="mssqlserver_33028"></a>MSSQLSERVER_33028
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
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
  
