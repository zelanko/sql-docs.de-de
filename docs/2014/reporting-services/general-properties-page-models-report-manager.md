---
title: Allgemeine Eigenschaften (Seite), Modelle (Berichts-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.modelproperties.general.f1
ms.assetid: 7ad59850-8135-4c4d-95e9-6d705b6d77a8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 815b8594977321ea8223c16fed166e110008a8b4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66109110"
---
# <a name="general-properties-page-models-report-manager"></a>Allgemein (Eigenschaftenseite) (Modelle, Berichts-Manager)
  Auf der Seite Allgemeine Eigenschaften für Berichtsmodelle können Sie die Modelldefinitionsdatei (Dateinamenerweiterung SMDL) umbenennen, löschen, verschieben oder ersetzen. Einzelheiten zu dem Benutzer, der das Modell erstellt oder geändert hat, und zum Zeitpunkt der Änderungen sind oben auf der Seite aufgeführt.  
  
## <a name="navigation"></a>Navigation  
 Verwenden Sie folgendes Verfahren, um zu dieser Position in der Benutzeroberfläche zu navigieren.  
  
###### <a name="to-open-the-general-properties-page-for-a-model"></a>So öffnen Sie die Seite 'Allgemeine Eigenschaften' für ein Modell  
  
1.  Öffnen Sie den Berichts-Manager, und suchen Sie das Modell, für das Sie Eigenschaften anzeigen oder konfigurieren möchten.  
  
2.  Zeigen Sie auf das Modell, und klicken Sie auf den Dropdownpfeil.  
  
3.  Klicken Sie im Dropdownmenü auf **Verwalten**. Dadurch wird die Seite Allgemeine Eigenschaften für das Modell geöffnet.  
  
## <a name="options"></a>Tastatur  
 **Name**  
 Gibt den Namen des Modells an. Der Name muss mindestens ein alphanumerisches Zeichen enthalten. Er kann auch Leerzeichen und Sonderzeichen enthalten. Folgende Zeichen können beim Angeben eines Namens nicht verwendet werden:  
  
 ; ? : \@ & = +, $/* \< > | " /  
  
 **Beschreibung**  
 Geben Sie eine Beschreibung des Modells ein. Diese Beschreibung wird für Benutzer, die über die Zugriffsberechtigung auf das Modell verfügen, auf der Seite Inhalt angezeigt.  
  
 **In Listenansicht ausblenden**  
 Aktivieren Sie dieses Kontrollkästchen, um das Element auszublenden, wenn der Ordner auf Listenansicht festgelegt ist. Die Listenansicht ist ein vom Berichts-Manager unterstützter Modus für die Anzeige von Ordnerinhalten. Diese Option können Sie in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] festlegen, um zu definieren, wie das Element im Berichts-Manager angezeigt wird. Weitere Informationen zu den Ansichtsmodi in Berichts-Manager finden Sie unter [Inhaltsseite &#40;Berichts-Manager&#41;](../../2014/reporting-services/contents-page-report-manager.md).  
  
 **Anwenden**  
 Klicken Sie auf diese Schaltfläche, um die Änderungen zu speichern.  
  
 **Löschen**  
 Klicken Sie auf diese Schaltfläche, um das Modell aus der Berichtsserver-Datenbank zu löschen. Mit dem Löschen eines Modells wird weder die abhängige freigegebene Datenquelle gelöscht, die Verbindungsinformationen bereitstellt, noch werden die Berichte gelöscht, die das Modell als Datenquelle verwenden. Berichte, die das Modell verwenden, werden jedoch nicht mehr ausgeführt, nachdem das Modell gelöscht wurde.  
  
 **Move**  
 Klicken Sie auf diese Schaltfläche, um ein Modell in der Ordnerhierarchie des Berichtsservers zu verschieben. Durch Klicken auf diese Schaltfläche wird die Seite Elemente verschieben geöffnet, auf der Sie Ordner nach einem neuen Speicherort durchsuchen können. Weitere Informationen finden Sie auf der [Seite zum Verschieben von Elementen &#40;Berichts-Manager&#41;](../../2014/reporting-services/move-items-page-report-manager.md).  
  
 **Sicher**  
 Klicken Sie auf diese Schaltfläche, um eine schreibgeschützte Kopie der Modelldefinition zu speichern. Abhängig von den auf Ihrem Computer definierten Dateizuordnungen wird die Datei in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oder einer anderen Anwendung geöffnet. In den meisten Fällen wird das Modell als XML-Datei geöffnet.  
  
 Die von Ihnen geöffnete Kopie ist mit der ursprünglichen Modelldefinition identisch, die auf dem Berichtsserver veröffentlicht wurde. Alle Eigenschaften, die für das Modell nach dessen Veröffentlichung festgelegt wurden (wie Parameter und Datenquelleneigenschaften) sind nicht in der von Ihnen geöffneten Datei enthalten.  
  
 Sie können die Modelldefinition ändern und als neue Datei in einem freigegebenen Ordner speichern. Dann können Sie die Modelldefinition als neues Element auf den Berichtsserver hochladen. Die Änderungen, die Sie an der Modelldefinition vornehmen, während sie in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (oder einer anderen Anwendung) geöffnet ist, werden nicht direkt auf dem Berichtsserver gespeichert. Sie müssen die Datei hochladen, um das geänderte Modell auf dem Berichtsserver zu veröffentlichen.  
  
 Wenn Sie das Berichtsmodell im Modell-Designer öffnen möchten, dann sollten Sie das Modell als SMDL-Datei speichern und diese Datei dann im Modell-Designer in ein Projekt einfügen.  
  
 **Stelle**  
 Klicken Sie auf diese Schaltfläche, um die Modelldefinition durch eine andere aus einer SMDL-Datei im Dateisystem zu ersetzen. Wenn Sie eine Modelldefinition aktualisieren, müssen Sie die Einstellungen der freigegebenen Datenquelle nach Abschluss der Aktualisierung zurücksetzen.  
  
 **Modell erneut generieren**  
 Klicken Sie auf diese Schaltfläche, um das Standardmodell erneut zu generieren, das die aktuelle Version ersetzt. Diese Option wird angezeigt, nachdem das Modell generiert wurde. Das generierte Modell basiert auf der freigegebenen Datenquelle. Es kann vor seiner Generierung nicht angepasst werden. Danach können Sie jedoch auf **Bearbeiten** klicken, um die Modelldefinition zu öffnen und sie in einer Datei zu speichern, die Sie dann im Modell-Designer einem Projekt hinzufügen können. Nachdem Sie das Modell verfeinert haben, können Sie es als neues Element auf den Berichtsserver hochladen oder auf dieser Seite auf **Aktualisieren** klicken, um das generierte Modell durch das von Ihnen im Modell-Designer bearbeitete Modell zu ersetzen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Binden eines Berichts oder Modells an eine freigegebene Datenquelle &#40;SSRS&#41;](report-data/bind-a-report-or-model-to-a-shared-data-source-ssrs.md)   
 [Berichtsserver im Management Studio (F1-Hilfe)](tools/report-server-in-management-studio-f1-help.md)  
  
  
