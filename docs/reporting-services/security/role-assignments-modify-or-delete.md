---
title: Ändern oder Löschen einer Rollenzuweisung (SSRS-Webportal) | Microsoft-Dokumentation
ms.date: 05/07/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: security
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
ms.openlocfilehash: 28695a4849b29c6e593f42489fc149efd9a8db53
ms.sourcegitcommit: dda9a1a7682ade466b8d4f0ca56f3a9ecc1ef44e
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 05/14/2019
ms.locfileid: "65570647"
---
# <a name="role-assignments---modify-or-delete"></a>Rollenzuweisungen: Ändern oder Löschen

Mit einer Rollenzuweisung wird ein Gruppen- oder Benutzerkonto einer vordefinierten Rolle zugewiesen, die die ausführbaren Aufgaben definiert. Dabei werden die Aufgabentypen festgelegt, die ein Benutzer für einen Ordner, einen Bericht, ein Modell oder einen anderen Inhaltstyp ausführen kann. Wenn Sie Rollenzuweisungen erstellen, ändern oder löschen möchten, verwenden Sie das SSRS-Webportal. Nach der Erstellung einer Rollenzuweisung für einen bestimmten Benutzer oder eine bestimmte Gruppe können Sie diese später durch Auswahl einer anderen Rolle ändern. Möchten Sie Berechtigungen für einen Berichtsserver widerrufen, können Sie die Rollenzuweisung vom Berichtsserver löschen.  

Je nach Zielsetzung können alternative Vorgehensweisen geeigneter sein. Beispiele hierfür sind die Anpassung oder Erstellung einer neuen Rollendefinition beziehungsweise die Änderung der Mitgliedschaft eines Gruppenkontos in Active Directory.  

Angenommen, Sie verfügen über eine Benutzergruppe, die ihren Inhalt verwalten muss, jedoch nicht über alle dem Inhalts-Manager zugewiesenen Berechtigungen verfügen soll. In diesem Fall könnten Sie eine neue Rollendefinition namens „Inhalts-Manager für die Abteilung“ erstellen. Diese könnte alle Aufgaben des Inhalts-Managers enthalten, mit Ausnahme der Aufgabe **Sicherheit für einzelne Elemente festlegen**.

Wenn Sie System- oder Netzwerkadministrator sind, ist es wahrscheinlich einfacher, Active Directory-Gruppenkonten zu verwalten als Rollenzuweisungen im Webportal. Sie können den Mehraufwand für das Verwalten von Rollenzuweisungen reduzieren, indem Sie eine einzige Rollenzuweisung für ein Gruppenkonto erstellen. In diesem Fall können Sie die Gruppenmitgliedschaft ändern, wenn Benutzer nicht mehr auf Berichte zugreifen müssen.
  
 Sollten Sie sich dafür entscheiden, dass das Ändern oder Löschen einer Rollenzuweisung die beste Vorgehensweise ist, denken Sie daran, die Rollenzuweisung sowohl auf Systemebene als auch auf Elementebene zu prüfen. Die einzelnen Rollenzuweisungstypen werden auf unterschiedlichen Seiten im Webportal konfiguriert.
  
## <a name="to-modify-or-delete-a-system-role-assignment"></a>So löschen oder ändern Sie eine Systemrollenzuweisung
  
1. Wechseln Sie zum [Webportal eines Berichtsservers &#40;einheitlicher SSRS-Modus&#41;](../../reporting-services/web-portal-ssrs-native-mode.md).

2. Klicken Sie auf **Siteeinstellungen** > **Sicherheit**. Alle aktuell für den Server oder die Bereitstellung für horizontales Skalieren definierten Rollenzuweisungen auf Systemebene werden anhand des Kontonamens aufgeführt.

3. Suchen Sie die zu ändernde oder zu löschende Rollenzuweisung.

4. Klicken Sie zum Hinzufügen oder Entfernen der Rolle für einen bestimmten Benutzer oder eine bestimmte Gruppe auf **Bearbeiten**.

5. Aktivieren Sie zum Löschen einer Rollenzuweisung das Kontrollkästchen neben dem Benutzer- oder Gruppennamen, und klicken Sie dann auf **Löschen**.

### <a name="to-modify-or-delete-an-item-role-assignment"></a>So löschen oder ändern Sie eine Elementrollenzuweisung

1. Wechseln Sie zum Webportal, und suchen Sie das Element, für das Sie eine Rollenzuweisung bearbeiten oder löschen möchten.

2. Zeigen Sie auf das Element, und klicken Sie auf den Dropdownpfeil.

3. Klicken Sie im Dropdownmenü auf **Sicherheit**.

4. Suchen Sie die zu ändernde oder zu löschende Rollenzuweisung.

5. Klicken Sie zum Hinzufügen oder Entfernen der Rolle für einen bestimmten Benutzer oder eine bestimmte Gruppe auf **Bearbeiten**.

6. Aktivieren Sie zum Löschen einer Rollenzuweisung das Kontrollkästchen neben dem Benutzer- oder Gruppennamen, und klicken Sie dann auf **Löschen**.

## <a name="see-also"></a>Siehe auch

[Create and Manage Role Assignments (Erstellen und Verwalten von Rollenzuweisungen)](../../reporting-services/security/create-and-manage-role-assignments.md)  
[Role Assignments (Rollenzuweisungen)](../../reporting-services/security/role-assignments.md)  
