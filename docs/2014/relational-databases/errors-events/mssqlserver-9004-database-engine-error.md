---
title: MSSQLSERVER_9004 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 9004 (Database Engine error)
ms.assetid: b528bb49-340c-4a81-9c8d-cefce6562f16
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c80678bc5463f3cf17d8442afb36c30dcc69534c
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37429409"
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
  
  
