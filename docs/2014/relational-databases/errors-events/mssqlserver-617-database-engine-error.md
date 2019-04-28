---
title: MSSQLSERVER_617 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 617 (Database Engine error)
ms.assetid: 213545d9-08a7-4427-bfd1-8b7e16644281
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f63983243d0859fcb7ebaaf1ac5d184757d1f274
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62867200"
---
# <a name="mssqlserver617"></a>MSSQLSERVER_617
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|617|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|NODESHASH|  
|Meldungstext|Der Deskriptor für die Objekt-ID %ld in der Datenbank mit der ID %d wurde in der Hashtabelle beim Versuch, ihn aus dieser zu entfernen, nicht gefunden. In einer Arbeitstabelle fehlt ein Eintrag. Führen Sie die Abfrage erneut aus. Falls ein Cursor beteiligt ist, schließen Sie den Cursor, und öffnen Sie ihn erneut.|  
  
## <a name="explanation"></a>Erklärung  
SQL Server kann die Arbeitstabelle für einen bestimmten Eintrag nicht finden.  
  
## <a name="user-action"></a>Benutzeraktion  
  
1.  Falls ein Cursor beteiligt ist, schließen Sie den Cursor, und öffnen Sie ihn dann erneut.  
  
2.  Führen Sie die Abfrage erneut aus.  
  
