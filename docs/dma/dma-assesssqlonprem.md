---
title: Führen Sie eine SQL Server-migrationsbewertung (Data Migration Assistant) | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Data Migration Assistant mit um einer lokalen SQL Server zu bewerten, bevor Sie eine Migration auf einen anderen SQL Server oder Azure SQL-Datenbank
ms.custom: ''
ms.date: 08/29/2018
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.suite: sql
ms.technology: dma
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: rajpo
manager: craigg
ms.openlocfilehash: 1a8de403a529ca5b74c6391f0e3f4cef2cca26d2
ms.sourcegitcommit: fb269accc3786715c78f8b6e2ec38783a6eb63e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2018
ms.locfileid: "43152781"
---
# <a name="perform-a-sql-server-migration-assessment-with-data-migration-assistant"></a>Führen Sie eine SQL Server-migrationsbewertung mit Data Migration Assistant

Die folgenden schrittweisen Anweisungen unterstützen Sie Ihre erste Bewertung durchführen, für die Migration zu einem lokalen SQL Server, SQL Server auf einer Azure-VM oder Azure SQL-Datenbank mithilfe von Data Migration Assistant.

## <a name="create-an-assessment"></a>Erstellen einer Bewertung

1.  Wählen Sie die **neu** (+)-Symbol, und wählen Sie dann die **Bewertung** Projekttyp.

2.  Der Typ der Quelle und Ziel-Server festgelegt.

    Wenn Sie Ihre lokalen SQL Server-Instanz auf einer modernen lokalen SQL Server-Instanz oder auf einer Azure-VM gehostete SQL Server aktualisieren, auf den Quell- und Ziel-Server-Datentyp festgelegt **SQL Server**. Wenn Sie zu Azure SQL-Datenbank migrieren, müssen Sie der Typ des Zielservers stattdessen festlegen, um **Azure SQL-Datenbank**.

3.  Klicken Sie auf **Erstellen**.

    ![Erstellen einer Bewertung](../dma/media/NewAssessment.png)

## <a name="choose-assessment-options"></a>Wählen Sie Bewertungsoptionen für die

1. Wählen Sie die SQL Server-Zielversion, der Sie zum migrieren möchten.

2. Wählen Sie den Bericht.

   Wenn Sie Ihre SQL Server-Quellinstanz für die Migration einer lokalen SQL Server oder SQL Server auf virtuellen Azure-Computer-Ziele gehostet bewerten sind, können Sie eine oder beide der folgenden bewertungsberichtsarten auswählen:

    -   **Probleme mit der Anwendungskompatibilität**

    -   **Empfehlung zu neuen features**

    ![Wählen Sie eine Assessment-Berichtstyp für SQL Server-Ziel](../dma/media/AssessmentTypes.png)

   Wenn Sie Ihre SQL Server-Quellinstanz für die Migration zu Azure SQL-Datenbank bewertet werden, können Sie eine oder beide der folgenden bewertungsberichtsarten auswählen:

    -   **Überprüfen Sie die Datenbankkompatibilität**

    -   **Featureparität überprüfen**

    ![Bewertung der Berichttyp für Ziel-SQL-Datenbank auswählen](../dma/media/AssessmentTypes_Azure.png)

## <a name="add-databases-to-assess"></a>Hinzufügen von Datenbanken, um zu bewerten

1.  Wählen Sie **Quellen hinzufügen** um die Verbindung Flyout-Menü zu öffnen.

2.  Geben Sie den SQL Server-Instanznamen, wählen Sie den Authentifizierungstyp, legen Sie die Eigenschaften für die richtige Verbindung und wählen Sie dann **Connect**.

3.  Wählen Sie die Datenbanken zu bewerten, und wählen Sie dann **hinzufügen**.

    > [!NOTE] 
    > Sie können mehrere Datenbanken entfernen, indem sie gleichzeitig die UMSCHALTTASTE oder STRG-Taste gedrückt halten, und klicken Sie dann auf Auswahl **Quellen entfernen**. Sie können auch Datenbanken von mehreren SQL Server-Instanzen hinzufügen, mit der **Quellen hinzufügen** Schaltfläche.

4.  Klicken Sie auf **Weiter** auf die Bewertung zu starten.

    ![Hinzufügen von Datenquellen und Bewertung starten](../dma/media/SelectDatabase.png)

## <a name="view-results"></a>Anzeigen der Ergebnisse

Die Dauer der Bewertung der hängt davon ab, die Anzahl der Datenbanken, die hinzugefügt und die Schemagröße der einzelnen Datenbanken. Ergebnisse werden für jede Datenbank angezeigt, sobald sie verfügbar sind.

1.  Wählen Sie die Datenbank, die die Bewertung abgeschlossen wurde, und wechseln Sie zwischen **Kompatibilitätsprobleme** und **Featureempfehlungen** mithilfe der Switcher.

2.  Überprüfen Sie die Kompatibilitätsprobleme für alle von der Ziel-SQL Server-Version unterstützt Kompatibilitätsgrade, die Sie ausgewählt haben, auf die **Optionen** Seite.

Sie können Kompatibilitätsprobleme prüfen, indem Sie analysieren, das betroffene Objekt, dessen Details und möglicherweise eine Lösung für jedes Problem identifiziert, die unter **wichtige Änderungen**, **verhaltensänderungen**, und  **Als veraltet markierte Funktionen**.

![Die Bewertung der Ergebnisse anzeigen](../dma/media/ReviewResults.png)

Auf ähnliche Weise können Sie überprüfen, Feature-Empfehlung für **Leistung**, **Storage**, und **Sicherheit** Bereiche.

Featureempfehlungen decken eine Vielzahl von Features wie z. B. In-Memory-OLTP und Columnstore, Stretch Database, Always Encrypted, dynamische Datenmaskierung und Transparent Data Encryption.

![Die Funktion Empfehlungen anzeigen](../dma/media/FeatureRecommendations.png)

Geben für Azure SQL-Datenbank Bewertungen, blockierende Probleme bei der Paketmigration und featureparitätsprobleme. Überprüfen Sie die Ergebnisse für beide Kategorien, die bestimmten Optionen auszuwählen.

- Die **SQL Server-Featureparität** Kategorie bietet eine umfassende Reihe von Empfehlungen, alternativen Ansätzen, die in Azure und Schritten zur Verfügung. Damit können Sie diesen Aufwand in Ihren Migrationsprojekten einplanen.

  ![Anzeigen von Informationen für SQL Server-Featureparität](../dma/media/SQLFeatureParity.png)

- Die **Kompatibilitätsprobleme** Kategorie bietet teilweise unterstützte oder nicht unterstützte Features, die Migration von lokalen SQL Server-Datenbanken zu Azure SQL-Datenbanken zu blockieren. Es bietet dann Empfehlungen können Sie diese Probleme zu beheben.

  ![Anzeigen von Kompatibilitätsproblemen](../dma/media/CompatibilityIssues.png)

## <a name="export-results"></a>Exportieren von Ergebnissen

Nachdem alle Datenbanken auf die Bewertung abgeschlossen haben, wählen Sie **Exportbericht** die Ergebnisse in eine JSON-Datei oder eine CSV-Datei exportieren. Sie können die Daten dann analysieren, Ihrem eigenen Ermessen.

Sie können mehrere Bewertungen gleichzeitig durchführen und den Zustand der Bewertungen anzeigen, öffnen die **alle Bewertungen** Seite.
