---
title: Seite "Site Einstellungen" (Berichts-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4d67a01c-eae4-49ba-a6e8-8e983c0248f5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 07fc0207020887d7e3ceb8716ee76c78a55d2bac
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66101120"
---
# <a name="site-settings-page-report-manager"></a>Siteeinstellungen (Seite) (Berichts-Manager)
  Verwenden Sie die Seite "Siteeinstellungen", um den Anwendungstitel zu ändern, serverweite Standardeinstellungen für die Grenzwerte des Berichtsverlaufs und Timeoutwerte für die Berichtsverarbeitung festzulegen und Rollenzuweisungen auf Systemebene sowie freigegebene Zeitpläne zu verwalten. Sie müssen über Inhalts-Manager- und Systemadministratorberechtigungen verfügen, um diese Seite anzuzeigen.  
  
> [!NOTE]  
>  Die folgenden Funktionen sind nicht in jeder Edition von SQL Server verfügbar: Berichtsverlauf, Berichtsausführung und freigegebene Zeitpläne. Eine Liste der Funktionen, die von den Editionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]unterstützt werden, finden Sie unter [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="navigation"></a>Navigation  
 Verwenden Sie folgendes Verfahren, um zu dieser Position in der Benutzeroberfläche zu navigieren.  
  
### <a name="to-open-the-site-settings-page"></a>So öffnen Sie die Seite "Siteeinstellungen"  
  
1.  Öffnen Sie den Berichts-Manager.  
  
2.  Klicken Sie oben auf der Seite auf **Siteeinstellungen**. Dadurch wird die Seite Allgemeine Eigenschaften der Website geöffnet.  
  
     **Hinweis:** Wenn die Option **Site Einstellungen** nicht im Menü angezeigt wird, verfügen Sie nicht über die erforderlichen Berechtigungen. Weitere Informationen finden Sie im Abschnitt "Site Einstellungen" unter [Konfigurieren eines Berichts Servers im einheitlichen Modus für die lokale Verwaltung &#40;SSRS&#41;](report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
## <a name="options"></a>Tastatur  
 **Name**  
 Geben Sie den Titel an, der für diese Instanz des Berichts-Managers von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] verwendet werden soll. Standardmäßig lautet der Titel "[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]".  
  
 **Wählen Sie Standardeinstellungen für den Berichtsverlauf aus**  
 Wählen Sie einen Standardwert für die Anzahl von Kopien aus, die im Berichtsverlauf gespeichert werden. Mithilfe eines Standardwertes werden Anfangseinstellungen bei den Grenzwerten für den Berichtsverlauf eingerichtet. Diese Einstellungen können auf Berichtsebene geändert werden. Weitere Informationen finden Sie unter [Momentaufnahmeoptionen (Eigenschaftenseite) (Berichts-Manager)](../../2014/reporting-services/snapshot-options-properties-page-report-manager.md).  
  
 Wenn Sie den Berichtsverlauf zu einem späteren Zeitpunkt einschränken und der vorhandene Berichtsverlauf den angegebenen Grenzwert übersteigt, verringert der Berichtsserver den vorhandenen Berichtsverlauf auf den neuen Grenzwert. Die ältesten Berichtsmomentaufnahmen werden zuerst gelöscht. Falls der Berichtsverlauf leer ist oder unter dem Grenzwert liegt, werden neue Berichtsmomentaufnahmen hinzugefügt. Ist der Grenzwert erreicht, wird die älteste Momentaufnahme gelöscht, sobald eine neue Berichtsmomentaufnahme hinzugefügt wird.  
  
 **Timeout für Berichtsausführung**  
 Geben Sie eine bestimmte Anzahl von Sekunden als Timeoutwert für die Berichtsverarbeitung an.  
  
 Dieser Wert gilt für die Berichtsverarbeitung auf einem Berichtsserver. Er hat keine Auswirkung auf die Datenverarbeitung auf dem Datenbankserver, der die Daten für den Bericht zur Verfügung stellt.  
  
 Der Zeitgeber für die Berichtsverarbeitung läuft ab dem Zeitpunkt der Auswahl des Berichts und wird mit dem Öffnen des Berichts beendet. Stellen Sie beim Festlegen dieses Werts genügend Zeit für die Daten- und die Berichtsverarbeitung zur Verfügung.  
  
 **Start-URL für benutzerdefinierten Berichts-Generator**  
 Geben Sie eine benutzerdefinierte URL an, wenn der Berichtsserver nicht die Standard-URL des Berichts-Generators verwendet. Diese Einstellung ist optional. Wenn Sie keinen Wert angeben, wird die Standard-URL verwendet, durch die der Berichts-Generator als ClickOnce-Anwendung gestartet wird. Die Standard-URL entspricht einem der folgenden Werte:  
  
 **Berichts Server im einheitlichen Modus:** Bei einer Installation im einheitlichen Modus hat die Standard-URL das Format http://\<*Computername*>/ReportServer/ReportBuilder/ReportBuilder_3_0_0_0. Application.  
  
 Integrierter SharePoint-Modus: die Standard-URL hat das Format http://\<*SharePoint_site*>/_vti_bin/ReportBuilder/ReportBuilder_3_0_0_0. Application. "  
  
 **Anwenden**  
 Klicken Sie auf diese Schaltfläche, um die Änderungen auf dem Berichtsserver zu speichern.  
  
 **Sicherheit**  
 Klicken Sie auf diesen Link, um die Seite "Systemrollenzuweisungen" zu öffnen, auf der Sie Benutzern und Gruppenkonten vordefinierte Systemrollen zuweisen können.  
  
 **Zeitpläne**  
 Klicken Sie auf diesen Link, um die Seite Freigegebene Zeitpläne zu öffnen. Auf dieser Seite können Sie Zeitpläne vordefinieren, die Benutzer für ihre Berichte und Abonnements auswählen können.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Erteilen von Berechtigungen für einen Berichtsserver im einheitlichen Modus](security/granting-permissions-on-a-native-mode-report-server.md)   
 [Vordefinierte Rollen](security/role-definitions-predefined-roles.md)   
 [Berichts-Manager (F1-Hilfe)](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
