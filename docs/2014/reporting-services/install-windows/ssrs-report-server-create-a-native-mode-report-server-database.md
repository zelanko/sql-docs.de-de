---
title: Erstellen einer Berichtsserver-Datenbank im einheitlichen Modus (SSRS-Konfigurations-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], databases
- databases [Reporting Services], creating
ms.assetid: 81b9f4ad-800b-4688-8b47-a5a83dc8ff10
caps.latest.revision: 9
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 8ff6878b05138bb1ad4c23e57699dd896ab7b441
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37198822"
---
# <a name="create-a-native-mode-report-server-database--ssrs-configuration-manager"></a>Erstellen einer Berichtsserver-Datenbank im einheitlichen Modus (SSRS-Konfigurations-Manager)
  Der einheitliche Modus für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] verwendet eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank für den Zentralspeicher. Die Datenbank ist erforderlich und wird zum Speichern von veröffentlichten Berichten, Modellen, freigegebenen Datenquellen, Sitzungsdaten, Ressourcen und Servermetadaten verwendet.  
  
 Um eine Berichtsserver-Datenbank zu erstellen oder die Verbindungszeichenfolge oder die Anmeldeinformationen zu ändern, verwenden Sie die Optionen auf der Datenbankseite im [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Im einheitlichen Modus|  
  
## <a name="when-to-create-or-configure-the-report-server-databases"></a>Der richtige Zeitpunkt zum Erstellen bzw. Konfigurieren von Berichtsserver-Datenbanken  
 Sie müssen die Berichtsserver-Datenbank erstellen und konfigurieren, wenn Sie den Berichtsserver im Modus für die ausschließliche Installation von Dateien installiert haben.  
  
 Wenn Sie installiert [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] entweder in der Standardkonfiguration für den einheitlichen Modus, der Berichtsserver-Datenbank wurde erstellt und automatisch konfiguriert wird, wenn die Berichtsserver-Instanz installiert wurde. Mit dem [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager können Sie die von Setup automatisch konfigurierten Einstellungen anzeigen bzw. ändern.  
  
##  <a name="rsdbrequirements"></a> Vorbereitungen  
 Das Erstellen bzw. die Konfiguration einer Berichtsserver-Datenbank erfolgt in mehreren Schritten. Bevor Sie die Berichtsserver-Datenbank erstellen, sollten Sie sich überlegen, wie Sie die folgenden Elemente angeben möchten:  
  
 Datenbankserver auswählen  
 Überprüfen Sie die unterstützten Versionen der [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], und überprüfen Sie die unterstützten Editionen im Thema [Erstellen einer Berichtsserver-Datenbank &#40;SSRS-Konfigurations-Manager&#41;](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md).  
  
 TCP/IP-Verbindungen aktivieren  
 Aktivieren Sie TCP/IP-Verbindungen für das [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Bei einigen [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Editionen wird TCP/IP nicht standardmäßig aktiviert. In diesem Thema finden Sie Anweisungen.  
  
 Port für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] öffnen  
 Wenn Sie Firewallsoftware verwenden, müssen Sie bei einem Remoteserver den Port öffnen, auf dem der [!INCLUDE[ssDE](../../includes/ssde-md.md)] lauscht.  
  
 Berichtsserver-Anmeldeinformationen festlegen  
 Legen Sie fest, wie der Berichtsserver eine Verbindung mit den Berichtsserver-Datenbanken herstellen soll. Zu den Anmeldeinformations-Typen gehören das Domänenbenutzerkonto, das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank-Benutzerkonto und das Berichtsserver-Dienstkonto.  
  
 Diese Anmeldeinformationen werden verschlüsselt und in der Datei RSReportServer.config gespeichert. Der Berichtsserver verwendet diese Anmeldeinformationen für ausgehende Verbindungen zur Berichtsserver-Datenbank. Wenn Sie ein Windows-Benutzerkonto oder ein Datenbank-Benutzerkonto verwenden möchten, müssen Sie ein bereits bestehendes Konto angeben. Der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager erstellt zwar einen Benutzernamen für die Anmeldung und legt die erforderlichen Berechtigungen fest, erstellt jedoch kein Konto. Weitere Informationen finden Sie unter [Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).  
  
 Sprache für den Berichtsserver festlegen  
 Wählen Sie eine Sprache für den Berichtsserver aus. Vordefinierte Rollennamen, Beschreibungen und die Ordner vom Typ Meine Berichte werden nicht in verschiedenen Sprachen angezeigt, wenn sich die Benutzer mit verschiedenen Sprachversionen eines Browsers beim Server anmelden.  
  
 Anmeldeinformationen zum Erstellen und Bereitstellen der Datenbank überprüfen  
 Vergewissern Sie sich, dass Sie über Kontoanmeldeinformationen verfügen, die Berechtigungen zum Erstellen von Datenbanken auf der [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz aufweisen. Diese Anmeldeinformationen werden für eine einmalige Verbindung verwendet, die zum Erstellen der Berichtsserver-Datenbank und von **RSExecRole**dient. Wenn noch kein Benutzername für die Anmeldung vorhanden ist, wird ein Datenbank-Benutzername für das Konto erstellt, das vom Berichtsserver für die Verbindung mit der Datenbank verwendet wird. Sie können eine Verbindung unter dem [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Konto herstellen, mit dem Sie angemeldet sind, oder einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank-Benutzernamen verwenden.  
  
### <a name="to-enable-access-to-a-remote-report-server-database"></a>So aktivieren Sie den Zugriff auf eine Remoteberichtsserver-Datenbank  
  
1.  Wenn Sie eine [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Remote-Instanz verwenden, melden Sie sich beim Datenbankserver an, um TCP/IP-Verbindungen zu überprüfen bzw. zu aktivieren.  
  
2.  Zeigen Sie auf **Start**, auf **Alle Programme**, auf **Microsoft SQL Server**, dann auf **Konfigurationstools**, und klicken Sie dann auf **SQL Server-Konfigurations-Manager**.  
  
3.  Öffnen Sie **SQL Server-Netzwerkkonfiguration**.  
  
4.  Wählen Sie die Instanz aus.  
  
5.  Mit der rechten Maustaste **TCP/IP** , und klicken Sie auf **aktiviert**.  
  
6.  Starten Sie den Dienst neu.  
  
7.  Öffnen Sie die Firewallsoftware, und öffnen Sie den Port, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lauscht. Für die Standardinstanz ist dies normalerweise Port 1433 für TCP/IP-Verbindungen. Weitere Informationen zur Windows-Firewall finden Sie unter [Konfigurieren einer Windows-Firewall für Datenbank-Engine-Zugriff](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
### <a name="to-create-a-local-report-server-database"></a>So erstellen Sie eine lokale Berichtsserver-Datenbank  
  
1.  Starten Sie das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager, und stellen Sie eine Verbindung mit der Berichtsserverinstanz her, für die Sie die Datenbank erstellen. Weitere Informationen finden Sie unter [Reporting Services-Konfigurations-Manager &#40;einheitlicher Modus&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
2.  Doppelklicken Sie auf der Seite Datenbank auf **Datenbank ändern**.  
  
3.  Klicken Sie auf **Neue Berichtsserver-Datenbank erstellen**und dann auf **Weiter**.  
  
4.  Stellen Sie eine Verbindung mit der Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] her, die Sie zum Erstellen und Hosten der Berichtsserver-Datenbank verwenden möchten.  
  
    1.  Geben Sie die [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] -Instanz ein, die Sie verwenden möchten. Der Assistent zeigt eine lokale [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz an, die als Standardinstanz ausgeführt wird, sofern sie verfügbar ist. Andernfalls müssen Sie den Server und die Instanz eingeben, die verwendet werden sollen. Benannte Instanzen werden in folgendem Format angegeben: \<Servername>\\<Instanzenname\>.  
  
    2.  Geben Sie die Anmeldeinformationen ein, die für eine einmalige Verbindung mit [!INCLUDE[ssDE](../../includes/ssde-md.md)] verwendet werden, um die Berichtsserver-Datenbanken zu erstellen. Weitere Informationen zur Verwendung dieser Anmeldeinformationen finden Sie in diesem Thema unter [Vorbereitungen](#rsdbrequirements) .  
  
    3.  Klicken Sie auf **Verbindung testen** , um die Verbindung zum Server zu überprüfen.  
  
    4.  Klicken Sie auf **Weiter**.  
  
5.  Geben Sie Eigenschaften an, die zum Erstellen der Datenbank verwendet werden. Weitere Informationen zur Verwendung dieser Eigenschaften finden Sie in diesem Thema unter [Vorbereitungen](#rsdbrequirements) .  
  
    1.  Geben Sie den Namen der Berichtsserver-Datenbank ein. Daraufhin werden eine temporäre Datenbank und die primäre Datenbank erstellt. Verwenden Sie ggf. einen beschreibenden Namen, um sich besser daran erinnern zu können, wie die Datenbank verwendet wird. Bedenken Sie, dass der angegebene Name während der gesamten Lebensdauer der Datenbank verwendet wird. Eine erstellte Berichtsserver-Datenbank kann nicht mehr umbenannt werden.  
  
    2.  Wählen Sie die Sprache aus, in der die Rollendefinitionen und Meine Berichte angezeigt werden sollen.  
  
    3.  Der Berichtsservermodus wird immer auf **Einheitlich**festgelegt.  
  
    4.  Klicken Sie auf **Weiter**.  
  
6.  Geben Sie die Anmeldeinformationen an, die vom Berichtsserver zum Herstellen der Verbindung zur Berichtsserver-Datenbank verwendet werden.  
  
    1.  Geben Sie den Authentifizierungstyp an:  
  
         Wählen Sie **Datenbank-Anmeldeinformationen** aus, um die Verbindung mithilfe eines bereits definierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank-Benutzernamens herzustellen. Die Verwendung von Datenbank-Anmeldinformationen wird empfohlen, wenn der Berichtsserver sich auf einem Computer in einer anderen Domäne, einer nicht vertrauenswürdigen Domäne oder hinter einer Firewall befindet.  
  
         Wählen Sie **Windows-Anmeldeinformationen** , wenn Sie ein Domänenbenutzerkonto mit geringen Privilegien verwenden, das über die Berechtigung zur Anmeldung bei dem Computer und dem Datenbankserver verfügt.  
  
         Wählen Sie **Anmeldeinformationen des Diensts** , wenn der Berichtsserver die Verbindung mithilfe seines Dienstkontos herstellen soll. Mit dieser Option stellt der Server die Verbindung mit integrierter Sicherheit her; Anmeldeinformationen werden nicht verschlüsselt oder gespeichert.  
  
    2.  Klicken Sie auf **Weiter**.  
  
7.  Überprüfen Sie die Informationen über die Zusammenfassungsseite, um zu überprüfen, ob die Einstellungen korrekt sind, und klicken Sie dann auf **Weiter**.  
  
8.  Überprüfen Sie die Verbindung durch Klicken auf eine URL auf der Seite Berichtsserver-URL bzw. auf der Seite Berichts-Manager-URL. Die URLs müssen definiert werden, damit dieser Test funktioniert. Wenn die Verbindung zur Berichtsserverdatenbank gültig ist, werden entweder die Berichtsserver-Ordnerhierarchie oder der Berichts-Manager in einem Browser-Fenster angezeigt. Weitere Informationen finden Sie unter [Überprüfen einer Installation von Reporting Services](verify-a-reporting-services-installation.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren eine Berichtsserver-Datenbankverbindung &#40;SSRS-Konfigurations-Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)   
 [Datenbank &#40;einheitlicher SSRS-Modus&#41;](../../sql-server/install/database-ssrs-native-mode.md)   
 [Verwalten eines Reporting Services im einheitlichen Modus-Berichtsservers](../report-server/manage-a-reporting-services-native-mode-report-server.md)   
 [Reporting Services-Konfigurations-Manager &#40;einheitlicher Modus&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
