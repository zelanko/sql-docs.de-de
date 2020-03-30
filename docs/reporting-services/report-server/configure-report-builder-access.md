---
title: Konfigurieren des Berichts-Generatorzugriffs | Microsoft-Dokumentation
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.date: 06/06/2019
ms.openlocfilehash: 724fac17abf7f5da45101a6ff22d3185a7ade93b
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "68255171"
---
# <a name="configure-report-builder-access"></a>Konfigurieren des Berichts-Generator-Zugriffs
Der Berichts-Generator ist ein Tool für die Ad-hoc-Berichterstellung, das mit einem für den einheitlichen oder den integrierten SharePoint-Modus konfigurierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Berichtsserver zusammen installiert wird.  

Der Zugriff auf den Berichts-Generator ist von den folgenden Faktoren abhängig:  

- Servereigenschaften, mit denen bestimmt wird, ob der Berichts-Generator auf dem Berichtsserver verfügbar ist.  

- Rollenzuweisungen oder Berechtigungen, mit denen der Berichts-Generator einzelnen Benutzern oder Gruppen zur Verfügung gestellt wird.  

- Authentifizierungseinstellungen, die bestimmten, ob Benutzeranmeldeinformationen an den Berichtsserver weitergegeben werden können oder anonymer Zugriff für die Anwendungsdateien konfiguriert wird.

## <a name="prerequisites"></a>Voraussetzungen

Der Berichts-Generator ist nicht in jeder Edition von [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Eine Liste der Funktionen, die von den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Editionen unterstützt werden, finden Sie unter [Unterstützte Funktionen von SQL Server 2017](../../sql-server/editions-and-components-of-sql-server-2017.md).  

Auf dem Clientcomputer muss [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4.6 oder 4.6.1 für SSRS 2016 bzw. 2017 installiert sein. [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] stellt die Infrastruktur zum Ausführen von [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] -Anwendungen bereit.  

Sie müssen [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer 11 oder höher oder einen anderen modernen Browser verwenden.  

Der Berichts-Generator wird immer im Modus für volle Vertrauenswürdigkeit ausgeführt; Sie können ihn nicht so konfigurieren, dass er im Modus für teilweise Vertrauenswürdigkeit ausgeführt wird. In früheren Versionen war es möglich, den Berichts-Generator im Modus für partielle Vertrauenswürdigkeit auszuführen, aber diese Option wird in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höheren Versionen nicht unterstützt.  

## <a name="enabling-and-disabling-report-builder"></a>Aktivieren und Deaktivieren des Berichts-Generators  

Der Berichts-Generator ist in der Standardeinstellung aktiviert. Berichtsserveradministratoren können den Berichts-Generator deaktivieren, indem sie die Berichtsserver-Systemeigenschaft **ShowDownloadMenu** auf **FALSE** festlegen. Wenn Sie diese Eigenschaft festlegen, werden die Downloads für den Berichts-Generator, den Publisher für mobile Berichte und Power BI Mobile für diesen Berichtsserver deaktiviert.  

 Zum Festlegen der Berichtsserver-Systemeigenschaften können Sie Management Studio oder ein Skript verwenden:   

 - Wenn Sie Management Studio verwenden möchten, stellen Sie eine Verbindung mit dem Berichtsserver her und legen auf der Seite mit den erweiterten Servereigenschaften **ShowDownloadMenu** auf **FALSE** fest. Weitere Informationen zum Öffnen dieser Seite finden Sie unter [Festlegen von Berichtsservereigenschaften (Management Studio)](../../reporting-services/tools/set-report-server-properties-management-studio.md).      

 - Ein Beispielskript, das eine Berichtsservereigenschaft festlegt, finden Sie unter [Skripts für Bereitstellungs- und Verwaltungsaufgaben](../../reporting-services/tools/script-deployment-and-administrative-tasks.md).  

## <a name="role-assignments-granting-report-builder-access-on-a-native-mode-report-server"></a>Rollenzuweisungen, die auf einem Berichtsserver im einheitlichen Modus Zugriff auf den Berichts-Generator gewähren  

Erstellen Sie auf einem Berichtsserver im einheitlichen Modus Benutzerrollenzuweisungen, die Tasks zum Verwenden des Berichts-Generators einschließen. Sie müssen Inhalts-Manager und Systemadministrator sein, um Rollendefinitionen und Rollenzuweisungen auf der Element- und Websiteebene erstellen oder ändern zu können.  

Die folgenden Anweisungen gehen davon aus, dass Sie vordefinierte Rollen verwenden. Wenn Sie die Rollendefinitionen abgeändert oder von SQL Server 2000 aktualisiert haben, überprüfen Sie die Rollen, um sicherzustellen, dass sie die erforderlichen Tasks enthalten. Weitere Informationen zum Erstellen von Rollenzuweisungen finden Sie unter [Gewähren von Benutzerzugriff auf einen Berichtsserver](../../reporting-services/security/grant-user-access-to-a-report-server.md).

Nachdem Sie die Rollenzuweisungen erstellt haben, sind die Benutzer zu Folgendem berechtigt:  

- Benutzer, denen die Rollen Systembenutzer und Browser zugewiesen wurden, können veröffentlichte Berichts-Generator-Berichte auf einem Berichtsserver anzeigen, ohne den Berichts-Generator starten zu müssen.  

- Benutzer, denen die Rollen Systembenutzer und Berichts-Generator zugewiesen wurden, können Modelle erzeugen, den Berichts-Generator starten und Berichte erstellen sowie Berichte auf dem Berichtsserver speichern.  

- Benutzer, denen die Rollen Systembenutzer und Verleger zugewiesen wurden, können Modelle aus dem Modell-Designer auf dem Berichtsserver veröffentlichen. Modelle werden im Berichts-Generator als Datenquellen verwendet.  

- Benutzer, denen die Rollen Systemadministrator und Inhalts-Manager zugewiesen wurden, verfügen über sämtliche Berechtigungen zum Erstellen, Anzeigen und Verwalten von Berichts-Generator-Berichten.  

### <a name="to-verify-required-tasks-are-in-the-role-definitions"></a>So überprüfen Sie, ob die Rollendefinitionen die erforderlichen Tasks enthalten  

1. Starten Sie Management Studio, und stellen Sie eine Verbindung mit dem Berichtsserver her.  

2. Öffnen Sie den Ordner **Sicherheit** .  

3. Öffnen Sie den Ordner **Systemrollen** .  

4. Klicken Sie mit der rechten Maustaste auf **Systemadministrator**, und wählen Sie **Eigenschaften**aus.  

5. Wählen Sie **Berichtsdefinitionen ausführen** aus, und klicken Sie auf **OK**.  

6. Klicken Sie mit der rechten Maustaste auf **Systembenutzer**, und wählen Sie **Eigenschaften**aus.  

7. Wählen Sie **Berichtsdefinitionen ausführen** aus, und klicken Sie auf **OK**.  

8. Öffnen Sie den Ordner **Rollen** .  

9. Klicken Sie mit der rechten Maustaste auf **Browser**, und wählen Sie **Eigenschaften**aus.  

10. Wählen Sie **Modelle anzeigen** aus, und klicken Sie auf **OK**.  

11. Klicken Sie mit der rechten Maustaste auf **Inhalts-Manager**, und wählen Sie **Eigenschaften**aus.  

12. Wählen Sie **Modelle anzeigen**, **Modelle verwalten**und **Berichte lesen**aus, und klicken Sie auf **OK**.  

13. Klicken Sie mit der rechten Maustaste auf **Verleger**, und wählen Sie **Eigenschaften**aus.  

14. Wählen Sie **Modelle verwalten** aus, und klicken Sie auf **OK**.  

15. Erstellen Sie die Berichts-Generator-Rolle, wenn sie nicht vorhanden ist:  

    1. Öffnen Sie den Ordner **Sicherheit** .  

    2. Klicken Sie mit der rechten Maustaste auf **Rollen**, und wählen Sie **Neue Rolle**aus.  

    3. Geben Sie im Feld Name den Namen **Berichts-Generator**ein.  

    4. Geben Sie im Feld Beschreibung eine Rollenbeschreibung ein, damit die Benutzer im Webportal wissen, wozu ihre Rolle dient.  

    5. Fügen Sie die folgenden Aufgaben hinzu: **Berichte lesen**, **Berichte anzeigen**, **Modelle anzeigen**, **Ressourcen anzeigen**, **Ordner anzeigen**und **Einzelne Abonnements verwalten**.  

    6. Klicken Sie auf **OK** , um die Rolle zu speichern.  

#### <a name="to-create-role-assignments-that-grant-access-to-report-builder"></a>So erstellen Sie Rollenzuweisungen, die Zugriff auf den Berichts-Generator gewähren  

1. Starten Sie das Webportal.  

2. Klicken Sie oben rechts auf der Startseite des Webportals auf das Zahnradsymbol, und wählen Sie im Dropdownmenü **Siteeinstellungen** aus.  
![das Zahnradsymbol und Menü des Webportals](../../reporting-services/report-builder/media/configure-report-builder-access/ssrswebportal-site-settings-gear-icon-and-menu.png)

3. Klicken Sie auf **Sicherheit**.  

4. Wenn für den Benutzer oder die Gruppe, für den bzw. die Sie den Zugriff auf den Berichts-Generator konfigurieren möchten, klicken Sie auf **Bearbeiten**.  
Andernfalls klicken Sie auf **Neue Rollenzuweisung**. Geben Sie unter Gruppe oder Benutzer ein Windows-Domänenbenutzer- oder -Gruppenkonto im folgenden Format ein: \<Domäne>\\<Konto\>. Wenn Sie die Formularauthentifizierung oder die benutzerdefinierte Sicherheit verwenden, geben Sie das Benutzer- oder Gruppenkonto in dem für Ihre Bereitstellung richtigen Format an.  

5. Wählen Sie **Systembenutzer**aus, und klicken Sie dann auf **OK**.  

6. Klicken Sie auf **Startseite**.  

7. Klicken Sie auf die Registerkarte **Ordnereinstellungen** .  

8. Klicken Sie auf die Registerkarte **Sicherheit** .  

9. Wenn für den Benutzer oder die Gruppe, für den bzw. die Sie den Zugriff auf den Berichts-Generator konfigurieren möchten, klicken Sie auf **Bearbeiten**.  

    Andernfalls klicken Sie auf **Neue Rollenzuweisung**. Geben Sie unter Gruppe oder Benutzer ein Windows-Domänenbenutzer- oder -Gruppenkonto im folgenden Format ein: \<Domäne>\\<Konto\>. Wenn Sie die Formularauthentifizierung oder die benutzerdefinierte Sicherheit verwenden, geben Sie das Benutzer- oder Gruppenkonto in dem für Ihre Bereitstellung richtigen Format an.  

10. Wählen Sie **Berichts-Generator**aus, und klicken Sie dann auf **Anwenden**.  

11. Wiederholen Sie den Vorgang, um Rollenzuweisungen für weitere Benutzer oder Gruppen zu erstellen oder ändern.  

## <a name="permissions-granting-report-builder-access-on-a-sharepoint-integrated-mode-report-server"></a>Berechtigungen, die auf einem Berichtsserver im integrierten SharePoint-Modus Zugriff auf den Berichts-Generator gewähren  

Auf einem Berichtsserver im integrierten SharePoint-Modus wird SharePoint-Benutzern, die über die Berechtigungsstufen Teilnehmen oder Vollzugriff verfügen, Zugriff auf den Berichts-Generator gewährt.  

Wenn Sie benutzerdefinierte Berechtigungsstufen verwenden, müssen Sie Elemente hinzufügen und Elemente bearbeiten in die Berechtigungsstufe aufnehmen. Weitere Informationen zum Zugriff auf den Berichts-Generator über integrierte Berechtigungsstufen finden Sie unter [Verwenden der integrierten Sicherheit in Windows SharePoint Services für Berichtsserverelemente](../../reporting-services/security/use-built-in-security-in-windows-sharepoint-services-for-report-server-items.md). Weitere Informationen zu Berechtigungsanforderungen für benutzerdefinierte Berechtigungsstufen finden Sie unter [Festlegen von Berechtigungen für Berichtsservervorgänge in einer SharePoint-Webanwendung](../../reporting-services/security/set-permissions-for-report-server-operations-in-a-sharepoint-web-application.md).  

## <a name="authentication-considerations-and-credential-reuse"></a>Authentifizierungsüberlegungen und Wiederverwendung von Anmeldeinformationen  

- Der Berichts-Generator stellt eine eigene Verbindung mit einem Berichtsserver her. Wenn Sie nicht die integrierte Sicherheit von Windows mit einmaliger Anmeldung verwenden, müssen die Benutzer die Anmeldeinformationen für die Verbindung zwischen Berichts-Generator und Berichtsserver erneut eingeben.  

In der folgenden Tabelle werden die vom Berichtsserver unterstützten Authentifizierungstypen beschrieben, und es wird angegeben, ob zusätzliche Konfigurationsschritte für den Zugriff auf den Berichts-Generator erforderlich sind.  

## <a name="see-also"></a>Weitere Informationen  

- [Authentication with the Report Server (Authentifizierung mit dem Berichtsserver)](../../reporting-services/security/authentication-with-the-report-server.md)
- [Browser Support for Reporting Services and Power View (Browserunterstützung für Reporting Services und Power View)](../../reporting-services/browser-support-for-reporting-services-and-power-view.md)
- [Start Report Builder (Starten des Berichts-Generators.)](../../reporting-services/report-builder/start-report-builder.md)
- [Das Webportal eines Berichtsservers (einheitlicher SSRS-Modus)](../web-portal-ssrs-native-mode.md)
- [Connect to a Report Server in Management Studio (Vorgehensweise: Herstellen einer Verbindung mit einem Berichtsserver in Management Studio)](../../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)
- [Berichtsserver-Systemeigenschaften](../../reporting-services/report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md)
