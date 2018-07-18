---
title: MSSQLSERVER_5245 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 5245 (Database Engine error)
ms.assetid: 6005c9ec-ccdd-4def-9eb4-37cdb599ddb3
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f2df27a5e730b67ea9c95c9b3f1eca52204659f0
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37427979"
---
# <a name="mssqlserver5245"></a>MSSQLSERVER_5245
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|5245|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC4_TABLE_LOCK_TIMEOUT_EXCEEDED|  
|Meldungstext|Objekt-ID O_ID ('NAME'-Objekt): DBCC konnte keine Sperre für dieses Objekt erhalten, da das Timeout für die Sperranforderung überschritten wurde. Das Objekt wurde ausgelassen und wird nicht verarbeitet.|  
  
## <a name="explanation"></a>Erklärung  
 Ein Sperrtimeout ist aufgetreten, während DBCC auf eine Tabellensperre für das angegebene Objekt gewartet hat.  
  
## <a name="user-action"></a>Benutzeraktion  
 Führen Sie den DBCC-Befehl erneut aus.  
  
  
