---
title: MSSQLSERVER_1807 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 1807 (Database Engine error)
ms.assetid: 13c1b240-098b-4d9e-89aa-21599548e074
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 69acb74bd1c50900ae4852c41b3304da7ca7c00c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62869463"
---
# <a name="mssqlserver1807"></a>MSSQLSERVER_1807
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|1807|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|CANNOT_EX_LOCK|  
|Meldungstext|Es konnte keine exklusive Sperre für die '%.*ls'-Datenbank erhalten werden. Wiederholen Sie den Vorgang zu einem späteren Zeitpunkt.|  
  
## <a name="explanation"></a>Erklärung  
Ein Vorgang, für den ein exklusiver Zugriff auf die Datenbank erforderlich war, konnte ihn nicht erhalten.  
  
## <a name="user-action"></a>Benutzeraktion  
Trennen Sie alle Verbindungen mit der entsprechenden Datenbank, oder versuchen Sie die Abfrage zu einem späteren Zeitpunkt erneut.  
  
