---
title: Erstellen einer Berichtsserver-Datenbank (SSRS-Konfigurations-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], databases
- report server database
- databases [Reporting Services], creating
ms.assetid: 8a3a6ffe-4001-46be-8548-94532550f6a5
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: b18b94289516d1ba38be392a13438e3a38029c4a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48206270"
---
# <a name="create-a-report-server-database--ssrs-configuration-manager"></a>Erstellen einer Berichtsserver-Datenbank (SSRS-Konfigurations-Manager)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] **von** verwendet zwei relationale [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbanken, um Berichtsserver-Metadaten und -Objekte zu speichern. Eine Datenbank, die als primärer Speicher dient, und eine zweite Datenbank zum Speichern temporärer Daten. Die Datenbanken werden gemeinsam erstellt und sind durch ihre Namen aneinander gebunden. Bei einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Standardinstanz erhalten die Datenbanken die Namen `reportserver` und `reportservertempdb`. Zusammen werden die beiden Datenbanken als "Berichtsserver-Datenbank" oder "Berichtsserver-Katalog" bezeichnet.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] **von** schließt eine dritte Datenbank ein, die für Datenwarnungsmetadaten verwendet wird. Die drei Datenbanken werden für jede [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendung erstellt, und die Datenbanknamen enthalten standardmäßig einen GUID, der die Dienstanwendung darstellt. Im Folgenden finden Sie Beispielnamen der drei Datenbanken im SharePoint-Modus:  
  
-   ReportingService_90a9f37075544f22953c4a62e4a9f370  
  
-   ReportingService_90a9f37075544f22953c4a62e4a9f370TempDB  
  
-   ReportingService_90a9f37075544f22953c4a62e4a9f370_Alerting  
  
> [!IMPORTANT]  
>  Schreiben Sie keine Anwendungen, um Abfragen auf der Berichtsserver-Datenbank auszuführen. Die Berichtsserver-Datenbank ist kein öffentliches Schema. Die Tabellenstruktur kann sich von einer Version zur nächsten ändern. Verwenden Sie für den Zugriff auf die Berichtsserver-Datenbank stets [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -APIs, wenn Sie eine Anwendung schreiben, die auf die Berichtsserver-Datenbank zugreifen muss.  
>   
>  Dies gilt nicht für die Ausführungsprotokollsichten. Weitere Informationen finden Sie unter [Berichtsserver-Ausführungsprotokoll und die ExecutionLog3-Ansicht](../../reporting-services/report-server/report-server-executionlog-and-the-executionlog3-view.md)  
  
## <a name="ways-to-create-the-report-server-database"></a>Möglichkeiten zum Erstellen der Berichtsserver-Datenbank  
 **Einheitlicher Modus** : Sie können die Berichtsserver-Datenbank im einheitlichen Modus wie folgt erstellen:  
  
-   Automatisch: Verwenden Sie den Setup-Assistenten für SQL Server, wenn Sie die Installationsoption für die Standardkonfiguration auswählen. Im SQL Server-Installations-Assistenten ist dies die Option **Installieren und konfigurieren** auf der Seite Berichtsserver-Installationsoptionen. Wenn Sie die Option **Nur installieren** auswählen, müssen Sie die Datenbank mithilfe des Reporting Services-Konfigurations-Managers erstellen.  
  
-   Manuell: Verwenden Sie den Konfigurations-Manager für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Sie müssen die Berichtsserver-Datenbank manuell erstellen, wenn Sie zum Hosten der Datenbank Remote- [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] verwenden. Weitere Informationen finden Sie unter [Erstellen einer Berichtsserver-Datenbank im einheitlichen Modus (SSRS-Konfigurations-Manager)](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md).  
  
 **SharePoint-Modus** : Die Seite Berichtsserver-Installationsoptionen besitzt nur eine Option für den SharePoint-Modus von **Nur installieren**. Diese Option installiert alle [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dateien und den gemeinsamen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienst. Der nächste Schritt besteht darin mindestens eine [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendung in einer der folgenden Methoden zu erstellen:  
  
-   Verwenden Sie die SharePoint-Zentraladministration, um eine [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendung zu erstellen. Weitere Informationen finden Sie im Abschnitt "Dienstanwendung" [Schritt 3: Erstellen einer Reporting Services-Dienstanwendung](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md#bkmk_create_serrviceapplication).  
  
-   Verwenden Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -PowerShell-Cmdlets zum Erstellen einer Dienstanwendung und der Berichtsserver-Datenbanken. Weitere Informationen finden Sie im Beispiel für die Erstellung von dienstanwendungen im Thema [PowerShell-Cmdlets für Reporting Services SharePoint Mode](../../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md).  
  
## <a name="database-server-version-requirements"></a>Anforderungen für die Datenbankserver-Version  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird zum Hosten der Berichtsserver-Datenbanken verwendet. Die Instanz [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] kann eine lokale oder eine Remoteinstanz sein. Im Folgenden finden Sie die unterstützten Version von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , die zum Hosten der Berichtsserver-Datenbanken verwendet werden können.  
  
- SQLServer 2014
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005  
  
 Wenn Sie die Berichtsserver-Datenbank auf einem Remotecomputer erstellen, müssen Sie die Verbindung so konfigurieren, dass ein Domänenbenutzerkonto oder ein Dienstkonto mit Netzwerkzugriff verwendet wird. Wenn Sie eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Remoteinstanz verwenden, sollten Sie sorgfältig überlegen, welche Anmeldeinformationen der Berichtsserver für die Verbindung zur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz verwenden soll. Weitere Informationen finden Sie unter [Konfigurieren einer Berichtsserver-Datenbankverbindung &#40;SSRS-Konfigurations-Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).  
  
> [!IMPORTANT]  
>  Der Berichtsserver und die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, die die Berichtsserver-Datenbank hostet, können sich in verschiedenen Domänen befinden. Bei einer Internetbereitstellung ist es üblich, einen Server zu verwenden, der sich hinter einer Firewall befindet. Wenn Sie einen Berichtsserver für den Internetzugriff konfigurieren, sollten Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldeinformationen verwenden, um die Verbindung mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz hinter der Firewall herzustellen, und IPSec zum Schützen dieser Verbindung.  
  
## <a name="database-server-edition-requirements"></a>Anforderungen für die Datenbankserver-Edition  
 Wenn Sie eine Berichtsserver-Datenbank erstellen, sollten Sie beachten, dass nicht alle Editionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zum Hosten der Datenbank verwendet werden können. Weitere Informationen finden Sie im Abschnitt "Report Serveranforderungen Datenbankserver-Edition" [von den SQL Server 2014-Editionen unterstützte Funktionen](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Reporting Services-Konfigurations-Manager &#40;del&#41;](/sql/2014/sql-server/install/reporting-services-configuration-manager-native-mode)  
  
  
