---
title: Bekannte Probleme für die Sprache R und Python-Integration – SQL Server Machine Learning Services
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 805dd613c49351c0106231b9147a4af54ac8cf0d
ms.sourcegitcommit: a91c3f4fe2587d474cd4d470bda93239ba2693bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/14/2019
ms.locfileid: "67140724"
---
# <a name="known-issues-in-machine-learning-services"></a>Bekannte Probleme in Machine Learning-Dienste
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel beschreibt bekannte Probleme oder Einschränkungen im Zusammenhang mit Machine Learning-Komponenten, die als eine Option bereitgestellt werden [SQL Server 2016 R Services](install/sql-r-services-windows-install.md) und [SQL Server 2017 Machine Learning-Services mit R und Python](install/sql-machine-learning-services-windows-install.md).

## <a name="setup-and-configuration-issues"></a>Setup und Konfiguration Probleme

Eine Beschreibung der Prozesse und häufig gestellte Fragen, die anfängliche Einrichtung und Konfiguration zugeordnet sind, finden Sie unter [häufig gestellte Fragen zu Upgrade und Installation](r/upgrade-and-installation-faq-sql-server-r-services.md). Sie enthält Informationen zu Upgrades, Seite-an-Seite-Installation, und Installieren neuer R oder Python-Komponenten.

### <a name="1-inconsistent-results-in-mkl-computations-due-to-missing-environment-variable"></a>1. Inkonsistente Ergebnisse in Berechnungen der MKL aufgrund fehlender-Umgebungsvariable

**Gilt für:** R_SERVER Binärdateien 9.0 9.1, 9.2 oder 9.3.

R_SERVER verwendet Intel Math Kernel Library (MKL). Für Berechnungen im Zusammenhang mit MKL können inkonsistente Ergebnisse auftreten, wenn Ihr System eine Umgebungsvariable vorhanden ist. 

Legen Sie die Umgebungsvariable `'MKL_CBWR'=AUTO` um bedingte numerische Reproduzierbarkeit in R_SERVER sicherzustellen. Weitere Informationen finden Sie unter [Einführung zum bedingten numerische Reproduzierbarkeit (CNR)](https://software.intel.com/articles/introduction-to-the-conditional-numerical-reproducibility-cnr).

**Problemumgehung**

1. Klicken Sie in der Systemsteuerung auf **System und Sicherheit** > **System** > **Erweiterte Systemeinstellungen**  >   **Umgebungsvariablen**.

2. Erstellen Sie eine neue Variable für Benutzer- oder Systemkonto. 

  + Legen Sie die Variablennamen, um "MKL_CBWR".
  + Der 'Variablenwert' auf 'AUTO' festgelegt.

3. Starten Sie neu R_SERVER. Auf SQL Server können Sie SQL Server Launchpad-Dienst neu starten.

> [!NOTE]
> Wenn Sie der 2019-Vorschau von SQL Server unter Linux ausführen, bearbeiten oder erstellen Sie *bash_profile* durch Hinzufügen der Zeile, in Ihrem Basisverzeichnis des Benutzers, `export MKL_CBWR="AUTO"`. Führen Sie die Datei durch Eingabe `source .bash_profile` in einer Bash-Eingabeaufforderung. Starten Sie durch Eingabe R_SERVER neu `Sys.getenv()` an der R-Eingabeaufforderung.

### <a name="2-r-script-runtime-error-sql-server-2017-cu5-cu7-regression"></a>2. Laufzeitfehler des R-Skripts (SQL Server 2017 CU5 – CU7 Regression)

Für SQL Server 2017 in kumulativen Updates 5 bis 7, besteht eine Regression in der **rlauncher.config** Datei, wobei der Pfad des temporären Verzeichnisses-Datei ein Leerzeichen enthält. Diese Regression wurde in CU8 behoben.

Der Fehler, die beim Ausführen von R-Skript angezeigt wird, enthält die folgenden Meldungen:

> *Für die Kommunikation mit der Laufzeit für 'R'-Skript nicht möglich. Überprüfen Sie die Anforderungen der 'R'-Laufzeit.*
>
> Stderr-Meldung(en) aus dem externen Skript: 
>
> *Schwerwiegender Fehler: 'R_TempDir' kann nicht erstellt werden.*

**Problemumgehung**

Wenden Sie CU8, sobald diese verfügbar ist. Alternativ kann neu erstellt werden **rlauncher.config** mit **Registerrext** mit deinstallieren/installieren Sie auf eine Eingabeaufforderung mit erhöhten Rechten. 

```cmd
<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRExt.exe /uninstall /sqlbinnpath:<SQLInstanceBinnPath> /userpoolsize:0 /instance:<SQLInstanceName>

<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRExt.exe /install /sqlbinnpath:<SQLInstanceBinnPath> /userpoolsize:0 /instance:<SQLInstanceName>
```

Das folgende Beispiel zeigt die Befehle mit der Standardinstanz "MSSQL14. MSSQLSERVER"installiert" c:\Programme\Microsoft SQLServer\":

```cmd
"C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRext.exe" /uninstall /sqlbinnpath:"C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\Binn" /userpoolsize:0 /instance:MSSQLSERVER

"C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRext.exe" /install /sqlbinnpath:"C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\Binn" /userpoolsize:0 /instance:MSSQLSERVER
```

### <a name="3-unable-to-install-sql-server-machine-learning-features-on-a-domain-controller"></a>3. Kann nicht zum Installieren von SQL Server Machine Learning-Features auf einem Domänencontroller

Wenn Sie versuchen, SQL Server 2016 R Services oder SQL Server 2017-Machine Learning Services auf einem Domänencontroller zu installieren, treten beim Setup, diese Fehler:

> *Während der Installation des Features ist ein Fehler aufgetreten.*
> 
> *Mit der Identität wurde nicht gefunden.*
> 
> *Komponente-Fehlercode: 0x80131509*

Der Fehler tritt auf, weil, auf einem Domänencontroller, der Dienst die 20 lokalen Konten, die zum Ausführen von Machine Learning erforderlich nicht erstellt werden. Im Allgemeinen empfehlen wir nicht SQL Server auf einem Domänencontroller installieren. Weitere Informationen finden Sie unter [Unterstützung Bulletin 2032911](https://support.microsoft.com/help/2032911/you-may-encounter-problems-when-installing-sql-server-on-a-domain-cont).

### <a name="4-install-the-latest-service-release-to-ensure-compatibility-with-microsoft-r-client"></a>4. Installieren Sie der letzten Dienstversion zum Sicherstellen der Kompatibilität mit Microsoft R Client

Wenn Sie die neueste Version von Microsoft R Client installieren und sie zum Ausführen von R auf SQL Server in einem remotecomputekontext verwenden, erhalten Sie möglicherweise einen Fehler wie folgt:

> *Sie werden Version 9.x.x von Microsoft R Client auf Ihrem Computer ist nicht mit Microsoft R Server-Version 8.x.x ausgeführt. Laden Sie eine kompatible Version herunter und installieren Sie sie.*

SQL Server 2016 ist erforderlich, dass die R-Bibliotheken auf dem Client genau die R-Bibliotheken auf dem Server übereinstimmen. Die Einschränkung wurde als R Server 9.0.1 Versionen entfernt. Wenn dieser Fehler auftritt, überprüfen Sie jedoch die Version der R-Bibliotheken, die von Ihrem Client und Server verwendet werden soll, und aktualisieren Sie bei Bedarf des Clients für der Serverversion entsprechen.

Die Version von R, die mit SQL Server R Services installiert ist wird aktualisiert, wenn eine SQL Server-Service-Version installiert ist. Um sicherzustellen, dass Sie immer die aktuellsten Versionen von R-Komponenten verfügen, müssen Sie alle Servicepacks installieren zur Verfügung.

Um die Kompatibilität mit Microsoft R Client 9.0.0 sichergestellt ist, installieren Sie die Updates, die beschrieben werden, in diesem [Support-Artikel](https://support.microsoft.com/kb/3210262).

Um Probleme mit der R-Pakete zu vermeiden, können Sie auch die Version der R-Bibliotheken, die auf dem Server installiert sind, durch Ändern Ihrer Wartung Vereinbarung die Modern Lifecycle Support-Richtlinie verwenden, wie in beschrieben aktualisieren [im nächsten Abschnitt](#bkmk_sqlbindr). Wenn Sie dies tun, wird die Version von R, die mit SQL Server installiert ist, auf dem gleichen Zeitplan zum Aktualisieren von Machine Learning Server (ehemals Microsoft R Server) aktualisiert.

**Gilt für:** SQL Server 2016 R Services mit R Server führen Version 9.0.0 oder früher

### <a name="5-r-components-missing-from-cu3-setup"></a>5. R-Komponenten fehlen CU3-setup

Eine begrenzte Anzahl von virtuellen Azure-Computer wurden ohne die Dateien der R-Installation bereitgestellt, die in SQL Server enthalten sein sollen. Das Problem betrifft in den Zeitraum aus 2018-01-05-2018-01-23 bereitgestellte virtuelle Computer. Dieses Problem kann auch für lokale Installationen, betreffen, wenn Sie das Update CU3 für SQL Server 2017 während des Zeitraums von 2018-01-05 auf 2018-01-23 angewendet.

Ein Service Release wurde bereitgestellt, die richtige Version der R-Installationsdateien enthält.

+ [Kumulatives Updatepaket 3 für SQL Server 2017 KB4052987](https://www.microsoft.com/download/details.aspx?id=56128).

Installieren die Komponenten, und Reparieren der SQL Server 2017 CU3, müssen Sie CU3 deinstallieren und installieren Sie die aktualisierte Version:

1. Laden Sie die aktualisierte CU3-Installationsdatei, zählen die R-Installationsprogramme herunter.
2. Deinstallieren Sie CU3. Suchen Sie in der Systemsteuerung für **Deinstallieren eines Updates**, und wählen Sie dann auf "Hotfix 3015 für SQLServer 2017 (KB4052987) (64-Bit)". Fahren Sie mit der Schritte zur Deinstallation fort.
3. Installieren Sie das Update CU3 durch Doppelklicken auf das Update für KB4052987, die Sie gerade heruntergeladen haben: `SQLServer2017-KB4052987-x64.exe`. Befolgen Sie die Installationsanweisungen.

### <a name="6-unable-to-install-python-components-in-offline-installations-of-sql-server-2017-ctp-20-or-later"></a>6. Kann nicht zum Installieren von Python-Komponenten in offline-Installationen von SQL Server 2017 CTP 2.0 oder höher

Wenn Sie eine Vorabversion von SQL Server 2017 auf einem Computer ohne Internetzugriff installieren, kann das Installationsprogramm auf der Seite angezeigt, die für den Speicherort der heruntergeladenen Python-Komponenten werden aufgefordert, fehl. In diesem Fall können Sie das Machine Learning Services-Feature, aber nicht die Python-Komponenten installieren.

Dieses Problem wurde in der endgültigen Version behoben. Darüber hinaus gilt diese Einschränkung nicht für R-Komponenten.

**Gilt für:** SQLServer 2017 mit Python

### <a name="bkmk_sqlbindr"></a> Warnung vor einer inkompatiblen Version bei einer älteren Version von SQL Server R Services auf einem Client mit der Verbindung [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]

Beim Ausführen von R-Code in einem SQL Server 2016-computekontext, möglicherweise den folgenden Fehler angezeigt:

> *Sie führen Version 9.0.0 von Microsoft R Client auf Ihrem Computer aus. Diese ist nicht mit der Microsoft R Server-Version 8.0.3 kompatibel. Laden Sie eine kompatible Version herunter und installieren Sie sie.*

Diese Meldung wird angezeigt, wenn eine der beiden folgenden Anweisungen ist "true",

+ Sie können R Server (eigenständig) auf einem Clientcomputer installiert, mithilfe des Setup-Assistenten für [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)].
+ Installation von Microsoft R Server unter Verwendung der [separate Windows Installer](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows).

Um sicherzustellen, dass der Server und der Client die gleiche Version verwenden, Sie möglicherweise verwenden müssen _Bindung_, für die Microsoft R Server 9.0 und späteren Versionen ist, aktualisieren Sie die R-Komponenten in SQL Server 2016-Instanzen unterstützt. Bestimmt, ob die Unterstützung für Aktualisierungen ist verfügbar, für Ihre Version von R Services finden Sie unter [Aktualisieren einer Instanz von R Services mithilfe von SqlBindR.exe](install/upgrade-r-and-python.md).

**Gilt für:** SQL Server 2016 R Services mit R Server führen Version 9.0.0 oder früher

### <a name="7-setup-for-sql-server-2016-service-releases-might-fail-to-install-newer-versions-of-r-components"></a>7. Setup für SQL Server 2016 Service Releases kann unter Umständen keine neueren R-Komponenten installieren

Wenn Sie ein kumulatives Update installieren oder ein Servicepack für SQL Server 2016 auf einem Computer, der nicht mit dem Internet verbunden ist, möglicherweise der Setup-Assistenten die Eingabeaufforderung an, die Sie die R-Komponenten mithilfe heruntergeladene CAB-Dateien aktualisieren können. Dieser Fehler tritt normalerweise auf, wenn mehrere Komponenten zusammen mit der Datenbank-Engine installiert wurden.

Dieses Problem zu umgehen, können Sie das Service Release installieren, indem Sie mithilfe der Befehlszeile und Angeben der `MRCACHEDIRECTORY` Argument wie in diesem Beispiel gezeigt wird, die CU1-Updates installiert:

`C:\<path to installation media>\SQLServer2016-KB3164674-x64.exe /Action=Patch /IACCEPTROPENLICENSETERMS /MRCACHEDIRECTORY=<path to CU1 CAB files>`

Rufen Sie die neuesten Installer finden Sie unter [Machine Learning-Komponenten ohne Internetzugang installieren](install/sql-ml-component-install-without-internet-access.md).

**Gilt für:** SQL Server 2016 R Services mit R Server führen Version 9.0.0 oder früher

### <a name="8-launchpad-services-fails-to-start-if-the-version-is-different-from-the-r-version"></a>8. Launchpad-Dienste nicht gestartet werden, wenn die Version der R-Version unterscheidet

Wenn Sie SQL Server R Services separat der Datenbank-Engine installieren und die Buildversionen unterscheiden, können Sie den folgenden Fehler in das Systemereignisprotokoll finden Sie unter:

> *Der SQL Server Launchpad-Dienst wurde aufgrund des folgenden Fehlers nicht gestartet: Der Dienst hat nicht auf die Start- oder Anforderung rechtzeitig reagiert.*

Beispielsweise kann dieser Fehler auftreten, wenn Sie die Datenbank-Engine mit der endgültigen Produktversion installieren, aktualisieren Sie die Datenbank-Engine einen Patch anwenden und dann die R-Funktion mit der endgültigen Produktversion hinzufügen.

Um dieses Problem zu vermeiden, verwenden Sie ein Hilfsprogramm wie z. B. Datei-Manager, um die Versionen der Launchpad.exe mit Version von SQL-Binärdateien, z. B. sqldk.dll zu vergleichen. Alle Komponenten sollten dieselbe Versionsnummer aufweisen. Wenn Sie eine Komponente aktualisieren, müssen Sie dasselbe Upgrade auf alle anderen installierten Komponenten anwenden.

Suchen Sie nach dem Launchpad, die in der `Binn` Ordner für die Instanz. Z. B. in einer Standardinstallation von SQL Server 2016, der Pfad möglicherweise `C:\Program Files\Microsoft SQL Server\MSSQL.13.InstanceNameMSSQL\Binn`. 

### <a name="9-remote-compute-contexts-are-blocked-by-a-firewall-in-sql-server-instances-that-are-running-on-azure-virtual-machines"></a>9. Remoterechenkontexte werden durch eine Firewall in SQL Server-Instanzen blockiert, die auf Azure Virtual Machines ausgeführt werden

Wenn Sie installiert haben [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] auf einer Windows Azure-VM, Sie möglicherweise nicht-rechenkontext zu verwenden, die Verwendung des virtuellen Computers Workspace erforderlich sind. Der Grund ist, dass die Firewall auf virtuellen Azure-Computern eine Regel standardmäßig enthält, dass der Netzwerkzugriff für lokale Benutzerkonten für R blockiert.

Öffnen Sie dieses Problem zu umgehen, klicken Sie auf der Azure-VM **Windows-Firewall mit erweiterter Sicherheit**Option **Ausgangsregeln**, und deaktivieren Sie die folgende Regel: **Netzwerkzugriff für lokale Benutzerkonten für R in SQL Server-Instanz MSSQLSERVER blockieren**. Sie können auch die Regel aktiviert lassen, aber ändern Sie die Eigenschaft für die Sicherheit auf **zulassen bei sicheren Verbindungen**.

### <a name="10-implied-authentication-in-sqlexpress"></a>10. Implizite Authentifizierung in SQLEXPRESS

Wenn Sie R-Aufträge auf einer remote Data Science-Arbeitsstation ausführen, mithilfe der integrierten Windows-Authentifizierung, SQL Server verwendet *implizite Authentifizierung* um lokale ODBC-Aufrufe zu generieren, die das Skript möglicherweise benötigt. Im RTM-Build der SQL Server Express Edition funktionierte diese Funktion jedoch nicht.

Um das Problem zu beheben, empfehlen wir die Aktualisierung auf ein neueres Service Release.

Wenn das Upgrade nicht möglich ist, dieses Problem zu umgehen, können Sie eine SQL-Anmeldung remote R-Aufträge ausführen, die eingebettete ODBC-Aufrufe möglicherweise.

**Gilt für:** SQL Server 2016 R Services Express Edition

### <a name="11-performance-limits-when-libraries-used-by-sql-server-are-called-from-other-tools"></a>11. Leistungseinschränkungen, wenn Bibliotheken, die von SQL Server verwendet, die von anderen Tools aufgerufen werden

Es ist möglich, rufen Sie die Machine learning-Bibliotheken, die für SQL Server aus einer externen Anwendung wie RGui installiert werden. Auf diese Weise kann am besten für bestimmte Aufgaben wie neue Pakete installieren oder Ausführen von ad-hoc-Tests in sehr kurzen Codebeispielen sein. Außerhalb von SQL Server, kann Leistung allerdings beschränkt werden. 

Beispielsweise auch, wenn Sie die Enterprise Edition von SQL Server verwenden, führt R im Singlethread Modus beim Ausführen Ihres R-Codes mithilfe externer Tools. Rufen Sie die Vorteile der Leistung in SQL Server eine SQL Server-Verbindung initiieren, und verwenden Sie [Sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) aufrufen, die externen Skript-Laufzeit.

Vermeiden Sie generell das Aufrufen der Machine learning-Bibliotheken, die von externen Tools von SQL Server verwendet werden. Wenn die Debug-R oder Python-Code erforderlich, ist es in der Regel einfacher, dazu außerhalb von SQL Server. Um die gleichen Bibliotheken zu erhalten, die in SQL Server sind, können Sie Microsoft R Client installieren [Machine Learning Server (eigenständig) für SQL Server 2017](install/sql-machine-learning-standalone-windows-install.md), oder [SQL Server 2016 R Server (eigenständig)](install/sql-r-standalone-windows-install.md).

### <a name="12-sql-server-data-tools-does-not-support-permissions-required-by-external-scripts"></a>12. Externer Skripts, die erforderlichen Berechtigungen für unterstützt SQL Server Data Tools nicht.

Wenn Sie Visual Studio oder SQL Server Data Tools zum Veröffentlichen eines Datenbankprojekts, verwenden Wenn Prinzipal Berechtigungen, die spezifisch für die Ausführung des externen Skripts verfügt, erhalten Sie möglicherweise einen Fehler wie diesen:

> *TSQL-Modell: Fehler beim reverse engineering der Datenbank erkannt. Die Berechtigung wurde nicht erkannt und nicht importiert wurde.*

Das DACPAC-Modell unterstützt derzeit nicht die Berechtigungen, die von R Services oder Machine Learning-Dienste, z. B. GRANT ANY EXTERNAL SCRIPT oder EXECUTE ANY EXTERNAL SCRIPT verwendet werden. Dieses Problem wird in einer künftigen Version behoben werden.

Dieses Problem zu umgehen führen Sie die zusätzliche Zuweisung Anweisungen in einem Skript nach der Bereitstellung.

### <a name="13-external-script-execution-is-throttled-due-to-resource-governance-default-values"></a>13. Externen skriptausführung wird aufgrund der Standardwerte der Ressourcenkontrolle gedrosselt.

In Enterprise Edition können Sie Ressourcenpools verwenden, um externe Skriptprozesse zu verwalten. In einigen Builds frühen Version wurde der maximale Arbeitsspeicher, der die die R-Prozesse zugeordnet werden kann, 20 Prozent. Aus diesem Grund hätte der Server über 32 GB RAM, können die ausführbaren R-Dateien (RTerm.exe und BxlServer.exe) maximal 6,4 GB in einer einzelnen Anforderung verwenden.

Wenn Sie ressourceneinschränkungen auftreten, überprüfen Sie die vom aktuellen Standardwert auf. Wenn 20 Prozent nicht ausreichend ist, finden Sie in der Dokumentation [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] dazu, wie Sie diesen Wert ändern.

**Gilt für:** SQL Server 2016 R Services, Enterprise Edition

## <a name="r-script-execution-issues"></a>Probleme bei der Ausführung von R-Skript

Dieser Abschnitt enthält bekannte Probleme, die zum Ausführen von R auf SQL Server spezifisch sind, sowie einige Probleme im Zusammenhang mit der R-Bibliotheken und Tools von Microsoft, einschließlich RevoScaleR veröffentlicht werden.

Weitere bekannte Probleme, die R-Lösungen auswirken, finden Sie unter den [Machine Learning Server](https://docs.microsoft.com/machine-learning-server/resources-known-issues) Standort.

### <a name="1-access-denied-warning-when-executing-r-scripts-on-sql-server-in-a-non-default-location"></a>1. Warnung beim Ausführen von R-Skripts zu SQL Server auf einem nicht standardmäßigen Speicherort Zugriff verweigert

Wenn die Instanz von SQL Server wie z. B. an einen nicht standardmäßigen Speicherort installiert wurde außerhalb der `Program Files` Ordner, der die Warnung ACCESS_DENIED ausgelöst wird, wenn Sie versuchen, Skripts auszuführen, die ein Paket zu installieren. Zum Beispiel:

> *In `normalizePath(path.expand(path), winslash, mustWork)` : path[2]="~ExternalLibraries/R/8/1": Zugriff wird verweigert.*

Der Grund ist, dass eine R-Funktion versucht, den Pfad zu lesen, und schlägt fehl, wenn die integrierten Benutzergruppe **SQLRUserGroup**, hat keinen Lesezugriff. Die Warnung, die ausgelöst wird, blockiert die Ausführung der aktuellen R-Skripts nicht, aber die Warnung möglicherweise wiederholt wiederholt, wenn der Benutzer alle anderen R-Skript ausgeführt wird.

Wenn Sie SQL Server am Standardspeicherort installiert haben, dieser Fehler tritt nicht auf, da alle Windows-Benutzer auf den schreibgeschützten Zugriff verfügen die `Program Files` Ordner.

Dieses Problem behoben ia in eines bevorstehenden Service Release. Dieses Problem zu umgehen, geben Sie die Gruppe **SQLRUserGroup**, mit Lesezugriff für alle übergeordneten Ordner der `ExternalLibraries`.

### <a name="2-serialization-error-between-old-and-new-versions-of-revoscaler"></a>2. Serialisierungsfehler zwischen alten und neuen Version von RevoScaleR

Wenn Sie ein Modell mit einem serialisierten Format zu einer Remoteinstanz von SQL Server übergeben, erhalten Sie möglicherweise den Fehler: 

> *Fehler in MemDecompress (Daten, Typ = Dekomprimieren) interner Fehler-3 in memDecompress(2).*

Dieser Fehler wird ausgelöst, wenn Sie das Modell unter Verwendung der Serialisierungsfunktion, einer aktuellen Version gespeichert [RxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel), aber SQL Server-Instanz, in dem Sie das Modell deserialisieren, ist eine ältere Version der RevoScaleR-APIs von SQL Server-2017-CU2 oder früher.

Dieses Problem zu umgehen können Sie die Instanz für SQL Server 2017 CU3 oder höher aktualisieren.

Der Fehler wird nicht angezeigt, wenn die API-Version übereinstimmt, oder wenn Sie ein Modell mit einer älteren Serialisierungsfunktion auf einem Server, der eine neuere Version der Serialisierung API verwendet gespeicherte verschieben.

Das heißt, verwenden Sie die gleiche Version von RevoScaleR für sowohl Serialisierung und Deserialisierung Vorgänge.

### <a name="3-real-time-scoring-does-not-correctly-handle-the-learningrate-parameter-in-tree-and-forest-models"></a>3. Echtzeitbewertung nicht ordnungsgemäß behandelt die _LearningRate_ Parameter in der Struktur und Gesamtstruktur-Modellen

Wenn Sie ein Modell mithilfe einer Entscheidungsstruktur oder Decision Forest-Methode erstellen und der Lernrate angeben, Sie möglicherweise inkonsistente Ergebnisse bei Verwendung `sp_rxpredict` oder der SQL- `PREDICT` -Funktion im Vergleich zu mit `rxPredict`.

Die Ursache ist ein Fehler in der API, Prozesse, die serialisiert modelliert und ist auf die `learningRate` Parameter: z. B. in [RxBTrees](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxbtrees), oder

Dieses Problem wird in einer bevorstehenden Service Release behoben.

### <a name="4-limitations-on-processor-affinity-for-r-jobs"></a>4. Einschränkungen der Prozessoraffinität für R-Aufträge

Im ersten Release-Build von SQL Server 2016 konnte die Prozessoraffinität nur für CPUs in der ersten k-Gruppe festgelegt werden. Wenn der Server einen 2-Socket-Computer mit zwei k-Gruppen handelt, werden beispielsweise nur Prozessoren der ersten k-Gruppe für die R-Prozesse verwendet. Die gleiche Einschränkung gilt beim Konfigurieren der Ressourcenkontrolle für R-skriptaufträge.

Dieses Problem wurde in SQL Server 2016 Service Pack 1 behoben. Es wird empfohlen, ein upgrade auf die neueste Dienstversion.

**Gilt für:** SQL Server 2016 R Services-RTM-version

### <a name="5-changes-to-column-types-cannot-be-performed-when-reading-data-in-a-sql-server-compute-context"></a>5. Änderungen an Spaltentypen nicht möglich, wenn Daten in SQL Server-Rechenkontext gelesen werden

Wenn der Rechenkontext auf die SQL Server-Instanz festgelegt ist, können Sie das Argument _ColClasses_ (oder andere ähnliche Argumente) nicht verwenden, um den Datentyp von Spalten in Ihrem R-Code zu ändern.

Die folgende Anweisung würde beispielsweise zu einem Fehler würden, wenn die Spalte CRSDepTimeStr keine Ganzzahl ist:

```R
data <- RxSqlServerData(
  sqlQuery = "SELECT CRSDepTimeStr, ArrDelay  FROM AirlineDemoSmall", 
  connectionString = connectionString, 
  colClasses = c(CRSDepTimeStr = "integer"))
```

Dieses Problem zu umgehen, können Sie die SQL-Abfrage, um die Umwandlung verwenden umschreiben oder konvertiert und mit den richtigen Datentyp auf R zu präsentieren. Leistung ist im Allgemeinen besser beim mit Daten mithilfe von SQL statt durch Ändern von Daten im R-Code arbeiten.

**Gilt für:** SQL Server 2016 R Services

### <a name="6-limits-on-size-of-serialized-models"></a>6. Grenzwerte für Größe der serialisierten Modelle

Wenn Sie ein Modell in einer SQL Server-Tabelle speichern, müssen Sie Serialisieren des Modells und speichern Sie ihn in ein binäres Format. Theoretisch ist die maximale Größe eines Modells, die mit dieser Methode gespeichert werden können, 2 GB sind, die die maximale Größe der Varbinary-Spalten in SQL Server ist.

Wenn Sie größere Modelle verwenden müssen, sind die folgenden problemumgehungen verfügbar:

+ Führen Sie die Schritte aus, um die Größe des Modells zu verringern. Einige open Source-R-Pakete enthalten einen Großteil der Informationen in das Modellobjekt, und viele dieser Informationen kann für die Bereitstellung entfernt werden. 
+ Verwenden Sie zur Featureauswahl, um nicht benötigte Spalten zu entfernen.
+ Wenn Sie einen open-Source-Algorithmus verwenden, sollten Sie eine ähnliche Implementierung, die mit dem entsprechenden Algorithmus in MicrosoftML oder RevoScaleR. Diese Pakete sind für Szenarien optimiert worden.
+ Nachdem das Modell hat wurde Ebene "optimiert", und verringert die Größe der vorherigen Schritte, festzustellen, ob die [MemCompress](https://www.rdocumentation.org/packages/base/versions/3.4.1/topics/memCompress) -Funktion in R, Basis kann verwendet werden, um die Größe des Modells, die vor der Übergabe an SQL Server zu reduzieren. Diese Option empfiehlt sich, wenn das Modell in der Nähe der maximal 2 GB ist.
+ Für größere Modelle können Sie die SQL Server [FileTable](../relational-databases/blob/filetables-sql-server.md) zum Speichern der Modelle die Funktion, anstatt eine Varbinary-Spalte.

    Um FileTables verwenden zu können, müssen Sie eine Firewallausnahme hinzufügen, da Daten in FileTables gespeichert sind, die von den Filestream-Dateisystem-Treiber in SQL Server verwaltet werden und Firewall-Standardregeln Blockieren des Netzwerkzugriffs für die Datei. Weitere Informationen finden Sie unter [aktivieren erforderlichen Komponenten für FileTable](../relational-databases/blob/enable-the-prerequisites-for-filetable.md).

    Nachdem Sie die FileTable aktiviert haben, Schreiben Sie das Modell, Sie erhalten einen Pfad von SQL-Anweisung mit der FileTable-API und dann das Modell zu diesem Speicherort aus Ihrem Code schreiben. Wenn Sie das Modell lesen möchten, rufen Sie den Pfad von SQL, und Sie rufen Sie dann das Modell unter Verwendung des Pfads in Ihrem Skript. Weitere Informationen finden Sie unter [zugreifen auf FileTables mit Datei-e / a-APIs](../relational-databases/blob/access-filetables-with-file-input-output-apis.md).

### <a name="7-avoid-clearing-workspaces-when-you-execute-r-code-in-a-includessnoversionincludesssnoversion-mdmd-compute-context"></a>7. Beim Ausführen von R-Code in das Löschen von Arbeitsbereichen vermeiden einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] compute Context verwenden

Wenn Sie einen R-Befehl verwenden, um Objekte aus Ihrem Arbeitsbereich zu löschen, während der Ausführung von R-Code in einem [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] computekontext durchführen, oder wenn Sie den Arbeitsbereich im Rahmen eines R-Skripts löschen aufgerufen werden, mithilfe von [Sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md), erhalten Sie möglicherweise diese Fehlermeldung : *Arbeitsbereich Objekt RevoScriptConnection wurde nicht gefunden.*

`revoScriptConnection` ist ein Objekt im R-Arbeitsbereich, das Informationen über eine R-Sitzung enthält, die aus [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]aufgerufen wird. Wenn Ihr R-Code jedoch einen Befehl zum Löschen des Arbeitsbereichs enthält (wie z.B. `rm(list=ls()))`), werden alle Informationen über die Sitzung und andere Objekte im R-Arbeitsbereich ebenfalls gelöscht.

Dieses Problem zu umgehen, vermeiden Sie willkürliches Löschen von Variablen und anderen Objekten, während Sie R ausführen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Obwohl das Löschen des Arbeitsbereichs häufig vorkommt, ist bei der Arbeit in der R-Konsole haben sie unerwartete Ergebnisse liefern.

* Um bestimmte Variablen zu löschen, verwenden Sie die `remove` Funktion: z.B. `remove('name1', 'name2', ...)`
* Wenn mehrere zu löschende Variablen vorhanden sind, speichern Sie die Namen temporärer Variablen in einer Liste und führen eine regelmäßige automatische Speicherbereinigung durch.

### <a name="8-restrictions-on-data-that-can-be-provided-as-input-to-an-r-script"></a>8. Einschränkungen von Daten, die als Eingabe für ein R-Skript bereitgestellt werden können

Sie können die folgenden Typen von Abfrageergebnissen nicht in einem R-Skript verwenden:

- Daten aus einer [!INCLUDE[tsql](../includes/tsql-md.md)] -Abfrage, die auf „AlwaysEncrypted“-Spalten verweist.
  
- Daten aus einer [!INCLUDE[tsql](../includes/tsql-md.md)] -Abfrage, die auf maskierte Spalten verweist.
  
     Wenn Sie maskierte Daten in einem R-Skript verwenden müssen, ist eine mögliche Problemumgehung das Erstellen einer Kopie der Daten in einer temporären Tabelle und anschließende Verwenden dieser Daten.

### <a name="9-use-of-strings-as-factors-can-lead-to-performance-degradation"></a>9. Verwenden von Zeichenfolgen als Faktoren zu Leistungseinbußen führen kann

Verwenden von Zeichenfolgenvariablen für Typ Faktoren erheblich die Arbeitsspeichermenge, die R-Vorgänge zum erhöhen können. Dies ist ein bekanntes Problem mit R im Allgemeinen ein, und es gibt zahlreiche Artikel zu diesem Thema. Beispielsweise finden Sie unter [Faktoren sind nicht als wesentliche Bestandteile in R, von John bereitstellen, im R-Blogger)](https://www.r-bloggers.com/factors-are-not-first-class-citizens-in-r/) oder [StringsAsFactors: Ein nicht autorisierter Biografie, von Roger Peng](https://simplystatistics.org/2015/07/24/stringsasfactors-an-unauthorized-biography/). 

Obwohl das Problem nicht spezifisch für SQL Server ist, kann es die Leistung von R-Code, führen Sie in SQl Server erheblich beeinträchtigen. Zeichenfolgen werden in der Regel als Varchar oder Nvarchar gespeichert, und wenn eine Spalte von Zeichenfolgendaten viele eindeutige Werte enthält, kann der Prozess der Konvertierung intern zu einer ganzen Zahl und wieder in Zeichenfolgen von R selbst zu aufgrund von Zuordnungsfehlern der Arbeitsspeicher führen.

Wenn Sie nicht unbedingt einen Zeichenfolgen-Datentyp für andere Vorgänge ausführen, benötigen die Zeichenfolgenwerte in einen numerischen (Integer) zuordnen geben Daten als Teil der Vorbereitung der Daten vom Standpunkt der Leistung und Skalierung von Vorteil wäre.

Eine Erläuterung der dieses Problem und Weitere Tipps, finden Sie unter [Leistung für R Services - datenoptimierung](r/r-and-data-optimization-r-services.md).

### <a name="10-arguments-varstokeep-and-varstodrop-are-not-supported-for-sql-server-data-sources"></a>10. Argumente *VarsToKeep* und *VarsToDrop* werden für SQL Server-Datenquellen nicht unterstützt

Wenn Sie die RxDataStep-Funktion verwenden, um die Ergebnisse in einer Tabelle zu schreiben, verwenden die *VarsToKeep* und *VarsToDrop* ist eine praktische Möglichkeit der Angabe der Spalten zum ein- bzw. ausschließen, die im Rahmen des Vorgangs. Allerdings sind diese Argumente für SQL Server-Datenquellen nicht unterstützt.

### <a name="11-limited-support-for-sql-data-types-in-spexecuteexternalscript"></a>11. Eingeschränkte Unterstützung für SQL-Datentypen in sp\_ausführen\_externe\_Skript

Nicht alle Datentypen, die in SQL unterstützt werden, können in r verwendet werden Dieses Problem zu umgehen, wandeln Sie den nicht unterstützten Datentyp in einen unterstützten Datentyp vor der Übergabe an sp\_ausführen\_externe\_Skript.

Weitere Informationen finden Sie unter [R-Bibliotheken und-Datentypen](r/r-libraries-and-data-types.md).

### <a name="12-possible-string-corruption-using-unicode-strings-in-varchar-columns"></a>12. Mögliche zeichenfolgenbeschädigung, die Verwendung von Unicodezeichenfolgen in Varchar-Spalten

Übergeben von Unicode-Daten in den Varchar-Spalten von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] R/Python zu fehlerhaften Zeichenfolge. Dies liegt an die Codierung für diese Unicode-Zeichenfolge in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Sortierungen entspricht möglicherweise nicht mit der Standardeinstellung UTF-8-Codierung, die in R/Python verwendet. 

Senden der Zeichenfolgedaten aus nicht-ASCII- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] zu R/Python, verwenden Sie UTF-8-Codierung (verfügbar in [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]), oder verwenden Sie für den gleichen Typ Nvarchar.

### <a name="13-only-one-value-of-type-raw-can-be-returned-from-spexecuteexternalscript"></a>13. Nur ein Wert vom Typ `raw` zurückgegeben werden `sp_execute_external_script`

Wenn ein binärer Datentyp (der R **unformatierten** -Datentyp) von R zurückgegeben wird, muss der Wert im ausgabedatenrahmen gesendet werden.

Mit Daten andere Datentypen als **unformatierten**, Sie können Parameterwerte zusammen mit den Ergebnissen der gespeicherten Prozedur zurückgeben, indem das Schlüsselwort OUTPUT hinzufügen. Weitere Informationen finden Sie unter [Parameter](https://docs.microsoft.com/sql/relational-databases/stored-procedures/parameters).

Wenn Sie mehrere ausgaberesultsets verwenden, die Werte des Typs einschließen möchten **unformatierten**, eine mögliche problemumgehung besteht darin, mehrere Aufrufe der gespeicherten Prozedur zu tun, oder senden das Ergebnis wird zurück auf [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] mithilfe von ODBC.

### <a name="14-loss-of-precision"></a>14. Genauigkeitsverlust

Da [!INCLUDE[tsql](../includes/tsql-md.md)] und R unterstützen verschiedene Datentypen, numerischen Datentypen können zu einem Verlust der Genauigkeit bei der Konvertierung.

Weitere Informationen zum impliziten Datentyp konvertieren, finden Sie unter [R-Bibliotheken und-Datentypen](r/r-libraries-and-data-types.md).

### <a name="15-variable-scoping-error-when-you-use-the-transformfunc-parameter"></a>15. Fehler Bereichsdefinition, wenn Sie den Parameter TransformFunc Verwenden von Variablen

Sie können zum Transformieren von Daten beim Erstellen von Modellen, übergeben einen *TransformFunc* Argument in einer Funktion wie z. B. `rxLinmod` oder `rxLogit`. Jedoch können Aufrufe geschachtelter Funktionen zum Festlegen des Gültigkeitsbereichs von Fehlern in den SQL Server-computekontext, führen, selbst wenn die Aufrufe im lokalen rechenkontext ordnungsgemäß.

> *Das Beispiel-DataSet für die Analyse wurde keine Variablen*

Nehmen wir beispielsweise an, dass Sie zwei Funktionen definiert haben `f` und `g`, in Ihrer lokalen globalen Umgebung und `g` Aufrufe `f`. Bei verteilten oder Remoteaufrufen unter Verwendung `g`, den Aufruf von `g` misslingen mit diesen Fehler, da `f` kann nicht gefunden werden, auch wenn Sie übergeben haben `f` und `g` an den Remoteaufruf.

Wenn dieses Problem auftritt, können Sie es umgehen, indem Sie die Definition von `f` innerhalb der Definition von `g`an einer Stelle einbetten, vor der `g` normalerweise `f`aufrufen würde.

Zum Beispiel:

```R
f <- function(x) { 2*x * 3 }
g <- function(y) {
              a <- 10 * y
               f(a)
}
```

Um den Fehler zu vermeiden, Schreiben Sie die Definition wie folgt:

```R
g <- function(y){
              f <- function(x) { 2*x +3}
              a <- 10 * y
              f(a)
}
```

### <a name="16-data-import-and-manipulation-using-revoscaler"></a>16. Importieren und Bearbeiten von Daten mithilfe von RevoScaleR

Wenn **Varchar** Spalten aus einer Datenbank gelesen werden Leerzeichen werden entfernt. Um dies zu verhindern, schließen Sie Zeichenfolgen in Zeichen ein, die keine Leerzeichen sind.

Wenn Funktionen wie `rxDataStep` dienen zum Erstellen von Tabellen, die **Varchar** Spalten, die Spaltenbreite wird basierend auf einer Stichprobe der Daten geschätzt. Wenn die Breite variieren kann, kann es notwendig, alle Zeichenfolgen in Länge aufgefüllt sein.

Das Verwenden einer Transformation zum Ändern des Datentyps einer Variablen wird nicht unterstützt, wenn wiederholte Aufrufe von `rxImport` oder `rxTextToXdf` zum Importieren und Anfügen von Zeilen verwendet werden, wobei mehrere Eingabedateien zu einer einzelnen XDF-Datei kombiniert werden.

### <a name="17-limited-support-for-rxexec"></a>17. Eingeschränkte Unterstützung für rxExec

In SQL Server 2016 die `rxExec` -Funktion, angegeben durch die RevoScaleR-Paket verwendet werden kann nur im Singlethread-Modus ist.

### <a name="18-increase-the-maximum-parameter-size-to-support-rxgetvarinfo"></a>18. Erhöhen Sie die maximale Parametergröße zur Unterstützung von rxGetVarInfo

Wenn Sie Datasets mit sehr großen Anzahl von Variablen (z. B. über 40.000) verwenden, legen Sie die `max-ppsize` zu kennzeichnen, wenn Sie R, um Funktionen zu verwenden, z. B. Starten `rxGetVarInfo`. Das `max-ppsize` -Flag gibt die maximale Pointer Protection Stack-Größe an.

Wenn Sie die R-Konsole (z. B. "RGui.exe" oder "RTerm.exe") verwenden, können Sie festlegen, dass den Wert des _Max-Ppsize_ auf 500000 eingeben:

```R
R --max-ppsize=500000
```

### <a name="19-issues-with-the-rxdtree-function"></a>19. Probleme mit der RxDTree-Funktion

Die `rxDTree` -Funktion unterstützt derzeit keine formelinternen Transformationen. Insbesondere das Verwenden der `F()` -Syntax zum Erstellen von Faktoren bei laufendem Betrieb wird nicht unterstützt. Numerische Daten werden jedoch automatisch klassifiziert.

Geordnete Faktoren werden in allen RevoScaleR-Analysefunktionen außer `rxDTree`genauso wie Faktoren behandelt.

### <a name="20-datatable-as-an-outputdataset-in-r"></a>20. Data.Table als ein "outputdataset" in R

Mithilfe von `data.table` als ein `OutputDataSet` in R wird nicht unterstützt in 13 für SQL Server 2017 kumulativen Update (CU13) und früheren Versionen. Möglicherweise die folgende Meldung angezeigt:

```
Msg 39004, Level 16, State 20, Line 2
A 'R' script error occurred during execution of 
'sp_execute_external_script' with HRESULT 0x80004004.
Msg 39019, Level 16, State 2, Line 2
An external script error occurred: 
Error in alloc.col(newx) : 
  Internal error: length of names (0) is not length of dt (11)
Calls: data.frame ... as.data.frame -> as.data.frame.data.table -> copy -> alloc.col

Error in execution.  Check the output for more information.
Error in eval(expr, envir, enclos) : 
  Error in execution.  Check the output for more information.
Calls: source -> withVisible -> eval -> eval -> .Call
Execution halted
```

`data.table` als ein `OutputDataSet` in R wird in SQL Server 2017 Kumulatives Update 14 (CU14) und höher unterstützt.

## <a name="python-script-execution-issues"></a>Probleme bei der Ausführung von Python-Skript

Dieser Abschnitt enthält bekannte Probleme, die spezifisch für die Ausführung von Python in SQL Server als auch Probleme im Zusammenhang mit der Python-Pakete, die von Microsoft veröffentlichten werden einschließlich [Revoscalepy](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package) und [Microsoftml](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package).

### <a name="1-call-to-pretrained-model-fails-if-path-to-model-is-too-long"></a>1. Vortrainierte Modell Aufruf fehlschlägt, wenn der Pfad zum Modell zu lang ist

Wenn Sie die vortrainierten Modelle in einer frühen Version von SQL Server 2017 installiert haben, kann der vollständige Pfad zu der Datei des trainierten Modells für Python lesen zu lang sein. Diese Einschränkung wurde in ein neueres Service Release behoben.

Es gibt mehrere mögliche Lösungen: 

+ Wenn Sie die vortrainierten Modelle installieren, wählen Sie einen benutzerdefinierten Speicherort.
+ Wenn möglich, installieren Sie SQL Server-Instanz unter ein benutzerdefinierter Installationspfad mit einem kürzeren Pfad, z. B. C:\SQL\MSSQL14. MSSQLSERVER.
+ Verwenden Sie das Windows-Dienstprogramm [Fsutil](https://technet.microsoft.com/library/cc788097(v=ws.11).aspx) um einen festen Link zu erstellen, die Modelldatei in einen kürzeren Pfad entspricht.
+ Aktualisieren Sie auf der letzten Dienstversion.

### <a name="2-error-when-saving-serialized-model-to-sql-server"></a>2. Fehler beim Speichern serialisierte Modell in SQL Server

Wenn Sie das Übergeben eines Modells zu einer Remoteinstanz von SQL Server, und versuchen Sie es in das binäre Modell, indem die `rx_unserialize` -Funktion in [Revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package), erhalten Sie möglicherweise die Fehlermeldung: 

> *NameError: Name 'Rx_unserialize_model' ist nicht definiert.*

Dieser Fehler wird ausgelöst, wenn Sie das Modell über eine aktuelle Version von die Serialisierungsfunktion gespeichert, aber SQL Server-Instanz, in dem Sie das Modell deserialisieren, die Serialisierung API nicht erkennt.

Um das Problem zu beheben, aktualisieren Sie die Instanz für SQL Server 2017 CU3 oder höher.

### <a name="3-failure-to-initialize-a-varbinary-variable-causes-an-error-in-bxlserver"></a>3. Fehler beim Initialisieren einer Variablen Varbinary verursacht einen Fehler in BxlServer

Wenn das Ausführen von Python-Code in SQL Server mithilfe `sp_execute_external_script`, und der Code erzeugt output Variablen vom Typ varbinary(max), varchar(max) oder ähnliche Typen, muss die Variable initialisiert oder als Teil des Skripts festlegen. Andernfalls löst die Exchange-Komponente, BxlServer, ein Fehler auftritt und aufhört zu funktionieren.

Diese Einschränkung wird in einer bevorstehenden Service Release behoben werden. Dieses Problem zu umgehen sicher, dass innerhalb der Python-Skript die Variable initialisiert wird. Jeder gültiger Wert kann verwendet werden, wie in den folgenden Beispielen:

```sql
declare @b varbinary(max);
exec sp_execute_external_script
  @language = N'Python'
  , @script = N'b = 0x0'
  , @params = N'@b varbinary(max) OUTPUT'
  , @b = @b OUTPUT;
go
```

```sql
declare @b varchar(30);
exec sp_execute_external_script
  @language = N'Python'
  , @script = N' b = ""  '
  , @params = N'@b varchar(30) OUTPUT'
  , @b = @b OUTPUT;
go
```

### <a name="4-telemetry-warning-on-successful-execution-of-python-code"></a>4. Telemetrie-Warnung bei erfolgreicher Ausführung des Python-code

Ab SQL Server 2017 CU2 können möglicherweise die folgende Meldung angezeigt, auch wenn andernfalls Python-Code erfolgreich ausgeführt wird:

> *Stderr-Meldung(en) aus dem externen Skript:* 
>  *~PYTHON_SERVICES\lib\site-packages\revoscalepy\utils\RxTelemetryLogger*
> *SyntaxWarning: Telemetry_state ist Bevor Sie globale Deklaration verwendet*

Dieses Problem wurde in SQL Server 2017 kumulative Update 3 (CU3) behoben wurden. 

### <a name="5-numeric-decimal-and-money-data-types-not-supported"></a>5. Numerisch, Dezimal und Money-Datentypen, die nicht unterstützt

Ab SQL Server 2017 Kumulatives Update 12 (CU12), numerische "," Decimal "und" Money-Datentypen in der WITH RESULT SETS werden nicht unterstützt bei Verwendung von Python mit `sp_execute_external_script`. Wird möglicherweise folgenden Meldungen angezeigt:

> *[Code: 39004, SQL-Status: S1000] ein "Python"-Skriptfehler ist aufgetreten, während der Ausführung von "Sp_execute_external_script" mit HRESULT 0 x 80004004.*

> *[Code: 39019, SQL-Status: S1000] ein externer Skriptfehler ist aufgetreten:*
> 
> *SqlSatelliteCall-Fehler: Nicht unterstützter Typ im Ausgabeschema. Unterstützte Typen: bit Smallint "," Int "," Datetime "," Smallmoney, echte und "float". Char, Varchar werden teilweise unterstützt.*

Dies wurde in SQL Server 2017 Kumulatives Update 14 (CU14) behoben wurden.

## <a name="revolution-r-enterprise-and-microsoft-r-open"></a>Revolution R Enterprise und Microsoft R Open

Dieser Abschnitt enthält spezifische Probleme mit R Konnektivität, Entwicklungs- und Leistungstools, die von Revolution Analytics bereitgestellt werden. Diese Tools wurden in früheren Vorabversionen von angegeben [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].

Im Allgemeinen empfehlen wir, dass Sie diese Vorabversionen deinstallieren und der neuesten Version von SQL Server oder Microsoft R Server installieren.

### <a name="1-revolution-r-enterprise-is-not-supported"></a>1. Revolution R Enterprise wird nicht unterstützt.

Installieren von Revolution R Enterprise parallel mit einer Version von [!INCLUDE[rsql_productname_md](../includes/rsql-productname-md.md)] wird nicht unterstützt.

Wenn Sie eine vorhandene Lizenz für Revolution R Enterprise haben, müssen Sie es ablegen, auf einem separaten Computer sowohl die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanz und einer beliebigen Arbeitsstation, die Sie für die Verbindung verwenden möchten die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Instanz.

Einige Vorabversionen von [!INCLUDE[rsql_productname](../includes/rsql-productname-md.md)] enthalten eine R-Entwicklungsumgebung für Windows, die von Revolution Analytics erstellt wurde. Dieses Tool wird nicht mehr bereitgestellt, und es wird nicht unterstützt.

Für die Kompatibilität mit [!INCLUDE[rsql_productname](../includes/rsql-productname-md.md)], es wird empfohlen, dass Sie stattdessen Microsoft R Client installieren. [R Tools für Visual Studio](https://www.visualstudio.com/vs/rtvs/) und [Visual Studio Code](https://code.visualstudio.com/) unterstützt auch Microsoft R-Lösungen.

### <a name="2-compatibility-issues-with-sqlite-odbc-driver-and-revoscaler"></a>2. Kompatibilitätsprobleme mit SQLite-ODBC-Treiber und RevoScaleR

Version 0.92 des SQLite-ODBC-Treibers ist nicht kompatibel mit RevoScaleR. Die Revisionen 0.88 0.91 und 0.93 und später sind bekanntermaßen kompatibel sein.

## <a name="see-also"></a>Siehe auch

[Neuerungen in SQL Server 2016](../sql-server/what-s-new-in-sql-server-2016.md)

[Problembehandlung bei Machine Learning in SQL Server](machine-learning-troubleshooting-faq.md)
