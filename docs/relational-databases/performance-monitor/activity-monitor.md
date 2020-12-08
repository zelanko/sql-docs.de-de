---
title: Aktivitätsmonitor | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie den Aktivitätsmonitor verwenden, um Informationen zu SQL Server-Prozessen anzuzeigen und dazu, wie sich diese Prozesse auf die aktuelle Instanz von SQL Server auswirken.
ms.custom: ''
ms.date: 04/07/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Activity Monitor [SQL Server]
ms.assetid: 1e6c430d-3a2a-468e-a3d5-ef5459c36c15
author: WilliamDAssafMSFT
ms.author: wiassaf
ms.openlocfilehash: 747cad801170aa9ef2e4907e96dde1b20ddc268e
ms.sourcegitcommit: 0e0cd9347c029e0c7c9f3fe6d39985a6d3af967d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96506046"
---
# <a name="activity-monitor"></a>Aktivitätsmonitor
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
Im Aktivitätsmonitor werden Informationen zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Prozessen angezeigt sowie Informationen dazu, welche Auswirkungen diese Prozesse auf die aktuelle Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]haben.  
  
Der Aktivitätsmonitor ist ein Dokumentfenster im Registerkartenformat, in dem folgende Bereiche erweitert und reduziert werden können: **Übersicht**, **Prozesse**, **Ressourcenwartevorgänge**, **Datendatei-E/A**, **Letzte ressourcenintensive Abfragen** und **Aktive ressourcenintensive Abfragen**. Wenn ein Bereich erweitert wird, fragt der Aktivitätsmonitor die Instanz nach Informationen ab. Wenn ein Bereich reduziert wird, werden sämtliche Abfrageaktivitäten für diesen Bereich angehalten. Sie können einen oder mehrere Bereiche gleichzeitig erweitern, um unterschiedliche Aktivitätstypen für die Instanz anzuzeigen.  
 
## <a name="customize-columns"></a>Anpassen von Spalten 
Für die Spalten in den Bereichen **Prozesse**, **Ressourcenwartevorgänge**, **Datendatei-E/A**, **Letzte ressourcenintensive Abfragen** und **Aktive ressourcenintensive Abfragen** können Sie die Anzeige auf folgende Weise anpassen:  
  
1.  Um die Spaltenreihenfolge zu ändern, klicken Sie auf die Spaltenüberschrift, und ziehen Sie diese an eine andere Stelle des Menübands.  
  
2.  Um eine Spalte zu sortieren, klicken Sie auf den Spaltennamen.  
  
3.  Um eine oder mehrere Spalten zu filtern, klicken Sie in der Spaltenüberschrift auf den Dropdownpfeil, und wählen Sie anschließend einen Wert aus.  

## <a name="more-information"></a>Weitere Informationen  
   
|BESCHREIBUNG|Thema|  
|-|-|  
|Beschreibt das Öffnen des Aktivitätsmonitors und das Festlegen des Aktualisierungsintervalls für den Aktivitätsmonitor.|[Öffnen des Aktivitätsmonitors &#40;SQL Server Management Studio&#41;](../../relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio.md)|  
|Stellt Links zu Themen zum Überwachen der Serverleistung und -aktivität bereit.|[Überwachen der Serverleistung und -aktivität](../../relational-databases/performance/server-performance-and-activity-monitoring.md)|  
  
  
