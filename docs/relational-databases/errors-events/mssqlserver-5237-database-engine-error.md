---
title: MSSQLSERVER_5237 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 5237 (Database Engine error)
ms.assetid: 9ff28935-d1eb-47ee-99b3-1a65cb948ce7
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8f69f46dc3f34a2697494bd316b40959a9854671
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47741498"
---
# <a name="mssqlserver5237"></a>MSSQLSERVER_5237
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|5237|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC4_INDEXED_VIEW_CHECK_QUERY_FAILED_NO_ERRORCODE|  
|Meldungstext|Fehler bei der rowsetübergreifenden DBCC-Überprüfung für das 'NAME'-Objekt (Objekt-ID O_ID) aufgrund eines internen Abfragefehlers.|  
  
## <a name="explanation"></a>Erklärung  
Ein interner Fehler ist aufgetreten, weil DBCC die Abfrage zum Überprüfen indizierter Sichten nicht ausführen konnte.  
  
## <a name="user-action"></a>Benutzeraktion  
Führen Sie den DBCC-Befehl erneut aus.  
  
