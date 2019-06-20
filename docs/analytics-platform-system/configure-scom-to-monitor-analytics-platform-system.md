---
title: Konfiguration von SCOM zum Überwachen von Analytics Platform System | Microsoft-Dokumentation
description: Um die System Center Operations Manager (SCOM) Management Packs für Analytics Platform System zu konfigurieren, gehen Sie wie folgt vor. Die Management Packs sind erforderlich, Analytics Platform System von SCOM zu überwachen.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 2dae92263d7be76490a51ea7027f79ab5fcd6118
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62509761"
---
# <a name="configure-system-center-operations-manager-scom-to-monitor-analytics-platform-system"></a>Konfigurieren Sie System Center Operationsmanager (SCOM), Analytics Platform System überwachen
Um die System Center Operations Manager (SCOM) Management Packs für Analytics Platform System zu konfigurieren, gehen Sie wie folgt vor. Die Management Packs sind erforderlich, Analytics Platform System von SCOM zu überwachen.  
  
## <a name="BeforeBegin"></a>Vorbereitungen  
**Erforderliche Komponenten**  
  
System Center Operationsmanager 2007 R2 muss installiert und ausgeführt werden.  
  
Die Management Packs müssen installiert und konfiguriert werden. Finden Sie unter [die SCOM-Management Packs &#40;Analytics-Plattformsystem&#41; ](install-the-scom-management-packs.md) und [Importieren des SCOM Management Packs für PDW &#40;Analytics-Plattformsystem&#41;](import-the-scom-management-pack-for-pdw.md).  
  
## <a name="ConfigureRunAsProfile"></a>Konfigurieren Sie Ausführende Profile in System Center  
Um System Center zu konfigurieren, müssen Sie führen Sie die folgenden Schritte aus:  
  
-   Erstellen des ausführenden Kontos für die **APS-Watcher** Domänenbenutzer und ordnen Sie es der **Microsoft APS-Watcher-Konto.**  
  
-   Erstellen des ausführenden Kontos für die **Monitoring_user** APS-Benutzer und ordnen ihn der **Microsoft APS-Aktionskonto**.  
  
Nachfolgend finden Sie ausführliche Anweisungen dazu, wie Sie die Aufgaben durchführen:  
  
1.  Erstellen der **APS-Watcher** ausführendes Konto mit **Windows** Kontotyp für die **APS-Watcher** Domänenbenutzer.  
  
    1.  Navigieren Sie zu der **Verwaltung** Bereich mit der rechten Maustaste auf **Ausführen als-Konfiguration** -> **Konten** , und wählen Sie **ausführendes Konto erstellen...**  
  
        ![ConfigureScomCreateRunAsAccount](./media/configure-scom-to-monitor-analytics-platform-system/ConfigureScomCreateRunAsAccount.png "ConfigureScomCreateRunAsAccount")  
  
    2.  Die **erstellen Assistenten** Dialogfeld wird geöffnet. Auf der **Einführung** auf **Weiter**.  
  
    3.  Auf der **allgemeine Eigenschaften** Seite **Windows** aus **Typ des ausführenden Kontos** , und geben Sie "APS-Watcher" als die **Anzeigenamen**.  
  
        ![CreateRunAsAccountWizardGeneralProperties](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardGeneralProperties.png "CreateRunAsAccountWizardGeneralProperties")  
  
    4.  Auf der **Anmeldeinformationen** Seite ![CreateRunAsAccountWizardCredentials](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardCredentials.png "CreateRunAsAccountWizardCredentials")  
  
    5.  Auf der **Verteilungssicherheit** Seite **unsicherer** , und klicken Sie auf die **erstellen** Schaltfläche, um den Vorgang abzuschließen.  
  
        ![CreateRunAsAccountWizardDistributionSecurity](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardDistributionSecurity.png "CreateRunAsAccountWizardDistributionSecurity")  
  
        1.  Wenn Sie verwenden möchten. die **sicherer** auswählen, müssen Sie manuell Computer angeben, der die Anmeldeinformationen verteilt werden werden. Klicken Sie dazu nach dem Erstellen des ausführenden Kontos, mit der rechten Maustaste darauf, und wählen Sie **Eigenschaften**.  
  
        2.  Navigieren Sie zu der **Verteilung** Registerkarte und **hinzufügen** gewünschten Computer.  
  
            ![RunAsAccountProperties](./media/configure-scom-to-monitor-analytics-platform-system/RunAsAccountProperties.png "RunAsAccountProperties")  
  
2.  Legen Sie die **Microsoft-APS-Watcher** zu verwendende Profil **APS-Watcher** ausführendes Konto.  
  
    1.  Navigieren Sie zu **Verwaltung** -> **Ausführen als Konfiguration** -> **Profile**.  
  
        ![AdministrationRunAsConfigurationProfiles](./media/configure-scom-to-monitor-analytics-platform-system/AdministrationRunAsConfigurationProfiles.png "AdministrationRunAsConfigurationProfiles")  
  
    2.  Klicken Sie mit der rechten Maustaste auf **Microsoft-APS-Watcher** aus der Liste und wählen Sie **Eigenschaften**.  
  
        ![MicrosoftApsWatcherAccountProperties](./media/configure-scom-to-monitor-analytics-platform-system/MicrosoftApsWatcherAccountProperties.png "MicrosoftApsWatcherAccountProperties")  
  
    3.  Die **Assistenten für ausführende Profile** Dialogfeld wird geöffnet. Überspringen der **Einführung** Seite, indem Sie auf **Weiter**.  
  
    4.  Auf der **allgemeine Eigenschaften** auf **Weiter**.  
  
    5.  Auf der **ausführende Konten** klicken Sie auf die **hinzufügen...**  Schaltfläche, und wählen Sie das zuvor erstellte **APS-Watcher** ausführendes Konto.  
  
        ![RunAsProfileWizardAdd](./media/configure-scom-to-monitor-analytics-platform-system/RunAsProfileWizardAdd.png "RunAsProfileWizardAdd")  
  
    6.  Klicken Sie auf **speichern** profilzuweisung abgeschlossen.  
  
3.  Warten Sie, bis der APS-Einheiten, die Ermittlung abgeschlossen ist.  
  
    1.  Navigieren Sie zu der **Überwachung** Bereich, und öffnen Sie die **SQL Server-Appliance** -> **Microsoft Analytics Platform System**  ->   **Appliances** Statusansicht.  
  
        ![SqlServerApplianceMicrosoftApsAppliances](./media/configure-scom-to-monitor-analytics-platform-system/SqlServerApplianceMicrosoftApsAppliances.png "SqlServerApplianceMicrosoftApsAppliances")  
  
    2.  Warten Sie, bis das Gerät in der Liste angezeigt wird. Der Name des Geräts sollte gleich eins der in der Registrierung angegeben sein. Nach Abschluss der Ermittlung sollten alle Geräte aufgeführt, aber nicht überwacht angezeigt werden. Um Überwachung zu aktivieren, führen Sie in den nächsten Schritten.  
  
    > [!NOTE]  
    > Die nächsten Schritte können parallel erfolgen, während Sie das erste Gerät Ermittlung warten.  
  
4.  Erstellen Sie einen anderen neuen ausführenden Kontos zum Abfragen APS Integrität Abrufen von Daten.  
  
    1.  Beginnen Sie, erstellen ein neues ausführendes Konto aus, wie in Schritt 1 beschrieben.  
  
    2.  Auf der **allgemeine Eigenschaften** Seite **Standardauthentifizierung** Kontotyp.  
  
        ![CreateRunAsAccountWizardGeneralProperties2](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardGeneralProperties2.png "CreateRunAsAccountWizardGeneralProperties2")  
  
    3.  Auf der **Anmeldeinformationen** Seite, geben Sie gültige Anmeldeinformationen für den Zugriff auf APS-Integritätsstatus DMVs.  
  
        ![CreateRunAsAccountWizardCredentials2](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardCredentials2.png "CreateRunAsAccountWizardCredentials2")  
  
5.  Konfigurieren der **Microsoft APS-Aktionskonto** Profils, das das neu erstellte ausführende Konto für die APS-Instanz verwendet.  
  
    1.  Navigieren Sie zu der **Microsoft APS-Aktionskonto** Eigenschaften wie in Schritt 2 beschrieben.  
  
    2.  Auf der **ausführende Konten** auf **hinzufügen...**  und 
    3.  Wählen Sie das neu erstellte ausführende Konto an.  
  
        ![RunAsProfileWizardAdd2](./media/configure-scom-to-monitor-analytics-platform-system/RunAsProfileWizardAdd2.png "RunAsProfileWizardAdd2")  
  
## <a name="next-step"></a>Nächster Schritt  
Nun, dass Sie die Management Packs konfiguriert haben, können Sie sich beim Starten der Überwachung der Appliances. Weitere Informationen finden Sie unter [Überwachen der Appliance, indem Sie mithilfe von System Center Operations Manager &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md).  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
