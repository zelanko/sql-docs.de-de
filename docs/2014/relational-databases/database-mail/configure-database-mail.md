---
title: Konfigurieren des Datenbank-E-Mail-Features | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- Sql12.swb.sqlimail.newaccount.f1
- Sql12.swb.sqlimail.manageexistingaccount.f1
- Sql12.swb.dbmail.manageexistingaccount.f1
- Sql12.swb.sqlimail.manageexistingprofile.f1
- Sql12.swb.sqlimail.newprofile.f1
- Sql12.swb.sqlimail.profileandaccountmanagement.f1
- Sql12.swb.dbmail.configuresystem.f1
- Sql12.swb.dbmail.profileandaccountmanagement.f1
- Sql12.swb.dbmail. manageprofilesecurity.profileview.f1
- Sql12.swb.dbmail.selectconfiguration.f1
- Sql12.swb.dbmail.newsqlimailaccount.f1
- Sql12.swb.sqlimail.manageprofilesecurity.profileview.f1
- Sql12.swb.sqlimail.newsqlimailaccount.f1
- Sql12.swb.dbmail.newaccount.f1
- Sql12.swb.dbmail.manageexistingprofile.f1
- Sql12.swb.sqlimail.configuresystem.f1
- Sql12.swb.sqlimail.selectconfiguration.f1
- Sql12.swb.dbmail.completewizard.f1
- Sql12.swb.sqlimail.welcome.f1
- sql12.swb.dbmail.sendtestemail.f1
- Sql12.swb.sqlimail.addaccounttoprofile.f1
- Sql12.swb.dbmail.welcome.f1
- Sql12.swb.dbmail.newprofile.f1
- Sql12.swb.dbmail.addaccounttoprofile.f1
- sql12.swb.dbmail.sendtestemail.test.f1
- Sql12.swb.sqlimail.completewizard.f1
- Sql12.swb.sqlimail.manageprofilesecurity.principalview.f1
- Sql12.swb.dbmail.manageprofilesecurity.principalview.f1
ms.assetid: 7edc21d4-ccf3-42a9-84c0-3f70333efce6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e480363941d8928d270f978471b5474a8e24b0a1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68418881"
---
# <a name="configure-database-mail"></a>Konfigurieren des Datenbank-E-Mail-Features
  Dieses Thema beschreibt die Aktivierung und Konfiguration von Datenbank-E-Mails mithilfe des Assistenten zum Konfigurieren von Datenbank-E-Mails sowie die Erstellung eines Datenbank-E-Mail-Konfigurationsskripts anhand von Vorlagen.  
  

  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
 Verwenden Sie die Option **DatabaseMail XPs** , um Datenbank-E-Mail auf diesem Server zu aktivieren. Weitere Informationen finden Sie im Referenzthema [Database Mail XPs (Serverkonfigurationsoption)](../../database-engine/configure-windows/database-mail-xps-server-configuration-option.md) .  
  
###  <a name="Restrictions"></a> Einschränkungen  
 Zum Aktivieren von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service Broker in einer Datenbank ist eine Datenbanksperrung erforderlich. Wurde Service Broker in **msdb**deaktiviert, müssen Sie zum Aktivieren von Datenbank-E-Mails zuerst den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent beenden, damit Service Broker die erforderliche Sperre abrufen kann.  
  
###  <a name="Security"></a> Sicherheit  
 Sie müssen zum Konfigurieren von Datenbank-E-Mails ein Mitglied der festen Serverrolle **sysadmin** sein. Zum Senden von Datenbank-E-Mail muss der Benutzer ein Mitglied der **DatabaseMailUserRole** -Datenbankrolle in der **msdb** -Datenbank sein.  
  
##  <a name="SSMSProcedure"></a>Verwenden des Konfigurations-Assistenten für Datenbank-E-Mail  
 **So konfigurieren Sie Datenbank-E-Mail mithilfe eines Assistenten**  
  
1.  Erweitern Sie im Objekt-Explorer den Knoten für die Instanz, für die Sie Datenbank-E-Mails konfigurieren möchten.  
  
2.  Erweitern Sie den Knoten **Verwaltung** .  
  
3.  Klicken Sie mit der rechten Maustaste auf **Datenbank-E-Mail**, und klicken Sie dann auf **Datenbank-E-Mail konfigurieren**.  
  
4.  Abschließen der Dialogfelder des Assistenten  
  

  
  
  
###  <a name="Welcome"></a>Willkommensseite  
 Diese Seite beschreibt die Schritte zum Konfigurieren von Datenbank-E-Mails.  
  
 **Diese Seite nicht mehr anzeigen** : Aktivieren Sie diese Option, um zu überspringen, dass diese Willkommensseite in Zukunft angezeigt wird.  
  
 **Weiter** : wechselt zur Seite **Konfigurations Aufgabe auswählen** .  
  
 **Abbrechen** : beendet den Assistenten, ohne zu konfigurieren Datenbank-E-Mail  
  
 
  
###  <a name="ConfigTask"></a>Konfigurations Task auswählen  
 Geben Sie auf der Seite **Konfigurationsaufgabe auswählen** die Aufgabe an, die Sie bei jeder Verwendung des Assistenten ausführen. Wenn Sie Ihre Entscheidung vor dem Beenden des Assistenten ändern, können Sie mithilfe der Schaltfläche **Zurück** zu dieser Seite zurückkehren und eine andere Aufgabe auswählen.  
  
> [!NOTE]  
>  Wenn die Datenbank-E-Mail nicht aktiviert wurde, wird folgende Meldung angezeigt: **Die Datenbank-E-Mail-Funktion ist nicht verfügbar.  Möchten Sie dieses Feature aktivieren?** Die Auswahl von **Ja**entspricht der Aktivierung von Datenbank-E-Mails mit der [Database Mail XPs](../../database-engine/configure-windows/database-mail-xps-server-configuration-option.md) -Option der gespeicherten Systemprozedur **sp_configure** .  
  
 **Richten Sie Datenbank-E-Mail ein, indem Sie die folgenden Aufgaben ausführen:**  
 Führt alle Aufgaben durch, die zum ersten Einrichten der Datenbank-E-Mails erforderlich sind. Diese Option umfasst alle anderen drei Optionen.  
  
 **Verwalten von Datenbank-E-Mail Konten und Profilen**  
 Erstellt neue Datenbank-E-Mail-Konten und -Profile oder ändert oder löscht vorhandene Datenbank-E-Mail-Konten und -Profile oder zeigt diese an.  
  
 **Profil Sicherheit verwalten**  
 Konfiguriert, welche Benutzer Zugriff auf Datenbank-E-Mail-Profile haben.  
  
 **Anzeigen oder Ändern von Systemparametern**  
 Konfiguriert Datenbank-E-Mail-Systemparameter wie die maximale Dateigröße für Anlagen.  
  

  
###  <a name="NewAccount"></a>Seite "neues Konto"  
 Auf dieser Seite können Sie ein neues Konto für Datenbank-E-Mails erstellen. Ein Konto für Datenbank-E-Mails enthält Informationen für das Senden von E-Mails an einen SMTP-Server.  
  
 Ein Konto für Datenbank-E-Mails enthält Informationen, mit deren Hilfe von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] E-Mail-Nachrichten an einen SMTP-Server gesendet werden. Jedes Konto enthält Informationen für einen E-Mail-Server.  
  
 Ein Konto für Datenbank-E-Mail wird nur für Datenbank-E-Mail verwendet. Ein Konto für Datenbank-E-Mail entspricht nicht einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konto oder einem Microsoft Windows-Konto. Datenbank-E-Mail kann mit den Anmeldeinformationen von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], mit von Ihnen angegebenen Anmeldeinformationen oder anonym gesendet werden. Bei Verwendung der Standardauthentifizierung werden der Benutzername und das Kennwort in einem Konto für Datenbank-E-Mail nur für die Authentifizierung beim E-Mail-Server verwendet. Ein Konto muss keinem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Benutzer oder einem Benutzer auf dem Computer entsprechen, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ausgeführt wird.  
  
 **Kontoname**  
 Geben Sie den Namen des neuen Kontos ein.  
  
 **Beschreibung**  
 Geben Sie eine Beschreibung des Kontos ein. Die Angabe einer Beschreibung ist optional.  
  
 **E-Mail Adresse**  
 Geben Sie den Namen der E-Mail-Adresse für das Konto ein. Dies ist die E-Mail-Adresse, von der aus E-Mails versendet werden. Ein Konto für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent könnte E-Mails beispielsweise von der Adresse SqlAgent@Adventure-Works.com aus versenden.  
  
 **Anzeige Name**  
 Geben Sie den Namen ein, der in den von diesem Konto aus versendeten E-Mail-Nachrichten angezeigt wird. Der angezeigte Name ist optional. Es handelt sich dabei um den Namen, der in den von diesem Konto versendeten Nachrichten angezeigt wird. Ein Konto für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] könnte beispielsweise den Namen "SQL Server Agent Automated Mailer" in den E-Mail-Nachrichten anzeigen.  
  
 **Antworten auf e-Mail**  
 Geben Sie die E-Mail-Adresse ein, die für Antworten auf E-Mail-Nachrichten aus diesem Konto verwendet wird. Der Eintrag für die Antwort-E-Mail ist optional. Antworten auf ein Konto von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent könnten beispielsweise an den Datenbankadministrator gehen, danw@Adventure-Works.com.  
  
 **Servername**  
 Geben Sie den Namen oder die IP-Adresse des SMTP-Servers ein, der von diesem Konto zum Senden von E-Mails verwendet wird. In der Regel hat dies ein ähnliches Format `smtp.` wie *<YOUR_COMPANY>* `.com`. Informationen hierzu erhalten Sie von Ihrem E-Mail-Administrator.  
  
 **Port Nummer**  
 Geben Sie die Portnummer des SMTP-Servers für dieses Konto ein. Die meisten SMTP-Server verwenden Port 25.  
  
 **Dieser Server erfordert eine sichere Verbindung (SSL).**  
 Verschlüsselt die Kommunikation mit SSL (Secure Sockets Layer).  
  
 **Windows-Authentifizierung mithilfe von Datenbank-Engine-Dienst Anmelde Informationen**  
 Die Verbindung mit dem SMTP-Server wird mithilfe der für den Dienst [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] konfigurierten Anmeldeinformationen hergestellt.  
  
 **Standardauthentifizierung**  
 Geben Sie den für den SMTP-Server erforderlichen Benutzernamen und das Kennwort ein.  
  
 **Benutzername**  
 Geben Sie den Benutzernamen ein, mit dem Datenbank-E-Mail sich beim SMTP-Server anmeldet. Der Benutzername ist erforderlich, wenn der SMTP-Server die Standardauthentifizierung erfordert.  
  
 **Kennwort**  
 Geben Sie das Kennwort ein, mit dem Datenbank-E-Mail sich beim SMTP-Server anmeldet. Das Kennwort ist erforderlich, wenn der SMTP-Server die Standardauthentifizierung erfordert.  
  
 **Kennwort bestätigen**  
 Geben Sie das Kennwort zur Bestätigung erneut ein. Das Kennwort ist erforderlich, wenn der SMTP-Server die Standardauthentifizierung erfordert.  
  
 **Anonyme Authentifizierung**  
 E-Mail wird ohne Anmeldeinformationen an den SMTP-Server gesendet. Verwenden Sie diese Option, wenn für den SMTP-Server keine Authentifizierung erforderlich ist.  
  
 
  
###  <a name="ExistingAccount"></a>Seite "vorhandenes Konto verwalten"  
 Mithilfe dieser Seite können Sie ein vorhandenes Datenbank-E-Mail-Konto verwalten.  
  
 **Kontoname**  
 Wählen Sie hier den Kontonamen aus, der angezeigt, aktualisiert oder gelöscht werden soll.  
  
 **Löschen**  
 Löscht das ausgewählte Konto. Sie müssen dieses Konto aus zugeordneten Profilen entfernen oder diese Profile löschen, bevor Sie das ausgewählte Konto löschen.  
  
 **Beschreibung**  
 In diesem Bereich können Sie die Beschreibung des Kontos anzeigen oder bearbeiten. Die Angabe einer Beschreibung ist optional.  
  
 **E-Mail Adresse**  
 Hier können Sie den Namen der E-Mail-Adresse für das Konto anzeigen oder aktualisieren. Dies ist die E-Mail-Adresse, von der aus E-Mails versendet werden. Beispielsweise kann ein Konto für Microsoft SQL Server-Agent e-Mail von der Adresse **SqlAgent@Adventure-Works.com**senden.  
  
 **Anzeige Name**  
 Hier können Sie den Namen anzeigen oder bearbeiten, der in den von diesem Konto aus versendeten E-Mail-Nachrichten angezeigt wird. Der angezeigte Name ist optional. Es handelt sich dabei um den Namen, der in den von diesem Konto versendeten Nachrichten angezeigt wird. Ein Konto für SQL Server Agent könnte beispielsweise den Namen **SQL Server Agent Automated Mailer** in den E-Mails anzeigen.  
  
 **Antworten auf e-Mail**  
 Hier können Sie die E-Mail-Adresse anzeigen und bearbeiten, die für Antworten auf E-Mail-Nachrichten für dieses Konto verwendet wird. Der Eintrag für die Antwort-E-Mail ist optional. Antworten auf ein Konto für SQL Server-Agent können z. b. an den Datenbankadministrator **danw@Adventure-Works.com**weitergeleitet werden.  
  
 **Servername**  
 Hier können Sie den Namen des SMTP-Servernamens anzeigen und bearbeiten, der zum Senden von E-Mail von diesem Konto verwendet wird. Normalerweise hat der Eintrag ein ähnliches Format wie **smtp.<Ihr_Unternehmen>.com**. Informationen hierzu erhalten Sie von Ihrem E-Mail-Administrator.  
  
 **Port Nummer**  
 Hier können Sie die Portnummer des SMTP-Servers für dieses Konto anzeigen und bearbeiten. Die meisten SMTP-Server verwenden Port 25.  
  
 **Dieser Server erfordert eine sichere Verbindung (SSL).**  
 Verschlüsselt die Kommunikation mit SSL (Secure Sockets Layer).  
  
 **Windows-Authentifizierung mithilfe von Datenbank-Engine-Dienst Anmelde Informationen**  
 Die Verbindung mit dem SMTP-Server wird mithilfe der für den Dienst [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] konfigurierten Anmeldeinformationen hergestellt.  
  
 **Standardauthentifizierung**  
 Geben Sie den für den SMTP-Server erforderlichen Benutzernamen und das Kennwort ein.  
  
 **Benutzername**  
 Hier können Sie den Benutzernamen anzeigen und bearbeiten, mit dem die Datenbank-E-Mail sich beim SMTP-Server anmeldet. Der Benutzername ist erforderlich, wenn der SMTP-Server die Standardauthentifizierung erfordert.  
  
 **Kennwort**  
 Ändert das Kennwort, mit dem die Datenbank-E-Mail sich beim SMTP-Server anmeldet. Das Kennwort ist erforderlich, wenn der SMTP-Server die Standardauthentifizierung erfordert.  
  
 **Kennwort bestätigen**  
 Geben Sie das Kennwort zur Bestätigung erneut ein. Das Kennwort ist erforderlich, wenn der SMTP-Server die Standardauthentifizierung erfordert.  
  
 **Anonyme Authentifizierung**  
 E-Mail wird ohne Anmeldeinformationen an den SMTP-Server gesendet. Verwenden Sie diese Option, wenn für den SMTP-Server keine Authentifizierung erforderlich ist.  
  

  
###  <a name="NewProfile"></a>Seite "neues Profil"  
 Auf dieser Seite können Sie ein Profil für Datenbank-E-Mails erstellen. Ein Datenbank-E-Mail-Profil ist eine Auflistung von Datenbank-E-Mail-Konten. In Fällen, wo ein E-Mail-Server nicht erreichbar ist, sorgen Profile für mehr Zuverlässigkeit, indem sie alternative Datenbank-E-Mail-Konten bereitstellen. Es ist mindestens ein Datenbank-E-Mail-Konto erforderlich. Weitere Informationen zum Festlegen der Prioritäten von Datenbank-E-Mail-Konten im Profil finden Sie unter [Create a Database Mail Profile](create-a-database-mail-profile.md).  
  
 Mithilfe der Schaltflächen **Nach oben** und **Nach unten** ändern Sie die Reihenfolge, in der die Datenbank-E-Mail-Konten verwendet werden. Diese Reihenfolge wird durch einen Wert namens Sequenznummer festgelegt. Nach **oben** senkt die Sequenznummer und **nach unten** erhöht die Sequenznummer. Über die Sequenznummer wird die Reihenfolge festgelegt, in der Konten im Profil von Datenbank-E-Mail verwendet werden. Für eine neue E-Mail-Nachricht beginnt Datenbank-E-Mail mit dem Konto mit der niedrigsten Sequenznummer. Wenn dieses Konto fehlschlägt, verwendet Datenbank-E-Mail das Konto mit der nächsthöheren Sequenznummer usw., bis entweder Datenbank-E-Mail die Nachricht erfolgreich versendet oder das Konto mit der höchsten Sequenznummer fehlschlägt. Wenn das Konto mit der höchsten Sequenznummer fehlschlägt, unterbricht Datenbank-E-Mail den Versuch, die E-Mail zu versenden, für den Zeitraum, der im Datenbank-E-Mail-Parameter **AccountRetryDelay** festgelegt ist. Verwenden Sie den **AccountRetryAttempts** -Parameter, um zu konfigurieren, wie oft der externe Mailprozess versuchen soll, die E-Mail mithilfe der einzelnen Konten des angegebenen Profils zu versenden. Sie können die Parameter **AccountRetryDelay** und **AccountRetryAttempts** auf der Seite **Systemparameter konfigurieren** des Assistenten zum Konfigurieren von Datenbank-E-Mail konfigurieren.  
  
 **Profilname**  
 Geben Sie einen Namen für das neue Profil ein. Das Profil wird mit diesem Namen erstellt. Verwenden Sie nicht den Namen eines bereits vorhandenen Profils.  
  
 **Beschreibung**  
 Geben Sie eine Beschreibung für das Profil ein. Die Angabe einer Beschreibung ist optional.  
  
 **SMTP-Konten**  
 Wählen Sie für das Profil eines oder mehrere Konten aus. Die Priorität legt die Reihenfolge fest, in der Konten von Datenbank-E-Mail verwendet werden. Wenn keine Konten aufgelistet werden, müssen Sie zum Fortfahren auf **Hinzufügen** klicken und dann ein neues SMTP-Konto hinzufügen.  
  
 **Add (Hinzufügen)**  
 Hinzufügen eines Kontos zum Profil.  
  
 **Remove**  
 Entfernen des ausgewählten Kontos aus dem Profil.  
  
 **Nach oben**  
 Erhöhen Sie die Priorität des ausgewählten Kontos.  
  
 **Nach unten**  
 Verringern Sie die Priorität des ausgewählten Kontos.  
  

  
###  <a name="ExistingProfile"></a>Seite "vorhandenes Profil verwalten"  
 Mit dieser Seite können Sie ein vorhandenes Datenbank-E-Mail-Profil verwalten. Ein Datenbank-E-Mail-Profil ist eine Auflistung von Datenbank-E-Mail-Konten. In Fällen, wo ein E-Mail-Server nicht erreichbar ist, sorgen Profile für mehr Zuverlässigkeit, indem sie alternative Datenbank-E-Mail-Konten bereitstellen. Es ist mindestens ein Datenbank-E-Mail-Konto erforderlich. Weitere Informationen zum Festlegen der Prioritäten von Datenbank-E-Mail-Konten im Profil finden Sie unter [Create a Database Mail Profile](create-a-database-mail-profile.md).  
  
 Mithilfe der Schaltflächen **Nach oben** und **Nach unten** ändern Sie die Reihenfolge, in der die Datenbank-E-Mail-Konten verwendet werden. Diese Reihenfolge wird durch einen Wert namens Sequenznummer festgelegt. Nach **oben** senkt die Sequenznummer und **nach unten** erhöht die Sequenznummer. Über die Sequenznummer wird die Reihenfolge festgelegt, in der Konten im Profil von Datenbank-E-Mail verwendet werden. Für eine neue E-Mail-Nachricht beginnt Datenbank-E-Mail mit dem Konto mit der niedrigsten Sequenznummer. Wenn dieses Konto fehlschlägt, verwendet Datenbank-E-Mail das Konto mit der nächsthöheren Sequenznummer usw., bis entweder Datenbank-E-Mail die Nachricht erfolgreich versendet oder das Konto mit der höchsten Sequenznummer fehlschlägt. Wenn das Konto mit der höchsten Sequenznummer fehlschlägt, unterbricht Datenbank-E-Mail den Versuch, die E-Mail zu versenden, für den Zeitraum, der im Datenbank-E-Mail-Parameter **AccountRetryDelay** festgelegt ist. Verwenden Sie den **AccountRetryAttempts** -Parameter, um zu konfigurieren, wie oft der externe Mailprozess versuchen soll, die E-Mail mithilfe der einzelnen Konten des angegebenen Profils zu versenden. Sie können die Parameter **AccountRetryDelay** und **AccountRetryAttempts** auf der Seite **Systemparameter konfigurieren** des Assistenten zum Konfigurieren von Datenbank-E-Mail konfigurieren.  
  
 **Profilname**  
 Wählen Sie den Namen des zu verwaltenden Profils aus.  
  
 **Löschen**  
 Löscht das ausgewählte Profil. Sie werden aufgefordert, **Ja** auszuwählen, um das ausgewählte Profil zu löschen und nicht gesendete Nachrichten abzubrechen, oder **Nein** auszuwählen, um das ausgewählte Profil nur zu löschen, wenn keine ungesendeten Nachrichten vorhanden sind.  
  
 **Beschreibung**  
 Zeigen Sie die Beschreibung des ausgewählten Profils an oder ändern Sie diese. Die Angabe einer Beschreibung ist optional.  
  
 **SMTP-Konten**  
 Wählen Sie für das Profil eines oder mehrere Konten aus. Die Failoverpriorität legt die Reihenfolge fest, in der Datenbank-E-Mail die Konten bei einem Failover verwendet.  
  
 **Add (Hinzufügen)**  
 Hinzufügen eines Kontos zum Profil.  
  
 **Remove**  
 Entfernen des ausgewählten Kontos aus dem Profil.  
  
 **Nach oben**  
 Erhöht die Failoverpriorität des ausgewählten Kontos.  
  
 **Nach unten**  
 Verringert die Failoverpriorität des ausgewählten Kontos.  
  
 **Haben**  
 Anzeigen der aktuellen Failoverpriorität des Kontos.  
  
 **Kontoname**  
 Anzeigen des Namens des Kontos.  
  
 **E-Mail Adresse**  
 Anzeigen der E-Mail-Adresse des Kontos.  
  

  
###  <a name="AddAccount"></a>Seite "Konto zum Profil hinzufügen"  
 Verwenden Sie diese Seite, um das dem Profil hinzuzufügende Konto auszuwählen. Wählen Sie ein vorhandenes Konto aus dem Feld **Kontoname** , oder klicken Sie auf **Neues Konto**.  
  
 **Kontoname**  
 Wählen Sie den Namen des Kontos aus, das Sie dem Profil hinzufügen möchten.  
  
 **E-Mail Adresse**  
 Zeigt die E-Mail-Adresse des ausgewählten Kontos an. Sie können die E-Mail-Adresse auf dieser Seite nicht ändern. Gehen Sie zum Ändern der E-Mail-Adresse zurück zur Hauptseite des Assistenten, und wählen Sie die Option **Konten und Profile für Datenbank-E-Mail verwalten** aus.  
  
 **Servername**  
 Zeigt den Namen des Mailservers des ausgewählten Kontos an. Sie können den Servernamen auf dieser Seite nicht ändern. Gehen Sie zum Ändern des Servernamens für das Konto zurück zur Hauptseite des Assistenten, und wählen Sie die Option **Konten und Profile für Datenbank-E-Mail verwalten** aus.  
  
 **Neues Konto**  
 Erstellt ein neues Konto.  
  

  
###  <a name="AccountsProfiles"></a>Seite "Konten und Profile verwalten"  
 Verwenden Sie diese Seite, um eine Aufgabe zum Verwalten eines Profils oder Kontos auszuwählen.  
  
 **Erstellen eines neuen Kontos**  
 Erstellt ein neues Konto.  
  
 **Vorhandenes Konto anzeigen, ändern oder löschen**  
 Verwaltet oder löscht ein vorhandenes Konto.  
  
 **Erstellen eines neuen Profils**  
 Erstellt ein neues Profil.  
  
 **Vorhandenes Profil anzeigen, ändern oder löschen. Sie können auch Konten verwalten, die dem Profil zugeordnet sind.**  
 Aktualisiert oder löscht ein vorhandenes Profil. Mit dieser Option können Sie außerdem Konten verwalten, die dem Profil zugeordnet sind.  
  

  
###  <a name="ProfileSecurityPublic"></a>Profil Sicherheit verwalten, Registerkarte "öffentlich"  
 Verwenden Sie diese Seite zum Konfigurieren eines öffentlichen Profils.  
  
 Profile sind entweder öffentlich oder privat. Auf ein privates Profil können nur bestimmte Benutzer oder Rollen zugreifen. Mit einem öffentlichen Profil kann jeder Benutzer oder jede Rolle mit Zugriff auf die Mailhostdatenbank (**msdb**) E-Mails mithilfe dieses Profils senden.  
  
 Ein Profil kann ein Standardprofil sein. In diesem Fall können Benutzer oder Rollen E-Mails mithilfe des Profils senden, ohne das Profil explizit anzugeben. Falls der Benutzer oder die Rolle, die/der die E-Mail-Nachricht sendet, über ein privates Standardprofil verfügt, verwendet Datenbank-E-Mail dieses Profil. Verfügt der Benutzer oder die Rolle nicht über ein privates Standardprofil, verwendet **sp_send_dbmail** das öffentliche Standardprofil für die **msdb** -Datenbank. Falls weder ein privates Standardprofil für den Benutzer oder die Rolle noch ein öffentliches Standardprofil für die Datenbank vorhanden ist, gibt **sp_send_dbmail** einen Fehler zurück. Nur ein Profil kann als Standardprofil gekennzeichnet werden.  
  
 **Publikums**  
 Wählen Sie diese Option aus, um das angegebene Profil als öffentliches Profil festzulegen.  
  
 **Profile Name (Profilname)**  
 Zeigt den Namen des Profils an.  
  
 **Standardprofil**  
 Wählen Sie diese Option aus, um das angegebene Profil als Standardprofil festzulegen.  
  
 **Nur vorhandene öffentliche Profile anzeigen**  
 Wählen Sie diese Option aus, um nur öffentliche Profile in der angegebenen Datenbank anzuzeigen.  
  

  
###  <a name="ProfileSecurityPrivate"></a>Profil Sicherheit verwalten, Registerkarte "Privat"  
 Verwenden Sie diese Seite zum Konfigurieren eines privaten Profils.  
  
 Profile sind entweder öffentlich oder privat. Auf ein privates Profil können nur bestimmte Benutzer oder Rollen zugreifen. Mit einem öffentlichen Profil kann jeder Benutzer oder jede Rolle mit Zugriff auf die Mailhostdatenbank (**msdb**) E-Mails mithilfe dieses Profils senden.  
  
 Ein Profil kann ein Standardprofil sein. In diesem Fall können Benutzer oder Rollen E-Mails mithilfe des Profils senden, ohne das Profil explizit anzugeben. Falls der Benutzer oder die Rolle, die/der die E-Mail-Nachricht sendet, über ein privates Standardprofil verfügt, verwendet Datenbank-E-Mail dieses Profil. Verfügt der Benutzer oder die Rolle nicht über ein privates Standardprofil, verwendet **sp_send_dbmail** das öffentliche Standardprofil für die **msdb** -Datenbank. Falls weder ein privates Standardprofil für den Benutzer oder die Rolle noch ein öffentliches Standardprofil für die Datenbank vorhanden ist, gibt **sp_send_dbmail** einen Fehler zurück.  
  
 **Benutzername**  
 Wählen Sie in der **msdb** -Datenbank einen Benutzer oder eine Rolle aus.  
  
 **zugreifen**  
 Wählen Sie aus, ob der Benutzer oder die Rolle Zugriff auf das angegebene Profil hat.  
  
 **Profilname**  
 Zeigen Sie den Namen des Profils an.  
  
 **Ist Standardprofil**  
 Wählen Sie aus, ob das Profil das Standardprofil für den Benutzer oder die Rolle ist. Jeder Benutzer oder jede Rolle kann nur über ein Standardprofil verfügen.  
  
 **Nur vorhandene private Profile für diesen Benutzer anzeigen**  
 Wählen Sie diese Option aus, um nur Profile anzuzeigen, auf die der angegebene Benutzer oder die angegebene Rolle bereits Zugriff hat.  
  

  
###  <a name="SystemParameters"></a>System Parameter konfigurieren  
 Verwenden Sie diese Seite, um Systemparameter für die Datenbank-E-Mail festzulegen. Zeigen Sie die Systemparameter und den aktuellen Wert der einzelnen Parameter an. Wählen Sie einen Parameter aus, um eine kurze Beschreibung im Informationsbereich anzuzeigen.  
  
 **Wiederholungs Versuche für das Konto**  
 Gibt an, wie oft der externe E-Mail-Prozess versucht, die E-Mail-Nachricht zu senden, wobei jedes Konto im angegebenen Profil verwendet wird.  
  
 **Wiederholungs Verzögerung für das Konto (Sekunden)**  
 Gibt die Zeitdauer in Sekunden an, die der externe E-Mail-Prozess nach dem Versuch, eine Nachricht mithilfe aller Konten im Profil zu übermitteln, warten soll, bevor er alle Konten erneut ausprobiert.  
  
 **Maximale Dateigröße (Bytes)**  
 Die maximale Größe einer Anlage in Bytes.  
  
 **Nicht zulässige Erweiterungen für Anlagen Dateien**  
 Eine durch Trennzeichen getrennte Liste mit Erweiterungen, die nicht als Anlagen einer E-Mail-Nachricht gesendet werden können. Klicken Sie auf die Schaltfläche zum Durchsuchen (**...**), um zusätzliche Erweiterungen hinzuzufügen.  
  
 **Minimale Lebensdauer der Datenbank-E-Mail ausführbaren Datei (Sekunden)**  
 Gibt an, wie lange (in Sekunden) der externe E-Mail-Prozess mindestens aktiv bleibt. Der Prozess bleibt aktiv, solange sich E-Mails in der Datenbank-E-Mail-Warteschlange befinden. Dieser Parameter gibt die Zeitdauer an, für die der Prozess aktiv bleibt, wenn keine Nachrichten zum Verarbeiten vorhanden sind.  
  
 **Protokolliergrad**  
 Gibt an, welche Nachrichten im Datenbank-E-Mail-Protokoll aufgezeichnet werden. Die folgenden Werte sind möglich:  
  
-   Normal - Nur Fehler werden protokolliert.  
  
-   Erweitert - Fehler, Warnungen und Informationsmeldungen werden protokolliert.  
  
-   Ausführlich - Fehler, Warnungen, Informationsmeldungen, Erfolgsmeldungen und zusätzliche interne Meldungen werden protokolliert. Verwenden Sie die ausführliche Protokollierung für die Problembehandlung.  
  
 Standardwert: Erweitert.  
  
 **Alle zurücksetzen**  
 Aktivieren Sie diese Option, um die Werte auf der Seite auf die Standardwerte zurückzusetzen.  
  

  
###  <a name="CompleteWizard"></a>Assistenten Seite beenden  
 Mithilfe dieser Seite können Sie die Aktionen überprüfen, die der **Assistent zum Konfigurieren von Datenbank-E-Mail** ausführt. Bis zum Abschließen des Assistenten werden keine Änderungen angewendet.  
  

  
###  <a name="TestEmail"></a>E-Mail-Test Seite senden  
 Verwenden Sie die Seite **Test-e-Mail senden von** _<instance_name>_ , um eine E-Mail mit dem angegebenen Datenbank-E-Mail Profil zu senden. Nur Mitglieder der festen Serverrolle **sysadmin** können Test-E-Mails über diese Seite senden.  
  
 **Datenbank-E-Mail Profil**  
 Wählen Sie aus der Liste ein Datenbank-E-Mail-Profil aus. Dies ist ein Pflichtfeld. Wenn keine Profile angezeigt werden, gibt es keine Profile, oder Sie haben für ein Profil keine Berechtigung. Verwenden Sie den **Assistent zum Konfigurieren von Datenbank-E-Mail** zum Erstellen und Konfigurieren von Profilen. Wenn keine Profile angezeigt werden, erstellen Sie mithilfe des Assistenten zum Konfigurieren von Datenbank-E-Mail ein Profil für die eigene Verwendung.  
  
 **An**  
 Die E-Mail-Adresse der Nachrichtenempfänger. Mindestens ein Empfänger muss angegeben werden.  
  
 **Betreff**  
 Die Betreffzeile für die Test-E-Mail. Ändern Sie den Standardbetreff, damit Sie Ihre E-Mail bei der Problembehandlung besser identifizieren können.  
  
 **Instanz**  
 Der Text der Test-E-Mail. Ändern Sie den Standardbetreff, damit Sie Ihre E-Mail bei der Problembehandlung besser identifizieren können.  
  
 Das Dialogfeld **Test-E-Mail von Datenbank-E-Mail** bestätigt, dass die Datenbank-E-Mail versuchte, die Testnachricht zu senden, und stellt die **mailitem_id** für die Test-E-Mail bereit. Fragen Sie beim Empfänger nach, ob die E-Mail angekommen ist. E-Mails werden normalerweise in wenigen Minuten empfangen. Aufgrund einer geringen Netzwerkleistung, eines Rückstands an Nachrichten beim Mailserver oder wenn der Server vorübergehend nicht erreichbar ist, kann es jedoch zu Verzögerungen beim E-Mail-Empfang kommen. Verwenden Sie die **mailitem_id** zur Problembehandlung.  
  
 **Gesendete e-Mail**  
 Die **mailitem_id** der Test-E-Mail.  
  
 **Problembehandlung**  
 Klicken Sie, um die Onlinedokumentation für das Thema [Problembehandlung bei Datenbank-E-Mail](https://msdn.microsoft.com/library/ms188663.aspx)zu öffnen.  
  

  
##  <a name="Template"></a>Verwenden von Vorlagen  
 **So erstellen Sie ein Datenbank-E-Mail Konfigurationsskript**  
  
1.  Wählen Sie im Menü **Ansicht** den **Vorlagen-Explorer**aus.  
  
2.  Erweitern Sie im Fenster **Vorlagen-Explorer** den Ordner **Database Mail** .  
  
3.  Doppelklicken Sie auf **Simple Database Mail Configuration**. Die Vorlage wird in einem neuen Abfragefenster geöffnet.  
  
4.  Wählen Sie im Menü **Abfrage** die Option **Werte für Vorlagenparameter angeben**aus. Das Fenster **Vorlagenparameter ersetzen** wird geöffnet.  
  
5.  Geben Sie die Werte für **profile_name**, **account_name**, **SMTP_servername**, **email_address**und **display_name**ein. SQL Server Management Studio füllt die Vorlage mit den von Ihnen angegebenen Werten aus.  
  
6.  Führen Sie das Skript aus, damit die Konfiguration erstellt wird.  
  
7.  Das Skript gewährt keinem Datenbankbenutzer den Zugriff auf das Profil. Aus diesem Grund kann das Profil standardmäßig nur durch Mitglieder der festen Sicherheitsrolle **sysadmin** verwendet werden. Weitere Informationen zum Gewähren des Zugriffs auf Profile finden Sie unter [sysmail_add_principalprofile_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-principalprofile-sp-transact-sql).  
  
  
