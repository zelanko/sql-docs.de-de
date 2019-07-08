---
title: Erstellen, löschen oder Ändern eines Ordners - Reporting Services | Microsoft-Dokumentation
ms.date: 06/26/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
ms.assetid: 70a38879-856c-414b-8479-5f9dead38f15
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 874fb7ba143c8f08a0f25501e1852b4d2b280cb2
ms.sourcegitcommit: c0e48b643385ce19c65ca6e348ce83b2d22b6514
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2019
ms.locfileid: "67492855"
---
# <a name="create-delete-or-modify-a-folder---reporting-services"></a>Erstellen, löschen oder Ändern eines Ordners - Reporting Services
  Sie können Ordner erstellen, um die auf einem Berichtsserver zu veröffentlichenden Elemente zu organisieren und zu verwalten. Mit der Erstellung von Ordnern können Benutzer relevante Berichte leichter finden. Für Inhalts-Manager stellen Ordner ein Framework für die Anwendung von Berechtigungen dar. Sie können Rollenzuweisungen für bestimmte Ordner erstellen, um den Zugriff auf Berichte einzuschränken, die sich aktuell in der Entwicklung befinden oder die nur bestimmten Personen zugänglich gemacht werden sollen.  

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"

## <a name="to-create-a-folder"></a>So erstellen Sie einen Ordner  
  
1.  Starten Sie den [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](https://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896).  
  
2.  Wählen Sie im Berichts-Manager den Ordner Home, und klicken Sie auf **Neuer Ordner**. Sie können einen Ordner auch unter einem vorhandenen Ordner erstellen. Navigieren Sie auf der Seite **Inhalt** zu diesem Ordner, und klicken Sie darauf, um ihn zu öffnen. Klicken Sie dann auf **Neuer Ordner**.  
  
     Die Seite **Neuer Ordner** wird geöffnet.  
  
3.  Geben Sie einen Ordnernamen ein. Ein Ordnername darf Leerzeichen enthalten, aber keine reservierten Zeichen, die für die URL-Codierung verwendet werden: „\;“, „\?“ \: \@ \& \= \+ \, \$ \/ \* \< \> \|. Sie können keine Reihe von Ordnernamen eingeben, um mehrere Ordner gleichzeitig zu erstellen.  
  
4.  Geben Sie optional eine Beschreibung ein.  
  
5.  Wählen Sie **In Listenansicht ausblenden** aus, wenn Sie den Ordner nicht in der Standardansicht der Seite **Inhalt** anzeigen möchten. Der Ordner wird Benutzern nur dann angezeigt, wenn sie auf der Seite **Inhalt** auf **Details anzeigen** klicken.  
  
6.  Klicken Sie auf **OK**.  
  
## <a name="to-delete-a-folder"></a>So löschen Sie einen Ordner  
  
1.  Navigieren Sie im Berichts-Manager zur Seite **Inhalt** , und suchen Sie das zu ändernde Element.  
  
2.  Zeigen Sie auf das Element, und klicken Sie auf den Dropdownpfeil.  
  
3.  Klicken Sie im Dropdownmenü auf **Löschen**.  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="to-modify-or-delete-a-folder"></a>So ändern oder löschen Sie einen Ordner  
  
1.  Navigieren Sie im Berichts-Manager zur Seite **Inhalt** , und suchen Sie das zu ändernde Element.  
  
2.  Zeigen Sie auf das Element, und klicken Sie auf den Dropdownpfeil.  
  
3.  Klicken Sie im Dropdownmenü auf **Verwalten**. Die Seite Allgemeine Eigenschaften wird geöffnet.  
  
4.  Klicken Sie auf **Verschieben**, um den Speicherort des Ordners zu ändern. Geben Sie den Speicherort des Zielordners ein, oder wählen Sie den Zielordner aus der Struktur aus, und klicken Sie dann auf **OK**.  
  
5.  Sie können die Ordnereigenschaften auch folgendermaßen ändern:  
  
    -   Geben Sie einen Namen oder eine Beschreibung ein, um den angezeigten Text über den Ordner zu ändern.  
  
    -   Um den Ordner in der Standardansicht auf der Seite **Inhalt** anzuzeigen, deaktivieren Sie die Option **In Listenansicht ausblenden**.  
  
6.  Sie können den Ordner und seinen Inhalt auch entfernen, indem Sie auf **Löschen**klicken.  
  
7.  Klicken Sie auf **Anwenden** , um die Änderungen zu speichern.  

::: moniker-end

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
 
## <a name="to-create-a-folder"></a>So erstellen Sie einen Ordner  
  
1. Öffnen Sie [das Webportal eines Berichtsservers (einheitlicher SSRS-Modus)](../../reporting-services/web-portal-ssrs-native-mode.md).  
  
2. Navigieren Sie zum Ordner oder Unterordner, in dem Sie den neuen Ordner zu suchen möchten. Wählen Sie die **Startseite** Ordner durch Auswählen der **Durchsuchen** auf der Symbolleiste am oberen Rand auf die Schaltfläche links auf der Seite für die Erstellung am oberen Rand der Ordnerhierarchie.  
  
3. Wählen Sie die **neu** der oben rechts auf der Symbolleiste des Berichts-Server, und klicken Sie auf die Schaltfläche **Ordner** im Dropdown-Menü.  
  
4. In der **erstellen Sie einen neuen Ordner (aktuelle Namen)** Dialogfeld Geben Sie den Namen des neuen Ordners erstellt werden. Ein Ordnername darf Leerzeichen enthalten, aber keine reservierten Zeichen wie \; oder \?, die für die URL-Codierung verwendet werden. \: \@ \& \= \+ \, \$ \/ \* \< \> \|. Sie können zudem nicht mehrere Ordnernamen eingeben, um mehrere Ordner gleichzeitig zu erstellen.  
  
5. Wählen Sie **erstellen** zum Abschließen der Aktion.  
  
## <a name="to-delete-a-folder"></a>So löschen Sie einen Ordner  
  
1. Klicken Sie im Webportal navigieren Sie der Ordnerhierarchie, und suchen Sie den Ordner, den Sie löschen möchten.  
  
2. Right-click-des-Ordners, und wählen **löschen** im Dropdown-Menü.  
  
3. Wählen Sie die **löschen** Schaltfläche der **löschen <foldername>**  im Dialogfeld, um den Löschvorgang zu bestätigen.  
  
## <a name="to-modify-a-folders-properties"></a>Zum Ändern der Eigenschaften eines Ordners  
  
1. Klicken Sie im Webportal navigieren Sie der Ordnerhierarchie, und suchen Sie den Ordner, den Sie löschen möchten.  
  
2. Right-click-des-Ordners, und wählen **löschen** im Dropdown-Menü.  
  
3. Wählen Sie die Registerkarte **Eigenschaften** aus. Die **Eigenschaften** Seite wird standardmäßig angezeigt.  
  
4. Sie können den Namen des Ordners im Ändern der *Namen** Textfeld.  
  
5. Sie können das Hinzufügen oder ändern Sie die Beschreibung des Ordners, in der *Beschreibung** Textfeld.  
  
6. Sie können ausblenden oder durch Aktivieren bzw. Deaktivieren des Ordners im Hintergrund Aufheben der **dieses Element ausblenden** Kontrollkästchen bzw.  
  
7. Wählen Sie **übernehmen** zum Speichern der eigenschaftenänderungen.  
  
8. Optional können Sie verschieben oder löschen Sie den Ordner, indem Sie auswählen können die **verschieben** oder **löschen** Schaltflächen am oberen Rand der **Eigenschaften** Seite. Finden Sie unter den [verschieben oder Löschen eines Elements (Webportal)](../../reporting-services/report-server/move-or-delete-an-item-report-manager.md) Weitere Informationen.  
  
## <a name="see-also"></a>Siehe auch  
 [Create, Delete, or Modify a Folder (web portal) (Erstellen, Löschen oder Ändern eines Ordners (Webportal))](../../reporting-services/report-server/create-delete-or-modify-a-folder-web-portal.md)   
 [Verwalten von Berichtsserverinhalten (einheitlicher SSRS-Modus)](../../reporting-services/report-server/report-server-content-management-ssrs-native-mode.md)   
 [Suchen, Anzeigen und Verwalten von Berichten (Berichts-Generator und SSRS )](../../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)    
  
::: moniker-end