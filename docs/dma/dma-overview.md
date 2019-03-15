---
title: Übersicht über Data Migration Assistant (SQLServer) | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie mit Data Migration Assistant zum Migrieren von SQL Server-Datenbanken zu anderen SQL Server oder Azure-Datenbanken
ms.custom: ''
ms.date: 03/12/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, overview
ms.assetid: ''
author: HJToland3
ms.author: rajpo
manager: craigg
ms.openlocfilehash: 0bb91177a204f93bd141d57b90420678dcd0b722
ms.sourcegitcommit: e9fcd10c7eb87a4f09ac2d8f7647018e83a5f5c5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57973789"
---
# <a name="overview-of-data-migration-assistant"></a>Übersicht über Data Migration Assistant
Die Data Migration Assistant (DMA) können, die Sie ein upgrade auf eine moderne Datenplattform durch das Erkennen von Kompatibilitätsproblemen, die Datenbankfunktionalität in die neue Version der SQL Server oder Azure SQL-Datenbank beeinflussen können. DMA empfiehlt, zuverlässigkeitverbesserungen der Leistung und für Ihre zielumgebung und ermöglicht es Ihnen, Ihr Schema, Daten und nicht enthaltene Objekte vom Quellserver zum Zielserver zu verschieben.

> [!NOTE] 
> Bei großen Migrationen (im Hinblick auf Anzahl und Größe der Datenbanken), empfehlen wir die Verwendung der [Azure Database Migration Service](/azure/dms/dms-overview), können die Datenbanken migrieren.
  
## <a name="get-data-migration-assistant"></a>Abrufen von Data Migration Assistant
Um DMA zu installieren, laden Sie die neueste Version des Tools aus der [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=53595), und führen Sie dann die **DataMigrationAssistant.msi** Datei.

## <a name="capabilities"></a>Funktionen
- Bewerten von lokalen SQL Server-Instanzen, die Migration zu Azure SQL-Datenbanken. Der Workflow für die Bewertung können Sie die folgenden Probleme zu erkennen, die kann die Migration von Azure SQL-Datenbank beeinträchtigen und enthält detaillierte Anleitungen zu deren Behebung.

  - Blockierende Migrationsprobleme: Ermittelt die Kompatibilitätsprobleme, die die Migration von lokalen SQL Server-Datenbank(en) zu Azure SQL-Datenbank zu verhindern. DMA finden Sie Empfehlungen können Sie diese Probleme zu beheben.

  - Teilweise unterstützte oder nicht unterstützte Features: Erkennt teilweise unterstützte oder nicht unterstützte Features, die derzeit in der SQL Server-Quellinstanz verwendet werden. DMA bietet eine umfassende von Empfehlungen, alternativen Ansätzen, die in Azure und Schritten zur Verfügung, damit Sie sie bei Ihren Migrationsprojekten integrieren können.

- Ermitteln Sie Probleme, die ein Upgrade auf einem lokalen SQL Server auswirken können. Diese werden als Kompatibilitätsprobleme beschrieben und sind in folgenden Kategorien unterteilt:

  - Wichtige Änderungen
  - Verhaltensänderungen
  - Veraltete Features

- Entdecken Sie neue Features in der SQL Server-Zielplattform, die die Datenbank nach einem Upgrade von profitieren kann. Diese werden als Vorschläge zu Features beschrieben und sind in folgenden Kategorien unterteilt:

  - Leistung
  - Sicherheit
  - Speicherung

- Migrieren einer lokalen SQL Server-Instanz, eine moderne SQLServer-Instanz gehostet auf lokale oder auf einem virtuellen Azure-Computer (VM), der aus Ihrem lokalen Netzwerk zugänglich ist. Der Azure-VM kann mithilfe von VPN- oder anderen Technologien zugegriffen werden. Workflow bei der Migration können Sie die folgenden Komponenten migrieren:

  - Schema der Datenbanken
  - Daten und Benutzer
  - Serverrollen
  - SQL Server und Windows-Anmeldungen

- Nachdem eine erfolgreiche Migration können Anwendungen nahtlos mit der Ziel-SQL Server-Datenbanken verbinden.

## <a name="prerequisites"></a>Erforderliche Komponenten
Um eine Bewertung ausführen zu können, müssen Sie Mitglied der SQL Server **Sysadmin** Rolle.

## <a name="supported-source-and-target-versions"></a>Unterstützte Versionen von Quelle und Ziel
DMA ersetzt alle frühere Versionen von SQL Server Upgrade Advisor und für Upgrades für die meisten SQL Server-Versionen verwendet werden soll. Quelle und Ziel-Versionen werden unterstützt:

**Datenquellen**
- SQL Server 2005
- SQL Server 2008
- SQL Server 2008 R2
- SQL Server 2012 
- SQLServer 2014
- SQL Server 2016
- SQLServer 2017 unter Windows

**Ziele**
- SQL Server 2012
- SQLServer 2014
- SQL Server 2016
- SQLServer 2017 unter Windows und Linux
- Azure SQL-Datenbank
- Verwaltete Azure SQL-Datenbank-Instanz.

## <a name="see-also"></a>Siehe auch
[Bewerten Sie Ihre Migration zu SQL Server](../dma/dma-assesssqlonprem.md)     
[Data Migration Assistant: Konfigurationseinstellungen](../dma/dma-configurationsettings.md)     
[Migrate On-Premises SQL Server mithilfe von Data Migration Assistant](../dma/dma-migrateonpremsql.md)     
[Data Migration Assistant: Bewährte Methoden](../dma/dma-bestpractices.md)     
