---
title: Konfigurieren von Ausführungseigenschaften für einen Bericht (Reporting Services) | Microsoft-Dokumentation
ms.date: 06/26/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reports
ms.topic: conceptual
helpviewer_keywords:
- report execution properties [Reporting Services]
- reports [Reporting Services], properties
- reports [Reporting Services], execution options
ms.assetid: 73cc8dcc-ef80-40d7-9739-d33bba0eb28a
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 6dfb24b6314529b19fb7bb5edb81534f30dc018a
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67492757"
---
# <a name="configure-execution-properties-for-a-report"></a>Konfigurieren von Ausführungseigenschaften für einen Bericht
  Sie können Berichtsverarbeitungsoptionen festlegen, um anzugeben, wann Daten für einen Bericht abgerufen werden sollen. Es ist hilfreich, die Datenverarbeitung für einen Bericht zu planen, wenn die externe Datenquelle zu bestimmten Zeiten aktualisiert wird (beispielsweise bei einem Data Warehouse, das täglich oder wöchentlich aktualisiert wird) und Sie vermeiden wollen, dass bei jeder Berichtsanforderung dieselben Daten abgerufen werden. Das Planen der Datenverarbeitung ist außerdem hilfreich, wenn Sie die Verarbeitungslast für den externen Datenbankserver steuern möchten oder wenn Sie einheitliche Ergebnisse für verschiedene Benutzer bereitstellen möchten, die mit identischen Datensätzen arbeiten sollen. Bei flüchtigen Daten kann ein bedarfsgesteuerter Bericht von einer Minute zur nächsten unterschiedliche Ergebnisse liefern. Dagegen können Sie mit einer Berichtsmomentaufnahme gültige Vergleiche mit anderen Berichten oder Analysetools ausführen, die Daten desselben Zeitpunkts enthalten.  
  
 Eine Berichtsmomentaufnahme ist ein Bericht, der Layoutanweisungen und Abfrageergebnisse enthält, die zu einem bestimmten Zeitpunkt abgerufen wurden. Während für bedarfsgesteuerte Berichte aktuelle Abfrageergebnisse abgerufen werden, wenn Sie den Bericht auswählen, werden Berichtsmomentaufnahmen anhand eines Zeitplans verarbeitet und anschließend auf einem Berichtsserver gespeichert. Wenn Sie eine Berichtsmomentaufnahme zum Anzeigen auswählen, ruft der Berichtsserver den gespeicherten Bericht aus der Berichtsserver-Datenbank ab und zeigt die Daten und das Layout an, die zum Zeitpunkt der Momentaufnahmeerstellung für den Bericht aktuell waren.  
  
 Berichtsmomentaufnahmen werden in keinem speziellen Renderingformat gespeichert. Stattdessen werden Berichtsmomentaufnahmen erst dann in einem endgültigen Anzeigeformat (wie HTML) gerendert, wenn sie von einem Benutzer oder einer Anwendung angefordert werden. Durch das verzögerte Rendering wird eine Momentaufnahme portabel. Der Bericht kann jeweils im richtigen Format für das anfordernde Gerät oder den anfordernden Webbrowser gerendert werden.  

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
  
## <a name="to-configure-report-processing-options"></a>So konfigurieren Sie Berichtsverarbeitungsoptionen  
  
1.  Starten Sie den [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](https://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896).  
  
2.  Navigieren Sie zu dem Bericht, für den Sie Berichtsverarbeitungsoptionen festlegen möchten, und öffnen Sie den Bericht.  
  
 Zeigen Sie auf den Bericht, und klicken Sie auf den Dropdownpfeil.  
  
1.  Klicken Sie im Dropdownmenü auf **Verwalten** , und wählen Sie dann die Registerkarte **Verarbeitungsoptionen** aus.  
  
2.  Klicken Sie auf **Diesen Bericht aus einer Berichtsausführungs-Momentaufnahme rendern**, und wählen Sie dann eine der folgenden Optionen:  
  
    -   Falls Sie eine Momentaufnahme erstellen möchten, wählen Sie **Berichtsausführungs-Momentaufnahmen entsprechend diesem Zeitplan erstellen**aus, und definieren Sie anschließend einen berichtsspezifischen Zeitplan, oder wählen Sie aus der Liste **Freigegebener Zeitplan** einen Zeitplan aus.  
  
    -   Wenn Sie sofort eine Momentaufnahme erstellen möchten, wählen Sie **Erstellen Sie eine Momentaufnahme des Berichts, wenn Sie auf dieser Seite auf die Schaltfläche "Anwenden" klicken**aus.  
  
3.  Klicken Sie auf **Anwenden**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Festlegen von Berichtsverarbeitungseigenschaften](../../reporting-services/report-server/set-report-processing-properties.md)   
 [Inhalt &#40;Seite, Berichts-Manager&#41;](https://msdn.microsoft.com/library/6b16869b-158a-4934-9c85-bee934b35378)   
 [Verwalten von Berichtsserverinhalten &#40;einheitlicher SSRS-Modus&#41;](../../reporting-services/report-server/report-server-content-management-ssrs-native-mode.md)   
 [Verarbeitungsoptionen (Eigenschaftenseite) (Berichts-Manager)](https://msdn.microsoft.com/library/28f07c70-7132-4d15-9505-4fdf31dc9cc0)  
  
::: moniker-end

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
  
## <a name="to-configure-report-execution-properties"></a>So konfigurieren Sie Berichtsausführungseigenschaften  
  
Führen Sie folgende Schritte im [Webportal eines Berichtsservers (einheitlicher SSRS-Modus)](../../reporting-services/web-portal-ssrs-native-mode.md) durch:  
  
1. Navigieren Sie zu dem Bericht, dessen Ausführungseigenschaften Sie konfigurieren möchten.  
  
2. Klicken Sie mit der rechten Maustaste auf den Bericht, und klicken Sie im Dropdownmenü auf **Manage** (Verwalten).

3. Klicken Sie auf die Registerkarte **History snapshots** (Verlaufsmomentaufnahmen), um die Seite **History snapshots** (Verlaufsmomentaufnahmen) anzuzeigen.  
  
4. Klicken Sie auf die Schaltfläche **Schedules and settings** (Zeitpläne und Einstellungen), und aktivieren Sie die Option **Create history snapshots on a schedule** (Verlaufsmomentaufnahmen nach einem Zeitplan erstellen), falls diese noch nicht aktiviert ist.
  
5. Wählen Sie nach Belieben entweder einen **freigegebenen Zeitplan** oder einen **berichtsspezifischen Zeitplan** aus.  
  
6. Wählen Sie dann im Abschnitt **Advanced** (Erweitert) die gewünschte **Aufbewahrungsrichtlinie** für die Verlaufsmomentaufnahmen aus.  
  
7. Wählen Sie **Übernehmen**.  
  
   >[!NOTE]
   >Wenn Sie sofort eine Momentaufnahme erstellen möchten, klicken Sie anstelle der Schaltfläche **Schedules and settings** (Zeitpläne und Einstellungen) auf die Schaltfläche **New history snapshot** (Neue Verlaufsmomentaufnahme), woraufhin sofort eine Berichtsmomentaufnahme erstellt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Festlegen von Berichtsverarbeitungseigenschaften](../../reporting-services/report-server/set-report-processing-properties.md)   
 [Verwalten von Berichtsserverinhalten (einheitlicher SSRS-Modus)](../../reporting-services/report-server/report-server-content-management-ssrs-native-mode.md)   
 [Set Report Processing Properties (Festlegen von Berichtsverarbeitungseigenschaften)](../../reporting-services/report-server/set-report-processing-properties.md)   

::: moniker-end