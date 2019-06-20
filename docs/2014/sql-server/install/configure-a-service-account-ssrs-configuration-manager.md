---
title: Konfigurieren eines Dienstkontos (SSRS-Konfigurations-Manager) | Microsoft-Dokumentation
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
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 84f6f2bdb4c5c512cb75dfea554b5ae28e3c3f02
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66096097"
---
# <a name="configure-a-service-account-ssrs-configuration-manager"></a>Konfigurieren eines Dienstkontos (SSRS-Konfigurations-Manager)
  In einer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Installation werden der Report Server-Webdienst, der Berichts-Manager und eine Hintergrundverarbeitungsanwendung innerhalb eines einzelnen Diensts ausgeführt. Das Konto, unter dem der Dienst ausgeführt wird, wird beim Setup definiert, wenn Sie das Konto auf der Seite für die Dienstidentität angeben. Wenn Sie ein anderes Konto verwenden oder das Kennwort aktualisieren möchten, können Sie jedoch das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Konfigurationstool verwenden.  
  
 Wenn Sie einen Berichtsserver, der zur Verwendung des integrierten SharePoint-Modus konfiguriert ist und Sie das Dienstkonto ändern, mit der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationstool, müssen Sie auch SharePoint-Zentraladministration öffnen und verwenden Sie die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  **Gewähren von Datenbankzugriff** Seite, um die Einstellungen für Server und die Instanz erneut anwenden. Dieser Schritt wird den neuen Dienstkontenzugriff auf die SharePoint-Datenbanken ist erforderlich, für die Integration von gewährt [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] mit [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] oder [!INCLUDE[SPS2010](../../includes/sps2010-md.md)].  
  
 Verwenden Sie zum Aktualisieren des Dienstkontos immer das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Konfigurationstool, sodass andere Einstellungen, die von der Dienstidentität abhängen, gleichzeitig aktualisiert werden können.  
  
> [!NOTE]  
>  Integrierte Windows-Dienstkonten (Lokaler Dienst oder Netzwerkdienst) werden auf einem Domänencontrollercomputer nicht als Berichtsserver-Dienstkonten unterstützt.  
  
 Vorgehensweisen  
  
### <a name="to-configure-the-report-server-service-account"></a>So konfigurieren Sie das Berichtsserver-Dienstkonto  
  
1.  Starten Sie den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager, und stellen Sie eine Verbindung mit dem Berichtsserver her.  
  
2.  Wählen Sie auf der Seite Dienstkontoseite die Option aus, die den gewünschten Kontotyp beschreibt. Empfehlungen zu welchen Kontotyp aus, um anzugeben, finden Sie unter [konfigurieren Sie die Berichtsserver-Dienstkontos &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md).  
  
3.  Wenn Sie ein Windows-Benutzerkonto ausgewählt haben, geben Sie das neue Konto und das Kennwort an. Der Kontoname darf nicht länger als 20 Zeichen sein.  
  
     Wenn der Berichtsserver in einem Netzwerk bereitgestellt wird, der die Kerberos-Authentifizierung unterstützt, müssen Sie den Berichtsserver-Dienstprinzipalnamen (Service Principal Name, SPN) mit dem Domänenbenutzerkonto registrieren, das Sie soeben angegeben haben. Weitere Informationen finden Sie unter [Registrieren eines Dienstprinzipalnamens (SPN) für einen Berichtsserver](../../reporting-services/report-server/register-a-service-principal-name-spn-for-a-report-server.md).  
  
4.  Klicken Sie auf **Anwenden**.  
  
5.  Geben Sie bei der Aufforderung zum Sichern des symmetrischen Schlüssels einen Dateinamen und einen Speicherort für die Sicherung des symmetrischen Schlüssels ein, geben Sie ein Kennwert zum Sperren und Entsperren der Datei ein, und klicken Sie auf **OK**.  
  
6.  Wenn der Berichtsserver die Verbindung zur Berichtsserver-Datenbank mithilfe des Dienstkontos erstellt, werden die Verbindungsinformationen auf das neue Konto oder Kennwort aktualisiert. Zum Aktualisieren der Verbindungsinformationen ist eine Verbindung mit der Datenbank erforderlich. Wenn das Dialogfeld für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **-Datenbankverbindung** angezeigt wird, geben Sie die Anmeldeinformationen ein, die zur Verbindung mit der Datenbank berechtigen, und klicken Sie anschließend auf **OK**.  
  
7.  Geben Sie bei der Aufforderung zum Wiederherstellen des symmetrischen Schlüssels das in Schritt 5 angegebene Kennwort ein, und klicken Sie auf **OK**.  
  
8.  Überprüfen Sie die Statusmeldungen im Ergebnisbereich, um zu überprüfen, ob alle Tasks erfolgreich abgeschlossen wurden.  
  
## <a name="troubleshooting-service-identity-update-errors"></a>Problembehandlung bei Fehlern beim Update der Dienstidentität  
 Durch Ändern der Dienstidentität wird eine Reihe von Ereignissen ausgelöst, einschließlich Neustart des Diensts, Aktualisieren des kennwortgeschützten Verschlüsselungsschlüssels, Aktualisieren von URL-Reservierungen und Aktualisieren der Verbindungsinformationen für die Berichtsserver-Datenbank, wenn Sie das Dienstkonto zum Herstellen der Verbindung zur Berichtsserver-Datenbank verwenden. Sie können den Status dieser Ereignisse überwachen, indem Sie die Benachrichtigungen im Ergebnisbereich unten auf der Seite anzeigen. Wenn während dieses Prozesses Fehler auftreten, können Sie versuchen, sie mit den folgenden Techniken zu beheben:  
  
-   Wenn der symmetrische Schlüssel nicht wiederhergestellt werden kann, können Sie versuchen, ihn manuell wiederherzustellen, indem Sie auf der Seite mit Verschlüsselungsschlüsseln auf **Wiederherstellen** klicken. Wenn das nicht funktioniert, erwägen Sie, den verschlüsselten Inhalt zu löschen. Sie müssen die Verbindungsinformationen und Abonnements für die Datenquelle neu erstellen, der übrige Inhalt ist jedoch weiterhin verfügbar. Weitere Informationen finden Sie unter [Back Up and Restore Reporting Services Encryption Keys](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md).  
  
-   Wird der Dienst nicht gestartet, starten Sie ihn manuell über die Dienstkonsolenanwendung in der Verwaltung.  
  
-   URL-Reservierungsfehler können auftreten, wenn Sie das Dienstkonto aktualisieren. Jede URL-Reservierung umfasst eine Sicherheitsbeschreibung mit einer freigegebenen Zugriffssteuerungsliste (Discretionary Access Control List, DACL), die das Dienstkonto berechtigt, Anforderungen für die URL zu akzeptieren. Wenn Sie das Konto aktualisieren, muss die URL erneut erstellt werden, um die DACL mit den neuen Kontoinformationen zu aktualisieren. Wenn die URL-Reservierung nicht neu erstellt werden kann und das Konto mit Sicherheit gültig ist, versuchen Sie, den Computer neu zu starten. Wenn der Fehler weiterhin auftritt, versuchen Sie, ein anderes Konto zu verwenden.  
  
## <a name="see-also"></a>Siehe auch  
 [Reporting Services-Konfigurations-Manager &#40;einheitlicher Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)   
 [Konfigurieren des Berichtsserver-Dienstkontos &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Konfigurieren einer Verbindung mit der Berichtsserver-Datenbank &#40;SSRS-Konfigurations-Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)   
 [Dienstkonto &#40;einheitlicher SSRS-Modus&#41;](../../../2014/sql-server/install/service-account-ssrs-native-mode.md)   
 [Konfigurieren und Verwalten von Verschlüsselungsschlüsseln &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-manage-encryption-keys.md)  
  
  
