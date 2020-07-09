---
title: MSSQLSERVER_611 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 611 (Database Engine error)
ms.assetid: ac6a213f-5c38-44ad-bc85-a62863786614
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 92875014b61628330f42a2ee9e631eb4b3b89ba9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85733801"
---
# <a name="mssqlserver_611"></a>MSSQLSERVER_611
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|SQL Server|  
|Ereignis-ID|611|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|VAR_SIZE_TOO_BIG|  
|Meldungstext|Es kann keine Zeile eingefügt oder aktualisiert werden, da die Gesamtgröße der Variablenspalte, einschließlich Verwaltungsbytes, die maximal zulässige Größe um %d Bytes überschreitet.|  
  
## <a name="explanation"></a>Erklärung  
Die Maximalgröße der Variablenspalte übersteigt die vom Schema zugelassene Größe. Fehler 611 wird zurückgegeben, wenn die Variablenspalte die maximal zulässige Größe überschreitet, sofern das vardecimal-Speicherformat aktiviert ist, oder wenn die Größe der Variablenspalte die in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] für komprimierte Datensätze maximal zulässige Größe überschreitet.  
  
## <a name="user-action"></a>Benutzeraktion  
Reduzieren Sie die Größe des Datensatzes.  
  
