---
title: Allgemeine Eigenschaftenseite, freigegebene Datasets (Berichts-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 10798e41-24c3-4e69-893b-7ee6af7fc958
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7ed5b54ea07249a69e6f599e53658e8aba10d656
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63260758"
---
# <a name="general-properties-page-shared-datasets-report-manager"></a>Allgemeine Eigenschaften (Seite), Freigegebene Datasets (Berichts-Manager)
  Verwenden Sie die Seite Freigegebenes Dataset, um Eigenschaften für ein freigegebenes Datasetelement anzuzeigen und zu verwalten.  
  
 Die Definition des freigegebenen Datasets einschließlich der Abfrage können im Berichts-Manager nicht angezeigt oder geändert werden. Zum Ändern der Definition müssen Sie diese mit einem Erstellungstool öffnen, ändern und anschließend auf dem Berichtsserver speichern.  
  
 Mit einem freigegebenen Dataset können Sie die Einstellungen für ein Dataset getrennt von Berichten, Komponenten und anderen Katalogelementen verwalten, von denen es verwendet wird.  
  
## <a name="navigation"></a>Navigation  
 Verwenden Sie folgendes Verfahren, um zu dieser Position in der Benutzeroberfläche zu navigieren.  
  
###### <a name="to-open-the-shared-dataset-properties-page-for-a-shared-dataset"></a>So öffnen Sie die Eigenschaftenseite "Freigegebenes Dataset" für ein freigegebenes Dataset  
  
1.  Öffnen Sie den Berichts-Manager, und suchen Sie das freigegebene Dataset, für das Sie Eigenschaften konfigurieren möchten.  
  
2.  Zeigen Sie auf das freigegebene Dataset, und klicken Sie auf den Dropdownpfeil.  
  
3.  Klicken Sie in der Dropdownliste auf **Verwalten**. Die Eigenschaftenseite Allgemein wird geöffnet.  
  
## <a name="options"></a>Optionen  
 **Name**  
 Geben Sie einen Namen für das freigegebene Dataset ein, der zum Identifizieren des Elements innerhalb der Ordnerhierarchie des Berichtsservers verwendet wird.  
  
 **Beschreibung**  
 Stellen Sie Informationen zum freigegebenen Dataset bereit. Diese Beschreibung wird auf der Seite Inhalt angezeigt.  
  
 **In Listenansicht ausblenden**  
 Blenden Sie das freigegebene Dataset für Benutzer aus, die den Listenansichtsmodus im Berichts-Manager verwenden. Der Listenansichtsmodus ist das Standardanzeigeformat beim Durchsuchen der Ordnerhierarchie auf dem Berichtsserver. In der Listenansicht erstrecken sich Namen und Beschreibungen über die Seite. Das alternative Format ist die Detailansicht. Detailansichten lassen Beschreibungen aus, enthalten jedoch andere Informationen zum Element. Obwohl Sie ein Element in der Listenansicht ausblenden können, kann es in der Detailansicht nicht ausgeblendet werden. Wenn Sie den Zugriff auf ein Element einschränken möchten, müssen Sie eine Rollenzuweisung erstellen.  
  
 **Timeout für abfrageausführung**  
 Geben Sie die Anzahl an Sekunden als Timeoutwert für die Abfrage ein. Lautet der Wert 0, gibt es für die Abfrage kein Timeout.  
  
 **Anwenden**  
 Speichern Sie die Änderungen.  
  
 **Löschen**  
 Entfernen Sie das freigegebene Dataset aus der Berichtsserver-Datenbank. Durch das Löschen eines freigegebenen Datasets werden alle Berichte oder zwischengespeicherten Versionen deaktiviert. Um einen Bericht erneut zu aktivieren, müssen Sie jeden Bericht in einem Berichterstellungstool öffnen und ein Dataset mit dem gleichen Namen und der gleichen Feldauflistung angeben. Alternativ können Sie jeden Datenbereichsverweis für die Verwendung eines anderen Datasets mit der gleichen Feldauflistung aktualisieren.  
  
 **Verschieben**  
 Verschieben Sie ein freigegebenes Dataset in der Ordnerhierarchie des Berichtsservers. Durch Klicken auf diese Schaltfläche wird die Seite Elemente verschieben geöffnet, auf der Sie Ordner nach einem neuen Speicherort durchsuchen können. Weitere Informationen finden Sie unter [Seite "Elemente" verschieben &#40;Berichts-Manager&#41;](../../2014/reporting-services/move-items-page-report-manager.md).  
  
 **Download**  
 Extrahieren Sie eine Kopie der Definition des freigegebenen Datasets. Abhängig von den auf Ihrem Computer definierten Dateizuweisungen wird die Datei in Visual Studio oder einer anderen Anwendung geöffnet. In den meisten Fällen wird das freigegebene Dataset als XML-Datei geöffnet.  
  
 **Ersetzen**  
 Ersetzen Sie die Definition des freigegebenen Datasets durch eine andere Definition aus einer RSD-Datei im Dateisystem.  
  
## <a name="see-also"></a>Siehe auch  
 [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Inhalt &#40;Seite, Berichts-Manager&#41;](../../2014/reporting-services/contents-page-report-manager.md)   
 [Berichts-Manager-F1-Hilfe](../../2014/reporting-services/report-manager-f1-help.md)   
 [Zwischenspeichern von Optionen zur Cacheaktualisierung &#40;Berichts-Manager&#41;](../../2014/reporting-services/cache-refresh-options-report-manager.md)   
 [Zwischenspeichern (Seite), freigegebene Datasets &#40;Berichts-Manager&#41;](../../2014/reporting-services/caching-page-shared-datasets-report-manager.md)   
 [Verwalten von freigegebenen Datasets](report-data/manage-shared-datasets.md)   
 [Zwischenspeichern von freigegebenen Datasets &#40;SSRS&#41;](report-server/cache-shared-datasets-ssrs.md)  
  
  
