---
title: Konfigurieren von Ausführungseigenschaften für einen Bericht (Berichts-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report execution properties [Reporting Services]
- reports [Reporting Services], properties
- reports [Reporting Services], execution options
ms.assetid: 73cc8dcc-ef80-40d7-9739-d33bba0eb28a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f3de8f9e708149669a65b8abf4114227392aa15a
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66102711"
---
# <a name="configure-execution-properties-for-a-report--report-manager"></a>Konfigurieren von Ausführungseigenschaften für einen Bericht (Berichts-Manager)
  Sie können Berichtsverarbeitungsoptionen festlegen, um anzugeben, wann Daten für einen Bericht abgerufen werden sollen. Es ist hilfreich, die Datenverarbeitung für einen Bericht zu planen, wenn die externe Datenquelle zu bestimmten Zeiten aktualisiert wird (beispielsweise bei einem Data Warehouse, das täglich oder wöchentlich aktualisiert wird) und Sie vermeiden wollen, dass bei jeder Berichtsanforderung dieselben Daten abgerufen werden. Das Planen der Datenverarbeitung ist außerdem hilfreich, wenn Sie die Verarbeitungslast für den externen Datenbankserver steuern möchten oder wenn Sie einheitliche Ergebnisse für verschiedene Benutzer bereitstellen möchten, die mit identischen Datensätzen arbeiten sollen. Bei flüchtigen Daten kann ein bedarfsgesteuerter Bericht von einer Minute zur nächsten unterschiedliche Ergebnisse liefern. Dagegen können Sie mit einer Berichtsmomentaufnahme gültige Vergleiche mit anderen Berichten oder Analysetools ausführen, die Daten desselben Zeitpunkts enthalten.  
  
 Eine Berichtsmomentaufnahme ist ein Bericht, der Layoutanweisungen und Abfrageergebnisse enthält, die zu einem bestimmten Zeitpunkt abgerufen wurden. Während für bedarfsgesteuerte Berichte aktuelle Abfrageergebnisse abgerufen werden, wenn Sie den Bericht auswählen, werden Berichtsmomentaufnahmen anhand eines Zeitplans verarbeitet und anschließend auf einem Berichtsserver gespeichert. Wenn Sie eine Berichtsmomentaufnahme zum Anzeigen auswählen, ruft der Berichtsserver den gespeicherten Bericht aus der Berichtsserver-Datenbank ab und zeigt die Daten und das Layout an, die zum Zeitpunkt der Momentaufnahmeerstellung für den Bericht aktuell waren.  
  
 Berichtsmomentaufnahmen werden in keinem speziellen Renderingformat gespeichert. Stattdessen werden Berichtsmomentaufnahmen erst dann in einem endgültigen Anzeigeformat (wie HTML) gerendert, wenn sie von einem Benutzer oder einer Anwendung angefordert werden. Durch das verzögerte Rendering wird eine Momentaufnahme portabel. Der Bericht kann jeweils im richtigen Format für das anfordernde Gerät oder den anfordernden Webbrowser gerendert werden.  
  
### <a name="to-configure-report-processing-options"></a>So konfigurieren Sie Berichtsverarbeitungsoptionen  
  
1.  Starten Sie den [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../report-manager-ssrs-native-mode.md).  
  
2.  Navigieren Sie zu dem Bericht, für den Sie Berichtsverarbeitungsoptionen festlegen möchten, und öffnen Sie den Bericht.  
  
 Zeigen Sie auf den Bericht, und klicken Sie auf den Dropdownpfeil.  
  
1.  Klicken Sie im Dropdownmenü auf **Verwalten** , und wählen Sie dann die Registerkarte **Verarbeitungsoptionen** aus.  
  
2.  Klicken Sie auf **Diesen Bericht aus einer Berichtsausführungs-Momentaufnahme rendern**, und wählen Sie dann eine der folgenden Optionen:  
  
    -   Falls Sie eine Momentaufnahme erstellen möchten, wählen Sie **Berichtsausführungs-Momentaufnahmen entsprechend diesem Zeitplan erstellen**aus, und definieren Sie anschließend einen berichtsspezifischen Zeitplan, oder wählen Sie aus der Liste **Freigegebener Zeitplan** einen Zeitplan aus.  
  
    -   Wenn Sie sofort eine Momentaufnahme erstellen möchten, wählen Sie **Erstellen Sie eine Momentaufnahme des Berichts, wenn Sie auf dieser Seite auf die Schaltfläche "Anwenden" klicken**aus.  
  
3.  Klicken Sie auf **Anwenden**.  
  
## <a name="see-also"></a>Siehe auch  
 [Festlegen von Berichtsverarbeitungseigenschaften](../report-server/set-report-processing-properties.md)   
 [Öffnen und Schließen eines Berichts &#40;Berichts-Manager&#41;](../reports/open-and-close-a-report-report-manager.md)   
 [Inhalt &#40;Seite, Berichts-Manager&#41;](../contents-page-report-manager.md)   
 [Verwalten von Berichtsserverinhalten &#40;einheitlicher SSRS-Modus&#41;](../report-server/report-server-content-management-ssrs-native-mode.md)   
 [Verarbeitungsoptionen (Eigenschaftenseite) &#40;Berichts-Manager&#41;](../processing-options-properties-page-report-manager.md)  
  
  
