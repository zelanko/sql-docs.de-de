---
title: Gewähren von Benutzerzugriff auf einen Berichtsserver (Berichts-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- removing role assignments
- permissions [Reporting Services], granting report server access
- roles [Reporting Services], assignments
- modifying role assignments
- deleting role assignments
ms.assetid: 2144c020-3253-4b47-8cda-e14c928bb471
caps.latest.revision: 52
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: b705997e16e2f41fb92ed7a5385a0907db09d99e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37256142"
---
# <a name="grant-user-access-to-a-report-server-report-manager"></a>Gewähren von Benutzerzugriff auf einen Berichtsserver (Berichts-Manager)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] verwendet rollenbasierte Sicherheit, um Benutzerzugriff auf einen Berichtsserver zu gewähren. Bei der Installation eines neuen Berichtsservers haben nur Benutzer, die Mitglieder der lokalen Administratorengruppe sind, Zugriff auf Berichtsserverinhalte und -vorgänge. Damit der Berichtsserver auch von anderen Benutzern verwendet werden kann, müssen Sie Rollenzuweisungen erstellen, mit denen Benutzer- oder Gruppenkonten einer vordefinierten Rolle zugeordnet werden, die eine Auflistung von Tasks festlegt.  
  
 **Berichtsserver im SharePoint-Modus:** Für Berichtsserver, die für den integrierten SharePoint-Modus konfiguriert sind, muss der Zugriff von einer SharePoint-Website mit SharePoint-Berechtigungen konfiguriert werden. Die Berechtigungsebenen der SharePoint-Website legen den Zugriff auf Berichtsserverinhalt und -vorgänge fest. Sie müssen Websiteadministrator sein, um Berechtigungen auf einer SharePoint-Website gewähren zu können. Weitere Informationen finden Sie unter [Erteilen von Berechtigungen für Berichtsserverelemente auf einer SharePoint-Website](granting-permissions-on-report-server-items-on-a-sharepoint-site.md).  
  
 **Berichtsserver im einheitlichen Modus:** In diesem Thema liegt der Schwerpunkt auf einem für den einheitlichen Modus konfigurierten Berichtsserver und der Verwendung des Berichts-Managers zum Zuweisen von Benutzern zu Rollen. Die folgenden beiden Rollen stehen zur Verfügung:  
  
-   Rollen auf Elementebene werden verwendet, um Berichtsserverinhalte, Abonnements, Berichtsverarbeitung und Berichtsverlauf anzuzeigen, hinzuzufügen und zu verwalten. Rollenzuweisungen auf Elementebene werden im Stammknoten (dem Stammordner) oder in bestimmten Ordnern oder Elementen weiter unten in der Hierarchie definiert.  
  
-   Rollen auf Systemebene gewähren Zugriff auf siteweite Vorgänge, die an kein bestimmtes Element gebunden sind. Beispiele sind die Verwendung des Berichts-Generators und die Verwendung von freigegebenen Zeitplänen.  
  
     Diese beiden Rollentypen ergänzen sich gegenseitig und sollten zusammen verwendet werden. Das Hinzufügen eines Benutzers zu einem Berichtsserver ist daher ein Vorgang mit zwei Teilvorgängen. Wenn Sie einen Benutzer einer Rolle auf Elementebene zuweisen, sollten Sie ihn ebenfalls einer Rolle auf Systemebene zuweisen. Beim Zuweisen eines Benutzers zu einer Rolle müssen Sie eine bereits definierte Rolle wählen. Verwenden Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], um Rollen zu erstellen, zu ändern oder zu löschen. Weitere Informationen finden Sie unter [erstellen, löschen oder Ändern einer Rolle &#40;Management Studio&#41;](role-definitions-create-delete-or-modify.md).  
  
## <a name="before-you-start"></a>Vorbereitungen  
 Überprüfen Sie die folgende Liste vor dem Hinzufügen von Benutzern zu einem Berichtsserver im einheitlichen Modus.  
  
-   Sie müssen ein Mitglied der lokalen Administratorengruppe auf dem Berichtsservercomputer sein. Wenn Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] auf [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)] oder Windows Server 2008 bereitstellen, sind zusätzliche Konfigurationsschritte erforderlich, bevor Sie einen Berichtsserver lokal verwalten können. Anweisungen finden Sie unter [Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
-   Um diese Aufgabe an andere Benutzer zu delegieren, erstellen Sie Rollenzuweisungen, die Benutzerkonten den Rollen Inhalts-Manager und Systemadministrator zuordnen. Benutzer, die über Inhalts-Manager- und Systemadministrator-Berechtigungen verfügen, können einem Berichtsserver Benutzer hinzufügen.  
  
-   Sehen Sie sich in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]die vordefinierten Systemrollen und Benutzerrollen an, damit Ihnen die mit den einzelnen Rollen verbundenen Tasks vertraut sind. Im Berichts-Manager stehen keine Taskbeschreibungen zur Verfügung, sodass Sie die Rollen kennen sollten, bevor Sie Benutzer hinzufügen.  
  
-   Passen Sie die Rollen optional an, oder definieren Sie zusätzliche Rollen, um die Auflistung von benötigten Tasks einzuschließen. Wenn Sie zum Beispiel benutzerdefinierte Sicherheitseinstellungen für einzelne Elemente verwenden möchten, können Sie eine neue Rollendefinition erstellen, die Lesezugriff für Ordner gewährt.  
  
### <a name="to-add-a-user-or-group-to-a-system-role"></a>So fügen Sie einer Systemrolle einen Benutzer oder eine Gruppe hinzu  
  
1.  Starten Sie den [Berichts-Manager im einheitlichen SSRS-Modus](../report-manager-ssrs-native-mode.md).  
  
2.  Klicken Sie auf **Siteeinstellungen**.  
  
3.  Klicken Sie auf **Sicherheit**.  
  
4.  Klicken Sie auf **Neue Rollenzuweisung**.  
  
5.  In **Gruppen-oder Benutzername**, geben Sie einen Windows-Domänenbenutzer oder ein-Gruppenkonto im folgenden Format: \<Domäne >\\< Konto\>. Wenn Sie die Formularauthentifizierung oder die benutzerdefinierte Sicherheit verwenden, geben Sie das Benutzer- oder Gruppenkonto in dem für Ihre Bereitstellung richtigen Format an.  
  
6.  Wählen Sie eine Systemrolle aus, und klicken Sie anschließend auf **OK**.  
  
     Rollen sind kumulativ, das heißt, wenn Sie sowohl die Systemadministrator- als auch die Systembenutzerrolle wählen, kann ein Benutzer oder eine Gruppe die Tasks beider Rollen ausführen.  
  
7.  Wiederholen Sie den Vorgang, um weiteren Benutzern oder Gruppen Rollen zuzuweisen.  
  
### <a name="to-add-a-user-or-group-to-an-item-role"></a>So fügen Sie einem Benutzer oder einer Gruppe eine Elementrolle hinzu  
  
1.  Starten Sie den **Berichts-Manager** , und suchen Sie das Berichtselement, für das Sie einen Benutzer oder eine Gruppe hinzufügen möchten.  
  
2.  Zeigen Sie auf das Element, und klicken Sie auf den Dropdownpfeil.  
  
3.  Klicken Sie im Dropdownmenü auf **Sicherheit**.  
  
4.  Klicken Sie auf **Neue Rollenzuweisung**.  
  
    > [!NOTE]  
    >  Falls ein Element aktuell die Sicherheitseinstellungen eines übergeordneten Elements erbt, klicken Sie auf der Symbolleiste auf **Elementsicherheit bearbeiten** , um die Sicherheitseinstellungen zu ändern. Klicken Sie dann auf **Neue Rollenzuweisung**.  
  
5.  In **Gruppen-oder Benutzername**, geben Sie einen Windows-Domänenbenutzer oder ein-Gruppenkonto im folgenden Format: \<Domäne >\\< Konto\>. Wenn Sie die Formularauthentifizierung oder die benutzerdefinierte Sicherheit verwenden, geben Sie das Benutzer- oder Gruppenkonto in dem für Ihre Bereitstellung richtigen Format an.  
  
6.  Wählen Sie mindestens eine Rollendefinition aus, die beschreibt, wie der Benutzer oder die Gruppe auf das Element zugreifen soll, und klicken Sie dann auf **OK**.  
  
7.  Wiederholen Sie den Vorgang, um weiteren Benutzern oder Gruppen Rollen zuzuweisen.  
  
## <a name="see-also"></a>Siehe auch  
 (erstellen-und-Verwaltung-Rolle-assignments.md)   
 [Neue Rollenzuweisung: Bearbeiten der Zuweisung Rollenseite &#40;Berichts-Manager&#41;](../new-role-assignment-edit-role-assignment-page-report-manager.md)   
 [Sicherheit (Eigenschaftenseite) Elemente &#40;Berichts-Manager&#41;](../security-properties-page-items-report-manager.md)   
 [Rollenzuweisungen](role-assignments.md)   
 [Rollendefinitionen](role-definitions.md)  
  
  
