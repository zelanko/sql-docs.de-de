---
title: 'Neue System Rollenzuweisungen: Seite "System Rollenzuweisungen bearbeiten" (Berichts-Manager) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 62a22ab9-1eb4-4ce5-8dd7-06b5ed2d9a2a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 661ae0cafe5b484839bbee2531f82f3b62f72c75
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66108131"
---
# <a name="new-system-role-assignments-edit-system-role-assignments-page-report-manager"></a>Neue Systemrollenzuweisung: Systemrollenzuweisung bearbeiten (Seite, Berichts-Manager)
  Verwenden Sie zum Definieren der Sicherheit für den Berichtsserver die Seite Neue Systemrollenzuweisung oder Systemrollenzuweisung bearbeiten. Die gesamte Sicherheit wird durch Rollenzuweisungen definiert, in denen spezifische Benutzer oder Gruppen zu Aufgaben zugeordnet werden, die diese ausführen können. Die Aufgabenliste stellt eine Rollendefinition dar, die Sie beim Erstellen einer Rollenzuweisung auswählen.  
  
 Auf der Systemebene gelten die von Ihnen erstellten oder geänderten Rollenzuweisungen für den gesamten Berichtsserver. Die Berechtigung zum Erstellen freigegebener Zeitpläne wird z. B. auf der Systemebene angegeben, da freigegebene Zeitpläne im gesamten System verwendet werden.  
  
 Standardmäßig stellt Reporting Services zwei vordefinierte Systemebenenrollen bereit:  
  
-   Die Systembenutzerrolle umfasst Aufgaben, die es Benutzern ermöglichen, Berichtsservereigenschaften und freigegebene Zeitpläne anzuzeigen. Außerdem können Benutzer Berichtsdefinitionen ausführen, wodurch sie Berichte mit Durchklicken, die auf dem Berichtsserver veröffentlicht wurden, anzeigen können. Die meisten Benutzer sollten dieser Rolle zugewiesen werden.  
  
-   Systemadministrator schließt Aufgaben für das Erstellen und Verwalten freigegebener Zeitpläne, das Festlegen von Servereigenschaften und das Erstellen von Rollenzuweisungen auf Systemebene für andere Benutzer ein. Nur wenige Benutzer benötigen Berechtigungen dieser Ebene.  
  
## <a name="navigation"></a>Navigation  
 Verwenden Sie folgendes Verfahren, um zu dieser Position in der Benutzeroberfläche zu navigieren.  
  
###### <a name="to-open-the-new-system-role-assignments-or-edit-system-role-assignments-page"></a>So öffnen Sie die Seite 'Neue Systemrollenzuweisung' oder 'Systemrollenzuweisungen bearbeiten'  
  
1.  Öffnen Sie den Berichts-Manager.  
  
2.  Klicken Sie in der oberen rechten Ecke der Seite auf **Siteeinstellungen**. Dadurch wird die Seite Allgemeine Eigenschaften der Website geöffnet.  
  
3.  Wählen Sie die Registerkarte **Sicherheit** aus. Sie müssen über Inhalts-Manager-und System Administrator Berechtigungen verfügen, um auf diese Seite zuzugreifen.  
  
4.  Um eine neue Rollenzuweisung zu erstellen, klicken Sie auf der Symbolleiste auf **Neue Rollenzuweisung** . Um eine vorhandene Rollenzuweisung zu bearbeiten, klicken Sie neben einer Gruppe oder einem Benutzer auf der Eigenschaftenseite Sicherheit auf **Bearbeiten** .  
  
## <a name="options"></a>Optionen  
 **Gruppe oder Benutzer**  
 Geben Sie den Namen eines Gruppen- oder Benutzerkontos in der Domäne ein. Wenn der Berichtsserver unter einem lokalen Konto ausgeführt wird, müssen Sie lokale Gruppen oder Benutzer angeben. Wenn der Berichtsserver unter einem Domänenkonto ausgeführt wird, müssen Sie Domänengruppen oder -benutzer angeben. Geben Sie das Konto im folgenden Format \<ein: \\ Domäne>\><Konto.  
  
> [!NOTE]  
>  Dieses Feld ist nur auf der Seite Neue Rollenzuweisung verfügbar.  
  
 **Rollen**  
 Stellt eine Liste von Rollen auf Systemebene bereit, die Sie anderen Benutzern zuweisen können. Sie können mehrere Rollen für eine einzelne Rollenzuweisung angeben.  
  
 Der Berichts-Manager zeigt die Aufgaben in jeder Rolle nicht an und bietet auch keine Möglichkeit, Aufgaben hinzuzufügen oder sie zu ändern. Sie müssen die Rollen so verwenden, wie sie definiert sind. Verwenden [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]Sie, um Rollen zu erstellen, zu ändern oder zu löschen. Weitere Informationen finden Sie unter [Erstellen, Löschen oder Ändern einer Rolle &#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md).  
  
 Beachten Sie, dass Sie bei Verwendung von [!INCLUDE[ssExpressEd2005](../includes/ssexpressed2005-md.md)] with Advanced Services die vorhandenen Rollen verwenden müssen.  
  
 **Beschreibungen**  
 Zeigt zusätzliche Informationen zur Rolle an. Bei vordefinierten Rollen wie z. B. Systembenutzer oder Systemadministrator werden in der Beschreibung die Aufgaben zusammengefasst, die von einer Rolle unterstützt werden.  
  
 **Rollenzuweisung löschen**  
 Klicken Sie auf diese Schaltfläche, um eine vorhandene Rollenzuweisung für einen Benutzer oder eine Gruppe zu löschen. Die letzte Rollenzuweisung kann nicht gelöscht werden, da jedes Element über mindestens eine Rollenzuweisung verfügen muss.  
  
> [!NOTE]  
>  Diese Schaltfläche ist nur auf der Seite Rollenzuweisung bearbeiten verfügbar.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Berichts-Manager F1-Hilfe](../../2014/reporting-services/report-manager-f1-help.md)   
 [Rollenzuweisungen](security/role-assignments.md)   
 [Rollendefinitionen](security/role-definitions.md)  
  
  
