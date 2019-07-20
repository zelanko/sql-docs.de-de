---
title: Häufige Probleme mit dem Launchpad-Dienst und externer Skriptausführung
ms.prod: sql
ms.technology: ''
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 3786ab3ee17bbbc0b54e439e3466236af098ffd3
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345169"
---
# <a name="common-issues-with-launchpad-service-and-external-script-execution-in-sql-server"></a>Häufige Probleme mit dem Launchpad-Dienst und der externen Skriptausführung in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

 SQL Server vertrauenswürdigen Launchpad-Dienst unterstützt die Ausführung externer Skripts für R und python. Auf SQL Server 2016 R Services stellt SP1 den-Dienst bereit. SQL Server 2017 enthält den Launchpad-Dienst als Teil der Erstinstallation.

Mehrere Probleme können verhindern, dass Launchpad gestartet wird, einschließlich Konfigurationsprobleme, Änderungen oder fehlende Netzwerkprotokolle. Dieser Artikel enthält Anleitungen zur Problembehandlung für viele Probleme. Für jeden, den wir verpasst haben, können Sie im [Machine Learning Server Forum](https://social.msdn.microsoft.com/Forums/en-US/home?category=MicrosoftR)Fragen stellen.

## <a name="determine-whether-launchpad-is-running"></a>Bestimmen, ob Launchpad ausgeführt wird

1. Öffnen Sie den Bereich **Dienste** (Services. msc). Oder geben Sie in der Befehlszeile **SQLServerManager13. msc** oder **SQLServerManager14. msc** ein, um [SQL Server-Konfigurations-Manager](https://docs.microsoft.com/sql/relational-databases/sql-server-configuration-manager)zu öffnen.

2. Notieren Sie sich das Dienst Konto, unter dem das Launchpad ausgeführt wird. Jede Instanz, bei der R oder python aktiviert ist, sollte über eine eigene Instanz des Launchpad-Dienstanbieter verfügen. Beispielsweise könnte der Dienst für eine benannte Instanz etwa wie folgt lauten: _mssqllaunchpad $ instanceName_.

3. Wenn der Dienst beendet wurde, starten Sie ihn neu. Wenn bei einem Neustart Probleme mit der Konfiguration vorliegen, wird eine Meldung im System Ereignisprotokoll veröffentlicht, und der Dienst wird wieder beendet. Überprüfen Sie das System Ereignisprotokoll, um zu erfahren, warum der Dienst angehalten wurde.

4. Überprüfen Sie den Inhalt von rsetup. log, und stellen Sie sicher, dass das Setup keine Fehler enthält. Beispielsweise zeigt die Meldung, die *mit Code 0* beendet wird, an, dass der Dienst nicht gestartet werden konnte.

5. Überprüfen Sie den Inhalt von rlauncher. log, um nach anderen Fehlern zu suchen.

## <a name="check-the-launchpad-service-account"></a>Überprüfen Sie das Launchpad-Dienst Konto.

Das Standard Dienst Konto ist möglicherweise "NT\$Service SQL2016" oder "NT\$Service SQL2017". Der endgültige Teil kann je nach Name der SQL-Instanz variieren.

Der Launchpad-Dienst (launchpad. exe) wird mithilfe eines Dienst Kontos mit geringen Berechtigungen ausgeführt. Um R und python zu starten und mit der Daten Bank Instanz zu kommunizieren, benötigt das Launchpad-Dienst Konto jedoch die folgenden Benutzerrechte:

- Anmelden als Dienst (SeServiceLogonRight)
- Ersetzen von Token auf Prozessebene (SeAssignPrimaryTokenPrivilege)
- Umgehen von durchsuchenden Prüfungen (SeChangeNotifyPrivilege)
- Anpassen von Speicher Kontingenten für einen Prozess (seinkreasequotasizeprivilege)

Weitere Informationen zu diesen Benutzerrechten finden Sie im Abschnitt "Windows-Berechtigungen und-Rechte" unter [Konfigurieren von Windows-Dienst Konten und-Berechtigungen](../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).

> [!TIP]
> Wenn Sie mit der Verwendung des SDP-Tools (Support Diagnostics Platform) für SQL Server Diagnose vertraut sind, können Sie SDP verwenden, um die Ausgabedatei mit dem Namen "MachineName_UserRights. txt" zu überprüfen.

## <a name="user-group-for-launchpad-cannot-log-on-locally"></a>Die Benutzergruppe für Launchpad kann sich nicht lokal anmelden.

Beim Setup von Machine Learning Services erstellt SQL Server die Windows-Benutzergruppe **sqlrusergroup** und stellt diese dann mit allen Rechten bereit, die für das Launchpad erforderlich sind, um eine Verbindung mit SQL Server herzustellen und externe Skript Aufträge auszuführen. Wenn diese Benutzergruppe aktiviert ist, wird Sie auch verwendet, um python-Skripts auszuführen.

In Organisationen, in denen restriktivere Sicherheitsrichtlinien erzwungen werden, wurden die für diese Gruppe erforderlichen Rechte jedoch möglicherweise manuell entfernt, oder Sie werden möglicherweise automatisch durch die Richtlinie widerrufen. Wenn die Rechte entfernt wurden, kann das Launchpad keine Verbindung mehr mit SQL Server herstellen, und SQL Server kann die externe Laufzeit nicht mehr aufgerufen werden.

Stellen Sie sicher, dass die Gruppe **SQLRUserGroup** über die Systemberechtigung **Allow Log in locally**  (Lokale Anmeldung erlauben) verfügt, um dieses Problem zu beheben.

Weitere Informationen finden Sie unter [Konfigurieren von Windows-Dienstkonten und -Berechtigungen](../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).

## <a name="permissions-to-run-external-scripts"></a>Berechtigungen zum Ausführen externer Skripts

Auch wenn Launchpad ordnungsgemäß konfiguriert ist, wird ein Fehler zurückgegeben, wenn der Benutzer nicht über die Berechtigung zum Ausführen von R-oder python-Skripts verfügt.

Wenn Sie SQL Server als Datenbankadministrator oder als Datenbankbesitzer installiert haben, wird Ihnen diese Berechtigung automatisch erteilt. Andere Benutzer haben jedoch in der Regel eingeschränkte Berechtigungen. Wenn Sie versuchen, ein R-Skript auszuführen, erhalten Sie einen Launchpad-Fehler.

Um das Problem zu beheben, kann ein Sicherheitsadministrator in SQL Server Management Studio den SQL-Anmelde Namen oder das Windows-Benutzerkonto ändern, indem er das folgende Skript ausführen:

```sql
GRANT EXECUTE ANY EXTERNAL SCRIPT TO <username>
```

Weitere Informationen finden Sie unter [Grant (Transact-SQL](../t-sql/statements/grant-transact-sql.md)).

## <a name="common-launchpad-errors"></a>Häufige Launchpad-Fehler

In diesem Abschnitt werden die häufigsten Fehlermeldungen aufgelistet, die von Launchpad zurückgegeben werden.

## <a name="unable-to-launch-runtime-for-r-script"></a>"Die Laufzeit für R-Skript kann nicht gestartet werden."

Wenn sich die Windows-Gruppe für R-Benutzer (auch für python verwendet) nicht bei der Instanz anmelden können, auf der R Services ausgeführt wird, werden möglicherweise die folgenden Fehler angezeigt:

- Fehler, die beim Versuch generiert werden, R-Skripts auszuführen:

    * *Laufzeit für 'R'-Skript kann nicht gestartet werden. Überprüfen Sie die Konfiguration der 'R'-Laufzeit.*

    * *Ein externer Skriptfehler ist aufgetreten. Laufzeit kann nicht gestartet werden.*

- Fehler, die [!INCLUDE[rsql_launchpad](../includes/rsql-launchpad-md.md)] vom Dienst generiert wurden:

    * *Fehler beim Initialisieren des Startprogramms RLauncher.dll*

    * *Keine Startprogramm-DLLs registriert!*

    * *Sicherheitsprotokolle weisen darauf hin, dass sich der NT-Dienst des Kontos nicht anmelden konnte.*

Informationen dazu, wie Sie dieser Benutzergruppe die erforderlichen Berechtigungen erteilen, finden Sie unter [Install SQL Server 2016 R Services](install/sql-r-services-windows-install.md).

> [!NOTE]
> Diese Einschränkung gilt nicht, wenn Sie SQL-Benutzernamen verwenden, um von einer Remotearbeitsstation R-Skripts auszuführen.

## <a name="logon-failure-the-user-has-not-been-granted-the-requested-logon-type"></a>"Fehler bei der Anmeldung: dem Benutzer wurde nicht der angeforderte Anmeldetyp erteilt."

Standardmäßig [!INCLUDE[rsql_launchpad_md](../includes/rsql-launchpad-md.md)] verwendet das folgende Konto beim Start: `NT Service\MSSQLLaunchpad`. Das Konto wird vom [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] -Setup so konfiguriert, dass es über alle erforderlichen Berechtigungen verfügt.

Wenn Sie Launchpad ein anderes Konto zuweisen oder wenn das Rechte durch eine Richtlinie auf dem SQL Server Computer entfernt wird, verfügt das Konto möglicherweise nicht über die erforderlichen Berechtigungen, und möglicherweise wird der folgende Fehler angezeigt:

>*ERROR_LOGON_TYPE_NOT_GRANTED 1385 (0x569) 	Anmeldung fehlgeschlagen: Der Benutzer besitzt nicht den benötigten Anmeldetyp auf diesem Computer.*

Um dem neuen Dienst Konto die erforderlichen Berechtigungen zu erteilen, verwenden Sie die Anwendung lokale Sicherheitsrichtlinie, und aktualisieren Sie die Berechtigungen für das Konto so, dass es die folgenden Berechtigungen umfasst:

+ Anpassen des Arbeitsspeicherkontingents für einen Prozess (SeIncreaseQuotaPrivilege)
+ Umgehen von durchsuchenden Prüfungen (SeChangeNotifyPrivilege)
+ Anmelden als Dienst (SeServiceLogonRight)
+ Ersetzen von Token auf Prozessebene (SeAssignPrimaryTokenPrivilege)

## <a name="unable-to-communicate-with-the-launchpad-service"></a>"Die Kommunikation mit dem Launchpad-Dienst ist nicht möglich."

Wenn Sie Machine Learning installiert und dann aktiviert haben, dieser Fehler jedoch beim Versuch, ein R-oder Python-Skript auszuführen, angezeigt wird, wird der Launchpad-Dienst für die Instanz möglicherweise nicht mehr ausgeführt.

1. Öffnen Sie SQL Server Configuration Manager von Eingabeaufforderung aus. Weitere Informationen finden Sie unter [SQL Server Configuration Manager](https://docs.microsoft.com/sql/relational-databases/sql-server-configuration-manager).

2. Klicken Sie mit der rechten Maustaste auf SQL Server-Launchpad für die Instanz, und wählen Sie dann **Eigenschaften**aus.

3. Wählen Sie die Registerkarte **Dienst** aus, und überprüfen Sie dann, ob der Dienst ausgeführt wird. Wenn er nicht ausgeführt wird, ändern Sie den **Start Modus** in **automatisch**, **und wählen Sie**dann übernehmen aus.

4. Durch einen Neustart des Dienstes wird das Problem in der Regel behoben, sodass Machine Learning-Skripts ausgeführt werden können. Wenn das Problem durch den Neustart nicht behoben werden kann, notieren Sie den Pfad und die Argumente in der Eigenschaft **Binärpfad** , und führen Sie die folgenden Schritte aus:

    a. Überprüfen Sie die config-Datei des Start Programms, und stellen Sie sicher, dass das Arbeitsverzeichnis gültig ist.

    b. Stellen Sie sicher, dass die von Launchpad verwendete Windows-Gruppe eine Verbindung mit der SQL Server Instanz herstellen kann.

    c. Wenn Sie eine der Dienst Eigenschaften ändern, starten Sie den Launchpad-Dienst neu.

## <a name="fatal-error-creation-of-tmpfile-failed"></a>"Fehler bei der schwerwiegenden Fehler Erstellung von tmpfile".

In diesem Szenario haben Sie Machine Learning-Features erfolgreich installiert, und Launchpad wird ausgeführt. Sie versuchen, einen einfachen R-oder python-Code auszuführen, aber Launchpad schlägt mit einem Fehler wie dem folgenden fehl: 

>*Die Kommunikation mit der Laufzeit für das R-Skript ist nicht möglich. Überprüfen Sie die Anforderungen der R-Laufzeit.*

Gleichzeitig schreibt die externe Skript Laufzeit die folgende Nachricht als Teil der stderr-Meldung: 

>*Schwerwiegender Fehler: Fehler beim Erstellen von "tmpfile".*

Dieser Fehler weist darauf hin, dass das von Launchpad zu verwendende Konto nicht über die Berechtigung zum Anmelden bei der Datenbank verfügt. Diese Situation kann auftreten, wenn strikte Sicherheitsrichtlinien implementiert werden. Um zu ermitteln, ob dies der Fall ist, überprüfen Sie die SQL Server Protokolle, und überprüfen Sie, ob das MSSQLSERVER01-Konto bei der Anmeldung verweigert wurde. Die gleichen Informationen werden in den Protokollen bereitgestellt, die für R\_Services oder python\_-Dienste spezifisch sind. Suchen Sie nach extlauncherror. log.

Standardmäßig werden 20 Konten eingerichtet und dem launchpad. exe-Prozess mit den Namen MSSQLSERVER01 bis MSSQLSERVER20 zugeordnet. Wenn Sie R oder python stark nutzen, können Sie die Anzahl der Konten erhöhen.

Um das Problem zu beheben, stellen Sie sicher, dass für die Gruppe die Berechtigung " *Lokal anmelden zulassen* " für die lokale Instanz erteilt wurde, auf der Machine Learning-Funktionen installiert und aktiviert wurden. In einigen Umgebungen ist für diese Berechtigungsstufe möglicherweise eine GPO-Ausnahme vom Netzwerkadministrator erforderlich.

## <a name="not-enough-quota-to-process-this-command"></a>"Nicht genügend Kontingent zum Verarbeiten dieses Befehls"

Dieser Fehler kann eine der folgenden Ursachen haben:

- Das Launchpad weist möglicherweise nicht genügend externe Benutzer auf, um die externe Abfrage auszuführen. Wenn Sie z. b. mehr als 20 externe Abfragen gleichzeitig ausführen und nur 20 Standardbenutzer vorhanden sind, kann es vorkommen, dass mindestens eine Abfrage fehlschlägt.

- Zum Verarbeiten der R-Aufgabe ist nicht genügend Arbeitsspeicher verfügbar. Dieser Fehler tritt am häufigsten in einer Standardumgebung auf, bei der SQL Server möglicherweise bis zu 70 Prozent der Ressourcen des Computers verwendet. Informationen zum Ändern der Serverkonfiguration zur Unterstützung einer größeren Verwendung von Ressourcen durch R finden Sie unter [operationalisieren von r-Code](r/operationalizing-your-r-code.md).

## <a name="cant-find-package"></a>"Paket kann nicht gefunden werden"

Wenn Sie R-Code in SQL Server ausführen und diese Nachricht erhalten, aber die Nachricht nicht erhalten haben, als Sie denselben Code außerhalb SQL Server ausgeführt haben, bedeutet dies, dass das Paket nicht an dem von SQL Server verwendeten Standard Bibliotheks Speicherort installiert wurde.

Dieser Fehler kann in vielerlei Hinsicht auftreten:

- Sie haben ein neues Paket auf dem Server installiert, aber der Zugriff wurde verweigert, sodass das Paket von R in eine Benutzer Bibliothek installiert wurde.

- Sie haben r Services installiert und dann ein weiteres R-Tool oder eine Reihe von Bibliotheken installiert, einschließlich Microsoft R Server (eigenständig), Microsoft R Client, rstudio usw.

Um den Speicherort der R-paketbibliothek zu ermitteln, die von der Instanz verwendet wird, öffnen Sie SQL Server Management Studio (oder ein anderes Datenbankabfrage Tool), stellen Sie eine Verbindung mit der Instanz her, und führen Sie dann die folgende gespeicherte Prozedur aus:

```sql
EXEC sp_execute_external_script @language = N'R',  
@script = N' print(normalizePath(R.home())); print(.libPaths());'; 
```

#### <a name="sample-results"></a>Bespielergebnisse

*STDOUT message(s) from external script:*

*[1] "C:\\Programmdateien\\Microsoft SQL Server\\MSSQL13. SQL2016\\R_SERVICES "*

*[1] "C:/Program Files/Microsoft SQL Server/MSSQL13. SQL2016/R_SERVICES/Library "*

Um das Problem zu beheben, müssen Sie das Paket in der SQL Server-instanzbibliothek neu installieren.

>[!NOTE]
>Wenn Sie eine Instanz von SQL Server 2016 aktualisiert haben, um die neueste Version von Microsoft R zu verwenden, unterscheidet sich der Standard Speicherort der Bibliothek. Weitere Informationen finden Sie unter [Verwenden von sqlbindr zum Aktualisieren einer Instanz von R Services](install/upgrade-r-and-python.md).

## <a name="launchpad-shuts-down-due-to-mismatched-dlls"></a>Launchpad wird aufgrund von nicht übereinstimmenden DLLs heruntergefahren.

Wenn Sie die Datenbank-Engine mit anderen Features installieren, den Server patchen und später das Machine Learning Feature mithilfe der ursprünglichen Medien hinzufügen, ist möglicherweise die falsche Version der Machine Learning Komponenten installiert. Wenn das Launchpad einen Versions Konflikt erkennt, wird es heruntergefahren, und eine Dumpdatei wird erstellt.

Um dieses Problem zu vermeiden, stellen Sie sicher, dass Sie alle neuen Features auf derselben Patchebene wie die Serverinstanz installieren.

**Die falsche Upgrademethode:**

1. Installieren Sie SQL Server 2016 ohne R Services.
2. Upgrade SQL Server 2016 Kumulatives Update 2.
3. Installieren Sie R Services (in-Database) mithilfe des RTM-Mediums.

**Die korrekte Upgrademethode:**

1. Installieren Sie SQL Server 2016 ohne R Services.
2. Aktualisieren Sie SQL Server 2016 auf die gewünschte Patchebene. Installieren Sie z. b. Service Pack 1 und dann das kumulative Update 2.
3. Wenn Sie die Funktion auf der richtigen Patchebene hinzufügen möchten, führen Sie SP1 und Cu2 Setup erneut aus, und wählen Sie dann R Services (in-Database) aus. 

## <a name="launchpad-fails-to-start-if-8dot3-notation-is-required"></a>Launchpad kann nicht gestartet werden, wenn eine 8.3-Notation erforderlich ist.

> [!NOTE] 
> Auf älteren Systemen kann Launchpad nicht gestartet werden, wenn eine 8 DOT3-Notation erforderlich ist. Diese Anforderung wurde in späteren Versionen entfernt. SQL Server 2016 R Services-Kunden sollten einen der folgenden Schritte ausführen:
> * SQL Server 2016 SP1 und CU1: [Kumulatives Update 1 für SQL Server](https://support.microsoft.com/help/3208177/cumulative-update-1-for-sql-server-2016-sp1).
> * SQL Server 2016 RTM, Kumulatives Update 3 und dieses [Hotfix](https://support.microsoft.com/help/3210110/on-demand-hotfix-update-package-for-sql-server-2016-cu3), das bei Bedarf verfügbar ist.

Aus Gründen der Kompatibilität mit R erforderte SQL Server 2016 R Services (in-Database) das Laufwerk, auf dem das Feature installiert ist, um die Erstellung von kurzen Dateinamen mithilfe der *8.3-Notation*zu unterstützen. Ein 8,3-Dateiname wird auch als *kurzer*Dateiname bezeichnet und wird aus Gründen der Kompatibilität mit früheren Versionen von Microsoft Windows oder als Alternative zu langen Dateinamen verwendet.

Wenn das Volume, auf dem Sie r installieren, keine kurzen Dateinamen unterstützt, können die Prozesse, die r aus SQL Server starten, möglicherweise nicht die richtige ausführbare Datei finden, und Launchpad wird nicht gestartet.

Um dieses Problem zu umgehen, können Sie die 8 DOT3-Notation auf dem Volume aktivieren, auf dem SQL Server installiert ist und auf dem R Services installiert ist. Sie müssen dann den kurzen Namen für das Arbeitsverzeichnis in der R Services-Konfigurationsdatei angeben.

1. Um die 8.3-Notation zu aktivieren, führen Sie das Hilfsprogramm fsutil mit dem Argument *8dot3name* aus, wie hier beschrieben: [fsutil 8dot3name](https://technet.microsoft.com/library/ff621566(v=ws.11).aspx).

2. Nachdem die Schreibweise 8.3 aktiviert ist, öffnen Sie die Datei rlauncher. config, und notieren `WORKING_DIRECTORY`Sie sich die-Eigenschaft von. Informationen dazu, wie Sie diese Datei finden, finden Sie unter [Datensammlung für die Machine Learning Problem](data-collection-ml-troubleshooting-process.md)Behandlung.

3. Verwenden Sie das Hilfsprogramm fsutil mit dem *File* -Argument, um einen kurzen Dateipfad für den Ordner anzugeben, der in WORKING_DIRECTORY angegeben ist.

4. Bearbeiten Sie die Konfigurationsdatei, um das gleiche Arbeitsverzeichnis anzugeben, das Sie in der WORKING_DIRECTORY-Eigenschaft eingegeben haben. Alternativ können Sie ein anderes Arbeitsverzeichnis angeben und einen vorhandenen Pfad auswählen, der bereits mit der 8.3-Notation kompatibel ist.


## <a name="next-steps"></a>Nächste Schritte

[Machine Learning Services Problembehandlung und bekannte Probleme](machine-learning-troubleshooting-faq.md)

[Datensammlung für die Problembehandlung von Machine Learning](data-collection-ml-troubleshooting-process.md)

[Häufig gestellte Fragen zu Upgrade und Installation](r/upgrade-and-installation-faq-sql-server-r-services.md)

[Problembehandlung bei Datenbank-Engine-Verbindungen](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md)
