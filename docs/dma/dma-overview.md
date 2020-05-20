---
title: Übersicht über Datenmigrations-Assistent (SQL Server) | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Datenmigrations-Assistent zum Migrieren SQL Server Datenbanken zu anderen SQL Server oder Azure-Datenbanken verwenden.
ms.custom: ''
ms.date: 11/05/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, overview
ms.assetid: ''
author: rajeshsetlem
ms.author: rajpo
ms.openlocfilehash: ad6bf673fb9bfe435d517dfd9e2dcf71774191a1
ms.sourcegitcommit: fb1430aedbb91b55b92f07934e9b9bdfbbd2b0c5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82885797"
---
# <a name="overview-of-data-migration-assistant"></a>Übersicht über Datenmigrations-Assistent

Mit dem Datenmigrations-Assistent (DMA) können Sie ein Upgrade auf eine moderne Datenplattform durchführen, indem Sie Kompatibilitätsprobleme erkennen, die sich auf die Datenbankfunktionalität in ihrer neuen SQL Server oder Azure SQL-Datenbank auswirken können. DMA empfiehlt Leistungs- und Zuverlässigkeitsverbesserungen für Ihre Zielumgebung und ermöglicht es Ihnen, Ihr Schema, Ihre Daten und abhängige Objekte vom Quellserver auf Ihren Zielserver zu verschieben.

> [!NOTE]
> Für große Migrationen (in Bezug auf Anzahl und Größe von Datenbanken) empfiehlt es sich, die [Azure Database Migration Service](/azure/dms/dms-overview)zu verwenden, mit der Datenbanken skaliert migriert werden können.
  
## <a name="get-data-migration-assistant"></a>Abrufen von Data Migration Assistant

Um DMA zu installieren, laden Sie die neueste Version des Tools aus dem [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=53595)herunter, und führen Sie dann die Datei **datamigrationassistant. msi** aus.

## <a name="capabilities"></a>Funktionen

- Bewerten Sie lokale SQL Server Instanzen, die zu Azure SQL-Datenbank (en) migriert werden.Mit dem Bewertungs Workflow können Sie die folgenden Probleme erkennen, die sich auf die Migration der Azure SQL-Datenbank auswirken können. Sie erhalten eine ausführliche Anleitung, wie Sie Sie beheben können.

  - Probleme beim Blockieren der Migration: Hiermit werden die Kompatibilitätsprobleme ermittelt, die die Migration der lokalen SQL Server Datenbank (en) zu Azure SQL-Datenbank (en) blockieren.DMA bietet Empfehlungen, die Ihnen helfen, diese Probleme zu beheben.

  - Teilweise unterstützte oder nicht unterstützte Funktionen: erkennt teilweise unterstützte oder nicht unterstützte Funktionen, die zurzeit auf der Quell SQL Server Instanz verwendet werden.DMA bietet eine umfassende Reihe von Empfehlungen, alternative Ansätze in Azure und Entschärfung von Schritten, damit Sie Sie in Ihre Migrationsprojekte integrieren können.

- Entdecken Sie Probleme, die ein Upgrade auf eine lokale SQL Server beeinflussen können.Diese werden als Kompatibilitätsprobleme beschrieben und in den folgenden Kategorien organisiert:

  - Breaking Changes
  - Verhaltensänderungen
  - Veraltete Features

- Entdecken Sie neue Features auf der Ziel SQL Server Plattform, von der die Datenbank nach einem Upgrade profitieren kann. Diese werden als featureempfehlungen beschrieben und in den folgenden Kategorien organisiert:

  - Leistung
  - Sicherheit
  - Storage

- Migrieren Sie eine lokale SQL Server Instanz zu einer modernen SQL Server Instanz, die lokal oder auf einem virtuellen Azure-Computer (VM) gehostet wird, auf den von Ihrem lokalen Netzwerk aus zugegriffen werden kann. Auf den virtuellen Azure-Computer kann mithilfe von VPN oder anderen Technologien zugegriffen werden. Der Migrations Workflow unterstützt Sie beim Migrieren der folgenden Komponenten:

  - Schema der Datenbanken
  - Daten und Benutzer
  - Serverrollen
  - SQL Server-und Windows-Anmeldungen

- Nach einer erfolgreichen Migration können Anwendungen nahtlos eine Verbindung mit dem Ziel SQL Server Datenbanken herstellen.

- Bewerten Sie lokale SQL Server Integration Services (SSIS)-Pakete, die zu Azure SQL-Datenbank oder einer verwalteten Azure SQL-Datenbank-Instanz migriert werden. Mithilfe der Bewertung können Sie Probleme ermitteln, die sich auf die Migration auswirken können. Diese werden als Kompatibilitätsprobleme beschrieben und in den folgenden Kategorien organisiert:

  - Migrations Blockierer: ermittelt die Kompatibilitätsprobleme, die die Migration von Quellpaketen zu Azure blockieren. DMA bietet Empfehlungen, die Ihnen helfen, diese Probleme zu beheben.

  - Informationsprobleme: erkennt teilweise unterstützte oder veraltete Features, die in Quellpaketen verwendet werden.

## <a name="prerequisites"></a>Voraussetzungen

Zum Ausführen einer Bewertung müssen Sie ein Mitglied der Rolle SQL Server **sysadmin** sein.

## <a name="supported-source-and-target-versions"></a>Unterstützte Quell-und Zielversionen

DMA ersetzt alle vorherigen Versionen von SQL Server Upgrade Advisor und sollte für die meisten SQL Server Versionen verwendet werden. Die folgenden Quell-und Ziel Versionen werden unterstützt:

**Quellen**

- SQL Server 2005
- SQL Server 2008
- SQL Server 2008 R2
- SQL Server 2012
- SQL Server 2014
- SQL Server 2016
-  SQL Server 2017 unter Windows

**Ziele**

- SQL Server 2012
- SQL Server 2014
- SQL Server 2016
- SQL Server 2017 unter Windows und Linux
- SQL Server 2019
- Azure SQL-Datenbank – Singleton
- Azure SQL-Datenbank – Verwaltete Instanz
- SQL Server auf einem virtuellen Azure-Computer

## <a name="see-also"></a>Weitere Informationen

[Bewerten der SQL Server Migration](../dma/dma-assesssqlonprem.md)

[Datenmigrations-Assistent: Konfigurationseinstellungen](../dma/dma-configurationsettings.md)

[Lokale SQL Server mithilfe Datenmigrations-Assistent migrieren](../dma/dma-migrateonpremsql.md)

[Datenmigrations-Assistent: bewährte Methoden](../dma/dma-bestpractices.md)
