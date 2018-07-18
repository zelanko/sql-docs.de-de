---
title: MSSQLSERVER_1807 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 1807 (Database Engine error)
ms.assetid: 13c1b240-098b-4d9e-89aa-21599548e074
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e7cdba5b23f82f7051966ca171abaf18fed8e0d0
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2018
ms.locfileid: "34318241"
---
# <a name="mssqlserver1807"></a>MSSQLSERVER_1807
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|1807|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|CANNOT_EX_LOCK|  
|Meldungstext|Es konnte keine exklusive Sperre für die '%.*ls'-Datenbank erhalten werden. Wiederholen Sie den Vorgang zu einem späteren Zeitpunkt.|  
  
## <a name="explanation"></a>Erklärung  
Ein Vorgang, für den ein exklusiver Zugriff auf die Datenbank erforderlich war, konnte ihn nicht erhalten.  
  
## <a name="user-action"></a>Benutzeraktion  
Trennen Sie alle Verbindungen mit der entsprechenden Datenbank, oder versuchen Sie die Abfrage zu einem späteren Zeitpunkt erneut.  
  
