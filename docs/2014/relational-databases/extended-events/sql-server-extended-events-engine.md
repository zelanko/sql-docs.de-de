---
title: Engine für erweiterte Ereignisse von SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- extended events [SQL Server], engine
ms.assetid: d74642a5-42b9-4a15-aa3d-f98bfe695050
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 89d92fc60e18926351cc94e6e6c21a32a7371ed5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62638235"
---
# <a name="sql-server-extended-events-engine"></a>Engine für erweiterte Ereignisse von SQL Server
  Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Extended Events-Engine ist eine Sammlung von Diensten und Objekten, die:  
  
-   die Definition von Ereignissen ermöglichen,  
  
-   die Verarbeitung von Ereignisdaten ermöglichen,  
  
-   Dienste und Objekte für erweiterte Ereignisse im System verwalten und  
  
-   eine Liste von Sitzungen für erweiterte Ereignisse führen und den Zugriff auf diese Liste verwalten.  
  
 Die Engine für erweiterte Ereignisse selbst stellt keine Ereignisse oder beim Auslösen eines Ereignisses erforderlichen Aktionen bereit. Die Prozesse, die die Engine für erweiterte Ereignisse verwenden, definieren die Interaktion mit der Engine. Diese Prozesse fügen Ereignispunkte hinzu und stellen die bei Auslösung eines Ereignisses erforderlichen Aktionen bereit.  
  
 Die folgende Abbildung zeigt eine vereinfachte Ansicht einer Sitzung für erweiterte Ereignisse. Weitere Informationen finden Sie unter [SQL Server Extended Events Sessions](sql-server-extended-events-sessions.md).  
  
 ![Detaillierte Architektur von erweiterten Ereignissen](../../database-engine/media/xearchitecturedetailed.gif "Detailed extended events architecture")  
  
 Beachten Sie Folgendes:  
  
-   Jeder Windows-Prozess kann über ein oder mehrere Module (**Win32-Prozess**, **Win32-Modul**) verfügen. Diese werden auch als *Binärdateien* oder *ausführbare Module*bezeichnet.  
  
-   Jedes Windows-Prozessmodul kann mindestens ein Paket für erweiterte Ereignisse (**Paket**) enthalten, das wiederum mindestens ein Objekt für erweiterte Ereignisse (**Typ**, **Ziel**, **Aktion**, **Zuordnung**, **Prädikat**und **Ereignis**) enthalten kann.  
  
-   Ein Hostprozess kann nur eine Instanz der Engine für erweiterte Ereignisse (**Engine für erweiterte Ereignisse**) aufweisen. Dieses führt die folgenden Aufgaben aus:  
  
    -   Es verwaltet einige Aspekte der Sitzung (z. B. das Aufzählen von Sitzungen).  
  
    -   Es übernimmt die Verteilung (**Verteiler**). Dies ist mit einem Threadpool vergleichbar.  
  
    -   Es verarbeitet Speicherpuffer (**Puffer**) für Ereignisse. Wenn Puffer aufgefüllt sind, werden sie an Ziele verteilt.  
  
-   Wenn eine Sitzung erstellt wurde und optional Ereignisse an die Sitzung (**Sitzungskontext**) gebunden wurden:  
  
    -   Es können auch Instanzen von Zielen (**Zielinstanz**) erstellt und der Sitzung hinzugefügt werden.  
  
    -   Wenn Puffer aufgefüllt sind, werden diese an Ziele verteilt.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterte Ereignisse](extended-events.md)  
  
  
