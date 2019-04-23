---
title: Sicherheit (Eigenschaftenseite) Elementen (Berichts-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 351b8503-354f-4b1b-a7ac-f1245d978da0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bb1835a67ca1f909bf382fd227783cb0a20bbbf5
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59934766"
---
# <a name="security-properties-page-items-report-manager"></a>Sicherheit (Eigenschaftenseite) (Elemente, Berichts-Manager)
  Mithilfe der Eigenschaftenseite für Sicherheit können Sie die Sicherheitseinstellungen für den Zugriff auf Ordner, Berichte, Modelle, Ressourcen und freigegebene Datenquellen anzeigen und ändern. Diese Seite steht für Elemente zur Verfügung, für die Sie die Berechtigung zur Änderung der Sicherheitseinstellungen besitzen.  
  
 Der Zugriff auf Elemente wird durch Rollenzuweisungen definiert, in denen die Aufgaben angegeben sind, die eine Gruppe oder ein Benutzer ausführen kann. Eine Rollenzuweisung besteht aus einem Benutzer- oder Gruppennamen und einer oder mehreren Rollendefinitionen, die eine Sammlung von Aufgaben angeben.  
  
 Sicherheitseinstellungen werden vom Stammordner in der Hierarchie nach unten zu Unterordnern und Elementen in diesen Ordnern vererbt. Wenn Sie die Vererbung der Sicherheitseinstellungen nicht explizit unterbrechen, erben Unterordner und Elemente den Sicherheitskontext eines übergeordneten Elements. Wenn Sie die Sicherheitsrichtlinie eines Ordners in der Mitte der Hierarchie neu definieren, übernehmen alle dem Ordner untergeordneten Elemente einschließlich der Unterordner die neuen Sicherheitseinstellungen.  
  
## <a name="navigation"></a>Navigation  
 Verwenden Sie folgendes Verfahren, um zu dieser Position in der Benutzeroberfläche zu navigieren.  
  
###### <a name="to-open-the-security-page-for-an-item"></a>So öffnen Sie die Seite Sicherheit für ein Element  
  
1.  Öffnen Sie den Berichts-Manager, und suchen Sie das Element, für das Sie Sicherheitseinstellungen konfigurieren möchten.  
  
2.  Zeigen Sie auf das Element, und klicken Sie auf den Dropdownpfeil.  
  
3.  Führen Sie im Dropdownmenü einen der folgenden Schritte aus:  
  
    -   Klicken Sie auf **Sicherheit**. Dadurch wird die Eigenschaftenseite Sicherheit für das Element geöffnet.  
  
    -   Klicken Sie auf **Verwalten** , um die Seite Allgemeine Eigenschaften für das Element zu öffnen. Wählen Sie dann die Registerkarte **Sicherheit** aus.  
  
 **Elementsicherheit bearbeiten**  
 Klicken Sie auf diese Schaltfläche, um die Definition der Sicherheit für das aktuelle Element zu ändern. Wenn Sie die Sicherheit für einen Ordner bearbeiten, gelten die Änderungen für den Inhalt des aktuellen Ordners und aller Unterordner.  
  
 Für den Ordner Home steht diese Schaltfläche nicht zur Verfügung.  
  
 Die folgenden Schaltflächen sind beim Bearbeiten der Elementsicherheit verfügbar.  
  
 **Delete**  
 Aktivieren Sie das Kontrollkästchen neben der Gruppe oder dem Benutzernamen, den Sie löschen möchten, und klicken Sie auf **Löschen**. Die letzte Rollenzuweisung kann nicht gelöscht werden. Dasselbe gilt für eine integrierte Rollenzuweisung (Beispiel: "VORDEFINIERT\Administratoren"), in der die Sicherheitsbasis für den Berichtsserver definiert ist. Durch das Löschen einer Rollenzuweisung werden weder Gruppen- oder Benutzerkonten noch Rollendefinitionen gelöscht.  
  
 **Neue Rollenzuweisung**  
 Klicken Sie auf diese Schaltfläche, um die Seite Neue Rollenzuweisung zu öffnen. Auf dieser Seite können Sie weitere Rollenzuweisungen für das aktuelle Element erstellen. Weitere Informationen finden Sie unter [neue Rollenzuweisung: Bearbeiten Sie die Rollenseite für die Zuweisung &#40;Berichts-Manager&#41;](../../2014/reporting-services/new-role-assignment-edit-role-assignment-page-report-manager.md).  
  
 **Zur übergeordneten Sicherheit zurückkehren**  
 Aktivieren Sie diese Option, um die Sicherheitseinstellungen des Elements auf die des übergeordneten Elements zurückzusetzen. Wenn die Vererbung in der Berichtsserver-Ordnerhierarchie nicht unterbrochen ist, werden die Sicherheitseinstellungen des Ordners Home auf der höchsten Ebene verwendet.  
  
 **Gruppen- oder Benutzernamen**  
 Führt die Gruppen und Benutzer auf, die Teil einer vorhandenen Rollenzuweisung für das aktuelle Element sind. Vorhandene Rollenzuweisungen für den aktuellen Ordner werden für Gruppen und Benutzer definiert, die in dieser Spalte angezeigt werden. Sie können auf einen Gruppen- oder Benutzernamen klicken, um Einzelheiten zu Rollenzuweisungen anzuzeigen oder zu bearbeiten.  
  
 **Roles**  
 Führt eine oder mehrere Rollendefinitionen auf, die Teil einer vorhandenen Rollenzuweisung sind. Wenn einem Gruppen- oder Benutzerkonto mehrere Rollen zugewiesen sind, kann diese Gruppe bzw. dieser Benutzer alle Aufgaben ausführen, die zu diesen Rollen gehören. Wenn Sie die mit einer Rolle verbundenen Aufgaben anzeigen möchten, verwenden Sie SQL Server Management Studio, um die mit einer Rollendefinition verbundenen Aufgaben anzuzeigen.  
  
## <a name="see-also"></a>Siehe auch  
 [Berichts-Manager-F1-Hilfe](../../2014/reporting-services/report-manager-f1-help.md)   
 [Vordefinierte Rollen](security/role-definitions-predefined-roles.md)   
 [Erteilen von Berechtigungen für einen Berichtsserver im einheitlichen Modus](security/granting-permissions-on-a-native-mode-report-server.md)   
 [Rollenzuweisungen](security/role-assignments.md)   
 [Rollendefinitionen](security/role-definitions.md)  
  
  
