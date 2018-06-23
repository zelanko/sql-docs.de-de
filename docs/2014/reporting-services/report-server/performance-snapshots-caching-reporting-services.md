---
title: Leistung, Momentaufnahmen, Zwischenspeichern (Reporting Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance [Reporting Services]
- Reporting Services, performance
ms.assetid: 85afd00f-e8d7-4ef7-9174-2ff84d82f960
caps.latest.revision: 19
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: f2892c047bb3826b62da81f8f5f4ddcdea5b46f1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148763"
---
# <a name="performance-snapshots-caching-reporting-services"></a>Leistung, Momentaufnahmen, Zwischenspeichern (Reporting Services)
  Die Leistung des Berichtsservers wird von einer Reihe von Faktoren beeinflusst. Dazu zählen Hardware, Anzahl der Benutzer, die gleichzeitig auf Berichte zugreifen, Datenmenge in einem Bericht und Ausgabeformat. Um die Leistungsfaktoren, die spezifisch für Ihre Installation sind, und entsprechende Abhilfemaßnahmen zu ermitteln, müssen Sie sich zunächst mit den Basisdaten beschäftigen und Tests ausführen. Weitere Informationen zu Tools und Richtlinien stehen in den folgenden Publikationen auf MSDN zur Verfügung: [Leistungsoptimierung bei Reporting Services](http://blogs.msdn.com/b/sqlcat/archive/2013/10/30/reporting-services-performance-and-optimization.aspx) und [Verwenden von Visual Studio 2005 zum Ausführen von Ladetests für einen SQL Server 2005 Reporting Services-Berichtsserver](http://go.microsoft.com/fwlink/?LinkID=77519).  
  
 Folgende allgemeine Aspekte sind zu beachten:  
  
-   Die Berichtsverarbeitung und das Berichtsrendering sind speicherintensive Vorgänge. Wählen Sie wenn möglich einen Computer mit viel Arbeitsspeicher aus.  
  
-   Das Hosten von Berichtsserver und Berichtsserver-Datenbank auf verschiedenen Computern liefert in der Regel bessere Ergebnisse als das gemeinsame Hosten auf einem einzelnen leistungsstarken Computer.  
  
-   Wenn alle Berichte langsam verarbeitet werden, sollten Sie eine Bereitstellung für dezentrales Skalieren in Erwägung ziehen. Dabei unterstützen mehrere Berichtsserverinstanzen eine einzelne Berichtsserver-Datenbank. Verwenden Sie für beste Ergebnisse eine Lastenausgleichssoftware, die Anforderungen gleichmäßig über die Bereitstellung verteilt.  
  
-   Wird ein einzelner Bericht langsam verarbeitet, optimieren Sie die Datasetabfragen des Berichts, wenn der Bericht bei Bedarf ausgeführt werden muss. Weitere Möglichkeiten sind das Verwenden freigegebener Datasets, die Sie zwischenspeichern können, das Zwischenspeichern des Berichts oder das Ausführen des Berichts als Momentaufnahme.  
  
-   Wenn alle Berichte in einem spezifischen Format langsam verarbeitet werden (z. B. Rendern im PDF-Format), sollten Sie eine Dateifreigabeübermittlung, das Hinzufügen von Arbeitsspeicher oder die Auswahl eines anderen Formats erwägen.  
  
-   Die Dauer der Berichtsverarbeitung und andere Nutzungsdaten können Sie im Ausführungsprotokoll des Berichtsservers ermitteln. Weitere Informationen finden Sie unter [Berichtsserver-Ausführungsprotokoll und die ExecutionLog3-Ansicht](report-server-executionlog-and-the-executionlog3-view.md).  
  
-   Weitere Informationen über das Minimieren von Leistungsproblemen durch Optimieren der speicherverwaltungs-Konfigurationseinstellungen finden Sie unter [Konfigurieren des verfügbaren Arbeitsspeichers für Berichtsserveranwendungen](../report-server/configure-available-memory-for-report-server-applications.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Monitoring Report Server Performance (Überwachen der Leistung des Berichtsservers)](monitoring-report-server-performance.md)  
 Beschreibt die Leistungsobjekte, die Sie verwenden können, um die Verarbeitungslast auf dem Server zu verfolgen.  
  
 [Set Report Processing Properties (Festlegen von Berichtsverarbeitungseigenschaften)](set-report-processing-properties.md)  
 Beschreibt Möglichkeiten, einen Bericht so zu konfigurieren, dass er bedarfsgesteuert aus dem Cache oder nach Zeitplan als Berichtsmomentaufnahme ausgeführt wird.  
  
 [Configure Available Memory for Report Server Applications (Konfigurieren von verfügbarem Speicher für Berichtsserveranwendungen)](../report-server/configure-available-memory-for-report-server-applications.md)  
 Beschreibt, wie Sie das Standardverhalten bei der Arbeitsspeicherverwaltung überschreiben können.  
  
 [Zwischenspeichern von Berichten &#40;SSRS&#41;](caching-reports-ssrs.md)  
 Beschreibt das Verhalten beim Zwischenspeichern auf einem Berichtsserver.  
  
 [Zwischenspeichern von freigegebenen Datasets &#40;SSRS&#41;](cache-shared-datasets-ssrs.md)  
 Beschreibt das Verhalten beim Zwischenspeichern freigegebener Datasets auf einem Berichtsserver.  
  
 [Process Large Reports (Verarbeiten von großen Berichten)](process-large-reports.md)  
 Stellt Empfehlungen dazu bereit, wie ein großer Bericht konfiguriert und verteilt wird.  
  
 [Festlegen von Timeoutwerten für die Verarbeitung von Berichten und freigegebenen Datasets &#40;SSRS&#41;](setting-time-out-values-for-report-and-shared-dataset-processing-ssrs.md)  
 Erklärt, wie Timeouts für die Abfrage- und Berichtsverarbeitung festgelegt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten eines ausgeführten Prozesses](../subscriptions/manage-a-running-process.md)   
 [Verifying a Report Run (Überprüfen der Berichtsausführung)](verifying-a-report-run.md)  
  
  