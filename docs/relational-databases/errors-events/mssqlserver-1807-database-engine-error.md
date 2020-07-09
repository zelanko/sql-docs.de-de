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
ms.openlocfilehash: 0891558792174f7813446d5c532758e00b45b2e4
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85780675"
---
# <a name="mssqlserver_1807"></a>MSSQLSERVER_1807
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
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
  
