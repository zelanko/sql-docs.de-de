---
title: MSSQLSERVER_9004 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9004 (Database Engine error)
ms.assetid: b528bb49-340c-4a81-9c8d-cefce6562f16
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 93fa5124f0f64607c74f95d3db215fb35073ba0c
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85053503"
---
# <a name="mssqlserver_9004"></a>MSSQLSERVER_9004
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
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
  
  
