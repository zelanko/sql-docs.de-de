---
title: Erstellen, Löschen oder Ändern eines Ordners – Reporting Services | Microsoft-Dokumentation
ms.date: 06/26/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
ms.assetid: 70a38879-856c-414b-8479-5f9dead38f15
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 874fb7ba143c8f08a0f25501e1852b4d2b280cb2
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "67492855"
---
# <a name="create-delete-or-modify-a-folder---reporting-services"></a>Erstellen, Löschen oder Ändern eines Ordners – Reporting Services
  Sie können Ordner erstellen, um die auf einem Berichtsserver zu veröffentlichenden Elemente zu organisieren und zu verwalten. Mit der Erstellung von Ordnern können Benutzer relevante Berichte leichter finden. Für Inhalts-Manager stellen Ordner ein Framework für die Anwendung von Berechtigungen dar. Sie können Rollenzuweisungen für bestimmte Ordner erstellen, um den Zugriff auf Berichte einzuschränken, die sich aktuell in der Entwicklung befinden oder die nur bestimmten Personen zugänglich gemacht werden sollen.  

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"

## <a name="to-create-a-folder"></a>So erstellen Sie einen Ordner  
  
1.  Starten Sie den [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](https://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896).  
  
2.  Wählen Sie im Berichts-Manager den Ordner Home, und klicken Sie auf **Neuer Ordner**. Sie können einen Ordner auch unter einem vorhandenen Ordner erstellen. Navigieren Sie auf der Seite **Inhalt** zu diesem Ordner, und klicken Sie darauf, um ihn zu öffnen. Klicken Sie dann auf **Neuer Ordner**.  
  
     Die Seite **Neuer Ordner** wird geöffnet.  
  
3.  Geben Sie einen Ordnernamen ein. Ein Ordnername darf Leerzeichen enthalten, aber keine reservierten Zeichen, die für die URL-Codierung verwendet werden: \; \? \: \@ \& \= \+ \, \$ \/ \* \< \> \|. Sie können keine Reihe von Ordnernamen eingeben, um mehrere Ordner gleichzeitig zu erstellen.  
  
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
  
7.  Klicken Sie auf **Apply** (Übernehmen), um die Änderungen zu speichern.  

::: moniker-end

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
 
## <a name="to-create-a-folder"></a>So erstellen Sie einen Ordner  
  
1. Öffnen Sie [das Webportal eines Berichtsservers (einheitlicher SSRS-Modus)](../../reporting-services/web-portal-ssrs-native-mode.md).  
  
2. Navigieren Sie zu dem Ordner oder Unterordner, in Sie den neuen Ordner platzieren möchten. Wählen Sie den Ordner **Home** aus, indem Sie oben links auf der Symbolleiste der Seite auf die Schaltfläche **Durchsuchen** klicken, um den Ordner an oberster Stelle der Ordnerhierarchie zu erstellen.  
  
3. Klicken Sie oben rechts auf der Symbolleiste des Berichtsservers auf die Schaltfläche **Neu**, und wählen Sie aus dem Dropdownmenü die Option **Ordner** aus.  
  
4. Geben Sie im Dialogfeld **Neuen Ordner in „[aktueller Ordnername]“ erstellen** den Namen für den neuen Ordner ein, der erstellt werden soll. Ein Ordnername darf Leerzeichen enthalten, aber keine reservierten Zeichen, die für die URL-Codierung verwendet werden: \; \? \: \@ \& \= \+ \, \$ \/ \* \< \> \|. Sie können zudem nicht mehrere Ordnernamen eingeben, um mehrere Ordner gleichzeitig zu erstellen.  
  
5. Klicken Sie auf **Erstellen**, um die Aktion abzuschließen.  
  
## <a name="to-delete-a-folder"></a>So löschen Sie einen Ordner  
  
1. Navigieren Sie im Webportal zur Ordnerhierarchie, und suchen Sie den Ordner, den Sie löschen möchten.  
  
2. Klicken Sie mit der rechten Maustaste auf den Ordner, und wählen Sie im Dropdownmenü die Option **Löschen** aus.  
  
3. Klicken Sie im Dialogfeld **„<foldername>“ löschen** auf die Schaltfläche **Löschen**, um den Löschvorgang zu bestätigen.  
  
## <a name="to-modify-a-folders-properties"></a>So ändern Sie die Eigenschaften eines Ordners  
  
1. Navigieren Sie im Webportal zur Ordnerhierarchie, und suchen Sie den Ordner, den Sie löschen möchten.  
  
2. Klicken Sie mit der rechten Maustaste auf den Ordner, und wählen Sie im Dropdownmenü die Option **Löschen** aus.  
  
3. Wählen Sie die Registerkarte **Eigenschaften** aus. Die Seite **Eigenschaften** wird standardmäßig angezeigt.  
  
4. Sie können den Namen des Ordners im Textfeld *Name** ändern.  
  
5. Sie können die Beschreibung des Ordners im Textfeld *Beschreibung** hinzufügen oder ändern.  
  
6. Sie können den Ordner ein- oder ausblenden, indem Sie das Kontrollkästchen **Dieses Element ausblenden** aktivieren bzw. deaktivieren.  
  
7. Wählen Sie **Übernehmen** aus, um die Eigenschaftenänderungen zu speichern.  
  
8. Optional können Sie den Ordner verschieben oder löschen, indem Sie oben auf der Seite **Eigenschaften** die Schaltflächen **verschieben** oder **Löschen** auswählen. Weitere Informationen finden Sie im Artikel [Verschieben oder Löschen eines Elements (Webportal)](../../reporting-services/report-server/move-or-delete-an-item-report-manager.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Create, Delete, or Modify a Folder (web portal) (Erstellen, Löschen oder Ändern eines Ordners (Webportal))](../../reporting-services/report-server/create-delete-or-modify-a-folder-web-portal.md)   
 [Verwalten von Berichtsserverinhalten (einheitlicher SSRS-Modus)](../../reporting-services/report-server/report-server-content-management-ssrs-native-mode.md)   
 [Suchen, Anzeigen und Verwalten von Berichten (Berichts-Generator und SSRS )](../../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)    
  
::: moniker-end