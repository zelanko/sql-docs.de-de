---
title: Projekteinstellungen (Azure SQL-Datenbank) (sybasedesql) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 57002374-0d4d-43c1-b4e9-cbec02355a9c
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 0348d548d21ea9b593aa7fe4aa14986607ba76fb
ms.sourcegitcommit: 21bedbae28840e2f96f5e8b08bcfc794f305c8bc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2020
ms.locfileid: "87863442"
---
# <a name="project-settings-azure-sql-database--sybasetosql"></a>Projekteinstellungen (Azure SQL-Datenbank) (sybasedesql)
Mit den Azure SQL-Datenbankprojekt Einstellungen können Sie das Azure SQL-Daten Bank Suffix konfigurieren, das im Verbindungs Dialogfeld hinzugefügt werden soll, und die Implementierung des Takt Mechanismus in der Azure SQL-Datenbankverbindung  
  
Der Bereich Azure SQL-Datenbank ist in den Dialogfeldern **Projekteinstellungen** und **Standard Projekteinstellungen** verfügbar.  
  
-   Verwenden Sie das Dialogfeld Projekteinstellungen, um Konfigurationsoptionen für das aktuelle Projekt festzulegen. Um **auf die Azure** SQL-Datenbankeinstellungen zuzugreifen, wählen Sie im Menü Extras die Option **Projekteinstellungen**aus, klicken Sie unten im linken Bereich auf **Allgemein** , und wählen Sie dann **Azure SQL-Datenbank**aus.  
  
-   Verwenden Sie das Dialogfeld Standard Projekteinstellungen, um Konfigurationsoptionen für alle Projekte festzulegen. Um auf die Azure SQL-Datenbankeinstellungen zuzugreifen, wählen Sie **im Menü Extras** die Option **defaultproject Settings**aus, klicken Sie unten im linken Bereich auf **Allgemein** , und wählen Sie dann **Azure SQL-Datenbank**aus.  
  
## <a name="connectivity"></a>Konnektivität  
**Taktintervall**  
  
Gibt ein Zeitintervall an, das für den Takt Mechanismus verwendet wird, um die Azure SQL-Datenbankverbindung im Format "Minuten: Sekunden" zu wahren.  
  
**Standardwert**: "4:45"  
  
Der Wert muss im Format "m:SS" angegeben werden (z. b. "4:45" oder "0:50").  
  
**Azure SQL-Datenbank-Server Suffix**  
  
Gibt ein Azure SQL-Datenbankserver-Suffix an.  
  
**Standardwert**: "Database.Windows.net".  
  
