---
title: MSSQLSERVER_611 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 611 (Database Engine error)
ms.assetid: ac6a213f-5c38-44ad-bc85-a62863786614
caps.latest.revision: 19
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0c61febeb9eba4be69978e1966cbf754f8f1a3ff
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37424839"
---
# <a name="mssqlserver611"></a>MSSQLSERVER_611
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|611|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|VAR_SIZE_TOO_BIG|  
|Meldungstext|Es kann keine Zeile eingefügt oder aktualisiert werden, da die Gesamtgröße der Variablenspalte, einschließlich Verwaltungsbytes, die maximal zulässige Größe um %d Bytes überschreitet.|  
  
## <a name="explanation"></a>Erklärung  
 Die Maximalgröße der Variablenspalte übersteigt die vom Schema zugelassene Größe. Fehler 611 wird zurückgegeben, wenn die Variablenspalte die maximal zulässige Größe überschreitet, sofern das vardecimal-Speicherformat aktiviert ist, oder wenn die Größe der Variablenspalte die in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] für komprimierte Datensätze maximal zulässige Größe überschreitet.  
  
## <a name="user-action"></a>Benutzeraktion  
 Reduzieren Sie die Größe des Datensatzes.  
  
  
