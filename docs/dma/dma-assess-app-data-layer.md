---
title: Bewerten Sie die Datenzugriffs Ebene einer Anwendung mit Datenmigrations-Assistent
description: Erfahren Sie, wie Sie mit Datenmigrations-Assistent die Datenzugriffs Ebene einer Anwendung bewerten.
ms.date: 01/23/2020
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
author: HJToland3
ms.author: rajpo
ms.custom: seo-lt-2019
ms.openlocfilehash: 24763f190172da637d19df7ce36553b7341bd894
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "76761984"
---
# <a name="assess-an-apps-data-access-layer-with-data-migration-assistant"></a>Bewerten Sie die Datenzugriffs Ebene einer APP mit Datenmigrations-Assistent

Anwendungen verbinden und speichern Daten in der Regel in einer Datenbank. Die Datenzugriffs Ebene der Anwendung bietet vereinfachten Zugriff auf diese Daten. Datenmigrations-Assistent (DMA) hat es Benutzern ermöglicht, Ihre Datenbanken und zugehörigen Objekte zu bewerten. Die neueste Version von DMA (v 5.0) führt die Unterstützung für die Analyse von Datenbankverbindungen und eingebetteten SQL-Abfragen im Anwendungscode ein.

Beachten Sie das folgende c#-Codesegment:

![C#-Beispielcode Segment](../dma/media/dma-assess-app-data-layer/dma-sample-c-sharp-code-segment.png)

In diesem Fall können Sie sehen, dass die Anwendung eine SQL-Abfrage verwendet, um den Namen eines Mitarbeiters zu erhalten.

![Beispiel für c#-Codesegment Details](../dma/media/dma-assess-app-data-layer/dma-sample-c-sharp-code-detail.png)

Als Anwendungs Besitzer muss ich in der Lage sein, die verschiedenen Datenbanken zu identifizieren, mit denen die Anwendung eine Verbindung herstellen kann, sowie die Abfragen, die in die Datenzugriffs Ebene der Anwendung eingebettet werden. Außerdem muss ich alle Änderungen ermitteln, die für die Modernisierung der Anwendung in Azure Data Services erforderlich sind.

## <a name="assess-an-app-with-data-access-migration-toolkit"></a>Bewerten einer APP mit dem Data Access Migration Toolkit

Um diese Bewertung zu aktivieren, haben wir kürzlich das Data Access Migration Toolkit (damt) eingeführt, eine Visual Studio Code Erweiterung. Die neueste Version dieser Erweiterung (v 0,2) fügt Unterstützung für .NET-Anwendungen und T-SQL-Dialekt hinzu.

1. [Hier](https://code.visualstudio.com/download)können Sie vs Code herunterladen und installieren.
2. Aktivieren Sie die [Data Access Migration Toolkit-Erweiterung](https://marketplace.visualstudio.com/items?itemName=ms-databasemigration.data-access-migration-toolkit) aus dem Erweiterungs-Marketplace.

   ![Erweiterungs Seite für das Data Access Migration Toolkit](../dma/media/dma-assess-app-data-layer/dma-damt-extension-page.png)

3. Öffnen Sie das Anwendungsprojekt in Visual Studio Code.

   ![Anwendungsprojekt in Visual Studio Code](../dma/media/dma-assess-app-data-layer/dma-app-project-in-vscode.png)

4. Starten Sie die Erweiterungs Konsole (STRG-Shft-P), und führen Sie dann den Befehl **Datenzugriff: Arbeitsbereich analysieren** aus.

   ![Erweiterungs Konsole in Visual Studio Code](../dma/media/dma-assess-app-data-layer/dma-vscode-extension-console.png)

5. Wählen Sie den SQL Server Dialekt aus.

   ![SQL Server Dialekt Auswahl](../dma/media/dma-assess-app-data-layer/dma-sql-server-dialect.png)

   Am Ende der Analyse erstellt der Befehl einen Bericht über SQL-konnektivitätsbefehle und-Abfragen.

   ![Datenzugriffs Bericht](../dma/media/dma-assess-app-data-layer/dma-data-access-report.png)

6. Überprüfen Sie den Bericht auf datenkonnektivitätskomponenten und für SQL-Abfragen, die in den Anwendungscode eingebettet sind und hervorgehoben sind.

   ![SQL-Abfragen im Anwendungscode](../dma/media/dma-assess-app-data-layer/dma-sql-queries-in-app-code.png)

   Diese Abfragen können über DMA analysiert werden, um Kompatibilitäts-und featureparitäts Probleme basierend auf der SQL-Zielplattform zu beheben.

7. Um die Datenschicht der Anwendung zu bewerten, exportieren Sie den Bericht als JSON-Datei.

   ![JSON-Datei Export](../dma/media/dma-assess-app-data-layer/dma-json-file-export.png)

   In diesem Fall lautet die generierte Datei wie folgt:

   ![Anzeigen des Inhalts der JSON-Datei](../dma/media/dma-assess-app-data-layer/dma-json-file-contents.png)

   Datenmigrations-Assistent ermöglicht das Bewerten der Abfragen, die in der Anwendung identifiziert werden, im Zusammenhang mit der Modernisierung der Datenbank auf Azure Data Platform.

8. Starten Sie Datenmigrations-Assistent, und erstellen Sie dann ein Bewertungs Projekt.

   ![Neues Bewertungs Projekt Datenmigrations-Assistent](../dma/media/dma-assess-app-data-layer/dma-new-assessment-project.png)

9. Wählen Sie die Quell SQL Server Instanz aus.

   ![Datenmigrations-Assistent SQL Server Quelle auswählen](../dma/media/dma-assess-app-data-layer/dma-select-sql-source.png)

10. Wählen Sie die Datenbank aus, mit der die Anwendung eine Verbindung herstellt.

    ![Datenzugriffs Migration Select Application Database](../dma/media/dma-assess-app-data-layer/dma-select-app-database.png)

    Um die Datenzugriffs Bewertung zu vereinfachen, bietet DMA die Möglichkeit, JSON-Dateien mit Anwendungs Abfragen einzubinden. Als Nächstes fügen wir die zuvor erstellte JSON-Datei mit den Anwendungs Abfragen ein.

11. Wählen Sie die Datenbank aus, und navigieren Sie zu der aus dem Data Access Migration Toolkit exportierten JSON-Datei, um die Abfragen der Anwendung für die Bewertung einzubeziehen.

    ![Datenmigrations-Assistent Open dmat JSON-Datei](../dma/media/dma-assess-app-data-layer/dma-open-damt-json-file.png)

12. Starten Sie die Bewertung.

    ![Bewertung des Datenmigrations-Assistent Starts](../dma/media/dma-assess-app-data-layer/dma-start-assessment.png)

13. Überprüfen Sie den Bewertungsbericht. Der generierte Bericht enthält alle Kompatibilitäts-oder featureparitäts Probleme, die in den Anwendungs Abfragen erkannt werden, wie unten gezeigt.

    ![Datenmigrations-Assistent Bewertungsbericht](../dma/media/dma-assess-app-data-layer/dma-assessment-report.png)

Neben der Daten Bank Perspektive der Migration haben Benutzer nun auch eine Ansicht aus der Anwendungsperspektive.

## <a name="see-also"></a>Weitere Informationen

* [Übersicht über Datenmigrations-Assistent](../dma/dma-overview.md)
* [Datenmigrations-Assistent: Konfigurationseinstellungen](../dma/dma-configurationsettings.md)
* [Datenmigrations-Assistent: bewährte Methoden](../dma/dma-bestpractices.md)
* [Data Access Migration Toolkit](https://marketplace.visualstudio.com/items?itemName=ms-databasemigration.data-access-migration-toolkit)