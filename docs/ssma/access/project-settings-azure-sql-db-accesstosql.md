---
title: Projekteinstellungen (Azure SQL-Datenbank) (accesstosql) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Project Settings dialog box, SQL Azure
- SQL Azure settings
ms.assetid: bbb8a204-d0e4-4f0b-9709-271feb1f136e
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 60140559f94cdeebea935b423fbbeef24bce7a08
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67929469"
---
# <a name="project-settings-azure-sql-db-accesstosql"></a>Projekteinstellungen (Azure SQL-Datenbank) (accesstosql)
Mit den SQL Azure-Projekteinstellungen können Sie das SQL Azure Daten Bank Suffix konfigurieren, das im Verbindungs Dialogfeld hinzugefügt werden soll, und außerdem die Implementierung des Takt Mechanismus in SQL Azure Verbindung ermöglichen.  
  
Der SQL Azure Bereich ist in den Dialogfeldern **Projekteinstellungen** und **Standard Projekteinstellungen** verfügbar.  
  
-   Verwenden Sie das Dialogfeld Projekteinstellungen, um Konfigurationsoptionen für das aktuelle Projekt festzulegen. Um auf die SQL Azure Einstellungen zuzugreifen, wählen Sie **im Menü Extras die Option** **Projekteinstellungen**aus, klicken Sie unten im linken Bereich auf **Allgemein** , und wählen Sie dann **SQL Azure**aus.  
  
-   Verwenden Sie das Dialogfeld Standard Projekteinstellungen, um Konfigurationsoptionen für alle Projekte festzulegen. Um auf die SQL Azure Einstellungen zuzugreifen, wählen **Sie im Menü Extras die Option** **defaultproject Settings**aus, wählen Sie den Projekttyp im Kombinations Feld **Migrations Ziel Version** als "SQL Azure" aus, um auf die Einstellungen im SQL Azure Bereich zuzugreifen, klicken Sie unten im linken Bereich auf **Allgemein** , und wählen Sie dann **SQL Azure**aus.  
  
## <a name="options"></a>Tastatur  
  
## <a name="connectivity"></a>Konnektivität  
**Taktintervall**  
  
Gibt ein Zeitintervall an, das für den Takt Mechanismus verwendet wird, um die SQL Azure Verbindung im Format "Minutes: seconds" beizubehalten.  
  
**Standardwert**: "4:45"  
  
Der Wert muss im Format "m:SS" angegeben werden (z. b. "4:45" oder "0:50").  
  
**SQL Azure Server Suffix**  
  
Gibt das SQL Azure Server-Suffix an.  
  
**Standardwert**: "Database.Windows.net".  
  
