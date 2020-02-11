---
title: Gewähren von Benutzer Zugriff auf einen Berichts Server (Berichts-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- removing role assignments
- permissions [Reporting Services], granting report server access
- roles [Reporting Services], assignments
- modifying role assignments
- deleting role assignments
ms.assetid: 2144c020-3253-4b47-8cda-e14c928bb471
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 31c5fa6b3ca1f42ea87fc1514f55ce325f8a021a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66101989"
---
# <a name="grant-user-access-to-a-report-server-report-manager"></a>Gewähren von Benutzerzugriff auf einen Berichtsserver (Berichts-Manager)
  
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] verwendet rollenbasierte Sicherheit, um Benutzerzugriff auf einen Berichtsserver zu gewähren. Bei der Installation eines neuen Berichtsservers haben nur Benutzer, die Mitglieder der lokalen Administratorengruppe sind, Zugriff auf Berichtsserverinhalte und -vorgänge. Damit der Berichtsserver auch von anderen Benutzern verwendet werden kann, müssen Sie Rollenzuweisungen erstellen, mit denen Benutzer- oder Gruppenkonten einer vordefinierten Rolle zugeordnet werden, die eine Auflistung von Tasks festlegt.  
  
 **Berichts Server im SharePoint-Modus:** Für einen Berichts Server, der für den integrierten SharePoint-Modus konfiguriert ist, konfigurieren Sie den Zugriff von einer SharePoint-Website mithilfe von SharePoint-Berechtigungen. Die Berechtigungsebenen der SharePoint-Website legen den Zugriff auf Berichtsserverinhalt und -vorgänge fest. Sie müssen Websiteadministrator sein, um Berechtigungen auf einer SharePoint-Website gewähren zu können. Weitere Informationen finden Sie unter [Erteilen von Berechtigungen für Berichtsserverelemente auf einer SharePoint-Website](granting-permissions-on-report-server-items-on-a-sharepoint-site.md).  
  
 **Berichts Server im einheitlichen Modus:** Dieses Thema konzentriert sich auf einen Berichts Server, der für den einheitlichen Modus konfiguriert ist, und die Verwendung von Berichts-Manager zum Zuweisen von Benutzern zu einer Rolle. Die folgenden beiden Rollen stehen zur Verfügung:  
  
-   Rollen auf Elementebene werden verwendet, um Berichtsserverinhalte, Abonnements, Berichtsverarbeitung und Berichtsverlauf anzuzeigen, hinzuzufügen und zu verwalten. Rollenzuweisungen auf Elementebene werden im Stammknoten (dem Stammordner) oder in bestimmten Ordnern oder Elementen weiter unten in der Hierarchie definiert.  
  
-   Rollen auf Systemebene gewähren Zugriff auf siteweite Vorgänge, die an kein bestimmtes Element gebunden sind. Beispiele sind die Verwendung des Berichts-Generators und die Verwendung von freigegebenen Zeitplänen.  
  
     Diese beiden Rollentypen ergänzen sich gegenseitig und sollten zusammen verwendet werden. Das Hinzufügen eines Benutzers zu einem Berichtsserver ist daher ein Vorgang mit zwei Teilvorgängen. Wenn Sie einen Benutzer einer Rolle auf Elementebene zuweisen, sollten Sie ihn ebenfalls einer Rolle auf Systemebene zuweisen. Beim Zuweisen eines Benutzers zu einer Rolle müssen Sie eine bereits definierte Rolle wählen. Verwenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]Sie, um Rollen zu erstellen, zu ändern oder zu löschen. Weitere Informationen finden Sie unter [Erstellen, Löschen oder Ändern einer Rolle &#40;Management Studio&#41;](role-definitions-create-delete-or-modify.md).  
  
## <a name="before-you-start"></a>Vorbereitung  
 Überprüfen Sie die folgende Liste vor dem Hinzufügen von Benutzern zu einem Berichtsserver im einheitlichen Modus.  
  
-   Sie müssen ein Mitglied der lokalen Administratorengruppe auf dem Berichtsservercomputer sein. Wenn Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] auf [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)] oder Windows Server 2008 bereitstellen, sind zusätzliche Konfigurationsschritte erforderlich, bevor Sie einen Berichtsserver lokal verwalten können. Weitere Informationen finden Sie unter [Konfigurieren eines Berichtsservers im einheitlichen Modus für die lokale Verwaltung &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
-   Um diese Aufgabe an andere Benutzer zu delegieren, erstellen Sie Rollenzuweisungen, die Benutzerkonten den Rollen Inhalts-Manager und Systemadministrator zuordnen. Benutzer, die über Inhalts-Manager- und Systemadministrator-Berechtigungen verfügen, können einem Berichtsserver Benutzer hinzufügen.  
  
-   Zeigen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]Sie in die vordefinierten Rollen für System Rollen und Benutzer Rollen an, damit Sie mit den Arten von Aufgaben in den einzelnen Rollen vertraut sind. Im Berichts-Manager stehen keine Taskbeschreibungen zur Verfügung, sodass Sie die Rollen kennen sollten, bevor Sie Benutzer hinzufügen.  
  
-   Passen Sie die Rollen optional an, oder definieren Sie zusätzliche Rollen, um die Auflistung von benötigten Tasks einzuschließen. Wenn Sie zum Beispiel benutzerdefinierte Sicherheitseinstellungen für einzelne Elemente verwenden möchten, können Sie eine neue Rollendefinition erstellen, die Lesezugriff für Ordner gewährt.  
  
### <a name="to-add-a-user-or-group-to-a-system-role"></a>So fügen Sie einer Systemrolle einen Benutzer oder eine Gruppe hinzu  
  
1.  Starten Sie den [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../report-manager-ssrs-native-mode.md).  
  
2.  Klicken Sie auf **Siteeinstellungen**.  
  
3.  Klicken Sie auf **Sicherheit**.  
  
4.  Klicken Sie auf **Neue Rollenzuweisung**.  
  
5.  Geben Sie unter **Gruppen-oder Benutzername**ein Windows-Domänen Benutzer-oder-Gruppen \<Konto im \\ folgenden Format\>ein: Domäne><Konto. Wenn Sie die Formularauthentifizierung oder die benutzerdefinierte Sicherheit verwenden, geben Sie das Benutzer- oder Gruppenkonto in dem für Ihre Bereitstellung richtigen Format an.  
  
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
  
5.  Geben Sie unter **Gruppen-oder Benutzername**ein Windows-Domänen Benutzer-oder-Gruppen \<Konto im \\ folgenden Format\>ein: Domäne><Konto. Wenn Sie die Formularauthentifizierung oder die benutzerdefinierte Sicherheit verwenden, geben Sie das Benutzer- oder Gruppenkonto in dem für Ihre Bereitstellung richtigen Format an.  
  
6.  Wählen Sie mindestens eine Rollendefinition aus, die beschreibt, wie der Benutzer oder die Gruppe auf das Element zugreifen soll, und klicken Sie dann auf **OK**.  
  
7.  Wiederholen Sie den Vorgang, um weiteren Benutzern oder Gruppen Rollen zuzuweisen.  
  
## <a name="see-also"></a>Weitere Informationen  
 (Create-and-manage-role-assignments.MD)   
 [Neue Rollenzuweisung: Seite "Rollenzuweisung bearbeiten" &#40;Berichts-Manager&#41;](../new-role-assignment-edit-role-assignment-page-report-manager.md)   
 [Sicherheit (Eigenschaften Seite), Elemente &#40;Berichts-Manager&#41;](../security-properties-page-items-report-manager.md)   
 [Rollenzuweisungen](role-assignments.md)   
 [Rollendefinitionen](role-definitions.md)  
  
  
