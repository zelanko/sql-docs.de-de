---
title: Aktivitätsmonitor | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Activity Monitor [SQL Server]
ms.assetid: 1e6c430d-3a2a-468e-a3d5-ef5459c36c15
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f2420a4df5b971ae2190b2a66f24b226f472fee2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63249343"
---
# <a name="activity-monitor"></a>Aktivitätsmonitor
  Im Aktivitätsmonitor werden Informationen zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Prozessen angezeigt sowie Informationen dazu, welche Auswirkungen diese Prozesse auf die aktuelle Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]haben.  
  
## <a name="benefits-of-activity-monitor"></a>Vorteile des Aktivitätsmonitors  
 Aktivitätsmonitor ist ein Dokument mit Registerkarten im Fenster mit den folgenden erweiterbaren und reduzierbaren Bereichen: **Übersicht**, **Active User Tasks** (Aktive Benutzertasks), **Ressourcenwartevorgänge**, **Datendatei-E/A** und **Letzte ressourcenintensive Abfragen**. Wenn ein Bereich erweitert wird, fragt der Aktivitätsmonitor die Instanz nach Informationen ab. Wenn ein Bereich reduziert wird, werden sämtliche Abfrageaktivitäten für diesen Bereich angehalten. Sie können auch einen oder mehrere Bereiche gleichzeitig erweitern, um unterschiedliche Aktivitätstypen für die Instanz anzuzeigen.  
  
 Für die Spalten, die in enthalten sind die **aktive Benutzertasks**, **Ressourcenwartevorgänge**, **Data File i/o**, und **aktuelle wertvolle Abfragen** Bereiche, können Sie die Anzeige auf folgende Weise anpassen:  
  
1.  Um die Reihenfolge der Spalten zu ändern, klicken Sie auf die Spaltenüberschrift, und ziehen Sie diese an eine andere Stelle des Menübands.  
  
2.  Um eine Spalte zu sortieren, klicken Sie auf den Spaltennamen.  
  
3.  Um eine oder mehrere Spalten zu filtern, klicken Sie in der Spaltenüberschrift auf den Dropdownpfeil, und wählen Sie anschließend einen Wert aus.  
  
## <a name="related-tasks"></a>Related Tasks  
 Verwenden Sie für die ersten Schritte mit dem Aktivitätsmonitor die folgenden Tasks:  
  
|||  
|-|-|  
|**Beschreibung**|**Thema**|  
|Beschreibt das Öffnen des Aktivitätsmonitors und das Festlegen des Aktualisierungsintervalls für den Aktivitätsmonitor.|[Öffnen des Aktivitätsmonitors &#40;SQL Server Management Studio&#41;](../performance-monitor/open-activity-monitor-sql-server-management-studio.md)|  
|Stellt Links zu Themen zum Überwachen der Serverleistung und -aktivität bereit.|[Überwachen der Serverleistung und -aktivität](../performance/server-performance-and-activity-monitoring.md)|  
  
  
