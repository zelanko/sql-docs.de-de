---
title: MSSQLSERVER_9004 | Microsoft-Dokumentation
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
- 9004 (Database Engine error)
ms.assetid: b528bb49-340c-4a81-9c8d-cefce6562f16
caps.latest.revision: 16
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 80536d36b0e9dc955a5b64d9e79b36fdc7130e8e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36162256"
---
# <a name="mssqlserver9004"></a>MSSQLSERVER_9004
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|9004|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|LOG_CORRUPT|  
|Meldungstext|Fehler beim Verarbeiten des Protokolls für die '%.*ls'-Datenbank.  Führen Sie nach Möglichkeit eine Wiederherstellung von einer Sicherung aus. Falls keine Sicherung verfügbar ist, muss das Protokoll möglicherweise neu erstellt werden.|  
  
## <a name="explanation"></a>Erklärung  
 Bei der Verarbeitung des Protokolls während eines Rollbacks, einer Wiederherstellung oder Replikation ist ein Fehler aufgetreten. Dabei kann es sich um einen vom Betriebssystem erkannten Fehler oder um einen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erkannten internen Konsistenzfehler handeln.  
  
## <a name="user-action"></a>Benutzeraktion  
 Durch eine der folgenden Aktionen wird dieser Fehler korrigiert:  
  
-   Nehmen Sie eine Wiederherstellung aus einer Sicherung vor.  
  
-   Erstellen Sie das Protokoll neu.  
  
 Überprüfen Sie außerdem die Systemereignis- und Fehlerprotokolle, um Probleme innerhalb des Systems zu identifizieren, die für den Fehler verantwortlich sein können.  
  
  