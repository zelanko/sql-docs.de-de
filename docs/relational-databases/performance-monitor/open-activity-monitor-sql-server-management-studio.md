---
title: Öffnen des Aktivitätsmonitors (SSMS)
description: Informationen zum Öffnen des Aktivitätsmonitors in SQL Server Management Studio (SSMS)
ms.custom: seo-dt-2019
ms.date: 08/05/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Activity Monitor [SQL Server], setting the refresh interval
- refresh interval for Activity Monitor
- Activity Monitor [SQL Server], opening
- opening Activity Monitor
ms.assetid: 0a6eeb16-f02b-479d-9a60-543e40ebf46b
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 16d08bbc2b651ef21ee80be1e8af74a00b45a253
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85787440"
---
# <a name="open-activity-monitor-in-sql-server-management-studio-ssms"></a>Öffnen des Aktivitätsmonitors in SQL Server Management Studio (SSMS)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
   
 Der Aktivitätsmonitor führt Abfragen auf der überwachten Instanz aus, um Informationen für die Anzeigebereiche des Aktivitätsmonitors abzurufen. Wenn für das Intervall für die automatische Aktualisierung weniger als 10 Sekunden festgelegt sind, kann die für die Ausführung der Abfragen benötigte Zeit die Serverleistung beeinträchtigen.  
  
  
##  <a name="check-your-permissions"></a><a name="Permissions"></a> Überprüfen Sie Ihre Berechtigungen!  
 Zum Anzeigen der tatsächlichen Aktivität müssen Sie über die VIEW SERVER STATE-Berechtigung verfügen. Sie müssen zum Anzeigen des Abschnitts "Datendatei-E/A" des Aktivitätsmonitors neben VIEW SERVER STATE über die CREATE DATABASE-, ALTER ANY DATABASE- oder VIEW ANY DEFINITION-Berechtigung verfügen.  
  
 Zum Ausführen von KILL für einen Prozess muss ein Benutzer Mitglied der festen Serverrolle sysadmin oder processadmin sein.  
  
  
## <a name="open-activity-monitor"></a>Öffnen des Aktivitätsmonitors  

### <a name="keyboard-shortcut"></a>Tastenkombinationen  
 - Geben Sie **STRG+ALT+A** ein, um den Aktivitätsmonitor jederzeit zu öffnen.

 >**Tipp:** Bewegen Sie den Mauszeiger über ein Symbol in SSMS, um zu erfahren, wozu es dient und über welche Tastenkombination es aktiviert wird.

### <a name="toolbar"></a>Symbolleiste

Klicken Sie auf der Standardsymbolleiste auf das Symbol **Aktivitätsmonitor** . Es befindet sich in der Mitte, rechts neben den Schaltflächen „Rückgängig“ bzw. „Wiederholen“.
![Activity_Monitor_icon](../../relational-databases/performance-monitor/media/activity-monitor-icon.png)  
  
Stellen Sie das Dialogfeld **Verbindung mit Server herstellen** fertig, wenn Sie nicht bereits mit einer Instanz von SQL Server verbunden sind, die Sie überwachen möchten.
  
## <a name="launch-activity-monitor-and-object-explorer-on-startup"></a>Starten des Aktivitätsmonitors und Objekt-Explorers beim Start
  
1.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
2.  Erweitern Sie im Dialogfeld **Optionen** die Option **Umgebung**, und wählen Sie dann **Start**aus.  
  
3.  Wählen Sie in der Dropdownliste **Beim Start** die Option **Objekt-Explorer und Aktivitätsmonitor öffnen**aus.  

4.  Klicken Sie auf **OK**.

![open_object_explorer](../../relational-databases/performance-monitor/media/open-object-explorer.png)
  
  
## <a name="set-the-activity-monitor-refresh-interval"></a>Festlegen des Aktualisierungsintervalls für den Aktivitätsmonitor  
  
1.   Öffnen Sie Aktivitätsmonitor.  
  
2.   Klicken Sie mit der rechten Maustaste auf **Übersicht**, wählen Sie **Aktualisierungsintervall**aus, und wählen Sie anschließend das Intervall aus, in dem der Aktivitätsmonitor neue Instanzinformationen abrufen soll.  
  
  
