---
title: Deaktivieren oder Anhalten der Berichts- und Abonnementverarbeitung | Microsoft-Dokumentation
ms.date: 06/19/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: subscriptions
ms.topic: conceptual
helpviewer_keywords:
- pausing schedules
- subscriptions [Reporting Services], pausing
- report processing [Reporting Services], pausing
- shared data sources [Reporting Services]
- pausing subscription processing
- pausing report processing
- temporarily stopping report processing
- disabling shared data sources
- roles [Reporting Services], modifying
- shared schedules [Reporting Services], pausing
ms.assetid: 3cf9a240-24cc-46d4-bec6-976f82d8f830
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 228cb40e1c0f40d9525ca83129878d30b722b910
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "68893425"
---
# <a name="disable-or-pause-report-and-subscription-processing"></a>Deaktivieren oder Anhalten der Berichts- und Abonnementverarbeitung  
Es gibt verschiedene Methoden zum Deaktivieren oder Anhalten der Berichts- und Abonnementverarbeitung in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Die in diesem Artikel beschriebenen Ansätze reichen vom Deaktivieren eines Abonnements bis hin zum Unterbrechen der Datenquellenverbindung. Nicht alle Ansätze sind mit beiden [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Servermodi möglich. In den folgenden Tabellen werden die Methoden und unterstützten [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Servermodi zusammengefasst:  
  
##  <a name="in-this-article"></a><a name="bkmk_top"></a> Inhalt dieses Artikels  
  
||Unterstützter Servermodus|  
|-|---------------------------|  
|[Aktivieren und Deaktivieren von Abonnements](#bkmk_disable_subscription)|Einheitlicher Modus|  
|[Anhalten eines freigegebenen Zeitplans](#bkmk_pause_schedule)|Einheitlicher und SharePoint-Modus|  
|[Deaktivieren einer freigegebenen Datenquelle](#bkmk_disable_shared_datasource)|Einheitlicher und SharePoint-Modus|  
|[Ändern von Rollenzuweisungen zum Verhindern des Zugriffs auf einen Bericht (einheitlicher Modus)](#bkmk_modify_role_assignment)|Einheitlicher Modus|  
|[Entfernen von Berechtigungen zur Abonnementverwaltung aus Rolle (einheitlicher Modus)](#bkmk_remove_manage_subscriptions_permission)|Einheitlicher Modus|  
|[Deaktivieren von Übermittlungserweiterungen](#bkmk_disable_extensions)|Einheitlicher und SharePoint-Modus|  
  
##  <a name="enable-and-disable-subscriptions"></a><a name="bkmk_disable_subscription"></a>Aktivieren und Deaktivieren von Abonnements  
  
>[!TIP]  
>Neu in SQL 2016 Reporting Services: *Aktivieren und Deaktivieren von Abonnements*. Neue Optionen der Benutzeroberfläche ermöglichen Ihnen ein schnelles Aktivieren und Deaktivieren von Abonnements. Die deaktivierten Abonnements behalten ihre anderen Konfigurationseigenschaften, z. B. den Zeitplan, bei und können leicht erneut aktiviert werden. Sie können Abonnements auch programmgesteuert aktivieren und deaktivieren oder überwachen, welche Abonnements deaktiviert werden.  
  
  ![Die Schaltflächen zum Aktivieren und Deaktivieren auf der Seite „Abonnements“ ](../../reporting-services/subscriptions/media/disable-or-pause-report-and-subscription-processing/subscription-enable-and-disable-buttons.png)  
  
Wechseln Sie im Webportal zum Abonnement. Verwenden Sie dafür entweder die Seite **Meine Abonnements** oder die Seite **Abonnements** eines bestimmten Abonnements. Wählen Sie ein oder mehrere Abonnements aus, und klicken Sie auf dem Menüband auf die Schaltfläche „Deaktivieren“ oder auf die Schaltfläche „Aktivieren“ (siehe Bild oben). Die Statusspalte ändert sich zu „Deaktiviert“ bzw. „Aktiviert“.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] schreibt eine Zeile in das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Protokoll, wenn ein Abonnement aktiviert oder deaktiviert wird. In der Berichtsserver-Protokolldatei:  
  
 `C:\Program Files\Microsoft SQL Server Reporting Services\SSRS\LogFiles\RSPortal_2019_06_20_00_49_22.log`  
  
 werden in etwa folgende Zeilen angezeigt:  
  
 `RSPortal!subscription!RSPortal.exe!93!06/20/2019-01:16:47:: i INFO: Subscription 2b409d66-d4ea-408a-918c-0f9e41ce49ca disabled at 06/20/2019 01:16:47`  
  
 `RSPortal!subscription!RSPortal.exe!93!06/20/2019-01:16:51:: i INFO: Subscription 2b409d66-d4ea-408a-918c-0f9e41ce49ca enabled at 06/20/2019 01:16:51`  
  
![PowerShell-Inhalt](https://docs.microsoft.com/analysis-services/analysis-services/instances/install-windows/media/rs-powershellicon.jpg "PowerShell-Inhalt"): **Verwenden von Windows PowerShell zum Deaktivieren eines einzelnen Abonnements:** Verwenden Sie das folgende PowerShell-Skript, um ein bestimmtes Abonnement zu deaktivieren. Aktualisieren Sie den Servernamen und die Abonnement-ID im Skript.  
  
```PS  
#disable specific subscription  
$rs2010 = New-WebServiceProxy -Uri "https://SERVERNAME/ReportServer/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential;  
$subscriptionID = "subscription guid";  
$rs2010.DisableSubscription($subscriptionID);  
  
```  
  
 Mit dem folgenden Skript können Sie alle Abonnements mit ihren IDs auflisten. Aktualisieren Sie den Servernamen.  
  
```  
#list all subscriptions  
$rs2010 = New-WebServiceProxy -Uri "https://SERVERNAME /ReportServer/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential;  
$subscriptions = $rs2010.ListSubscriptions("/");  
$subscriptions | select subscriptionid, report, status, path  
  
```  
  
 ![PowerShell-Inhalt](https://docs.microsoft.com/analysis-services/analysis-services/instances/install-windows/media/rs-powershellicon.jpg "PowerShell-Inhalt") **Verwenden von Windows PowerShell zum Auflisten aller deaktivierten Abonnements:** Verwenden Sie das folgende PowerShell-Skript, um alle deaktivierten Abonnements auf dem aktuellen Berichtsserver im einheitlichen Modus aufzulisten. Aktualisieren Sie den Servernamen.  
  
```  
#list all disabled subscriptions  
$rs2010 = New-WebServiceProxy -Uri "https://uetestb03/ReportServer/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential;  
$subscriptions = $rs2010.ListSubscriptions("/");  
Write-Host "--- Disabled Subscriptions ---";  
Write-Host "----------------------------------- ";  
$subscriptions | Where-Object {$_.Active.DisabledByUserSpecified -and $_.Active.DisabledByUser } | select subscriptionid, report, status, lastexecuted,path | format-table -auto  
```  
  
 ![PowerShell-Inhalt](https://docs.microsoft.com/analysis-services/analysis-services/instances/install-windows/media/rs-powershellicon.jpg "PowerShell-Inhalt") **Verwenden von Windows PowerShell zum Aktivieren aller deaktivierten Abonnements:** Verwenden Sie das folgende PowerShell-Skript, um alle zurzeit deaktivierten Abonnements zu aktivieren. Aktualisieren Sie den Servernamen.  
  
```  
#enable all subscriptions  
$rs2010 = New-WebServiceProxy -Uri "https://SERVERNAME/ReportServer/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential;  
$subscriptions = $rs2010.ListSubscriptions("/") | Where-Object {$_.status -eq "disabled" } ;  
ForEach ($subscription in $subscriptions)  
{  
    $rs2010.EnableSubscription($subscription.SubscriptionID);  
    $subscription | select subscriptionid, report, path  
}  
  
```  
  
 ![PowerShell-Inhalt](https://docs.microsoft.com/analysis-services/analysis-services/instances/install-windows/media/rs-powershellicon.jpg "PowerShell-Inhalt") **Verwenden von Windows PowerShell zum Deaktivieren aller Abonnements:** Verwenden Sie das folgende PowerShell-Skript, um **ALLE** Abonnements zu deaktivieren.  
  
```  
#DISABLE all subscriptions  
$rs2010 = New-WebServiceProxy -Uri "https://SERVERNAME/ReportServer/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential;  
$subscriptions = $rs2010.ListSubscriptions("/") ;  
ForEach ($subscription in $subscriptions)  
{  
    $rs2010.DisableSubscription($subscription.SubscriptionID);  
    $subscription | select subscriptionid, report, path  
}  
```  
  
##  <a name="pause-a-shared-schedule"></a><a name="bkmk_pause_schedule"></a> Anhalten eines freigegebenen Zeitplans  
 Wenn ein Bericht oder ein Abonnement mit einem freigegebenen Zeitplan ausgeführt wird, können Sie den Zeitplan anhalten, um die Verarbeitung zu verhindern. Alle Berichts- und Abonnementverarbeitungen, die durch den Zeitplan gesteuert werden, werden zurückgestellt, bis der Zeitplan fortgesetzt wird.  
  
-   **SharePoint-Modus:** ![SharePoint-Einstellungen](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint-Einstellungen"): Wählen Sie unter **Standorteinstellungen** die Option **Freigegebene Zeitpläne verwalten** aus. Wählen Sie den Zeitplan aus, und klicken Sie auf **Ausgewählte Zeitpläne anhalten**.  
  
-   **Einheitlicher Modus :** Klicken Sie im Webportal auf der oberen Menüleiste auf die Schaltfläche **Einstellungen** ![Schaltfläche „Einstellungen“](media/ssrs-portal-settings-gear.png), und wählen Sie aus dem Dropdownmenü die Option **Standorteinstellungen** aus. Wählen Sie die Registerkarte **Zeitpläne** aus, um die Seite „Zeitpläne“ anzuzeigen. Aktivieren Sie die Kontrollkästchen neben den Zeitplänen, die Sie aktivieren oder deaktivieren möchten, und klicken Sie auf die Schaltfläche **Aktivieren** bzw. **Deaktivieren**, um die gewünschte Aktion auszuführen. Die Statusspalte wird entsprechend in „Aktiviert“ bzw. „Deaktiviert“ aktualisiert.  
  
##  <a name="disable-a-shared-data-source"></a><a name="bkmk_disable_shared_datasource"></a> Deaktivieren einer freigegebenen Datenquelle  
 Ein Vorteil des Verwendens freigegebener Datenquellen ist, dass Sie diese deaktivieren können, um die Ausführung eines Berichts oder eines datengesteuerten Abonnements zu verhindern. Durch das Deaktivieren einer freigegebenen Datenquelle wird die Verbindung des Berichts mit der externen Quelle getrennt. Die deaktivierte Datenquelle steht für keine Berichte und Abonnements zur Verfügung.  
  
 Beachten Sie, dass der Bericht weiterhin geladen wird, selbst wenn die Datenquelle nicht verfügbar ist. Der Bericht enthält keine Daten, aber Benutzer mit entsprechenden Berechtigungen haben Zugriff auf die Eigenschaftenseiten, Sicherheitseinstellungen, den Berichtsverlauf und die Abonnementinformationen für den Bericht.  
  
-   **SharePoint-Modus:** Um eine freigegebene Datenquelle in einem Berichtsserver im SharePoint-Modus zu deaktivieren, wechseln Sie zu der Dokumentbibliothek, die die Datenquelle enthält. ![Symbol für freigegebene Datenquelle](../../reporting-services/report-data/media/hlp-16datasource.png "Symbol für freigegebene Datenquelle") Klicken Sie auf die Datenquelle, und deaktivieren Sie das Kontrollkästchen **Diese Datenquelle aktivieren**.  
  
-   **Einheitlicher Modus :** Um eine freigegebene Datenquelle auf einem Berichtsserver im einheitlichen Modus zu deaktivieren, öffnen Sie die Datenquelle im Webportal, und deaktivieren Sie das Kontrollkästchen **Diese Datenquelle aktivieren**.  
  
##  <a name="modify-role-assignments-to-prevent-access-to-a-report-native-mode"></a><a name="bkmk_modify_role_assignment"></a> Ändern von Rollenzuweisungen zum Verhindern des Zugriffs auf einen Bericht (einheitlicher Modus)  
Eine Möglichkeit, um einen Bericht nicht verfügbar zu machen, ist das vorübergehende Entfernen der Rollenzuweisung, die den Zugriff auf den Bericht bereitstellt. Diese Vorgehensweise kann für alle Berichte unabhängig von der Art der Datenquellenverbindung verwendet werden. Dabei ist nur der Bericht betroffen. Die Ausführung anderer Berichte oder Elemente ist davon nicht betroffen.  
  
 Öffnen Sie die Seite **Sicherheit** des Berichts im Webportal, um die Rollenzuweisung zu entfernen. Falls der Bericht die Sicherheit von einem übergeordneten Bericht erbt, können Sie **Sicherheit anpassen** und anschließend im Dialogfeld **Elementsicherheit** die Option **Bestätigen** auswählen, um eine restriktive Sicherheitsrichtlinie zu erstellen, die Rollenzuweisungen für den Zugriff auf breiter Basis ausklammert (entfernen Sie z.B. eine Rollenzuweisung, die jedem Benutzer den Zugriff ermöglicht, und behalten Sie die Rollenzuweisung, die einer kleinen Benutzergruppe den Zugriff ermöglicht, wie z.B. Administratoren).  
  
##  <a name="remove-manage-subscription-permissions-from-role-native-mode"></a><a name="bkmk_remove_manage_subscriptions_permission"></a> Entfernen von Berechtigungen zur Abonnementverwaltung aus Rolle (einheitlicher Modus)  
 Entfernen Sie den Task **Einzelne Abonnements verwalten** aus der Rolle, um zu verhindern, dass Benutzer Abonnements erstellen. Wenn Sie diesen Task entfernen, sind die Abonnementseiten nicht verfügbar. Im Webportal scheint die Seite Meine Abonnements leer zu sein (kann nicht gelöscht werden), selbst wenn zuvor Abonnements enthalten waren. Das Entfernen von Tasks im Zusammenhang mit Abonnements verhindert, dass Benutzer Abonnements erstellen und ändern. Vorhandene Abonnements werden dadurch jedoch nicht gelöscht. Vorhandene Abonnements werden so lange weiter ausgeführt, bis Sie sie löschen. So entfernen Sie die Berechtigung:  
  
1.  Öffnen Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. 
  
2.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Berichtsserver her.  
  
3.  Erweitern Sie den Knoten **Sicherheit** .  
  
4.  Erweitern Sie den Knoten **Rollen**, und wählen Sie die gewünschte Rolle aus.  
  
5.  Klicken Sie mit der rechten Maustaste auf die Rolle, und wählen Sie **Eigenschaften** aus.  
  
6.  Deaktivieren Sie die Aufgaben **Einzelne Abonnements verwalten** und die **Alle Abonnements verwalten**.  
  
7.  Wählen Sie **OK** aus, um die Änderungen zu übernehmen.

  
##  <a name="disable-delivery-extensions"></a><a name="bkmk_disable_extensions"></a> Deaktivieren von Übermittlungserweiterungen  
 Alle auf einem Berichtsserver installierten Übermittlungserweiterungen sind für jeden Benutzer verfügbar, der Berechtigungen zum Erstellen eines Abonnements für einen vorhandenen Bericht hat. Die folgenden Übermittlungserweiterungen sind verfügbar und werden automatisch konfiguriert:  
  
-   Windows-Dateifreigabe  
  
-   SharePoint-Bibliothek (nur über eine SharePoint-Website verfügbar, die in einen Berichtsserver mit integriertem SharePoint-Modus integriert ist)  
  
 Die E-Mail-Übermittlung muss konfiguriert werden, bevor sie verwendet werden kann. Wenn Sie sie nicht konfigurieren, ist sie nicht verfügbar. Weitere Informationen finden Sie unter [E-Mail-Einstellungen: einheitlicher Modus von Reporting Services (Konfigurations-Manager)](../install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md).  
  
 Wenn Sie bestimmte Erweiterungen deaktivieren möchten, können Sie die Erweiterungseinträge in der Datei **RSReportServer.config** entfernen. Weitere Informationen finden Sie unter [Reporting Services-Konfigurationsdateien](../../reporting-services/report-server/reporting-services-configuration-files.md) und [E-Mail-Einstellungen: einheitlicher Modus von Reporting Services (Konfigurations-Manager)](../install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md).  
  
 Eine entfernte Übermittlungserweiterung ist im Webportal oder auf einer SharePoint-Website nicht mehr verfügbar. Das Entfernen einer Übermittlungserweiterung kann inaktive Abonnements zur Folge haben. Stellen Sie vor dem Entfernen einer Erweiterung sicher, dass Sie die Abonnements löschen oder sie so konfigurieren, dass sie eine andere Übermittlungserweiterung verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Abonnements und Übermittlung &#40;Reporting Services&#41;](../../reporting-services/subscriptions/subscriptions-and-delivery-reporting-services.md)   
 [Reporting Services-Konfigurationsdateien](../../reporting-services/report-server/reporting-services-configuration-files.md)   
 [Konfigurieren des Webportals](../../reporting-services/report-server/configure-web-portal.md)   
 [Reporting Services-Berichtsserver &#40;einheitlicher Modus&#41;](../../reporting-services/report-server/reporting-services-report-server-native-mode.md)   
 [Das Webportal eines Berichtsservers (einheitlicher SSRS-Modus)](../../reporting-services/web-portal-ssrs-native-mode.md)   
 [Securable Items (Sicherbare Elemente)](../../reporting-services/security/securable-items.md) 
  
