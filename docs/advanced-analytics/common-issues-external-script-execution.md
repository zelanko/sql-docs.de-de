---
title: Häufige Probleme mit dem Launchpad-Dienst und der externen skriptausführung – SQL Server Machine Learning Services
ms.prod: sql
ms.technology: ''
ms.date: 05/31/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: bddc2d2e4021ee0df196078b47e3ecbba96833b6
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58509697"
---
# <a name="common-issues-with-launchpad-service-and-external-script-execution-in-sql-server"></a>Häufige Probleme mit dem Launchpad-Dienst und der externen skriptausführung in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

 Trusted Launchpad für SQL Server-Dienst unterstützt die Ausführung des externen Skripts für R und Python. Auf SQL Server 2016 R Services bietet SP1 den Dienst. SQL Server 2017 beinhaltet den Launchpad-Dienst im Rahmen der Erstinstallation.

Mehrere Probleme können verhindern, dass Launchpad aus starten, einschließlich von Konfigurationsproblemen oder Änderungen oder fehlen von Netzwerkprotokollen. Dieser Artikel enthält Anleitungen zur Fehlerbehebung für viele Probleme. Für alle, die wir nicht angetroffen haben, können Sie Fragen zu den [Machine Learning Server-Forum](https://social.msdn.microsoft.com/Forums/en-US/home?category=MicrosoftR).

## <a name="determine-whether-launchpad-is-running"></a>Bestimmen Sie, ob Launchpad ausgeführt wird

1. Öffnen der **Services** Bereich ("Services.msc"). Oder geben Sie über die Befehlszeile **SQLServerManager13.msc** oder **SQLServerManager14.msc** öffnen [SQL Server-Konfigurations-Manager](https://docs.microsoft.com/sql/relational-databases/sql-server-configuration-manager).

2. Notieren Sie sich das Dienstkonto, unter dem Launchpad ausgeführt wird. Jede Instanz,, R oder Python aktiviert ist, sollte es sich um eine eigene Instanz des Launchpad-Diensts verfügen. Z. B. der Dienst für eine benannte Instanz könnte werden etwa _MSSQLLaunchpad$ InstanceName_.

3. Wenn der Dienst beendet wird, starten Sie ihn neu. Auf neu zu starten, wenn es Probleme bei der Konfiguration gibt, eine Meldung im Ereignisprotokoll veröffentlicht wird und der Dienst wird wieder beendet. Überprüfen Sie das Systemereignisprotokoll für Details, warum der Dienst beendet wurde.

4. Überprüfen Sie den Inhalt der RSetup.log, und stellen Sie sicher, dass keine Fehler, in der Einrichtung vorliegen. Zum Beispiel die Nachricht *mit Code 0 beendet wird,* gibt Fehler des Diensts zu starten.

5. Um nach anderen Fehlern suchen, überprüfen Sie den Inhalt der rlauncher.log.

## <a name="check-the-launchpad-service-account"></a>Überprüfen Sie das Konto des Launchpad-Dienst

Ist möglicherweise das Standarddienstkonto das Konto "NT-Dienst\$SQL2016" oder "NT-Dienst\$SQL 2017". Das letzte Teil variieren abhängig von der SQL-Instanzname.

Der Launchpad-Dienst (Launchpad.exe), die mithilfe eines Dienstkontos mit geringen Rechten-wird ausgeführt. Zum Starten von R und Python, und mit der Datenbankinstanz kommunizieren, erfordert das Launchpad-Dienstkonto jedoch die folgenden Berechtigungen:

- Anmelden als Dienst (SeServiceLogonRight)
- Ersetzen von Token auf Prozessebene (SeAssignPrimaryTokenPrivilege)
- Umgehen von durchsuchenden Prüfungen (SeChangeNotifyPrivilege)
- Anpassen des arbeitsspeicherkontingents für einen Prozess (SeIncreaseQuotaSizePrivilege)

Informationen zu dieser Benutzerrechte, finden Sie im Abschnitt "Windows-Berechtigungen und Rechte" in [konfigurieren Windows-Dienstkonten und-Berechtigungen service](../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).

> [!TIP]
> Wenn Sie mit der Verwendung des Support Diagnostics Platform (SDP) Tool für SQL Server-Diagnose vertraut sind, können Sie die SDP verwenden, um die Ausgabedatei mit dem Namen MachineName_UserRights.txt zu überprüfen.

## <a name="user-group-for-launchpad-cannot-log-on-locally"></a>Benutzergruppe für Launchpad kann nicht lokal anmelden

Während des Setups von Machine Learning-Dienste, SQL Server erstellt die Windows-Benutzergruppe **SQLRUserGroup** und wird dann mit der alle erforderlichen Rechte zur Launchpad für die Verbindung mit SQL Server und externen Skripts bereitgestellt. Wenn Benutzer der Gruppe aktiviert ist, wird er auch zum Ausführen von Python-Skripts verwendet.

In Organisationen, in denen striktere Sicherheitsrichtlinien gelten, die Rechte, die von dieser Gruppe erforderlich sind möglicherweise manuell entfernt wurde oder sie können automatisch per Richtlinie widerrufen werden. Wenn die Rechte entfernt wurden, Launchpad kann nicht mehr eine Verbindung mit SQL Server und SQL Server kann nicht die externe Laufzeit aufgerufen.

Stellen Sie sicher, dass die Gruppe **SQLRUserGroup** über die Systemberechtigung **Allow Log in locally**  (Lokale Anmeldung erlauben) verfügt, um dieses Problem zu beheben.

Weitere Informationen finden Sie unter [konfigurieren Windows-Dienstkonten und-Berechtigungen service](../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).

## <a name="permissions-to-run-external-scripts"></a>Berechtigungen zum Ausführen externer Skripts.

Auch wenn Launchpad ordnungsgemäß konfiguriert ist, wird ein Fehler zurückgegeben, wenn der Benutzer keine Berechtigung zum Ausführen von R- oder Python-Skripts.

Wenn Sie SQL Server als Datenbankadministrator installiert, oder Sie der Besitzer sind, werden Sie automatisch durch diese Berechtigung gewährt. Andere Benutzer haben jedoch in der Regel mehr Berechtigungen beschränkt. Wenn sie versuchen, ein R-Skript auszuführen, erhalten sie einen Launchpad-Fehler.

Zum Beheben des Problems, in SQL Server Management Studio kann ein Sicherheitsadministrator die SQL-Anmeldung oder der Windows-Benutzerkonto ändern, indem das folgende Skript ausführen:

```sql
GRANT EXECUTE ANY EXTERNAL SCRIPT TO <username>
```

Weitere Informationen finden Sie unter [GRANT (Transact-SQL](../t-sql/statements/grant-transact-sql.md).

## <a name="common-launchpad-errors"></a>Launchpad-Problemen

Dieser Abschnitt enthält die häufigsten Fehlermeldungen, die Launchpad zurückgibt.

## <a name="unable-to-launch-runtime-for-r-script"></a>"Kann nicht zum Starten der Laufzeit für R-Skript"

Wenn die Windows-Gruppe für Benutzer von R (auch für Python verwendet) auf die Instanz nicht anmelden können, die R Services ausgeführt wird, können Sie die folgenden Fehler angezeigt:

- Der Fehler generiert, wenn Sie versuchen, R-Skripts auszuführen:

    * *Laufzeit für 'R'-Skript kann nicht gestartet werden. Überprüfen Sie die Konfiguration der 'R'-Laufzeit.*

    * *Ein externer Skriptfehler ist aufgetreten. Laufzeit kann nicht gestartet werden.*

- Fehler von generiert die [!INCLUDE[rsql_launchpad](../includes/rsql-launchpad-md.md)] Dienst:

    * *Fehler beim Initialisieren des Startprogramms RLauncher.dll*

    * *Keine Startprogramm-DLLs registriert!*

    * *Sicherheitsprotokolle weisen darauf hin, dass das Konto NT-Dienst konnte sich nicht anmelden konnte.*

Informationen dazu, wie Sie Benutzer der Gruppe die erforderlichen Berechtigungen erteilen, finden Sie unter [Installieren von SQL Server 2016 R Services](install/sql-r-services-windows-install.md).

> [!NOTE]
> Diese Einschränkung gilt nicht, wenn Sie SQL-Benutzernamen verwenden, um von einer Remotearbeitsstation R-Skripts auszuführen.

## <a name="logon-failure-the-user-has-not-been-granted-the-requested-logon-type"></a>"Fehler bei der Anmeldung: der Benutzer hat nicht den angeforderten Anmeldungstyp gewährt"

In der Standardeinstellung [!INCLUDE[rsql_launchpad_md](../includes/rsql-launchpad-md.md)] verwendet das folgende Konto beim Start: `NT Service\MSSQLLaunchpad`. Das Konto wird konfiguriert, indem [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] Setup alle erforderlichen Berechtigungen verfügen.

Wenn Launchpad ein anderes Konto zuweisen, oder die Berechtigung durch eine Richtlinie auf dem SQL Server-Computer entfernt wird, das Konto möglicherweise nicht die erforderlichen Berechtigungen, und Sie erhalten möglicherweise folgenden Fehler:

>*ERROR_LOGON_TYPE_NOT_GRANTED 1385 (0x569) 	Anmeldung fehlgeschlagen: Der Benutzer besitzt nicht den benötigten Anmeldetyp auf diesem Computer.*

Um die erforderlichen Berechtigungen auf dem neuen Dienstkonto zu gewähren, verwenden Sie die lokale Sicherheitsrichtlinie-Anwendung, und aktualisieren Sie die Berechtigungen für das Konto folgenden Berechtigungen einschließen:

+ Anpassen des Arbeitsspeicherkontingents für einen Prozess (SeIncreaseQuotaPrivilege)
+ Umgehen von durchsuchenden Prüfungen (SeChangeNotifyPrivilege)
+ Anmelden als Dienst (SeServiceLogonRight)
+ Ersetzen von Token auf Prozessebene (SeAssignPrimaryTokenPrivilege)

## <a name="unable-to-communicate-with-the-launchpad-service"></a>"Kann nicht für die Kommunikation mit dem Launchpad-Dienst"

Wenn Sie installiert und Machine Learning aktiviert haben, aber Sie diesen Fehler, erhalten Wenn Sie versuchen, ein R- oder Python-Skript auszuführen, der Launchpad-Dienst für die Instanz möglicherweise nicht mehr haben ausgeführt.

1. Öffnen Sie SQL Server Configuration Manager von Eingabeaufforderung aus. Weitere Informationen finden Sie unter [SQL Server Configuration Manager](https://docs.microsoft.com/sql/relational-databases/sql-server-configuration-manager).

2. Mit der rechten Maustaste SQL Server Launchpad für die Instanz, und wählen Sie dann **Eigenschaften**.

3. Wählen Sie die **Service** Registerkarte, und stellen Sie sicher, dass der Dienst ausgeführt wird. Wenn er nicht ausgeführt wird, ändern Sie die **Startmodus** zu **automatische**, und wählen Sie dann **übernehmen**.

4. Neustarten des Diensts in der Regel wird das Problem behoben, damit Machine Learning-Skripts ausführen können. Wenn der Neustart das Problem nicht behoben wird, beachten Sie den Pfad und den Argumenten in der **Binärpfad** -Eigenschaft, und führen Sie folgende Schritte:

    a. Überprüfen Sie das Startprogramm für den config-Datei aus, und stellen Sie sicher, dass das Arbeitsverzeichnis gültig ist.

    b. Stellen Sie sicher, dass die Windows-Gruppe, die von Launchpad verwendete SQL Server-Instanz herstellen kann.

    c. Wenn Sie die Eigenschaften des Diensts ändern, starten Sie den Launchpad-Dienst neu.

## <a name="fatal-error-creation-of-tmpfile-failed"></a>"Erstellung TmpFile Schwerwiegender Fehler failed"

In diesem Szenario haben Sie Machine Learning-Features erfolgreich installiert und Launchpad ausgeführt wird. Sie versuchen, einige einfache R oder Python-Code auszuführen, aber Launchpad tritt ein Fehler wie folgt: 

>*Für die Kommunikation mit der Laufzeit für R-Skript nicht möglich. Überprüfen Sie die Anforderungen des R-Laufzeit.*

Zur gleichen Zeit schreibt die Laufzeit des externen Skripts die folgende Meldung als Teil der Nachricht "stderr" an: 

>*Schwerwiegender Fehler: Erstellung von Tmpfile-Fehler.*

Dieser Fehler weist darauf hin, dass das Konto, das Launchpad versucht, verwenden Sie keine Berechtigung zum Anmelden bei der Datenbank. Diese Situation kann eintreten, wenn der strengen Sicherheitsrichtlinien implementiert sind. Bestimmt, ob dies der Fall ist, überprüfen Sie die SQL Server-Protokolle, und prüfen um festzustellen, ob das Konto MSSQLSERVER01, bei der Anmeldung verweigert wurde. Die gleiche Informationen werden bereitgestellt, in den Protokollen, die für R spezifisch sind\_Dienste oder PYTHON\_Dienste. Suchen Sie nach ExtLaunchError.log.

Standardmäßig werden 20 Konten eingerichtet und dem Launchpad.exe-Prozess, mit dem Namen MSSQLSERVER01 über MSSQLSERVER20 zugeordnet. Wenn Sie die intensiven Gebrauch von R- oder Python vornehmen, können Sie die Anzahl der Konten erhöhen.

Um das Problem zu beheben, stellen Sie sicher, dass die Gruppe hat *lokal anmelden zulassen* Berechtigungen mit der lokalen Instanz, in denen Machine Learning-Features installiert und aktiviert wurde. In einigen Umgebungen kann diese Berechtigungsebene eine GPO-Ausnahme von der Netzwerkadministrator erfordern.

## <a name="not-enough-quota-to-process-this-command"></a>"Nicht genügend Kontingent zum Verarbeiten des Befehls"

Dieser Fehler kann es sich um eine von mehreren Aktionen bedeuten:

- Launchpad möglicherweise nicht genügend externe Benutzer, die externe Abfrage auszuführen. Wenn Sie mehr als 20 externe Abfragen gleichzeitig ausgeführt werden und nur 20 Standardbenutzer vorhanden sind, können z. B. eine oder mehrere Abfragen fehlschlagen.

- Nicht genügend Arbeitsspeicher ist verfügbar, um die R-Vorgang zu verarbeiten. Dieser Fehler tritt am häufigsten in einer standardumgebung, in dem SQL Server bis zu 70 Prozent der Computerressourcen möglicherweise verwenden. Informationen dazu, wie Sie die Serverkonfiguration zur Unterstützung von stärkerer Einsatz der Ressourcen von R zu ändern, finden Sie unter [Operationalisieren Ihres R-Codes](r/operationalizing-your-r-code.md).

## <a name="cant-find-package"></a>"Paket wurde nicht gefunden"

Wenn Sie R-Code in SQL Server ausführen und diese Meldung angezeigt, aber die Nachricht nicht abgerufen werden, wenn Sie den gleichen Code außerhalb von SQL Server ausgeführt haben, bedeutet dies, dass das Paket nicht am Standardspeicherort-Bibliothek verwendet, die von SQL Server installiert wurde.

Dieser Fehler kann in vielerlei Hinsicht auftreten:

- Sie haben ein neues Paket auf dem Server installiert, aber der Zugriff wurde verweigert, damit R das Paket in einer Benutzerbibliothek installiert.

- Sie R Services installiert haben und dann eine andere R-Tool installiert oder Satz von Bibliotheken, einschließlich Microsoft R Server (eigenständig), Microsoft R Client RStudio, usw.

Um den Speicherort der R-paketbibliothek zu bestimmen, die von der Instanz verwendet wird, öffnen Sie SQL Server Management Studio (oder jedes andere Datenbank-Abfrage-Tool), eine Verbindung mit der Instanz, und führen Sie dann die folgende gespeicherte Prozedur:

```sql
EXEC sp_execute_external_script @language = N'R',  
@script = N' print(normalizePath(R.home())); print(.libPaths());'; 
```

#### <a name="sample-results"></a>Bespielergebnisse

*STDOUT message(s) from external script:*

*[1] "C:\\Programmdateien\\Microsoft SQL Server\\MSSQL13. SQL2016\\R_SERVICES "*

*[1] "c: / Program Programme/Microsoft SQL Server/MSSQL13. SQL2016/R_SERVICES/Library"*

Um das Problem zu beheben, müssen Sie das Paket in der Bibliothek zu SQL Server-Instanz neu installieren.

>[!NOTE]
>Wenn Sie eine Instanz von SQL Server 2016 verwenden Sie die neueste Version von Microsoft R aktualisiert haben, unterscheidet sich der Standardspeicherort für die Bibliothek. Weitere Informationen finden Sie unter [Verwenden von SqlBindR zum Aktualisieren einer Instanz von R Services](r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

## <a name="launchpad-shuts-down-due-to-mismatched-dlls"></a>Launchpad heruntergefahren aufgrund nicht übereinstimmender DLLs

Wenn Sie die Datenbank-Engine mit anderen Funktionen, Patch, dem Server installieren, und klicken Sie dann später die Machine Learning-Funktion mit den ursprünglichen Medien hinzufügen, kann die falsche Version der Machine Learning-Komponenten installiert werden. Wenn Launchpad einen Versionskonflikt erkannt wird, heruntergefahren und erstellt eine Dumpdatei.

Um dieses Problem zu vermeiden, werden Sie darauf, dass keine neuen Features auf die gleiche Patchebene als Server-Instanz installiert.

**Die falsche Methode zum Aktualisieren:**

1. Installieren von SQLServer 2016 ohne R Services.
2. Aktualisieren Sie SQL Server 2016-Kumulatives Update 2.
3. Installieren von R-Services (Datenbankintern) mithilfe der RTM-Medien.

**Die richtige Methode zum Aktualisieren:**

1. Installieren von SQLServer 2016 ohne R Services.
2. Aktualisieren Sie SQL Server 2016, auf die gewünschte Patchebene. Installieren Sie z. B. Service Pack 1, und klicken Sie dann kumulativen Update 2.
3. Um die Funktion auf der richtigen Patch-Ebene hinzuzufügen, führen Sie SP1 und CU2-Setup erneut aus, und wählen Sie dann auf R Services (Datenbankintern). 

## <a name="launchpad-fails-to-start-if-8dot3-notation-is-required"></a>Launchpad kann nicht gestartet werden, wenn 8.3-Notation erforderlich ist.

> [!NOTE] 
> Bei älteren Systemen kann Launchpad nicht gestartet, wenn eine Anforderung der 8.3-Notation. Diese Anforderung wurde in späteren Versionen entfernt. SQL Server 2016 R Services-Kunden sollten die folgenden installieren:
> * SQL Server 2016 SP1 und CU1: [Kumulatives Update 1 für SQLServer](https://support.microsoft.com/help/3208177/cumulative-update-1-for-sql-server-2016-sp1).
> * SQL Server 2016 RTM, das kumulative Update 3 und dadurch [Hotfix](https://support.microsoft.com/help/3210110/on-demand-hotfix-update-package-for-sql-server-2016-cu3), die bei Bedarf verfügbar ist.

Kompatibilität mit R, SQL Server 2016 R Services (Datenbankintern) erforderlich, das Laufwerk, in dem die Funktion installiert wurde, um die Erstellung von kurzen Dateinamen mithilfe unterstützen *8.3-Notation*. Ein 8.3-Dateiname wird auch als bezeichnet ein *kurzer Dateiname*, und es wird verwendet, für die Kompatibilität mit früheren Versionen von Microsoft Windows oder als Alternative zu langen Dateinamen.

Wenn das Volume, auf dem Sie R installieren keine kurzen Dateinamen unterstützt, die Prozesse, starten R aus SQL Server, können möglicherweise nicht die richtige ausführbare Datei gefunden und Launchpad nicht gestartet.

Dieses Problem zu umgehen können Sie der 8.3-Notation auf dem Volume aktivieren, dem SQL Server installiert ist und dem R Services installiert ist. Sie müssen dann den kurzen Namen für das Arbeitsverzeichnis in der R Services-Konfigurationsdatei angeben.

1. Um 8.3-Notation aktivieren möchten, führen Sie das Hilfsprogramm Fsutil mit dem *8dot3name* -Argument wie hier beschrieben: [Fsutil 8dot3name](https://technet.microsoft.com/library/ff621566(v=ws.11).aspx).

2. Nach die 8.3-Notation aktiviert ist, öffnen Sie die Datei "RLauncher.config", und beachten Sie die Eigenschaft der `WORKING_DIRECTORY`. Informationen dazu, wie Sie diese Datei zu suchen, finden Sie unter [Datensammlung zur Problembehandlung von Machine Learning](data-collection-ml-troubleshooting-process.md).

3. Verwenden Sie das Hilfsprogramm Fsutil mit dem *Datei* Argument, um einen kurzen Dateipfad für den Ordner anzugeben, die unter WORKING_DIRECTORY angegeben wird.

4. Bearbeiten Sie die Konfigurationsdatei zum gleichen Arbeitsverzeichnis angeben, das Sie in der Eigenschaft für WORKING_DIRECTORY eingegeben haben. Alternativ können Sie ein anderes Arbeitsverzeichnis angeben, und wählen Sie einen vorhandenen Pfad, der bereits mit der 8.3-Notation kompatibel ist.


## <a name="next-steps"></a>Nächste Schritte

[Machine Learning-Dienste zur Problembehandlung und bekannte Probleme](machine-learning-troubleshooting-faq.md)

[Die Datensammlung für die Problembehandlung von Machine learning](data-collection-ml-troubleshooting-process.md)

[Häufig gestellte Fragen zu Upgrade und Installation](r/upgrade-and-installation-faq-sql-server-r-services.md)

[Problembehandlung bei Datenbank-Engine-Verbindungen](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md)
