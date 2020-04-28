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
ms.openlocfilehash: 829e7b0c51cd341193944fb2f28241f48618c407
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "70176222"
---
# <a name="project-settings-azure-sql-db--sybasetosql"></a>Projekteinstellungen (Azure SQL-DB) (SybaseToSQL)
Mit den Azure SQL-Datenbankprojekt Einstellungen können Sie das Azure SQL-Daten Bank Suffix konfigurieren, das im Verbindungs Dialogfeld hinzugefügt werden soll, und die Implementierung des Takt Mechanismus in der Azure SQL-Daten Bankverbindung  
  
Der Bereich Azure SQL-Datenbank ist in den Dialogfeldern **Projekteinstellungen** und **Standard Projekteinstellungen** verfügbar.  
  
-   Verwenden Sie das Dialogfeld Projekteinstellungen, um Konfigurationsoptionen für das aktuelle Projekt festzulegen. Um auf die Azure SQL-Datenbankeinstellungen zuzugreifen, wählen Sie **im Menü Extras** die Option **Projekteinstellungen**aus, klicken Sie unten im linken Bereich auf **Allgemein** , und wählen Sie dann **Azure SQL**-Datenbank aus.  
  
-   Verwenden Sie das Dialogfeld Standard Projekteinstellungen, um Konfigurationsoptionen für alle Projekte festzulegen. Um auf die Azure SQL-Datenbankeinstellungen zuzugreifen, wählen Sie **im Menü Extras** die Option **defaultproject Settings**aus, klicken Sie unten im linken Bereich auf **Allgemein** , und wählen Sie dann **Azure SQL**-Datenbank aus.  
  
## <a name="connectivity"></a>Verbindung  
**Taktintervall**  
  
Gibt ein Zeitintervall an, das für den Takt Mechanismus verwendet wird, um die Azure SQL-Daten Bankverbindung im Format "Minuten: Sekunden" zu wahren.  
  
**Standardwert**: "4:45"  
  
Der Wert muss im Format "m:SS" angegeben werden (z. b. "4:45" oder "0:50").  
  
**Azure SQL-DB-Server Suffix**  
  
Gibt ein Azure SQL-DB-Server Suffix an  
  
**Standardwert**: "Database.Windows.net".  
  
