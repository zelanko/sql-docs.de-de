---
title: Häufig auftretende Probleme bei Launchpad
description: Dieser Artikel enthält eine Anleitung zur Fehlerbehebung für viele Probleme, die das Starten des SQL Server Trusted Launchpad-Diensts verhindern, wie Konfigurationsprobleme bzw. -änderungen oder fehlende Netzwerkprotokolle.
ms.prod: sql
ms.technology: ''
ms.date: 07/30/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 68c731767a83acbd4b7df84843f2c140c5a63d3e
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "73727712"
---
# <a name="common-issues-with-launchpad-service-and-external-script-execution-in-sql-server"></a>Häufige Probleme mit dem Launchpad-Dienst und der Ausführung externer Skripts in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Der SQL Server Trusted Launchpad-Dienst unterstützt die Ausführung externer Skripts für R und Python. 

Verschiedene Ursachen können den Start von Launchpad verhindern. Dazu gehören Konfigurationsprobleme bzw. -änderungen oder fehlende Netzwerkprotokolle. Dieser Artikel enthält eine Anleitung zur Fehlerbehebung für viele Probleme. Sollten dennoch Lösungen zu Problemen fehlen, können Sie im [Machine Learning Server-Forum](https://social.msdn.microsoft.com/Forums/home?category=MicrosoftR) Fragen stellen.

## <a name="determine-whether-launchpad-is-running"></a>Feststellen, ob Launchpad ausgeführt wird

1. Öffnen Sie den Bereich **Dienste** (Services.msc). Oder geben Sie in der Befehlszeile **SQLServerManager13.msc** oder **SQLServerManager14.msc** ein, um [SQL Server-Konfigurations-Manager](https://docs.microsoft.com/sql/relational-databases/sql-server-configuration-manager) zu öffnen.

2. Notieren Sie sich das Dienstkonto, unter dem Launchpad ausgeführt wird. Jede Instanz, in der R oder Python aktiviert ist, sollte über eine eigene Instanz des Launchpad-Diensts verfügen. Der Dienst für eine benannte Instanz kann beispielsweise einen Namen wie _MSSQLLaunchpad$InstanceName_ aufweisen.

3. Wenn der Dienst gestoppt wird, starten Sie ihn neu. Beim Neustart wird bei Konfigurationsproblemen eine Meldung im Systemereignisprotokoll veröffentlicht und der Dienst wieder gestoppt. Im Systemereignisprotokoll finden Sie Details darüber, warum der Dienst gestoppt wurde.

4. Überprüfen Sie den Inhalt der RSetup.log-Datei, und stellen Sie sicher, dass das Setup keine Fehler enthält. Die Meldung *Beenden mit Code 0* zeigt beispielsweise an, dass der Dienst nicht gestartet werden konnte.

5. Wenn Sie nach anderen Fehlern suchen möchten, überprüfen Sie den Inhalt der rlauncher.log-Datei.

## <a name="check-the-launchpad-service-account"></a>Überprüfen des Launchpad-Dienstkontos

Das Standarddienstkonto kann „NT Service\$SQL2016“ oder „NT Service\$SQL2017“ sein. Der letzte Teil kann je nach Name Ihrer SQL Server-Instanz variieren.

Der Launchpad-Dienst (Launchpad.exe) wird über ein Konto mit niedriger Berechtigung ausgeführt. Um R und Python zu starten und mit der Datenbankinstanz zu kommunizieren, benötigt das Launchpad-Dienstkonto jedoch die folgenden Benutzerrechte:

- Anmelden als Dienst (SeServiceLogonRight)
- Ersetzen von Token auf Prozessebene (SeAssignPrimaryTokenPrivilege)
- Umgehen von durchsuchenden Prüfungen (SeChangeNotifyPrivilege)
- Anpassen von Speicherkontingenten für einen Prozess (SeIncreaseQuotaSizePrivilege)

Weitere Informationen zu diesen Benutzerrechten finden Sie im Abschnitt „Windows-Berechtigungen und Rechte“ in [Konfigurieren von Windows-Dienstkonten und -Berechtigungen](../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).

> [!TIP]
> Wenn Sie mit der Verwendung des Tools Support Diagnostics Platform (SDP) für die SQL Server-Diagnose vertraut sind, können Sie mit SDP die Ausgabedatei mit dem Namen „MachineName_UserRights.txt“ überprüfen.

## <a name="user-group-for-launchpad-cannot-log-on-locally"></a>Benutzergruppe für Launchpad kann sich nicht lokal anmelden.

Während der Einrichtung von Machine Learning Services erstellt SQL Server die Windows-Benutzergruppe **SQLRUserGroup**. Diese erhält dann alle Berechtigungen, die für Launchpad erforderlich sind, um eine Verbindung zu SQL Server herzustellen und externe Skripts auszuführen. Wenn diese Benutzergruppe aktiviert ist, wird sie auch zum Ausführen von Python-Skripts verwendet.

In Unternehmen, in denen restriktivere Sicherheitsrichtlinien durchgesetzt werden, wurden die für diese Gruppe erforderlichen Berechtigungen jedoch möglicherweise manuell entfernt oder sie werden automatisch durch Richtlinien widerrufen. Wenn die Berechtigungen entfernt wurden, kann sich Launchpad nicht mehr mit der SQL Server-Instanz verbinden, und SQL Server kann die externe Laufzeit nicht aufrufen.

Stellen Sie sicher, dass die Gruppe **SQLRUserGroup** über die Systemberechtigung **Allow Log in locally**  (Lokale Anmeldung erlauben) verfügt, um dieses Problem zu beheben.

Weitere Informationen finden Sie unter [Konfigurieren von Windows-Dienstkonten und -Berechtigungen](../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).

## <a name="permissions-to-run-external-scripts"></a>Berechtigungen zum Ausführen externer Skripts

Selbst wenn Launchpad korrekt konfiguriert ist, gibt es einen Fehler zurück, wenn der Benutzer keine Berechtigung zum Ausführen von R- oder Python-Skripten hat.

Wenn Sie SQL Server als Datenbankadministrator oder Datenbankbesitzer installiert haben, wird Ihnen diese Berechtigung automatisch erteilt. Andere Benutzer haben jedoch in der Regel eingeschränktere Berechtigungen. Bei dem Versuch, ein R-Skript auszuführen, wird ein Launchpad-Fehler angezeigt.

Um das Problem zu beheben, kann ein Sicherheitsadministrator in SQL Server Management Studio die SQL-Anmeldeinformationen oder das Windows-Benutzerkonto ändern, indem das folgende Skript ausgeführt wird:

```sql
GRANT EXECUTE ANY EXTERNAL SCRIPT TO <username>
```

Weitere Informationen finden Sie unter [GRANT (Transact-SQL)](../t-sql/statements/grant-transact-sql.md).

## <a name="common-launchpad-errors"></a>Häufig auftretende Launchpad-Fehler

In diesem Abschnitt werden die häufigsten Fehlermeldungen aufgeführt, die in Launchpad angezeigt werden.

::: moniker range=">=sql-server-2016||=sqlallproducts-allversions"
## <a name="unable-to-launch-runtime-for-r-script"></a>„Laufzeit für R-Skript kann nicht gestartet werden“

Wenn sich die Windows-Gruppe für R-Benutzer (oder auch für Python) nicht bei der Instanz anmelden kann, auf der R Services ausgeführt wird, werden Ihnen möglicherweise die folgenden Fehler angezeigt:

- Fehler, die beim Ausführen von R-Skripten auftreten:

    * *Laufzeit für 'R'-Skript kann nicht gestartet werden. Überprüfen Sie die Konfiguration der 'R'-Laufzeit.*

    * *Ein externer Skriptfehler ist aufgetreten. Laufzeit kann nicht gestartet werden.*

- Vom [!INCLUDE[rsql_launchpad](../includes/rsql-launchpad-md.md)]-Dienst generierte Fehlermeldungen:

    * *Fehler beim Initialisieren des Startprogramms RLauncher.dll*

    * *Keine Startprogramm-DLLs registriert!*

    * *Sicherheitsprotokolle weisen darauf hin, dass das Konto NT SERVICE sich nicht anmelden konnte.*

Informationen, wie Sie dieser Benutzergruppe die notwendigen Berechtigungen erteilen können, finden Sie unter [Installieren von SQL Server R Services](install/sql-r-services-windows-install.md).

> [!NOTE]
> Diese Einschränkung gilt nicht, wenn Sie SQL-Benutzernamen verwenden, um von einer Remotearbeitsstation R-Skripts auszuführen.
::: moniker-end

## <a name="logon-failure-the-user-has-not-been-granted-the-requested-logon-type"></a>„Fehler bei der Anmeldung: Dem Benutzer wurde der angeforderte Anmeldetyp nicht zugewiesen.“

[!INCLUDE[rsql_launchpad_md](../includes/rsql-launchpad-md.md)] verwendet standardmäßig das nachfolgende Konto beim Start: `NT Service\MSSQLLaunchpad`. Das Konto wird beim [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)]-Setup konfiguriert, um über alle erforderlichen Berechtigungen zu verfügen.

Wenn Sie Launchpad ein anderes Konto zuordnen oder die Berechtigung durch eine Richtlinie auf dem SQL Server-Computer entfernt wurde, verfügt das Konto möglicherweise nicht über die erforderlichen Berechtigungen, und Sie erhalten ggf. folgenden Fehler:

>*ERROR_LOGON_TYPE_NOT_GRANTED 1385 (0x569) 	Anmeldung fehlgeschlagen: Der Benutzer besitzt nicht den benötigten Anmeldetyp auf diesem Computer.*

Um die erforderlichen Berechtigungen für das neue Dienstkonto hinzuzufügen, verwenden Sie die Anwendung „Local Security Policy“ (Lokale Sicherheitsrichtlinie), und aktualisieren Sie die Berechtigungen für das Konto dahingehend, dass es die folgenden Berechtigungen umfasst:

+ Anpassen des Arbeitsspeicherkontingents für einen Prozess (SeIncreaseQuotaPrivilege)
+ Umgehen von durchsuchenden Prüfungen (SeChangeNotifyPrivilege)
+ Anmelden als Dienst (SeServiceLogonRight)
+ Ersetzen von Token auf Prozessebene (SeAssignPrimaryTokenPrivilege)

## <a name="unable-to-communicate-with-the-launchpad-service"></a>„Kommunikation mit dem Launchpad-Dienst nicht möglich.“

Wenn Sie die Machine Learning-Komponente installiert und dann aktiviert haben, aber beim Versuch, ein R- oder Python-Skript auszuführen, diese Fehlermeldung erhalten, ist der Launchpad-Dienst für die Instanz möglicherweise gestoppt worden.

1. Öffnen Sie SQL Server Configuration Manager von Eingabeaufforderung aus. Weitere Informationen finden Sie unter [SQL Server Configuration Manager](https://docs.microsoft.com/sql/relational-databases/sql-server-configuration-manager).

2. Klicken Sie mit der rechten Maustaste auf den Launchpad-Dienst für die SQL Server-Instanz, und klicken Sie dann auf **Eigenschaften**.

3. Klicken Sie auf die Registerkarte **Dienst**, und überprüfen Sie, ob der Dienst ausgeführt wird. Wenn dem nicht so ist, ändern Sie den **Startmodus** in **Automatisch**, und klicken Sie auf **Anwenden**.

4. Durch den Neustart des Diensts wird das Problem in der Regel behoben, sodass Machine Learning-Skripts ausgeführt werden können. Wenn das Problem durch den Neustart nicht behoben werden kann, notieren Sie den Pfad und die Argumente in der Eigenschaft **Binärer Pfad**, und führen Sie die folgenden Schritte aus:

    a. Überprüfen Sie die Konfigurationsdatei des Launchers, und stellen Sie sicher, dass das Arbeitsverzeichnis gültig ist.

    b. Stellen Sie sicher, dass die von Launchpad verwendete Windows-Gruppe eine Verbindung mit der SQL Server-Instanz herstellen kann.

    c. Starten Sie den Launchpad-Dienst neu, wenn Sie Änderungen an den Diensteinstellungen vorgenommen haben.

## <a name="fatal-error-creation-of-tmpfile-failed"></a>„Schwerwiegender Fehler bei Erstellung von tmpFile“

In diesem Szenario haben Sie die Machine Learning-Funktionen erfolgreich installiert, und Launchpad wird ausgeführt. Sie versuchen, einen einfachen R- oder Python-Code auszuführen, aber Launchpad schlägt mit einem Fehler wie dem folgenden fehl: 

>*Fehler beim Kommunizieren mit der Runtime für das R-Skript. Überprüfen Sie die Anforderungen der R-Runtime.*

Gleichzeitig schreibt die Laufzeit des externen Skripts die folgende Meldung als Teil der STDERR-Meldung: 

>*Schwerwiegender Fehler: Erstellung von tmpfile fehlgeschlagen.*

Diese Fehlermeldung gibt an, dass das Konto, das Launchpad zu verwenden versucht, keine Berechtigung für die Anmeldung bei der Datenbank hat. Diese Situation kann auftreten, wenn strenge Sicherheitsrichtlinien implementiert sind. Um festzustellen, ob dies der Fall ist, überprüfen Sie die SQL Server-Protokolle und ob das Konto MSSQLSERVER01 bei der Anmeldung abgelehnt wurde. Die gleichen Informationen werden in den Protokollen bereitgestellt, die spezifisch für R\_SERVICES oder PYTHON\_SERVICES sind. Suchen Sie nach der Datei „ExtLaunchError.log“.

Standardmäßig sind 20 Konten eingerichtet und dem Launchpad.exe-Prozess mit den Namen MSSQLSERVER01 bis MSSQLSERVER20 zugeordnet. Wenn Sie R oder Python häufig verwenden, können Sie die Anzahl der Konten erhöhen.

Zur Behebung des Problems stellen Sie sicher, dass die Gruppe über Berechtigungen vom Typ *Lokal anmelden zulassen* für die lokale Instanz verfügt, in der Machine Learning-Funktionen installiert und aktiviert wurden. In einigen Umgebungen kann diese Berechtigungsstufe eine GPO-Ausnahme durch den Netzwerkadministrator erfordern.

## <a name="not-enough-quota-to-process-this-command"></a>„Nicht genug Kontingent, um diesen Befehl zu verarbeiten.“

Dieser Fehler kann mehrere Ursachen haben:

- Launchpad hat möglicherweise nicht genügend externe Benutzer, um die externe Abfrage auszuführen. Wenn Sie beispielsweise mehr als 20 externe Abfragen gleichzeitig ausführen und es nur 20 Standardbenutzer gibt, können Abfragen fehlschlagen.

- Es steht nicht genügend Speicher zur Verfügung, um die R-Task zu verarbeiten. Dieser Fehler tritt am häufigsten in einer Standardumgebung auf, in der SQL Server bis zu 70 Prozent der Computerressourcen in Anspruch nehmen kann. Informationen darüber, wie Sie die Serverkonfiguration ändern können, um eine stärkere Ressourcennutzung durch R zu unterstützen, finden Sie unter [Operationalisieren Ihres R-Codes](r/operationalizing-your-r-code.md).

## <a name="cant-find-package"></a>„Paket kann nicht gefunden werden.“

Wenn Sie R-Code in SQL Server ausführen und diese Meldung erhalten, aber die Meldung nicht erhalten haben, wenn Sie den gleichen Code außerhalb von SQL Server ausgeführt haben, bedeutet dies, dass das Paket nicht an dem von SQL Server verwendeten Standardspeicherort der Bibliothek installiert wurde.

Dieser Fehler kann unterschiedliche Ursachen haben:

- Sie haben ein neues Paket auf dem Server installiert, aber der Zugriff wurde verweigert, sodass das Paket von R in einer Benutzerbibliothek installiert wurde.

- Sie haben R Services und dann ein anderes R-Tool oder mehrere Bibliotheken installiert, wie Microsoft R Server (Standalone), Microsoft R Client, RStudio und so weiter.

Um den Speicherort der R-Paketbibliothek zu bestimmen, die von der Instanz verwendet wird, öffnen Sie SQL Server Management Studio (oder ein anderes Datenbankabfragetool), verbinden sich mit der Instanz und führen dann die folgende gespeicherte Prozedur aus:

```sql
EXEC sp_execute_external_script @language = N'R',  
@script = N' print(normalizePath(R.home())); print(.libPaths());'; 
```

#### <a name="sample-results"></a>Bespielergebnisse

*STDOUT message(s) from external script:*

*[1] „C:\\Programme\\Microsoft SQL Server\\MSSQL13.SQL2016\\R_SERVICES“*

*[1] „C:/Programme/Microsoft SQL Server/MSSQL13.SQL2016/R_SERVICES/library“*

Zur Behebung des Problems müssen Sie das Paket erneut in der Bibliothek der SQL Server-Instanz installieren.

::: moniker range=">=sql-server-2016||=sqlallproducts-allversions"
>[!NOTE]
>Wenn Sie eine Instanz von SQL Server 2016 aktualisiert haben, um die neueste Version von Microsoft R zu verwenden, ist der Standardspeicherort der Bibliothek anders. Weitere Informationen finden Sie unter [Verwenden von SqlBindR zum Aktualisieren einer Instanz von R Services](install/upgrade-r-and-python.md).
::: moniker-end

::: moniker range=">=sql-server-2016||=sqlallproducts-allversions"
## <a name="launchpad-shuts-down-due-to-mismatched-dlls"></a>Launchpad wird aufgrund von nicht übereinstimmenden DLLs heruntergefahren.

Wenn Sie die Datenbank-Engine mit anderen Funktionen installieren, den Server patchen und später die Machine Learning-Funktion über das ursprüngliche Medium hinzufügen, ist möglicherweise die falsche Version der Machine Learning-Komponenten installiert. Wenn Launchpad einen Versionskonflikt erkennt, wird das Programm heruntergefahren und eine Sicherungsdatei erstellt.

Damit dieses Problem vermieden wird, müssen Sie alle neuen Funktionen auf der gleichen Patchebene wie die Serverinstanz installieren.

**Die falsche Upgrademethode:**

1. Installieren Sie SQL Server 2016 R Services.
2. Führen Sie ein Upgrade auf SQL Server 2016 (kumulatives Update 2) aus.
3. Installieren Sie R Services (datenbankintern) mithilfe der RTM-Medien.

**Die richtige Upgrademethode:**

1. Installieren Sie SQL Server 2016 R Services.
2. Führen Sie ein Upgrade von SQL Server 2016 auf die gewünschte Patchebene aus. Installieren Sie beispielsweise Service Pack 1 und anschließend das kumulative Update 2.
3. Um die Funktion auf der richtigen Patchebene hinzuzufügen, führen Sie das SP1- und CU2-Setup erneut aus und wählen Sie dann R Services (datenbankintern). 

## <a name="launchpad-fails-to-start-if-8dot3-notation-is-required"></a>Launchpad kann nicht gestartet werden, wenn die 8.3-Notation erforderlich ist.

> [!NOTE] 
> Auf älteren Systemen kann Launchpad nicht gestartet werden, wenn eine 8.3-Notation erforderlich ist. Diese Anforderung wurde in späteren Releases entfernt. Kunden von SQL Server 2016 R Services sollten eine der folgenden Installationen vornehmen:
> * SQL Server 2016 SP1 und CU1: [Kumulatives Update 1 für SQL Server](https://support.microsoft.com/help/3208177/cumulative-update-1-for-sql-server-2016-sp1).
> * SQL Server 2016 RTM, kumulatives Update 3, und dieses [Hotfix](https://support.microsoft.com/help/3210110/on-demand-hotfix-update-package-for-sql-server-2016-cu3), das bei Bedarf verfügbar ist.

Für die Kompatibilität mit R ist es erforderlich, dass SQL Server 2016 R Services (datenbankintern) auf das Laufwerk zugreifen kann, auf dem die Funktion installiert ist, um die Erstellung von kurzen Dateinamen mit der *8dot3*-Notation zu unterstützen. Ein 8.3-Dateiname wird auch als *kurzer Dateiname* bezeichnet und dient der Kompatibilität mit früheren Versionen von Microsoft Windows oder als Alternative zu langen Dateinamen.

Wenn das Volume, auf dem Sie R installieren, keine kurzen Dateinamen unterstützt, können die Prozesse, die R aus SQL Server starten, möglicherweise nicht die richtige ausführbare Datei finden, und Launchpad wird nicht gestartet.

Als Umgehung können Sie die 8.3-Notation auf dem Volume aktivieren, auf dem SQL Server und R Services installiert sind. Sie müssen dann den kurzen Namen für das Arbeitsverzeichnis in der R Services-Konfigurationsdatei angeben.

1. Führen Sie zum Aktivieren der 8.3-Notation das „fsutil“ -Hilfsprogramm mit dem *8dot3name*-Argument wie hier beschrieben aus: [fsutil 8dot3name](https://technet.microsoft.com/library/ff621566(v=ws.11).aspx).

2. Nachdem dem Aktivieren der 8.3-Notation öffnen Sie die Datei „RLauncher.config“ und notieren sich die Eigenschaft von `WORKING_DIRECTORY`. Informationen zum Auffinden dieser Datei finden Sie unter [Problembehandlung bei der Datensammlung für Machine Learning](data-collection-ml-troubleshooting-process.md).

3. Verwenden Sie das „fsutil“-Hilfsprogramm mit dem Argument *file*, um einen kurzen Dateipfad für den unter WORKING_DIRECTORY angegebenen Ordner anzugeben.

4. Bearbeiten Sie die Konfigurationsdatei, um das gleiche Arbeitsverzeichnis wie in der Eigenschaft WORKING_DIRECTORY anzugeben. Alternativ können Sie ein anderes Arbeitsverzeichnis angeben und einen vorhandenen Pfad wählen, der mit der 8.3-Notation kompatibel ist.
::: moniker-end

## <a name="next-steps"></a>Nächste Schritte

[Machine Learning Services – Problembehandlung und bekannte Probleme](machine-learning-troubleshooting-faq.md)

[Datensammlung zur Behandlung von Machine Learning-Problemen](data-collection-ml-troubleshooting-process.md)

[Häufig gestellte Fragen zu Upgrade und Installation](r/upgrade-and-installation-faq-sql-server-r-services.md)

[Problembehandlung bei Datenbank-Engine-Verbindungen](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md)
