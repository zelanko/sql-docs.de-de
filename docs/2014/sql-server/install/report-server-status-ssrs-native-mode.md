---
title: Berichts Server Status (einheitlicher SSRS-Modus) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.serverstatus.F1
ms.assetid: 2f63ad1c-1bc2-449d-b451-fb39a0060838
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 15a177080792eb26273399f41aad577962885376
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952462"
---
# <a name="report-server-status-ssrs-native-mode"></a>Berichtsserverstatus (einheitlicher SSRS-Modus)
  Verwenden Sie diese Seite, um Informationen zur Berichtsserverinstanz anzuzeigen, mit der Sie derzeit verbunden sind. Diese Seite ist die Startseite für die Berichtsserverkonfiguration. Zusätzliche Seiten stehen zum Konfigurieren von URLs, des Dienstkontos, der Berichtsserver-Datenbank, der Berichtsserver-E-Mail-Übermittlung, der Bereitstellung für horizontales Skalieren und von Verschlüsselungsschlüsseln zur Verfügung.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 Zum Öffnen der Seite starten Sie den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager, und stellen Sie eine Verbindung mit der Berichtsserverinstanz her. Weitere Informationen finden Sie unter [Konfigurations-Manager für Reporting Services &#40;del&#41;](reporting-services-configuration-manager-native-mode.md).  
  
> [!TIP]  
>  Die[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager (rsconfigtool. exe) ist mit der Berechtigungsstufe "highestAvailable" installiert. Dieses Verhalten ist beabsichtigt. Der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager erfordert Kommunikation mit [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI-APIs. Ein Teil der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI-Kommunikation erfordert eine höhere Stufe oder Administratorprivilegien.  
  
 Wenn Sie eine Verbindung mit dem Berichtsserver herstellen und alle Seitenlinks ausgegraut sind, überprüfen Sie, ob der Berichtsserverdienst gestartet wurde. Der **Berichts Dienst Status** sollte "gestartet" lauten. Sie können den Dienststatus auch mithilfe der Konsolenanwendung Dienste in den Administratortools überprüfen.  
  
## <a name="options"></a>Tastatur  
 **SQL Server Instanz**  
 Zeigt Informationen zu der Berichtsserverinstanz an, mit der Sie derzeit verbunden sind. Die Namen von Berichtsserverinstanzen basieren auf benannten Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Der Name der Standardinstanz lautet MSSQLSERVER. Eine benannte Instanz ist ein Wert, den Sie während des Setups angegeben haben. Weitere Informationen zu-Instanzen finden Sie unter [Arbeiten mit mehreren Versionen und Instanzen von SQL Server](../../../2014/sql-server/install/work-with-multiple-versions-and-instances-of-sql-server.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Online Dokumentation.  
  
> [!NOTE]  
>  In SQL Server Express with Advanced Services ist die Standardinstanz SQLExpress.  
  
 **Instanz-ID**  
 Entspricht einem Ordner im Dateisystem für die Programmdateien der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, mit der Sie verbunden sind. Der Wert **Instanz-ID** wird vom Setup im Format *Komponente*.*Instanz*zugewiesen, wobei *Komponente* ein Wert ist, der für eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Komponente steht, und *Instanz* ist ein Instanzname. Der Name der Standardinstanz lautet MSSQLSERVER. Wenn Sie beispielsweise Standardinstanzen der Komponenten von [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]und [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installieren, lauten die entsprechenden Ordnernamen wie folgt:  
  
-   MSSQL12.MSSQLSERVER  
  
-   MSAS12.MSSQLSERVER  
  
-   MSRS12.MSSQLSERVER  
  
 Wenn Sie eine zweite Instanz einer bereits installierten Komponente installieren, z. b. die [!INCLUDE[ssDE](../../includes/ssde-md.md)], und Sie der Instanz den Namen "kontoso" nennen, ist die **Instanz-ID** "MSSQL12". Contoso.  
  
 **Edition**  
 Zeigt Editionsinformationen an. Eine Liste der Funktionen, die von den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Editionen unterstützt werden, finden Sie unter [Von den SQL Server-Editionen unterstützte Funktionen](https://go.microsoft.com/fwlink/?linkid=232473).  
  
 **Produktversion**  
 Zeigt die von Ihnen installierte Version von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] an.  
  
 **Berichtsserver-Datenbank**  
 Zeigt den Namen der Berichtsserver-Datenbank an, die Anwendungsdaten für die aktuelle Berichtsserverinstanz speichert.  
  
 **Berichts Server Modus**  
 Hier muss immer der Wert **Einheitlich**angezeigt werden. Der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager unterstützt nur Berichtsserver im einheitlichen Modus. Wenn der Wert von **Integrierter SharePoint-Modus**angezeigt wird, deutet dies möglicherweise darauf hin, dass Ihre Bereitstellung im einheitlichen Modus nicht ordnungsgemäß konfiguriert wurde und Sie eine Verbindung mit einem Berichtskatalog für den einheitlichen Modus herstellen müssen. Verwenden Sie die Seite **Datenbank** des Konfigurations-Managers, um die Datenbank zu ändern und um entweder eine neue Datenbank zu erstellen oder eine Verbindung zu einem vorhandenen Berichtsserver-Datenbankkatalog im einheitlichen Modus herzustellen.  
  
 **Serverstatus**  
 Zeigt an, ob der Berichtsserver-Dienst ausgeführt wird.  
  
 **Start**  
 Startet den Berichtsserver-Dienst. Nach einigen Konfigurationsänderungen ist es erforderlich, den Dienst neu zu starten (z.&nbsp;B. wenn ein Berichtsserver nach der Änderung eines Computernamens neu konfiguriert wird). Wenn Sie die URL-Reservierungen neu konfigurieren, startet der Dienst automatisch neu. Der Neustart ist erforderlich, um die Änderungen zu übernehmen.  
  
 **Stop** (Beenden)  
 Beendet den Berichtsserver-Dienst. Durch das Beenden des Diensts bricht der Berichtsserver seine Tätigkeit ab. Weitere Informationen finden Sie unter [starten und Abbrechen des Berichts Server-Dienstanbieter](../../reporting-services/report-server/start-and-stop-the-report-server-service.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Online Dokumentation.  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurations-Manager für Reporting Services F1-Hilfe &#40;Themen SSRS im&#41; einheitlichen Modus](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Konfigurations-Manager für Reporting Services &#40;del&#41; ](/sql/sql-server/install/reporting-services-configuration-manager-native-mode) -   
 [Initialisieren eines Berichtsservers &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md)  
  
  
