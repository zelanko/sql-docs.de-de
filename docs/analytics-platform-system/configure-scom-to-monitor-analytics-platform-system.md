---
title: Konfigurieren von System Center Operations Manager zum Überwachen von APS
description: Führen Sie die folgenden Schritte aus, um die System Center Operations Manager Management Packs (SCOM) für Analytics Platform System zu konfigurieren. Die Management Packs sind erforderlich, um das Analytics-Platt Form System von SCOM zu überwachen.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 2840ba401c0b7f3df5b0b27726cbdaa05390f952
ms.sourcegitcommit: 442fbe1655d629ecef273b02fae1beb2455a762e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2020
ms.locfileid: "93235267"
---
# <a name="configure-system-center-operations-manager-scom-to-monitor-analytics-platform-system"></a>Konfigurieren von System Center Operations Manager (SCOM) zum Überwachen des Analytics-plattformsystems
Führen Sie die folgenden Schritte aus, um die System Center Operations Manager Management Packs (SCOM) für Analytics Platform System zu konfigurieren. Die Management Packs sind erforderlich, um das Analytics-Platt Form System von SCOM zu überwachen.  
  
## <a name="before-you-begin"></a><a name="BeforeBegin"></a>Vorbereitungen  
**Voraussetzungen**  
  
System Center Operations Manager 2007 R2 muss installiert sein und ausgeführt werden.  
  
Die Management Packs müssen installiert und konfiguriert sein. Weitere Informationen finden Sie unter [Installieren der SCOM-Management Packs &#40;Analytics Platform System&#41;](install-the-scom-management-packs.md) und [Importieren des SCOM-Management Packs für PDW &#40;Analytics Platform System&#41;](import-the-scom-management-pack-for-pdw.md).  
  
## <a name="configure-run-as-profile-in-system-center"></a><a name="ConfigureRunAsProfile"></a>Konfigurieren von Run-As Profil in System Center  
Zum Konfigurieren von System Center müssen Sie die folgenden Schritte ausführen:  
  
-   Erstellen Sie das Konto "Ausführen als" für den Benutzer " **APS Watcher** ", und ordnen Sie es dem **Microsoft APS Watcher-Konto zu.**  
  
-   Erstellen Sie das runas-Konto für den **monitoring_user** APS-Benutzer, und ordnen Sie es dem **Microsoft APS-Aktions Konto** zu.  
  
Im folgenden finden Sie ausführliche Anweisungen zum Ausführen der Aufgaben:  
  
1.  Erstellen Sie das runas-Konto " **APS Watcher** " mit dem **Windows** -Kontotyp für den Benutzer " **APS Watcher** ".  
  
    1.  Navigieren Sie zum Bereich **Verwaltung** , klicken Sie mit der rechten Maustaste auf **als Konfigurations**  ->  **Konten** ausführen, und wählen Sie dann **Ausführen als Konto erstellen aus.**  
  
        ![Ein Screenshot, der die Option "Ausführen als Konto erstellen" anzeigt.](./media/configure-scom-to-monitor-analytics-platform-system/ConfigureScomCreateRunAsAccount.png "Konfigurieren von "konfigurierbar"")  
  
    2.  Das Dialogfeld **Assistent zum Erstellen der Laufzeit als Konto** wird geöffnet. Klicken Sie auf der Seite **Einführung** auf **Weiter** .  
  
    3.  Wählen Sie auf der Seite **Allgemeine Eigenschaften** die Option **Windows** from **Run As Account Type** aus, und geben Sie "APS Watcher" als **anzeigen Amen** an.  
  
        ![Screenshot der Seite "Allgemeine Eigenschaften" des Assistenten zum Erstellen für das Ausführen als Konto](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardGeneralProperties.png ""Kreaterunasaccountwizardgeneralproperties"")  
  
    4.  Auf der Seite **Anmelde** Informationen wird ein ![Screenshot angezeigt, der die Seite Anmelde Informationen des Assistenten zum Erstellen der Laufzeit als Konto anzeigt.](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardCredentials.png ""Kreaterunasaccountwizard-Anmelde Informationen"")  
  
    5.  Wählen Sie auf der Seite **Verteilungs Sicherheit** die Option **weniger sicher** aus, und klicken Sie auf die Schaltfläche **Erstellen** , um den  
  
        ![Screenshot der Seite "Verteilungs Sicherheit" des Assistenten zum Erstellen für das Ausführen als Konto](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardDistributionSecurity.png ""Kreaterunasaccountwizarddistributionsecurity"")  
  
        1.  Wenn Sie sich entscheiden, die sicherere Option zu verwenden, müssen Sie Computer manuell angeben, an die die Anmelde **Informationen** verteilt werden. Klicken Sie dazu mit der rechten Maustaste auf das Konto, und wählen Sie **Eigenschaften** aus, um das Konto zu erstellen.  
  
        2.  Navigieren Sie zur Registerkarte **Verteilung** , und **fügen Sie** die gewünschten Computer hinzu.  
  
            ![Screenshot, der das Dialogfeld "Eigenschaften für das Ausführen als Konto" anzeigt](./media/configure-scom-to-monitor-analytics-platform-system/RunAsAccountProperties.png "Runasaccountproperties")  
  
2.  Legen Sie für das **Microsoft APS Watcher-Konto** Profil die Verwendung des Kontos " **APS Watcher** -Konto" fest.  
  
    1.  Navigieren Sie zu **Verwaltung**  ->  **Ausführen als Konfigurations**  ->  **profile** .  
  
        ![Screenshot, der die Option "Profile" anzeigt.](./media/configure-scom-to-monitor-analytics-platform-system/AdministrationRunAsConfigurationProfiles.png "Administrationrunasconfigurationprofiles")  
  
    2.  Klicken Sie in der Liste mit der rechten Maustaste auf das **Microsoft APS Watcher-Konto** , und wählen Sie **Eigenschaften**  
  
        ![Screenshot, der die Option "Properties" anzeigt.](./media/configure-scom-to-monitor-analytics-platform-system/MicrosoftApsWatcherAccountProperties.png ""Mikrosoftapswatcheraccountproperties"")  
  
    3.  Das Dialogfeld " **Assistent für das Ausführen als Profil** " wird geöffnet. Springen Sie die **Einführungs** Seite, indem Sie auf **weiter** klicken.  
  
    4.  Klicken Sie auf der Seite **Allgemeine Eigenschaften** auf **Weiter** .  
  
    5.  Klicken Sie auf der Seite **als Konten ausführen** auf die Schaltfläche **hinzufügen...** , und wählen Sie das zuvor erstellte Konto " **APS Watcher** ausführen als" aus.  
  
        ![Screenshot, der das Dialogfeld "Ausführen als Konto hinzufügen" anzeigt.](./media/configure-scom-to-monitor-analytics-platform-system/RunAsProfileWizardAdd.png "Runasprofilewizardadd")  
  
    6.  Klicken Sie auf **Speichern** , um die Profil Zuweisung abzuschließen.  
  
3.  Warten Sie, bis die APS-Geräte Ermittlung abgeschlossen ist.  
  
    1.  Navigieren Sie zum Bereich **Überwachung** , und öffnen Sie die Statusansicht **SQL Server Appliance**  ->  **Microsoft Analytics Platform System**  ->  **Appliances** .  
  
        ![Screenshot, der die Option Appliances anzeigt](./media/configure-scom-to-monitor-analytics-platform-system/SqlServerApplianceMicrosoftApsAppliances.png "Sqlserverappliancemikrosoftapsappliances")  
  
    2.  Warten Sie, bis das Gerät in der Liste angezeigt wird. Der Name der Appliance muss mit einer in der Registrierung angegebenen übereinstimmen. Nachdem die Ermittlung abgeschlossen ist, werden alle aufgeführten Geräte angezeigt, die aber nicht überwacht werden. Führen Sie die folgenden Schritte aus, um die Überwachung zu aktivieren.  
  
    > [!NOTE]  
    > Die nächsten Schritte können parallel ausgeführt werden, während Sie auf den Abschluss der anfänglichen Geräte Ermittlung warten.  
  
4.  Erstellen Sie ein weiteres neues Konto, um APS zum Abrufen von Integritäts Daten abzufragen  
  
    1.  Beginnen Sie mit dem Erstellen eines neuen, wie in Schritt 1 beschrieben.  
  
    2.  Wählen Sie auf der Seite **Allgemeine Eigenschaften** die Option Standard **Authentifizierungs** Kontotyp aus.  
  
        ![Screenshot der allgemeinen Eigenschaften Seite des Assistenten zum Erstellen für das Ausführen als Konto mit der Standard Authentifizierung, die in der Dropdown Liste "Ausführen als Konto" ausgewählt ist.](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardGeneralProperties2.png "CreateRunAsAccountWizardGeneralProperties2")  
  
    3.  Geben Sie auf der Seite **Anmelde** Informationen gültige Anmelde Informationen für den Zugriff auf die Integritäts Zustands-DMVs an.  
  
        ![Screenshot der Seite "Anmelde Informationen" des Assistenten zum Erstellen für das Ausführen als Konto mit gültigen Anmelde Informationen für den Zugriff auf APS-Integritäts Zustands-DMVs](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardCredentials2.png "CreateRunAsAccountWizardCredentials2")  
  
5.  Konfigurieren Sie das **Microsoft APS-Aktions Konto** Profil, um das neu erstellte runas-Konto für die APS-Instanz zu verwenden.  
  
    1.  Navigieren Sie zu den Eigenschaften des **Microsoft APS-Aktions Kontos** , wie in Schritt 2 beschrieben.  
  
    2.  Klicken Sie auf der Seite " **Ausführen als Konten** " auf **hinzufügen...** und 
    3.  Wählen Sie das neu erstellte Konto "Ausführen als" aus.  
  
        ![Screenshot, der das Dialogfeld "runas-Konto hinzufügen" mit der in der Dropdown Liste "Ausführen als Konto" ausgewählten APS-Aktion anzeigt.](./media/configure-scom-to-monitor-analytics-platform-system/RunAsProfileWizardAdd2.png "RunAsProfileWizardAdd2")  
  
## <a name="next-step"></a>Nächster Schritt  
Nachdem Sie die Management Packs konfiguriert haben, können Sie mit der Überwachung des Geräts beginnen. Weitere Informationen finden Sie unter [Überwachen der Appliance mithilfe System Center Operations Manager &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md).  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
