---
title: Öffnen des Aktivitätsmonitors (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Activity Monitor [SQL Server], setting the refresh interval
- refresh interval for Activity Monitor
- Activity Monitor [SQL Server], opening
- opening Activity Monitor
ms.assetid: 0a6eeb16-f02b-479d-9a60-543e40ebf46b
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 0d1c0312acfcd2e5dbb17d740fe2659cb8c91bbe
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63032004"
---
# <a name="open-activity-monitor-sql-server-management-studio"></a>Öffnen des Aktivitätsmonitors (SQL Server Management Studio)
  In diesem Thema wird das Öffnen des Aktivitätsmonitors beschrieben, der Informationen zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Prozesse und deren Auswirkungen auf die aktuelle Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]gibt. Zudem wird beschrieben, wie Sie das Aktualisierungsintervall des Aktivitätsmonitors festgelegen.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Sicherheit](#Security)  
  
-   **So öffnen Sie den Aktivitätsmonitor mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
-   So **legen Sie das Aktualisierungs Intervall fest mit:**[SQL Server Management Studio](#Refresh)    
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
 Der Aktivitätsmonitor führt Abfragen auf der überwachten Instanz aus, um Informationen für die Anzeigebereiche des Aktivitätsmonitors abzurufen. Wenn für das Intervall für die automatische Aktualisierung weniger als 10 Sekunden festgelegt sind, kann die für die Ausführung der Abfragen benötigte Zeit die Serverleistung beeinträchtigen.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Zum Anzeigen des Aktivitätsmonitors muss ein Benutzer über die VIEW SERVER STATE-Berechtigung verfügen. Sie müssen zum Anzeigen des Abschnitts "Datendatei-E/A" des Aktivitätsmonitors neben VIEW SERVER STATE über die CREATE DATABASE-, ALTER ANY DATABASE- oder VIEW ANY DEFINITION-Berechtigung verfügen.  
  
 Zum Ausführen von KILL für einen Prozess muss ein Benutzer Mitglied der festen Serverrolle sysadmin oder processadmin sein.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-open-activity-monitor-in-sql-server-management-studio"></a>So öffnen Sie den Aktivitätsmonitor in SQL Server Management Studio  
  
1.  Klicken Sie auf der [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] -Standardsymbolleiste auf **Aktivitätsmonitor**.  
  
2.  Wählen Sie im Dialogfeld **Verbindung mit Server herstellen** den Servernamen und den Authentifizierungsmodus aus, und klicken Sie anschließend auf **Verbinden**.  
  
 Sie können den Aktivitätsmonitor außerdem jederzeit öffnen, indem Sie STRG+ALT+A drücken.  
  
#### <a name="to-open-activity-monitor-in-object-explorer"></a>So öffnen Sie den Aktivitätsmonitor im Objekt-Explorer  
  
-   Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf den Instanznamen, und wählen Sie dann den **Aktivitätsmonitor**aus.  
  
#### <a name="to-open-activity-monitor-when-opening-sql-server-management-studio"></a>So öffnen Sie den Aktivitätsmonitor beim Öffnen des SQL Server Management Studios  
  
1.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
2.  Erweitern Sie im Dialogfeld **Optionen** die Option **Umgebung**, und wählen Sie dann **Allgemein**aus.  
  
3.  Wählen Sie im Feld **Beim Start** die Option **Objekt-Explorer und Aktivitätsmonitor öffnen**aus.  
  
4.  Damit diese Änderungen aktiv werden, müssen Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]schließen und erneut öffnen.  
  
###  <a name="Refresh"></a>So legen Sie das Aktualisierungs Intervall für den Aktivitäts Monitor fest  
  
-   Öffnen Sie Aktivitätsmonitor.  
  
-   Klicken Sie mit der rechten Maustaste auf **Übersicht**, wählen Sie **Aktualisierungsintervall**aus, und wählen Sie anschließend das Intervall aus, in dem der Aktivitätsmonitor neue Instanzinformationen abrufen soll.  
  
  
