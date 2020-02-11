---
title: Skripterstellung und PowerShell mit Reporting Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- scripts [Reporting Services]
- Reporting Services, scripting
- scripting [Reporting Services]
ms.assetid: 1ac2646d-ed5a-4436-b18f-2150c33f3d87
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1cbb7d07835b63509ecd854788ce21e382141728
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66099640"
---
# <a name="scripting-and-powershell-with-reporting-services"></a>Skripterstellung und PowerShell mit Reporting Services
  
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] unterstützt eine Vielzahl von Entwicklungs- und Verwaltungsszenarien über Skripts, beispielsweise das Befehlszeilenprogramm RS.exe, PowerShell-Cmdlets für Berichtsserver im SharePoint-Modus und die Nutzung des [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] -Objektmodells in PowerShell für den einheitlichen und den SharePoint-Modus.  
  
-   Administratoren können Skripts in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] schreiben, um die Bereitstellung und Verwaltung einer Berichts Server Installation zu automatisieren. Zudem können Administratoren [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skripts generieren und ausführen, mit denen eine Berichtsserver-Datenbank erstellt, konfiguriert und aktualisiert werden kann. Administratoren können auch die Funktionen zum Aufzeichnen und Wiedergeben von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] Skripts in verwenden, um routinemäßige Wartungsaufgaben zu automatisieren.  
  
-   Entwickler können benutzerdefinierte Anwendungen erstellen, die Skripts enthalten. Sie können Skripts ausführen, mit denen den Report Server-Webdienst aufgerufen wird. Fast jeder Vorgang, den Sie in verwaltetem Code schreiben können, kann auch als Skript geschrieben werden.  
  
-   [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]unter [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] stützt .NET-Skript als Skriptsprache, die vom Hilfsprogramm Rs. exe, einem auf dem Berichts Server ausgeführten Skript Host, verarbeitet werden kann.  
  
## <a name="reporting-services-sharepoint-mode-powershell-cmdlets-and-samples"></a>PowerShell-Cmdlets für Reporting Services im SharePoint-Modus und Beispiele  
 ![PowerShell-Inhalt](../media/rs-powershellicon.jpg "PowerShell-Inhalt")  
  
 
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint-Modus umfasst [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] -Cmdlets für die Verwaltung des Berichtsservers.  
  
-   [PowerShell-Cmdlets für Reporting Services SharePoint-Modus](../powershell-cmdlets-for-reporting-services-sharepoint-mode.md) Enthält die folgenden Beispiele:  
  
    -   Erstellen einer Dienstanwendung und eines Proxys  
  
    -   Überprüfen und Aktualisieren einer Übermittlungserweiterung  
  
    -   Abrufen und Festlegen von Eigenschaften der Reporting Services-Anwendungsdatenbank, z. B. Timeout der Datenbank  
  
    -   Datenerweiterungen auflisten  
  
## <a name="reporting-services-object-model-and-powershell-samples"></a>Reporting Services-Objektmodell und Powershell-Beispiele  
 ![PowerShell-Inhalt](../media/rs-powershellicon.jpg "PowerShell-Inhalt")  
  
 PowerShell-Aufruf des Kern-Objektmodells und zum größten Teil gültig für SharePoint- und einheitlichen Modus, z. B. die Migrationsarbeit, Abonnementarbeit und weitere Beispiele für Abonnementarbeit in SQL15.  
  
-   [Verwenden Sie PowerShell, um Reporting Services Abonnement Besitzer zu ändern und aufzulisten und ein Abonnement auszuführen](../subscriptions/manage-subscription-owners-and-run-subscription-powershell.md).  
  
-   [Verwenden Sie PowerShell, um eine Azure-VM mit einem Berichts Server im einheitlichen Modus zu erstellen](https://msdn.microsoft.com/library/azure/dn449661.aspx).  
  
-   Weitere Informationen finden Sie im Abschnitt „Zugreifen auf die WMI-Klassen mit PowerShell“ unter [Zugreifen auf den Reporting Services-WMI-Anbieter](access-the-reporting-services-wmi-provider.md).  
  
-   [Verwalten von SSRS mit PowerShell](https://www.sqlshack.com/how-to-administer-sql-server-reporting-services-ssrs-subscriptions-using-powershell/). scriptin  
  
## <a name="rsexe-scripting-samples"></a>Skriptbeispiele für RS.exe  
  
-   [Beispiel Reporting Services Skript "Rs. exe" zum Migrieren von Inhalten Zwischenberichts Servern](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).  
  
-   Zusätzliche Skripts, Anwendungs- und Erweiterungsbeispiele finden Sie unter [SQL Server Reporting Services-Produktbeispiele](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Rs. exe-Hilfsprogramm &#40;SSRS&#41;](rs-exe-utility-ssrs.md)   
 [Skript Bereitstellungs-und Verwaltungsaufgaben](script-deployment-and-administrative-tasks.md)   
 [Skripterstellung mit dem Hilfsprogramm rs.exe und dem Webdienst](script-with-the-rs-exe-utility-and-the-web-service.md)  
  
  
