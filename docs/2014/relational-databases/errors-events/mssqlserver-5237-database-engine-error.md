---
title: MSSQLSERVER_5237 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5237 (Database Engine error)
ms.assetid: 9ff28935-d1eb-47ee-99b3-1a65cb948ce7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 224317e290ce15aaed979129733b6273b3b663df
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85032736"
---
# <a name="mssqlserver_5237"></a>MSSQLSERVER_5237
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|5237|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC4_INDEXED_VIEW_CHECK_QUERY_FAILED_NO_ERRORCODE|  
|Meldungstext|Fehler bei der rowsetübergreifenden DBCC-Überprüfung für das 'NAME'-Objekt (Objekt-ID O_ID) aufgrund eines internen Abfragefehlers.|  
  
## <a name="explanation"></a>Erklärung  
 Ein interner Fehler ist aufgetreten, weil DBCC die Abfrage zum Überprüfen indizierter Sichten nicht ausführen konnte.  
  
## <a name="user-action"></a>Benutzeraktion  
 Führen Sie den DBCC-Befehl erneut aus.  
  
  
