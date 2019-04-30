---
title: Ändern oder Löschen einer Rollenzuweisung (Berichts-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- removing role assignments
- roles [Reporting Services], assignments
- system roles [Reporting Services]
- modifying role assignments
- deleting role assignments
ms.assetid: 523bdd32-92cb-4b48-a3a9-d58b2385bde7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f8810a4df8c04703667e1b817931ada65fda0e5f
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63461141"
---
# <a name="modify-or-delete-a-role-assignment-report-manager"></a>Ändern oder Löschen einer Rollenzuweisung (Berichts-Manager)
  Mit einer Rollenzuweisung werden eine Gruppe oder ein Benutzerkonto einer vordefinierten Rollendefinition zugewiesen, die ausführbare Aufgaben beinhaltet. Hiermit werden die Vorgangstypen festgelegt, die ein Benutzer für einen Ordner, einen Bericht, ein Modell oder einen anderen Inhaltstyp ausführen kann. Verwenden Sie den Berichts-Manager zum Erstellen, Löschen oder Ändern von Rollenzuweisungen. Nach der Erstellung einer Rollenzuweisung für einen bestimmten Benutzer oder eine bestimmte Gruppe können Sie diese später durch Auswahl einer anderen Rolle ändern. Möchten Sie Berechtigungen für einen Berichtsserver widerrufen, können Sie die Rollenzuweisung vom Berichtsserver löschen.  
  
 Je nach Zielsetzung können alternative Vorgehensweisen geeigneter sein. Beispiele hierfür sind die Anpassung oder Erstellung einer neuen Rollendefinition beziehungsweise die Änderung der Mitgliedschaft eines Gruppenkontos in Active Directory.  
  
 Angenommen, Sie verfügen beispielsweise über eine Benutzergruppe, die ihren Inhalt vollständig verwalten muss, jedoch nicht über alle dem Inhalts-Manager zugewiesenen Berechtigungen verfügen soll. In diesem Fall könnten Sie eine neue Rollendefinition mit der Bezeichnung "Inhalts-Manager für Abteilung" erstellen, die alle Aufgaben des Inhalts-Manager enthält, ausgenommen **Sicherheit für einzelne Elemente festlegen**.  
  
 Ähnliches gilt, falls Sie System- oder Netzwerkadministrator sind und Active Directory-Gruppenkonten einfacher verwalten können als Rollenzuweisungen im Berichts-Manager. In diesem Fall können Sie den Aufwand für die Verwaltung von Rollenzuweisungen durch die Erstellung einer einzelnen Rollenzuweisung für ein Gruppenkonto und die anschließende Anpassung der Gruppenmitgliedschaft, wenn Benutzer keinen Zugriff mehr auf Berichte benötigen, verringern.  
  
 Sollten Sie zu dem Schluss kommen, dass die Änderung oder Löschung einer Rollenzuweisung die beste Vorgehensweise ist, denken Sie daran, sowohl die Rollenzuweisungen auf Systemebene als auch die Rollenzuweisungen auf Elementebene zu prüfen. Jeder Rollenzuweisungstyp wird auf anderen Seiten im Berichts-Manager konfiguriert.  
  
### <a name="to-modify-or-delete-a-system-role-assignment"></a>So löschen oder ändern Sie eine Systemrollenzuweisung  
  
1.  Starten Sie den [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../report-manager-ssrs-native-mode.md).  
  
2.  Klicken Sie auf **Siteeinstellungen**.  
  
3.  Klicken Sie auf **Sicherheit**. Alle aktuell für den Server oder die Bereitstellung für horizontales Skalieren definierten Rollenzuweisungen auf Systemebene werden anhand des Kontonamens aufgeführt.  
  
4.  Suchen Sie die zu ändernde oder zu löschende Rollenzuweisung.  
  
5.  Zum Hinzufügen oder Entfernen der Rolle für einen bestimmten Benutzer oder eine bestimmte Gruppe klicken Sie auf **Bearbeiten**.  
  
6.  Aktivieren Sie zum Löschen einer Rollenzuweisung das Kontrollkästchen neben dem Gruppen- oder Benutzernamen, und klicken Sie dann auf **Löschen**.  
  
### <a name="to-modify-or-delete-an-item-role-assignment"></a>So löschen oder ändern Sie eine Elementrollenzuweisung  
  
1.  Starten Sie den **Berichts-Manager** , und suchen Sie das Element, für das Sie eine Rollenzuweisung bearbeiten oder löschen möchten.  
  
2.  Zeigen Sie auf das Element, und klicken Sie auf den Dropdownpfeil.  
  
3.  Klicken Sie im Dropdownmenü auf **Sicherheit**.  
  
4.  Suchen Sie die zu ändernde oder zu löschende Rollenzuweisung.  
  
5.  Zum Hinzufügen oder Entfernen der Rolle für einen bestimmten Benutzer oder eine bestimmte Gruppe klicken Sie auf **Bearbeiten**.  
  
6.  Aktivieren Sie zum Löschen einer Rollenzuweisung das Kontrollkästchen neben dem Gruppen- oder Benutzernamen, und klicken Sie dann auf **Löschen**.  
  
## <a name="see-also"></a>Siehe auch  
 (create-and-manage-role-assignments.md)   
 [Rollenzuweisungen](role-assignments.md)   
 [Site Settings Page (Report Manager) (Seite „Siteeinstellungen“ (Berichts-Manager))](../site-settings-page-report-manager.md)   
 [Neue Systemrollenzuweisung: Bearbeiten System Role Assignments Page &#40;Berichts-Manager&#41;](../new-system-role-assignments-edit-system-role-assignments-page-report-manager.md)  
  
  
