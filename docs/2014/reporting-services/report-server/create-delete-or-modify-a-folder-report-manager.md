---
title: Erstellen, Löschen oder Ändern eines Ordners (Berichts-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- removing folders
- modifying folders
- deleting folders
- folders [Reporting Services], creating
- folders [Reporting Services], deleting
- folders [Reporting Services], modifying
ms.assetid: d62159a8-ec67-4e28-a9f1-05a9250065bb
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 89b1476adadf6b409d68dbf524a9352d6b7cb6ab
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48129338"
---
# <a name="create-delete-or-modify-a-folder-report-manager"></a>Erstellen, Löschen oder Ändern eines Ordners (Berichts-Manager)
  Sie können Ordner erstellen, um die auf einem Berichtsserver zu veröffentlichenden Elemente zu organisieren und zu verwalten. Mit der Erstellung von Ordnern können Benutzer relevante Berichte leichter finden. Für Inhalts-Manager stellen Ordner ein Framework für die Anwendung von Berechtigungen dar. Sie können Rollenzuweisungen für bestimmte Ordner erstellen, um den Zugriff auf Berichte einzuschränken, die sich aktuell in der Entwicklung befinden oder die nur bestimmten Personen zugänglich gemacht werden sollen.  
  
### <a name="to-create-a-folder"></a>So erstellen Sie einen Ordner  
  
1.  Starten Sie [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../report-manager-ssrs-native-mode.md).  
  
2.  Wählen Sie im Berichts-Manager den Ordner Home, und klicken Sie auf **Neuer Ordner**. Sie können einen Ordner auch unter einem vorhandenen Ordner erstellen. Navigieren Sie auf der Seite **Inhalt** zu diesem Ordner, und klicken Sie darauf, um ihn zu öffnen. Klicken Sie dann auf **Neuer Ordner**.  
  
     Die Seite **Neuer Ordner** wird geöffnet.  
  
3.  Geben Sie einen Ordnernamen ein. Ein Ordnername kann Leerzeichen enthalten, jedoch keine reservierten Zeichen, die für die URL-Codierung verwendet werden: ; ? : \@ & = +, $ / * \< > |. Sie können keine Reihe von Ordnernamen eingeben, um mehrere Ordner gleichzeitig zu erstellen.  
  
4.  Geben Sie optional eine Beschreibung ein.  
  
5.  Wählen Sie **In Listenansicht ausblenden** aus, wenn Sie den Ordner nicht in der Standardansicht der Seite **Inhalt** anzeigen möchten. Der Ordner wird Benutzern nur dann angezeigt, wenn sie auf der Seite **Inhalt** auf **Details anzeigen** klicken.  
  
6.  Klicken Sie auf **OK**.  
  
### <a name="to-delete-a-folder"></a>So löschen Sie einen Ordner  
  
1.  Navigieren Sie im Berichts-Manager zur Seite **Inhalt** , und suchen Sie das zu ändernde Element.  
  
2.  Zeigen Sie auf das Element, und klicken Sie auf den Dropdownpfeil.  
  
3.  Klicken Sie im Dropdownmenü auf **Löschen**.  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-modify-or-delete-a-folder"></a>So ändern oder löschen Sie einen Ordner  
  
1.  Navigieren Sie im Berichts-Manager zur Seite **Inhalt** , und suchen Sie das zu ändernde Element.  
  
2.  Zeigen Sie auf das Element, und klicken Sie auf den Dropdownpfeil.  
  
3.  Klicken Sie im Dropdownmenü auf **Verwalten**. Die Seite Allgemeine Eigenschaften wird geöffnet.  
  
4.  Klicken Sie auf **Verschieben**, um den Speicherort des Ordners zu ändern. Geben Sie den Speicherort des Zielordners ein, oder wählen Sie den Zielordner aus der Struktur aus, und klicken Sie dann auf **OK**.  
  
5.  Sie können die Ordnereigenschaften auch folgendermaßen ändern:  
  
    -   Geben Sie einen Namen oder eine Beschreibung ein, um den angezeigten Text über den Ordner zu ändern.  
  
    -   Um den Ordner in der Standardansicht auf der Seite **Inhalt** anzuzeigen, deaktivieren Sie die Option **In Listenansicht ausblenden**.  
  
6.  Sie können den Ordner und seinen Inhalt auch entfernen, indem Sie auf **Löschen**klicken.  
  
7.  Klicken Sie auf **Anwenden** , um die Änderungen zu speichern.  
  
## <a name="see-also"></a>Siehe auch  
 [Seite "Neuer Ordner" &#40;Berichts-Manager&#41;](../new-folder-page-report-manager.md)   
 [Inhalt der Seite &#40;Berichts-Manager&#41;](../contents-page-report-manager.md)   
 [Suchen, Anzeigen und Verwalten von Berichten (Berichts-Generator und SSRS )](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
