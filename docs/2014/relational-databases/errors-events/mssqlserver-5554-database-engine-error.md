---
title: MSSQLSERVER_5554 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 5554 (Database Engine error)
ms.assetid: 7134bbe5-d240-4a98-85ce-b13cc8ae9b0e
caps.latest.revision: 11
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1c7db414ef084b8117b93607e13d76ec128688db
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37423869"
---
# <a name="mssqlserver5554"></a>MSSQLSERVER_5554
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|MSSQLSERVER|  
|Ereignis-ID|5554|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|FS_MINIVER_OVERFLOW|  
|Meldungstext|Das maximale Limit des Dateisystems an Versionen insgesamt für eine einzige Datei wurde erreicht.|  
  
## <a name="explanation"></a>Erklärung  
 In MARS (Multiple Active Result Sets) oder Triggerszenarios verwendet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Miniversion des Betriebssystems.  
  
## <a name="user-action"></a>Benutzeraktion  
 Versuchen Sie, wiederholte Datenupdates in derselben Transaktion zu vermeiden.  
  
  
