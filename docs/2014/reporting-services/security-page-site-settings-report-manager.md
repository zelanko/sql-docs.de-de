---
title: Sicherheit (Seite) (Siteeinstellungen, Berichts-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: acc9a905-90f8-4544-aec6-b2ab3a1b0015
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6c0b0cc68c73c66dabb237d859aba641fb234647
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66102183"
---
# <a name="security-page-site-settings-report-manager"></a>Sicherheit (Seite) (Siteeinstellungen, Berichts-Manager)
  Auf der Seite Sicherheit können Sie die Systemrollenzuweisungen anzeigen, die den Zugriff auf die Berichtsserversite steuern. Systemrollenzuweisungen sind außerhalb des Gültigkeitsbereichs des Berichtsserver-Namespace oder der Ordnerhierarchie vorhanden. Systemrollenzuweisungen sind global und für alle Elemente gleich. Die durch Systemrollenzuweisungen unterstützten Vorgänge schließen das Erstellen und Verwenden freigegebener Zeitpläne, das Verwenden des Berichts-Managers und das Festlegen von Standardwerten für einige Serverfunktionen ein.  
  
 Bei der Installation des Berichtsservers wird eine Standard-Systemrollenzuweisung erstellt. Diese Systemrollenzuweisung erteilt lokalen Systemadministratoren Berechtigungen zum Verwalten der Berichtsserverumgebung. Ein lokaler Systemadministrator kann immer die Sicherheit für einen lokalen Berichtsserver festlegen, auch wenn Systemrollenzuweisungen gelöscht werden.  
  
 Alle anderen Benutzer, die Zugriff auf den Berichts-Generator oder freigegebene Zeitpläne benötigen, müssen einer Systemrollenzuweisung zugewiesen werden.  
  
## <a name="navigation"></a>Navigation  
 Verwenden Sie folgendes Verfahren, um zu dieser Position in der Benutzeroberfläche zu navigieren.  
  
###### <a name="to-open-the-security-page-for-site-settings"></a>So öffnen Sie die Seite 'Sicherheit' für 'Siteeinstellungen'  
  
1.  Öffnen Sie den Berichts-Manager.  
  
2.  Klicken Sie oben auf der Seite auf **Siteeinstellungen**. Dadurch wird die Seite Allgemeine Eigenschaften der Website geöffnet.  
  
3.  Wählen Sie die Registerkarte **Sicherheit** aus.  
  
## <a name="options"></a>Tastatur  
 **Löschen**  
 Klicken Sie auf diese Schaltfläche, um eine vorhandene Rollenzuweisung zu löschen. Ehe Sie auf **Löschen**klicken, aktivieren Sie das Kontrollkästchen neben dem zu entfernenden Gruppen- oder Benutzernamen. Sie können keine Rollenzuweisung löschen, wenn sie die letzte und einzige Zuweisung ist. Durch das Löschen einer Rollenzuweisung werden weder Gruppen- oder Benutzerkonten noch Rollendefinitionen gelöscht.  
  
 **Neue Rollenzuweisung**  
 Klicken Sie auf diese Schaltfläche, um die Seite Neue Systemrollenzuweisung zu öffnen. Auf dieser Seite können Sie weitere Systemrollenzuweisungen für die Berichtsserversite erstellen. Weitere Informationen finden Sie unter [neue System Rollenzuweisungen: Seite "System Rollenzuweisungen bearbeiten" &#40;Berichts-Manager&#41;](../../2014/reporting-services/new-system-role-assignments-edit-system-role-assignments-page-report-manager.md).  
  
 **Bearbeiten**  
 Klicken Sie auf diese Schaltfläche, um die Seite Systemrollenzuweisungen bearbeiten zu öffnen. Auf dieser Seite können Sie einzelne Systemrollenzuweisungen für die Berichtsserversite bearbeiten. Weitere Informationen finden Sie unter [neue System Rollenzuweisungen: Seite "System Rollenzuweisungen bearbeiten" &#40;Berichts-Manager&#41;](../../2014/reporting-services/new-system-role-assignments-edit-system-role-assignments-page-report-manager.md).  
  
 **Gruppe oder Benutzer**  
 Führt die Gruppen und Benutzer auf, die Teil einer vorhandenen Rollenzuweisung sind. Vorhandene Rollenzuweisungen für den aktuellen Ordner werden für Gruppen und Benutzer definiert, die in dieser Spalte angezeigt werden. Klicken Sie auf **Bearbeiten** neben einem Gruppen- oder Benutzernamen, um Einzelheiten zu Rollenzuweisungen anzuzeigen oder zu bearbeiten.  
  
 **Rollen**  
 Führt eine oder mehrere Rollendefinitionen auf, die Teil einer vorhandenen Rollenzuweisung sind. Falls einem Gruppen- oder Benutzerkonto mehrere Rollen zugewiesen sind, kann diese Gruppe bzw. dieser Benutzer alle in diesen Rollen enthaltenen Tasks ausführen. Verwenden [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]Sie, um den von jeder Rolle unterstützten Satz von Aufgaben anzuzeigen. Sie können im Berichts-Manager keine Rollen anzeigen, erstellen, ändern oder löschen. Anweisungen hierzu finden Sie unter [erstellen, löschen oder Ändern einer Rolle &#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Berichts-Manager F1-Hilfe](../../2014/reporting-services/report-manager-f1-help.md)   
 [Granting Permissions on a Native Mode Report Server (Erteilen von Berechtigungen für einen Berichtsserver im einheitlichen Modus)](security/granting-permissions-on-a-native-mode-report-server.md)  
  
  
