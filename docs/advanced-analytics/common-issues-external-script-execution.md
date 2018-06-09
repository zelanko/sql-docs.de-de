---
title: Häufige Probleme mit dem Launchpad-Dienst und externen skriptausführung in SQL Server | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/31/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 08ab6e2db6d6cde5e41f7ddb88c8afd1da241df7
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34706838"
---
# <a name="common-issues-with-launchpad-service-and-external-script-execution-in-sql-server"></a>Häufige Probleme mit dem Launchpad-Dienst und externen skriptausführung in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

 SQL Server vertrauenswürdige Launchpad-Dienst unterstützt externen skriptausführung für R und Python. Auf SQL Server 2016 R Services SP1 stellt den Dienst bereit. SQL Server-2017 umfasst das Launchpad Lo als Teil der Installation des ersten.

Mehrere Probleme können Launchpad aus starten, einschließlich von Konfigurationsproblemen oder Änderungen oder fehlende Netzwerkprotokolle verhindert werden. Dieser Artikel enthält Anweisungen zur Problembehandlung für viele Probleme. Für eine beliebige wir verpasst, Fragen können Sie auf die [Machine Learning-Server-Forum](https://social.msdn.microsoft.com/Forums/home?category=MicrosoftR).

**Gilt für:** SQL Server 2016-R-Services, SqlServer 2017 Machine Learning-Dienste

## <a name="determine-whether-launchpad-is-running"></a>Bestimmen Sie, ob Launchpad ausgeführt wird

1. Öffnen der **Services** Bereich ("Services.msc"). Oder geben Sie an der Befehlszeile **"sqlservermanager13.msc"** oder **SQLServerManager14.msc** öffnen [SQL Server-Konfigurations-Manager](https://docs.microsoft.com/sql/relational-databases/sql-server-configuration-manager).

2. Notieren Sie das Dienstkonto, unter dem Launchpad ausgeführt wird. Jede Instanz, wobei R oder Python aktiviert ist, sollte eine eigene Instanz des Launchpad-Dienst haben. Beispielsweise der Dienst für eine benannte Instanz möglicherweise etwas _MSSQLLaunchpad$ InstanceName_.

3. Wenn der Dienst beendet wird, starten Sie ihn aus. Auf Neustart, wenn Probleme bei der Konfiguration vorhanden sind, eine Meldung in das Systemereignisprotokoll veröffentlicht wird und erneut wird der Dienst beendet. Überprüfen Sie das Systemereignisprotokoll für Details, warum der Dienst beendet wurde.

4. Überprüfen Sie den Inhalt der RSetup.log, und stellen Sie sicher, dass keine Fehler, im Setup vorliegen. Angenommen, die Nachricht *mit Code 0 beendet* weisen auf Fehler hin des Diensts zu starten.

5. Überprüfen Sie den Inhalt von "rlauncher.log", um nach anderen Fehlern suchen.

## <a name="check-the-launchpad-service-account"></a>Überprüfen Sie das Launchpad-Dienstkonto

Ist möglicherweise das Standarddienstkonto das Konto "NT-Dienst\$SQL2016" oder "NT-Dienst\$SQL2017". Das letzte Teil variieren abhängig von der SQL-Instanzname.

Der Launchpad-Dienst (Launchpad.exe) wird mithilfe eines Dienstkontos mit geringen Rechten-ausgeführt. Allerdings erfordert das Launchpad-Dienstkonto zum Starten von R und Python und kommunizieren mit der Datenbankinstanz, die folgenden Berechtigungen:

- Anmelden als Dienst (SeServiceLogonRight)
- Ersetzen von Token auf Prozessebene (SeAssignPrimaryTokenPrivilege)
- Umgehen von durchsuchenden Prüfungen (SeChangeNotifyPrivilege)
- Anpassen von Speicherkontingenten für einen Prozess (SeIncreaseQuotaSizePrivilege)

Informationen über diese Benutzerrechte, finden Sie im Abschnitt "Windows-Berechtigungen und Rechte" in [service Konfigurieren von Windows-Dienstkonten und-Berechtigungen](../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).

> [!TIP]
> Wenn Sie mit der Verwendung des Tools Unterstützung Diagnose Plattform (SDP) für SQL Server-Diagnose vertraut sind, können Sie SDP verwenden, um die Ausgabedatei mit dem Namen MachineName_UserRights.txt zu überprüfen.

## <a name="user-group-for-launchpad-cannot-log-on-locally"></a>Benutzergruppe für Launchpad kann nicht lokal anmelden

Während des Setups von Machine Learning-Services, SQL Server erstellt die Windows-Benutzergruppe **SQLRUserGroup** , und klicken Sie dann mit allen Regeln für Launchpad, um eine Verbindung mit SQL Server, und führen die externe Skripts für Aufträge erforderlichen bereitgestellt. Wenn der Benutzer der Gruppe aktiviert ist, wird er auch zum Ausführen von Python-Skripts verwendet.

Allerdings in Organisationen, die denen restriktivere Sicherheitsrichtlinien durchgesetzt werden, die Rechte, die von dieser Gruppe erforderlich sind möglicherweise manuell entfernt, oder sie können automatisch von der Richtlinie aufgehoben werden. Wenn die Rechte entfernt wurden, Launchpad kann nicht mehr Verbinden mit SQL Server und SQL Server kann nicht die externen Laufzeit aufgerufen.

Stellen Sie sicher, dass die Gruppe **SQLRUserGroup** über die Systemberechtigung **Allow Log in locally**  (Lokale Anmeldung erlauben) verfügt, um dieses Problem zu beheben.

Weitere Informationen finden Sie unter [service Konfigurieren von Windows-Dienstkonten und-Berechtigungen](https://msdn.microsoft.com/library/ms143504.aspx#Windows).

## <a name="permissions-to-run-external-scripts"></a>Berechtigungen zum Ausführen externer Skripts.

Auch wenn Launchpad ordnungsgemäß konfiguriert ist, wird ein Fehler zurückgegeben, wenn der Benutzer keine Berechtigung zum Ausführen von R oder Python-Skripts.

Wenn Sie SQL Server als ein Datenbankadministrator installiert, oder Sie ein Datenbankbesitzer sind, werden Sie automatisch durch diese Berechtigung gewährt. Allerdings haben andere Benutzer in der Regel mehr Berechtigungen beschränkt. Wenn sie versuchen, ein R-Skript auszuführen, erhalten sie einen Launchpad-Fehler.

Zum Beheben des Problems, in SQL Server Management Studio kann ein Administrator für die Sicherheit der SQL-Anmeldung oder die Windows-Benutzerkonto ändern, indem das folgende Skript ausführen:

```SQL
GRANT EXECUTE ANY EXTERNAL SCRIPT TO <username>
```

Weitere Informationen finden Sie unter [GRANT (Transact-SQL](../t-sql/statements/grant-transact-sql.md).

## <a name="common-launchpad-errors"></a>Häufige Launchpad-Fehler

Dieser Abschnitt enthält die häufigsten Fehlermeldungen, die Launchpad zurückgibt.

## <a name="unable-to-launch-runtime-for-r-script"></a>"Kann nicht Runtime für R-Skript gestartet werden"

Wenn die Windows-Gruppe für Benutzer von R (auch für Python verwendet) auf die Instanz nicht anmelden, die R-Services ausgeführt wird, können Sie die folgenden Fehler angezeigt:

- Der Fehler generiert, wenn Sie versuchen, R-Skripts auszuführen:

    * *Laufzeit für 'R'-Skript kann nicht gestartet werden. Überprüfen Sie die Konfiguration der 'R'-Laufzeit.*

    * *Ein externer Skriptfehler ist aufgetreten. Laufzeit kann nicht gestartet werden.*

- Fehler, die durch die [!INCLUDE[rsql_launchpad](../includes/rsql-launchpad-md.md)] Dienst:

    * *Fehler beim Initialisieren des Startprogramms RLauncher.dll*

    * *Keine Startprogramm-DLLs registriert!*

    * *Sicherheitsprotokolle darauf hinweisen, dass das Konto NT-Dienst konnte sich nicht anmelden*

Weitere Informationen zu dieser Benutzergruppe die erforderlichen Berechtigungen erteilen, finden Sie unter [Installieren von SQL Server 2016 R Services](install/sql-r-services-windows-install.md).

> [!NOTE]
> Diese Einschränkung gilt nicht, wenn Sie SQL-Benutzernamen verwenden, um von einer Remotearbeitsstation R-Skripts auszuführen.

## <a name="logon-failure-the-user-has-not-been-granted-the-requested-logon-type"></a>"Anmeldefehler: der Benutzer nicht erteilt wurde der Typ der angeforderten"

Standardmäßig [!INCLUDE[rsql_launchpad_md](../includes/rsql-launchpad-md.md)] verwendet das folgende Konto beim Start: `NT Service\MSSQLLaunchpad`. Das Konto wird konfiguriert, indem [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] Setup alle erforderliche Berechtigungen verfügen.

Wenn Sie ein anderes Konto zum Launchpad zuweisen, oder nach rechts durch eine Richtlinie auf dem SQL Server-Computer entfernt wird, das Konto möglicherweise nicht die erforderlichen Berechtigungen, und möglicherweise diese Fehlermeldung angezeigt:

>*ERROR_LOGON_TYPE_NOT_GRANTED 1385 (0x569) 	Anmeldung fehlgeschlagen: Der Benutzer besitzt nicht den benötigten Anmeldetyp auf diesem Computer.*

Um die erforderlichen Berechtigungen für das neue Dienstkonto zu gewähren, verwenden Sie die lokale Sicherheitsrichtlinie-Anwendung, und Aktualisieren der Berechtigungen für das Konto für die folgenden Berechtigungen:

+ Anpassen des Arbeitsspeicherkontingents für einen Prozess (SeIncreaseQuotaPrivilege)
+ Umgehen von durchsuchenden Prüfungen (SeChangeNotifyPrivilege)
+ Anmelden als Dienst (SeServiceLogonRight)
+ Ersetzen von Token auf Prozessebene (SeAssignPrimaryTokenPrivilege)

## <a name="unable-to-communicate-with-the-launchpad-service"></a>"Konnte keine Verbindung mit dem Launchpad-Dienst kommunizieren"

Wenn Sie installiert und aktiviert dann Machine Learning, aber Sie diesen Fehler, erhalten Wenn Sie versuchen, ein R oder Python-Skript auszuführen, das Launchpad-Dienst für die Instanz möglicherweise beendet wurden.

1. Öffnen Sie SQL Server Configuration Manager von Eingabeaufforderung aus. Weitere Informationen finden Sie unter [SQL Server Configuration Manager](https://docs.microsoft.com/sql/relational-databases/sql-server-configuration-manager).

2. Maustaste auf SQL Server Launchpad für die Instanz, und wählen Sie dann **Eigenschaften**.

3. Wählen Sie die **Service** Registerkarte, und überprüfen Sie, dass der Dienst ausgeführt wird. Wenn er nicht ausgeführt wird, ändern Sie die **Startmodus** auf **automatische**, und wählen Sie dann **übernehmen**.

4. Neustarten des Diensts in der Regel wird das Problem behebt, sodass Machine Learning-Skripts ausgeführt werden können. Wenn der Neustart nicht das Problem behoben wird, beachten Sie den Pfad und den Argumenten in der **Binärpfad** -Eigenschaft, und führen Sie folgende Schritte:

    A. Überprüfen Sie das Startprogramm config-Datei, und stellen Sie sicher, dass das Arbeitsverzeichnis gültig ist.

    B. Stellen Sie sicher, dass die Windows-Gruppe, die vom Launchpad verwendet SQL Server-Instanz herstellen kann wie in beschrieben die [vorherigen Abschnitt](#bkmk_LaunchpadTS).

    c. Wenn Sie die Diensteigenschaften nicht ändern, starten Sie den Launchpad-Dienst neu.

## <a name="fatal-error-creation-of-tmpfile-failed"></a>"Fehler beim Schwerwiegender Fehler beim Erstellen des TmpFile"

In diesem Szenario Machine Learning-Funktionen wurden erfolgreich installiert und Launchpad ausgeführt wird. Sie versuchen, einige einfache R oder Python-Code auszuführen, aber Launchpad tritt ein Fehler wie folgt: 

>*Kann nicht für die Kommunikation mit der Common Language Runtime für R-Skript. Überprüfen Sie die Anforderungen des R-Laufzeit.*

Gleichzeitig schreibt die Laufzeit des externen Skripts die folgende Meldung als Teil der Nachricht "stderr": 

>*Schwerwiegender Fehler: Erstellung von Tmpfile ist fehlgeschlagen.*

Dieser Fehler zeigt an, dass das Konto, das Launchpad versucht, verwenden Sie keine Berechtigung zum Anmelden bei der Datenbank. Diese Situation kann auftreten, wenn strengen Sicherheitsrichtlinien implementiert werden. Um zu bestimmen, ob dies der Fall ist, überprüfen Sie die SQL Server-Protokolle, und überprüfen um festzustellen, ob bei der Anmeldung für das Konto MSSQLSERVER01 verweigert wurde. Die gleiche Informationen werden bereitgestellt, in den Protokollen, die für R spezifisch sind\_Dienste oder PYTHON\_Dienste. Suchen Sie nach ExtLaunchError.log.

Standardmäßig werden 20 Konten einrichten und dem Launchpad.exe-Prozess, mit dem Namen MSSQLSERVER01 über MSSQLSERVER20 zugeordnet. Wenn Sie starke Nutzung von R oder Python vornehmen, können Sie die Anzahl der Konten erhöhen.

Um das Problem zu beheben, stellen Sie sicher, dass die Gruppe hat *lokal anmelden zulassen* Berechtigungen mit der lokalen Instanz, in dem Machine Learning-Funktionen installiert und aktiviert wurde. In einigen Umgebungen kann dieser Berechtigungsstufe eine Gruppenrichtlinienobjekt-Ausnahme aus der Netzwerkadministrator erfordern.

## <a name="not-enough-quota-to-process-this-command"></a>"Nicht genügend Kontingent für diesen Befehl"

Dieser Fehler kann eine von mehreren Aktionen bedeuten:

- Launchpad möglicherweise nicht genügend externe Benutzer auf die externe Abfrage auszuführen. Wenn Sie mehr als 20 externe Abfragen gleichzeitig ausgeführt werden, und es nur 20 Standardbenutzern sind, könnte z. B. eine oder mehrere Abfragen fehl.

- Nicht genügend Arbeitsspeicher ist verfügbar, um den R-Task zu verarbeiten. Dieser Fehler tritt am häufigsten in einer standardumgebung, in dem SQL Server bis zu 70 Prozent der Ressourcen des Computers verwendet werden kann. Informationen zum Ändern der Serverkonfiguration zur Unterstützung größer Verwendung von Ressourcen, die von R finden Sie unter [Operationalisieren Ihres R-Codes](r/operationalizing-your-r-code.md).

## <a name="cant-find-package"></a>"Paket wurde nicht gefunden"

Wenn Sie R-Code in SQL Server ausführen und diese Nachricht erhalten, aber die Nachricht nicht abgerufen werden, wenn Sie den gleichen Code außerhalb von SQL Server ausgeführt haben, bedeutet dies, dass das Paket nicht am Standardspeicherort-Bibliothek verwendet, die von SQL Server installiert wurde.

Dieser Fehler kann in vielerlei Hinsicht auftreten:

- Sie haben ein neues Paket auf dem Server installiert, aber der Zugriff wurde verweigert, damit R in einer Benutzerbibliothek das Paket installiert.

- Sie R Services installiert haben und dann ein anderes R-Tool installiert oder Satz von Bibliotheken, einschließlich Microsoft R Server (eigenständig), Microsoft R-Client RStudio, usw.

Um den Speicherort der R-Paket-Bibliothek zu bestimmen, die von der Instanz verwendet wird, öffnen Sie SQL Server Management Studio (oder einem anderen Datenbank-Abfrage-Tool), eine Verbindung mit der Instanz, und führen Sie die folgende gespeicherte Prozedur:

```SQL
EXEC sp_execute_external_script @language = N'R',  
@script = N' print(normalizePath(R.home())); print(.libPaths());'; 
```

#### <a name="sample-results"></a>Bespielergebnisse

*STDOUT message(s) from external script:*

*[1] "" c: "\\Programmdateien\\Microsoft SQL Server\\MSSQL13. SQL2016\\R_SERVICES "*

*[1] "c: / Program Programme/Microsoft SQL Server/MSSQL13. SQL2016/R_SERVICES/Library"*

Um das Problem zu beheben, müssen Sie das Paket in der Bibliothek der SQL Server-Instanz neu installieren.

>[!NOTE]
>Wenn Sie eine Instanz von SQL Server 2016, verwenden Sie die neueste Version von Microsoft R aktualisiert haben, unterscheidet sich der Standardspeicherort für die Bibliothek. Weitere Informationen finden Sie unter [verwenden SqlBindR zum Aktualisieren einer Instanz des R Services](r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

## <a name="launchpad-shuts-down-due-to-mismatched-dlls"></a>Aufgrund von nicht übereinstimmenden DLLs fährt Launchpad

Wenn Sie das Datenbankmodul mit anderen Funktionen, Patch für die Server installieren, und klicken Sie dann später die Machine Learning-Funktion mit den Originalmedien hinzufügen, kann die falsche Version der Machine Learning-Komponenten installiert werden. Wenn Launchpad einen Versionskonflikt erkennt, heruntergefahren und erstellt eine Dumpdatei.

Um dieses Problem zu vermeiden, werden Sie sicher, dass keine neuen Features auf dem gleichen Patchebene als die Server-Instanz zu installieren.

**Die falsche Möglichkeit, zu aktualisieren:**

1. Installieren von SQLServer 2016 ohne R-Services.
2. SQL Server 2016 Kumulatives Update 2 zu aktualisieren.
3. Installieren von R Services (Datenbankintern) unter Verwendung der RTM-Medien.

**Die richtige Vorgehensweise zum upgrade:**

1. Installieren von SQLServer 2016 ohne R-Services.
2. Aktualisieren Sie SQL Server 2016 auf die gewünschte Patchebene an. Installieren Sie z. B. Service Pack 1, und klicken Sie dann kumulativen Update 2.
3. Um die Funktion auf die richtige Patchebene hinzuzufügen, führen Sie SP1 und CU2-Setup erneut aus, und drücken Sie R Services (Datenbankintern). 

## <a name="launchpad-fails-to-start-if-8dot3-notation-is-required"></a>Launchpad kann nicht gestartet werden, wenn 8.3-Notation erforderlich ist.

> [!NOTE] 
> Bei älteren Systemen kann Launchpad nicht gestartet, wenn eine Anforderung der 8.3-Notation. Diese Anforderung wurde in späteren Versionen entfernt. SQL Server 2016-R-Services-Kunden sollten die folgenden installieren:
> * SQL Server 2016 SP1 und CU1: [kumulativen Update 1 für SQLServer](https://support.microsoft.com/help/3208177/cumulative-update-1-for-sql-server-2016-sp1).
> * SQL Server 2016 RTM, das kumulative Update 3 und dies [Hotfix](https://support.microsoft.com/help/3210110/on-demand-hotfix-update-package-for-sql-server-2016-cu3), die bei Bedarf verfügbar ist.

Aus Kompatibilitätsgründen mit R SQL Server 2016 R Services (Datenbankintern) erforderlich, das Laufwerk, in dem das Feature installiert wird, um die Erstellung von kurzen Dateinamen mithilfe von *8.3-Notation*. Ein 8.3-Dateiname wird auch bezeichnet eine *kurzer Dateiname*, und es wird verwendet, um die Kompatibilität mit früheren Versionen von Microsoft Windows oder alternativ langen Dateinamen.

Wenn das Volume, in dem Sie R installieren, keine kurze Dateinamen unterstützt, die Prozesse, die R aus SQL Server zu starten möglicherweise nicht die richtige ausführbare Datei zu suchen und Launchpad wird nicht gestartet.

Dieses Problem zu umgehen können Sie die 8.3-Notation auf dem Volume, auf dem SQL Server installiert ist und am Installationsort von R Services. Sie müssen dann den kurzen Namen für das Arbeitsverzeichnis in der R Services-Konfigurationsdatei angeben.

1. Um 8.3-Notation zu aktivieren, führen Sie das Dienstprogramm Fsutil mit der *8dot3name* Argument wie hier beschrieben: [Fsutil 8dot3name](https://technet.microsoft.com/library/ff621566(v=ws.11).aspx).

2. Nachdem die 8.3-Notation aktiviert ist, öffnen Sie die Datei RLauncher.config, und beachten Sie die Eigenschaft des `WORKING_DIRECTORY`. Weitere Informationen dazu, wie sich diese Datei befindet, finden Sie unter [Datensammlung für die Problembehandlung von Machine Learning](data-collection-ml-troubleshooting-process.md).

3. Verwenden Sie das Dienstprogramm Fsutil mit der *Datei* Argument, um einen kurzen Pfad für den Ordner anzugeben, die in WORKING_DIRECTORY angegeben ist.

4. Bearbeiten Sie die Konfigurationsdatei, um die gleichen Arbeitsverzeichnis angeben, das Sie in der Eigenschaft WORKING_DIRECTORY eingegeben haben. Sie können alternativ Geben Sie einen anderen Arbeitsverzeichnis und wählen Sie einen vorhandenen Pfad, der bereits mit dem 8.3-Notation kompatibel ist.


## <a name="next-steps"></a>Nächste Schritte

[Machine Learning Services Problembehandlung und bekannte Probleme](machine-learning-troubleshooting-faq.md)

[Die Datensammlung für die Problembehandlung von Machine learning](data-collection-ml-troubleshooting-process.md)

[Häufig gestellte Fragen zu Upgrade und Installation](r/upgrade-and-installation-faq-sql-server-r-services.md)

[Problembehandlung bei Datenbank-Engine-Verbindungen](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md)
