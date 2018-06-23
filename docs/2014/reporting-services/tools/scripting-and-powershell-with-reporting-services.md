---
title: Skripterstellung und PowerShell mit Reporting Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- scripts [Reporting Services]
- Reporting Services, scripting
- scripting [Reporting Services]
ms.assetid: 1ac2646d-ed5a-4436-b18f-2150c33f3d87
caps.latest.revision: 12
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 0d76693f37506cd78a7d198520344cb55f9d142f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36059953"
---
# <a name="scripting-and-powershell-with-reporting-services"></a>Skripterstellung und PowerShell mit Reporting Services
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] unterstützt eine Vielzahl von Entwicklungs- und Verwaltungsszenarien über Skripts, beispielsweise das Befehlszeilenprogramm rs.exe, PowerShell-Cmdlets für Berichtsserver im SharePoint-Modus und die Nutzung der [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] -Objektmodells in PowerShell für sowohl bei systemeigenen und SharePoint-Modus.  
  
-   Administratoren können Skripts in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] erstellen, um das Bereitstellen und Verwalten einer Berichtsserverinstallation zu automatisieren. Zudem können Administratoren [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skripts generieren und ausführen, mit denen eine Berichtsserver-Datenbank erstellt, konfiguriert und aktualisiert werden kann. Administratoren können auch die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] verfügbaren Funktionen zum Aufzeichnen und Wiedergeben von Skripts verwenden, um routinemäßige Wartungsaufgaben zu automatisieren.  
  
-   Entwickler können benutzerdefinierte Anwendungen erstellen, die Skripts enthalten. Sie können Skripts ausführen, mit denen den Report Server-Webdienst aufgerufen wird. Fast jeder Vorgang, den Sie in verwaltetem Code schreiben können, kann auch als Skript geschrieben werden.  
  
-   [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] unterstützt [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET Skript als Skriptsprache, die vom Hilfsprogramm RS.exe, einem Skripthost verarbeitet werden kann, die auf dem Berichtsserver ausgeführt wird.  
  
## <a name="reporting-services-sharepoint-mode-powershell-cmdlets-and-samples"></a>PowerShell-Cmdlets für Reporting Services im SharePoint-Modus und Beispiele  
 ![PowerShell-Inhalt](../media/rs-powershellicon.jpg "PowerShell related content")  
  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint-Modus schließt [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] -Cmdlets für die Verwaltung des Berichtsservers.  
  
-   [PowerShell cmdlets for Reporting Services SharePoint Mode](../powershell-cmdlets-for-reporting-services-sharepoint-mode.md) enthält die folgenden Beispiele:  
  
    -   Erstellen einer Dienstanwendung und eines Proxys  
  
    -   Überprüfen und Aktualisieren einer Übermittlungserweiterung  
  
    -   Abrufen und Festlegen von Eigenschaften der Reporting Services-Anwendungsdatenbank, z. B. Timeout der Datenbank  
  
    -   Datenerweiterungen auflisten  
  
## <a name="reporting-services-object-model-and-powershell-samples"></a>Reporting Services-Objektmodell und Powershell-Beispiele  
 ![PowerShell-Inhalt](../media/rs-powershellicon.jpg "PowerShell related content")  
  
 PowerShell-Aufruf des Kern-Objektmodells und zum größten Teil gültig für SharePoint- und einheitlichen Modus, z. B. die Migrationsarbeit, Abonnementarbeit und weitere Beispiele für Abonnementarbeit in SQL15.  
  
-   [Use PowerShell to Change und Auflisten von Reporting Services-Abonnementbesitzern aus, und führen Sie ein Abonnement](../subscriptions/manage-subscription-owners-and-run-subscription-powershell.md).  
  
-   [Verwenden von PowerShell zum Erstellen einer Azure-VM mit einem Berichtsserver im einheitlichen Modus](http://msdn.microsoft.com/library/azure/dn449661.aspx).  
  
-   Weitere Informationen finden Sie im Abschnitt „Zugriff auf die WMI-Klassen mit PowerShell“ in [Access the Reporting Services WMI Provider](access-the-reporting-services-wmi-provider.md).  
  
-   [Verwalten von SSRS mit PowerShell](http://curah.microsoft.com/13107/how-to-administer-ssrs-using-powershell).scriptin  
  
## <a name="rsexe-scripting-samples"></a>Skriptbeispiele für RS.exe  
  
-   [Beispiel zu Reporting Services-Beispielskript rs.exe zum Migrieren von Inhalten zwischen Berichtsservern](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).  
  
-   Zusätzliche Skripts, Anwendungs- und Erweiterungsbeispiele finden Sie unter [SQL Server Reporting Services-Produktbeispiele](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>Siehe auch  
 [Hilfsprogramm RS.exe &#40;SSRS&#41;](rs-exe-utility-ssrs.md)   
 [Skripts für Bereitstellungs- und Verwaltungsaufgaben](script-deployment-and-administrative-tasks.md)   
 [Script with the rs.exe Utility and the Web Service (Skripterstellung mit dem Hilfsprogramm rs.exe und dem Webdienst)](script-with-the-rs-exe-utility-and-the-web-service.md)  
  
  