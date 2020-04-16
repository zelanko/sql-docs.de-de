---
title: Konfigurieren eines Dienstkontos (SSRS Configuration Manager) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Report Server Web service, accounts
- service accounts [Reporting Services]
- Report Server Windows service, accounts
- Web service [Reporting Services], report server
ms.assetid: 25000ad5-3f80-4210-8331-d4754dc217e0
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 04dff943d1227f84ff514e593f65c2ce4d7a918f
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2020
ms.locfileid: "71952583"
---
# <a name="configure-a-service-account-ssrs-configuration-manager"></a>Konfigurieren eines Dienstkontos (SSRS-Konfigurations-Manager)
  In einer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Installation werden der Report Server-Webdienst, der Berichts-Manager und eine Hintergrundverarbeitungsanwendung innerhalb eines einzelnen Diensts ausgeführt. Das Konto, unter dem der Dienst ausgeführt wird, wird beim Setup definiert, wenn Sie das Konto auf der Seite für die Dienstidentität angeben. Wenn Sie ein anderes Konto verwenden oder das Kennwort aktualisieren möchten, können Sie jedoch das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Konfigurationstool verwenden.  
  
 Wenn Sie über einen Berichtsserver verfügen, der für die Verwendung des integrierten [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint-Modus konfiguriert ist, und Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] das Dienstkonto mithilfe des Konfigurationstools ändern, müssen Sie auch die SharePoint-Zentraladministration öffnen und die Seite **Datenbankzugriff gewähren** verwenden, um die Berichtsserver- und Instanzeinstellungen erneut anzuwenden. Dieser Schritt gewährt dem neuen Dienstkonto Zugriff auf die SharePoint-Datenbanken, die für die Integration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] mit [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] oder [!INCLUDE[SPS2010](../../includes/sps2010-md.md)]erforderlich sind.  
  
 Verwenden Sie zum Aktualisieren des Dienstkontos immer das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Konfigurationstool, sodass andere Einstellungen, die von der Dienstidentität abhängen, gleichzeitig aktualisiert werden können.  
  
> [!NOTE]  
>  Integrierte Windows-Dienstkonten (Lokaler Dienst oder Netzwerkdienst) werden auf einem Domänencontrollercomputer nicht als Berichtsserver-Dienstkonten unterstützt.  
  
 Prozeduren  
  
### <a name="to-configure-the-report-server-service-account"></a>So konfigurieren Sie das Berichtsserver-Dienstkonto  
  
1.  Starten Sie den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager, und stellen Sie eine Verbindung mit dem Berichtsserver her.  
  
2.  Wählen Sie auf der Seite Dienstkontoseite die Option aus, die den gewünschten Kontotyp beschreibt. Empfehlungen zu dem anzugebenden Kontotyp finden Sie unter [Konfigurieren des Berichtsserverdienstkontos &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md).  
  
3.  Wenn Sie ein Windows-Benutzerkonto ausgewählt haben, geben Sie das neue Konto und das Kennwort an. Der Kontoname darf nicht länger als 20 Zeichen sein.  
  
     Wenn der Berichtsserver in einem Netzwerk bereitgestellt wird, der die Kerberos-Authentifizierung unterstützt, müssen Sie den Berichtsserver-Dienstprinzipalnamen (Service Principal Name, SPN) mit dem Domänenbenutzerkonto registrieren, das Sie soeben angegeben haben. Weitere Informationen finden Sie unter [Registrieren eines Dienstprinzipalnamens (SPN) für einen Berichtsserver](../../reporting-services/report-server/register-a-service-principal-name-spn-for-a-report-server.md).  
  
4.  Klicken Sie auf **Anwenden**.  
  
5.  Geben Sie bei der Aufforderung zum Sichern des symmetrischen Schlüssels einen Dateinamen und einen Speicherort für die Sicherung des symmetrischen Schlüssels ein, geben Sie ein Kennwert zum Sperren und Entsperren der Datei ein, und klicken Sie auf **OK**.  
  
6.  Wenn der Berichtsserver die Verbindung zur Berichtsserver-Datenbank mithilfe des Dienstkontos erstellt, werden die Verbindungsinformationen auf das neue Konto oder Kennwort aktualisiert. Zum Aktualisieren der Verbindungsinformationen ist eine Verbindung mit der Datenbank erforderlich. Wenn in  das Dialogfeld für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Datenbankverbindung** angezeigt wird, geben Sie die Anmeldeinformationen ein, mit denen Sie eine Verbindung mit der Datenbank herstellen können, und klicken Sie anschließend auf **OK**.  
  
7.  Geben Sie bei der Aufforderung zum Wiederherstellen des symmetrischen Schlüssels das in Schritt 5 angegebene Kennwort ein, und klicken Sie auf **OK**.  
  
8.  Überprüfen Sie die Statusmeldungen im Ergebnisbereich, um zu überprüfen, ob alle Tasks erfolgreich abgeschlossen wurden.  
  
## <a name="troubleshooting-service-identity-update-errors"></a>Problembehandlung bei Fehlern beim Update der Dienstidentität  
 Durch Ändern der Dienstidentität wird eine Reihe von Ereignissen ausgelöst, einschließlich Neustart des Diensts, Aktualisieren des kennwortgeschützten Verschlüsselungsschlüssels, Aktualisieren von URL-Reservierungen und Aktualisieren der Verbindungsinformationen für die Berichtsserver-Datenbank, wenn Sie das Dienstkonto zum Herstellen der Verbindung zur Berichtsserver-Datenbank verwenden. Sie können den Status dieser Ereignisse überwachen, indem Sie die Benachrichtigungen im Ergebnisbereich unten auf der Seite anzeigen. Wenn während dieses Prozesses Fehler auftreten, können Sie versuchen, sie mit den folgenden Techniken zu beheben:  
  
-   Wenn der symmetrische Schlüssel nicht wiederhergestellt werden kann, können Sie versuchen, ihn manuell wiederherzustellen, indem Sie auf der Seite mit Verschlüsselungsschlüsseln auf **Wiederherstellen** klicken. Wenn das nicht funktioniert, erwägen Sie, den verschlüsselten Inhalt zu löschen. Sie müssen die Verbindungsinformationen und Abonnements für die Datenquelle neu erstellen, der übrige Inhalt ist jedoch weiterhin verfügbar. Weitere Informationen finden Sie unter [Back Up and Restore Reporting Services Encryption Keys](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md).  
  
-   Wird der Dienst nicht gestartet, starten Sie ihn manuell über die Dienstkonsolenanwendung in der Verwaltung.  
  
-   URL-Reservierungsfehler können auftreten, wenn Sie das Dienstkonto aktualisieren. Jede URL-Reservierung umfasst eine Sicherheitsbeschreibung mit einer freigegebenen Zugriffssteuerungsliste (Discretionary Access Control List, DACL), die das Dienstkonto berechtigt, Anforderungen für die URL zu akzeptieren. Wenn Sie das Konto aktualisieren, muss die URL erneut erstellt werden, um die DACL mit den neuen Kontoinformationen zu aktualisieren. Wenn die URL-Reservierung nicht neu erstellt werden kann und das Konto mit Sicherheit gültig ist, versuchen Sie, den Computer neu zu starten. Wenn der Fehler weiterhin auftritt, versuchen Sie, ein anderes Konto zu verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Reporting Services Configuration Manager &#40;nativer Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)   
 [Konfigurieren des Berichtsserverdienstkontos &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Konfigurieren einer Berichtsserverdatenbankverbindung &#40;SSRS Configuration Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)   
 [Dienstkonto &#40;SSRS Native Mode&#41;](../../../2014/sql-server/install/service-account-ssrs-native-mode.md)   
 [Konfigurieren und Verwalten von Verschlüsselungsschlüsseln &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-manage-encryption-keys.md)  
  
  
