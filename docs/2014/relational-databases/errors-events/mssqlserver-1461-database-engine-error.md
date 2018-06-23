---
title: MSSQLSERVER_1461 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 1461 (Database Engine error)
ms.assetid: fce10907-4753-441b-b624-f28e00ed7520
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 663aeec8ff61ce1717392c32d4f97e71403d1b5c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36057572"
---
# <a name="mssqlserver1461"></a>MSSQLSERVER_1461
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|1461|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBM_SAFETY_MISMATCH|  
|Meldungstext|Für die "%.*ls"-Datenbank wurden bei den Servern unterschiedliche Sicherheitsstufen für die Datenbankspiegelung gefunden. Die Sicherheitsstufe FULL wird verwendet.|  
  
## <a name="explanation"></a>Erklärung  
 Die Spiegelungsverbindungen wurden unterbrochen, als die Sicherheitsstufe der Transaktion geändert wurde, da die Sicherheitseinstellungen der Transaktion für die Prinzipal- und Spiegeldatenbank inkonsistent waren. Es wird die Standardsicherheitseinstellung der Sicherheit für vollständige Transaktionen verwendet. Die Sitzung wird im Modus für hohe Sicherheit ausgeführt.  
  
## <a name="user-action"></a>Benutzeraktion  
 Wenn Sie die Transaktionssicherheit initiieren möchten, führen Sie die ALTER DATABASE *Datenbank_Name* SET PARTNER SAFETY OFF-Anweisung für die Prinzipaldatenbank erneut aus.  
  
  