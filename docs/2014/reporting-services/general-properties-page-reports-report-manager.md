---
title: Allgemeine Eigenschaftenseite, Berichte (Berichts-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 66c99d28-ab41-45f0-bf02-ed560293595d
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 408d86a821d2596172570f513ee8398e43298f91
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56030271"
---
# <a name="general-properties-page-reports-report-manager"></a>Allgemeine Eigenschaften (Seite) (Berichte, Berichts-Manager)
  Mithilfe der Seite Allgemeine Eigenschaften für Berichte können Sie eine Berichtsdefinition umbenennen, löschen, verschieben oder ersetzen. Zudem ist mit dieser Seite das Erstellen eines verknüpften Berichts möglich. Details zum Benutzer, der den Bericht erstellt oder geändert hat, und zum Zeitpunkt der Änderungen sind oben auf der Seite aufgeführt.  
  
## <a name="navigation"></a>Navigation  
 Verwenden Sie folgendes Verfahren, um zu dieser Position in der Benutzeroberfläche zu navigieren.  
  
###### <a name="to-open-the-general-properties-page-for-a-report"></a>So öffnen Sie die Seite Allgemeine Eigenschaften für einen Bericht  
  
1.  Öffnen Sie den Berichts-Manager, und suchen Sie den Bericht, für den Sie Eigenschaften anzeigen oder konfigurieren möchten.  
  
2.  Zeigen Sie auf den Bericht, und klicken Sie auf den Dropdownpfeil.  
  
3.  Klicken Sie im Dropdownmenü auf **Verwalten**. Dadurch wird die Seite Allgemeine Eigenschaften für den Bericht geöffnet.  
  
## <a name="options"></a>Optionen  
 **Name**  
 Geben Sie einen Namen für den Bericht an. Der Name muss mindestens ein alphanumerisches Zeichen enthalten. Er kann auch Leerzeichen und bestimmte Sonderzeichen enthalten. Folgende Zeichen können nicht beim Angeben eines Namens verwendet werden: ; ? : \@ & = + , $ * \< >  
  
 " oder /.  
  
 **Beschreibung**  
 Geben Sie eine Beschreibung des Berichts ein. Diese Beschreibung wird für Benutzer, die über die Berechtigung zum Zugreifen auf den Bericht verfügen, auf der Seite Inhalt angezeigt.  
  
 **In Listenansicht ausblenden**  
 Wählen Sie diese Option aus, um den Bericht für Benutzer auszublenden, die den Listenansichtsmodus im Berichts-Manager verwenden. Der Listenansichtsmodus ist das Standardanzeigeformat beim Durchsuchen der Ordnerhierarchie auf dem Berichtsserver. In der Listenansicht erstrecken sich Namen und Beschreibungen über die Seite. Das alternative Format ist die Detailsansicht. Detailansichten lassen Beschreibungen aus, enthalten jedoch andere Informationen zum Element. Obwohl Sie ein Element in der Listenansicht ausblenden können, kann es in der Detailansicht nicht ausgeblendet werden. Wenn Sie den Zugriff auf ein Element einschränken möchten, müssen Sie eine Rollenzuweisung erstellen.  
  
 **Anwenden**  
 Klicken Sie auf diese Schaltfläche, um die Änderungen zu speichern.  
  
 **Delete**  
 Klicken Sie auf diese Schaltfläche, um den Bericht aus der Berichtsserver-Datenbank zu löschen. Durch das Löschen eines Berichts werden der gesamte Berichtsverlauf und alle berichtsspezifischen Zeitpläne und Abonnements gelöscht. Falls der Bericht mit verknüpften Berichten verbunden ist, werden die verknüpften Berichte ungültig.  
  
 **Verschieben**  
 Klicken Sie auf diese Schaltfläche, um einen Bericht in der Ordnerhierarchie des Berichtsservers zu verschieben. Durch Klicken auf diese Schaltfläche wird die Seite Elemente verschieben geöffnet, auf der Sie Ordner nach einem neuen Speicherort durchsuchen können. Weitere Informationen finden Sie unter [Seite "Elemente" verschieben &#40;Berichts-Manager&#41;](../../2014/reporting-services/move-items-page-report-manager.md).  
  
 **Verknüpften Bericht erstellen**  
 Klicken Sie auf diese Schaltfläche, um die Seite Neuer verknüpfter Bericht zu öffnen. Weitere Informationen zu dieser Seite und verknüpfte Berichte finden Sie unter [neue verknüpfte Berichtsseite &#40;Berichts-Manager&#41;](../../2014/reporting-services/new-linked-report-page-report-manager.md).  
  
 **Speichern**  
 Klicken Sie auf diese Schaltfläche, um eine schreibgeschützte Kopie der Berichtsdefinition zu extrahieren. Abhängig von den auf Ihrem Computer definierten Dateizuordnungen wird die Datei in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oder einer anderen Anwendung geöffnet. In den meisten Fällen wird der Bericht als XML-Datei geöffnet.  
  
 Die von Ihnen geöffnete Kopie ist mit der ursprünglichen Berichtsdefinition identisch, die auf dem Berichtsserver veröffentlicht wurde. Alle Eigenschaften, die für den Bericht nach dessen Veröffentlichung festgelegt wurden (wie Parameter und Datenquelleneigenschaften) sind nicht in der von Ihnen geöffneten Datei enthalten.  
  
 Die können die Berichtsdefinition ändern und als neue Datei in einem freigegebenen Ordner speichern. Dann können Sie die Berichtsdefinition als neues Element auf dem Berichtsserver hochladen. Die Änderungen, die Sie an der Berichtsdefinition vornehmen, während diese in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (oder einer anderen Anwendung) geöffnet ist, werden nicht direkt auf dem Berichtsserver gespeichert. Sie müssen die Datei hochladen, um den veränderten Bericht auf dem Berichtsserver zu veröffentlichen.  
  
 **Ersetzen**  
 Klicken Sie auf diese Schaltfläche, um die im aktuellen Bericht verwendete Berichtsdefinition durch eine andere aus einer RDL-Datei im Dateisystem zu ersetzen. Wenn Sie eine Berichtsdefinition aktualisieren, müssen Sie die Einstellungen zur Datenquelle nach Abschluss des Updates zurücksetzen.  
  
 **Link ändern**  
 Klicken Sie auf diese Schaltfläche, um eine andere Berichtsdefinition für den verknüpften Bericht auszuwählen. Diese Option wird angezeigt, wenn es sich um einen verknüpften Bericht handelt. Bei einem verknüpften Bericht kann durch Festlegen dieser Eigenschaft die Berichtsdefinition ersetzt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Berichts-Manager (F1-Hilfe)](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
