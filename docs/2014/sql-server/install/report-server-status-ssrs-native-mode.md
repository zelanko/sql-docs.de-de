---
title: Melden des Serverstatus (einheitlicher SSRS-Modus) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.serverstatus.F1
ms.assetid: 2f63ad1c-1bc2-449d-b451-fb39a0060838
caps.latest.revision: 14
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 8cf6558824461b0de36323f1788933a0cd01815c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37292220"
---
# <a name="report-server-status-ssrs-native-mode"></a>Berichtsserverstatus (einheitlicher SSRS-Modus)
  Verwenden Sie diese Seite, um Informationen zur Berichtsserverinstanz anzuzeigen, mit der Sie derzeit verbunden sind. Diese Seite ist die Startseite für die Berichtsserverkonfiguration. Zusätzliche Seiten stehen zum Konfigurieren von URLs, des Dienstkontos, der Berichtsserver-Datenbank, der Berichtsserver-E-Mail-Übermittlung, der Bereitstellung für horizontales Skalieren und von Verschlüsselungsschlüsseln zur Verfügung.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im einheitlichen Modus.  
  
 Zum Öffnen der Seite starten Sie den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Konfigurations-Manager, und stellen Sie eine Verbindung mit der Berichtsserverinstanz her. Weitere Informationen finden Sie unter [Konfigurations-Manager für Reporting Services &#40;del&#41;](/sql/2014/sql-server/install/reporting-services-configuration-manager-native-mode).  
  
> [!TIP]  
>  Die[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager (RSConfigTool.exe) ist mit "HighestAvailable" Privilegstufe installiert. Dieses Verhalten ist beabsichtigt. Der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Konfigurations-Manager erfordert Kommunikation mit [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI-APIs. Ein Teil der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI-Kommunikation erfordert eine höhere Stufe oder Administratorprivilegien.  
  
 Wenn Sie eine Verbindung mit dem Berichtsserver herstellen und alle Seitenlinks ausgegraut sind, überprüfen Sie, ob der Berichtsserverdienst gestartet wurde. Der **Berichtsdienststatus** sollte "Gestartet" lauten. Sie können den Dienststatus auch mithilfe der Konsolenanwendung Dienste in den Administratortools überprüfen.  
  
## <a name="options"></a>Tastatur  
 **SQL Server-Instanz**  
 Zeigt Informationen zu der Berichtsserverinstanz an, mit der Sie derzeit verbunden sind. Namen von Berichtsserverinstanzen basieren auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] benannte Instanzen. Der Name der Standardinstanz lautet MSSQLSERVER. Eine benannte Instanz ist ein Wert, den Sie während des Setups angegeben haben. Weitere Informationen zu Instanzen finden Sie unter [Verwenden mehrerer Versionen und Instanzen von SQL Server](../../../2014/sql-server/install/work-with-multiple-versions-and-instances-of-sql-server.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
> [!NOTE]  
>  In SQL Server Express with Advanced Services ist die Standardinstanz SQLExpress.  
  
 **Instanz-ID**  
 Entspricht einem Ordner im Dateisystem für die Programmdateien der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz, mit der Sie verbunden sind. Die **Instanz-ID** Wert im Format durch das Setup zugewiesen *Komponente*. *Instanz*, wobei *Komponente* ist ein Wert, der angibt, ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Komponente und *Instanz* ist ein Instanzname. Der Name der Standardinstanz lautet MSSQLSERVER. Beispielsweise wird bei der Installation von Standardinstanzen von der [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], und [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Komponenten, die entsprechenden Ordnernamen sind die folgenden:  
  
-   MSSQL12.MSSQLSERVER  
  
-   MSAS12.MSSQLSERVER  
  
-   MSRS12.MSSQLSERVER  
  
 Wenn Sie eine zweite Instanz einer Komponente, die Sie bereits installieren, wie z. B. installiert die [!INCLUDE[ssDE](../../includes/ssde-md.md)], und Sie die Instanz Contoso nennen, die **Instanz-ID** MSSQL12 ist. Contoso.  
  
 **Edition**  
 Zeigt Editionsinformationen an. Eine Liste der Funktionen, die von den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Editionen unterstützt werden, finden Sie unter [Von den SQL Server-Editionen unterstützte Funktionen](http://go.microsoft.com/fwlink/?linkid=232473).  
  
 **Produktversion**  
 Zeigt die Version der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , die Sie installiert.  
  
 **Berichtsserver-Datenbank**  
 Zeigt den Namen der Berichtsserver-Datenbank an, die Anwendungsdaten für die aktuelle Berichtsserverinstanz speichert.  
  
 **Berichtsserver-Modus**  
 Hier muss immer der Wert **Einheitlich**angezeigt werden. Die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager unterstützt nur Berichtsserver im einheitlichen Modus. Wenn der Wert von **Integrierter SharePoint-Modus**angezeigt wird, deutet dies möglicherweise darauf hin, dass Ihre Bereitstellung im einheitlichen Modus nicht ordnungsgemäß konfiguriert wurde und Sie eine Verbindung mit einem Berichtskatalog für den einheitlichen Modus herstellen müssen. Verwenden Sie die Seite **Datenbank** des Konfigurations-Managers, um die Datenbank zu ändern und um entweder eine neue Datenbank zu erstellen oder eine Verbindung zu einem vorhandenen Berichtsserver-Datenbankkatalog im einheitlichen Modus herzustellen.  
  
 **Serverstatus**  
 Zeigt an, ob der Berichtsserver-Dienst ausgeführt wird.  
  
 **Start**  
 Startet den Berichtsserver-Dienst. Nach einigen Konfigurationsänderungen ist es erforderlich, den Dienst neu zu starten (z.&nbsp;B. wenn ein Berichtsserver nach der Änderung eines Computernamens neu konfiguriert wird). Wenn Sie die URL-Reservierungen neu konfigurieren, startet der Dienst automatisch neu. Der Neustart ist erforderlich, um die Änderungen zu übernehmen.  
  
 **Beenden**  
 Beendet den Berichtsserver-Dienst. Durch das Beenden des Diensts bricht der Berichtsserver seine Tätigkeit ab. Weitere Informationen finden Sie unter [starten und Beenden des Berichtsserverdiensts](../../reporting-services/report-server/start-and-stop-the-report-server-service.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
## <a name="see-also"></a>Siehe auch  
 [Reporting Services-Konfigurations-Manager-F1-Hilfethemen &#40;einheitlicher SSRS-Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Reporting Services-Konfigurations-Manager &#40;del&#41;](/sql/2014/sql-server/install/reporting-services-configuration-manager-native-mode)   
 [Initialisieren eines Berichtsservers &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md)  
  
  
