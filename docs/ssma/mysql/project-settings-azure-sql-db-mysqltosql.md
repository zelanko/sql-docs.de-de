---
title: Projekteinstellungen (Azure SQL-Datenbank) (mysqlto SQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 8c06420a-533b-4de0-948d-a0c6b368c544
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 4125f73ec34418261d0308221c448cae1fb06298
ms.sourcegitcommit: 21bedbae28840e2f96f5e8b08bcfc794f305c8bc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2020
ms.locfileid: "87862311"
---
# <a name="project-settings-azure-sql-database-mysqltosql"></a>Projekteinstellungen (Azure SQL-Datenbank) (mysqlto SQL)
Mit den SQL Azure-Projekteinstellungen können Sie das SQL Azure Daten Bank Suffix konfigurieren, das im Verbindungs Dialogfeld hinzugefügt werden soll, und außerdem die Implementierung des Takt Mechanismus in SQL Azure Verbindung ermöglichen.  
  
Der SQL Azure Bereich ist in den Dialogfeldern **Projekteinstellungen** und **Standard Projekteinstellungen** verfügbar.  
  
-   Verwenden Sie das Dialogfeld Projekteinstellungen, um Konfigurationsoptionen für das aktuelle Projekt festzulegen. Um auf die SQL Azure Einstellungen zuzugreifen, wählen Sie **im Menü Extras die Option** **Projekteinstellungen**aus, klicken Sie unten im linken Bereich auf **Allgemein** , und wählen Sie dann **SQL Azure**aus.  
  
-   Verwenden Sie das Dialogfeld Standard Projekteinstellungen, um Konfigurationsoptionen für alle Projekte festzulegen. Um auf die SQL Azure Einstellungen zuzugreifen, wählen Sie **im Menü Extras** die Option **defaultproject Settings**aus, wählen Sie in der Dropdown Liste **Migrations Ziel Version** die Option Migrations projekttSQL Azure YP aus, um auf die Einstellungen in SQL Azure Bereich zuzugreifen, klicken Sie unten im linken Bereich auf **Allgemein** , und wählen Sie dann **SQL Azure**aus.  
  
## <a name="options"></a>Optionen  
  
## <a name="connectivity"></a>Konnektivität  
**Taktintervall**  
  
Gibt ein Zeitintervall an, das für den Takt Mechanismus verwendet wird, um die SQL Azure Verbindung im Format "Minutes: seconds" beizubehalten.  
  
**Standardwert**: "4:45"  
  
Der Wert muss im Format "m:SS" angegeben werden (z. b. "4:45" oder "0:50").  
  
**SQL Azure Server Suffix**  
  
Gibt das SQL Azure Server-Suffix an.  
  
**Standardwert**: "Database.Windows.net".  
  
