---
title: Allgemeine Eigenschaften (Seite), Berichts Teile (Berichts-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 93ddce72-31f1-42f7-abd5-8191acbb00c5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: aa3f8b6ec0cd81f1a29ea3262bd3ec52dd8158ae
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66109088"
---
# <a name="general-properties-page-report-parts-report-manager"></a>Allgemeine Eigenschaften (Seite), Berichtsteile (Berichts-Manager)
  Verwenden Sie die Eigenschaftenseite, um die allgemeinen Eigenschaften für einen Berichtsteil anzuzeigen und zu verwalten.  
  
 Die Darstellung sowie die Funktionen des Berichtsteils können nicht im Berichts-Manager angezeigt oder geändert werden. Zum Ändern des Entwurfs müssen Sie diesen mit einem Erstellungstool öffnen, ändern und anschließend wieder auf dem Server veröffentlichen.  
  
## <a name="navigation"></a>Navigation  
 Verwenden Sie folgendes Verfahren, um zu dieser Position in der Benutzeroberfläche zu navigieren.  
  
###### <a name="to-open-the-properties-page-for-a-report-part"></a>So öffnen Sie die Eigenschaftenseite für einen Berichtsteil  
  
1.  Öffnen Sie den Berichts-Manager, und suchen Sie den Berichtsteil, für den Sie Eigenschaften konfigurieren möchten.  
  
2.  Zeigen Sie auf den Berichtsteil, und klicken Sie auf den Dropdownpfeil.  
  
3.  Klicken Sie in der Dropdownliste auf **Verwalten**. Die Eigenschaftenseite Allgemein wird geöffnet.  
  
## <a name="options"></a>Optionen  
 **Geändert am**  
 Datum und Uhrzeit, zu denen die Berichtsteileigenschaften zuletzt auf dem Server geändert wurden oder eine neue Version des Berichtsteils auf dem Server veröffentlicht wurde. Schreibgeschützt.  
  
 **Geändert von**  
 Der Name des Benutzers, der den Berichtsteil zuletzt geändert hat. Schreibgeschützt.  
  
 **Erstellungsdatum**  
 Datum und Uhrzeit, zu denen der Berichtsteil ursprünglich auf dem Server veröffentlicht wurde. Schreibgeschützt.  
  
 **Erstellt von**  
 Der Name des Benutzers, der den Berichtsteil ursprünglich erstellt hat. Schreibgeschützt.  
  
 **Größe**  
 Die Dateigröße des Berichtsteils. Schreibgeschützt.  
  
 **Name**  
 Geben Sie einen Namen ein, um den Berichtsteil zu identifizieren.  
  
 **Beschreibung**  
 Stellen Sie Informationen zum Berichtsteil bereit. Die Beschreibung wird auf der Seite Inhalt des Berichts-Managers angezeigt. Der Beschreibungstext kann durchsucht werden, wenn ein Benutzer in einem Berichterstellungstool nach Berichtsteilen sucht.  
  
 **In Listenansicht ausblenden**  
 Wählen Sie diese Option aus, um den Berichtsteil für Benutzer auszublenden, die den Listenansichtsmodus im Berichts-Manager verwenden. Der Listenansichtsmodus ist das Standardansichtsformat beim Durchsuchen der Ordnerhierarchie des Berichtsservers. Obwohl Sie ein Element in der Listenansicht ausblenden können, kann es in der Detailansicht nicht ausgeblendet werden. Wenn Sie den Zugriff auf ein Element einschränken möchten, müssen Sie eine Rollenzuweisung erstellen.  
  
 **Typ**  
 Der Typ des Berichtsteils. Schreibgeschützt.  
  
 **übernehmen**  
 Speichern Sie die Änderungen.  
  
 **Löschen**  
 Entfernen Sie den Berichtsteil aus der Berichtsserver-Datenbank. Durch das Löschen eines Berichtsteils vom Server wird nicht verhindert, dass vorhandene Berichte, denen der Berichtsteil hinzugefügt wurde, gerendert werden.  
  
 **Move**  
 Klicken Sie auf diese Option, um die Seite Elemente verschieben zu öffnen und einen Berichtsteil innerhalb der Ordnerhierarchie des Berichtsservers zu verschieben. Weitere Informationen finden Sie auf der [Seite zum Verschieben von Elementen &#40;Berichts-Manager&#41;](../../2014/reporting-services/move-items-page-report-manager.md).  
  
 **Download**  
 Extrahieren Sie eine Kopie der Berichtsteildefinition, die als RSC-Datei gespeichert werden soll. Die RSC-Datei kann in einen Berichtsserverordner hochgeladen oder zum Ersetzen eines vorhandenen Berichtsteils in einem Berichtsserverordner verwendet werden.  
  
 **Stelle**  
 Ersetzen Sie die Berichtsteildefinition durch eine andere Definition aus einer RSC-Datei.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten von Berichts teilen](report-design/managing-report-parts.md)   
 [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Die Inhaltsseite &#40;Berichts-Manager&#41;](../../2014/reporting-services/contents-page-report-manager.md)   
 [Berichts Teile &#40;Berichts-Generator und SSRS&#41;](report-parts-report-builder-and-ssrs.md)   
 [Berichts-Manager F1-Hilfe](../../2014/reporting-services/report-manager-f1-help.md)   
 [Berichtsteile und Datasets in Berichts-Generator](report-data/report-parts-and-datasets-in-report-builder.md)  
  
  
