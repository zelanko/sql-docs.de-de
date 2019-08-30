---
title: Bekannte Probleme für python und R
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/23/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e762354a2f391ba4c52f8bc0aa5fece537c79288
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2019
ms.locfileid: "70155371"
---
# <a name="known-issues-in-sql-server-machine-learning-services"></a>Bekannte Probleme in SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dieser Artikel beschreibt bekannte Probleme oder Einschränkungen bei Machine Learning-Komponenten, die als Option in [SQL Server Machine Learning Services](what-is-sql-server-machine-learning.md) und [SQL Server 2016 R Services](r/sql-server-r-services.md)bereitgestellt werden.

## <a name="setup-and-configuration-issues"></a>Setup-und Konfigurationsprobleme

Eine Beschreibung der Prozesse und häufig gestellten Fragen im Zusammenhang mit der anfänglichen Einrichtung und Konfiguration finden Sie unter Häufig gestellte Fragen zu [Upgrade und Installation](r/upgrade-and-installation-faq-sql-server-r-services.md). Sie enthält Informationen über Upgrades, parallele Installationen und die Installation neuer R-oder python-Komponenten.

### <a name="1-inconsistent-results-in-mkl-computations-due-to-missing-environment-variable"></a>1. Inkonsistente Ergebnisse in MKL-Berechnungen aufgrund fehlender Umgebungsvariablen

**Gilt für:** R_SERVER-Binärdateien 9,0, 9,1, 9,2 oder 9,3.

R_SERVER verwendet die Intel Math Kernel Library (MKL). Bei Berechnungen, die MKL betreffen, können inkonsistente Ergebnisse auftreten, wenn in Ihrem System eine Umgebungsvariable fehlt. 

Legen Sie die Umgebungs `'MKL_CBWR'=AUTO` Variable fest, um eine bedingte numerische Reproduzierbarkeit in R_SERVER sicherzustellen. Weitere Informationen finden Sie unter [Einführung in die bedingte numerische Reproduzierbarkeit (CNR)](https://software.intel.com/articles/introduction-to-the-conditional-numerical-reproducibility-cnr).

**Problemumgehung**

1. Klicken Sie in der Systemsteuerung auf **System-und Sicherheits** > **System** > **Erweiterte Systemeinstellungen** > **Umgebungsvariablen**.

2. Erstellen Sie eine neue Benutzer-oder System Variable. 

  + Legen Sie Variablenname auf "MKL_CBWR" fest.
  + Legen Sie den Wert ' Variable ' auf ' Auto ' fest.

3. Starten Sie R_SERVER neu. Auf SQL Server können Sie SQL Server-Launchpad-Dienst neu starten.

> [!NOTE]
> Wenn Sie die SQL Server 2019 Preview unter Linux ausführen, bearbeiten oder erstellen Sie *. bash_profile* im Stammverzeichnis Ihrer Benutzer, indem Sie die `export MKL_CBWR="AUTO"`Zeile hinzufügen. Führen Sie diese Datei aus, indem Sie `source .bash_profile` in der Bash-Eingabeaufforderung eingeben. Starten Sie R_SERVER neu `Sys.getenv()` , indem Sie an der R-Eingabeaufforderung eingeben.

### <a name="2-r-script-runtime-error-sql-server-2017-cu5-cu7-regression"></a>2. Laufzeitfehler des R-Skripts (SQL Server 2017 CU5-CU7 Regression)

Bei SQL Server 2017 gibt es in den kumulativen Updates 5 bis 7 eine Regression in der Datei " **rlauncher. config** ", in der der temporäre Verzeichnis Dateipfad ein Leerzeichen enthält. Diese Regression wurde in CU8 korrigiert.

Der Fehler, der beim Ausführen von R-Skripts angezeigt wird, umfasst die folgenden Meldungen:

> *Die Kommunikation mit der Laufzeit für das Skript "R" ist nicht möglich. Überprüfen Sie die Anforderungen der "R"-Laufzeit.*
>
> Stderr-Meldung (en) aus dem externen Skript: 
>
> *Schwerwiegender Fehler: "R_TempDir" kann nicht erstellt werden*

**Problemumgehung**

CU8 anwenden, wenn Sie verfügbar wird. Alternativ können Sie **rlauncher. config** neu erstellen, indem Sie **registerrext** mit deinstallieren/installieren an einer Eingabeaufforderung mit erhöhten Rechten ausführen. 

```cmd
<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRExt.exe /uninstall /sqlbinnpath:<SQLInstanceBinnPath> /userpoolsize:0 /instance:<SQLInstanceName>

<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRExt.exe /install /sqlbinnpath:<SQLInstanceBinnPath> /userpoolsize:0 /instance:<SQLInstanceName>
```

Im folgenden Beispiel werden die Befehle mit der Standard Instanz "MSSQL14" gezeigt. MSSQLSERVER "installiert in" c:\Programme\Microsoft SQL Server\":

```cmd
"C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRext.exe" /uninstall /sqlbinnpath:"C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\Binn" /userpoolsize:0 /instance:MSSQLSERVER

"C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRext.exe" /install /sqlbinnpath:"C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\Binn" /userpoolsize:0 /instance:MSSQLSERVER
```

### <a name="3-unable-to-install-sql-server-machine-learning-features-on-a-domain-controller"></a>3. SQL Server Machine Learning-Funktionen auf einem Domänen Controller können nicht installiert werden.

Wenn Sie versuchen, SQL Server 2016 R-Dienste oder SQL Server Machine Learning Services auf einem Domänen Controller zu installieren, schlägt das Setup mit den folgenden Fehlern fehl:

> *Fehler beim Setup Vorgang des Features.*
> 
> *Gruppe mit Identität kann nicht gefunden werden.*
> 
> *Komponenten Fehlercode: 0x80131509*

Der Fehler tritt auf, weil der Dienst auf einem Domänen Controller die 20 lokalen Konten, die zum Ausführen von Machine Learning erforderlich sind, nicht erstellen kann. Im Allgemeinen empfiehlt es sich nicht, SQL Server auf einem Domänen Controller zu installieren. Weitere Informationen finden Sie [unter Support Bulletin 2032911](https://support.microsoft.com/help/2032911/you-may-encounter-problems-when-installing-sql-server-on-a-domain-cont).

### <a name="4-install-the-latest-service-release-to-ensure-compatibility-with-microsoft-r-client"></a>4. Installieren Sie die neueste Dienst Version, um die Kompatibilität mit Microsoft R Client sicherzustellen.

Wenn Sie die neueste Version von Microsoft R Client installieren und zum Ausführen von R auf SQL Server in einem remotecomputekontext verwenden, erhalten Sie möglicherweise eine Fehlermeldung wie die folgende:

> *Sie führen Version 9. x. x Microsoft R Client auf Ihrem Computer aus, die mit Microsoft R Server Version 8 nicht kompatibel ist. x Laden Sie eine kompatible Version herunter und installieren Sie sie.*

SQL Server 2016 erfordert, dass die r-Bibliotheken auf dem Client exakt mit den r-Bibliotheken auf dem Server übereinstimmen. Die Einschränkung wurde für Releases nach dem R Server 9.0.1 entfernt. Wenn dieser Fehler auftritt, überprüfen Sie jedoch die Version der R-Bibliotheken, die von Ihrem Client und dem Server verwendet werden, und aktualisieren Sie ggf. den Client entsprechend der Server Version.

Die Version von R, die mit SQL Server R Services installiert wird, wird immer dann aktualisiert, wenn eine SQL Server Service-Version installiert wird. Um sicherzustellen, dass Sie immer über die aktuellsten Versionen der R-Komponenten verfügen, müssen Sie alle Service Packs installieren.

Um die Kompatibilität mit Microsoft R Client 9.0.0 sicherzustellen, installieren Sie die Updates, die in diesem [Support Artikel](https://support.microsoft.com/kb/3210262)beschrieben werden.

Um Probleme mit r-Paketen zu vermeiden, können Sie auch die Version der r-Bibliotheken aktualisieren, die auf dem Server installiert sind, indem Sie den Wartungsvertrag so ändern, dass er die Support Richtlinie des modernen Lebenszyklus verwendet, wie im [nächsten Abschnitt](#bkmk_sqlbindr)beschrieben. In diesem Fall wird die Version von R, die mit SQL Server installiert wird, gemäß dem gleichen Zeitplan aktualisiert, der für Updates von Machine Learning Server (früher Microsoft R Server) verwendet wird.

**Gilt für:** SQL Server 2016 R Services mit R Server Version 9.0.0 oder früher

### <a name="5-r-components-missing-from-cu3-setup"></a>5. In CU3-Setup fehlende R-Komponenten

Es wurde eine begrenzte Anzahl von virtuellen Azure-Computern ohne die R-Installationsdateien bereitgestellt, die in SQL Server eingeschlossen werden sollten. Das Problem gilt für virtuelle Maschinen, die im Zeitraum zwischen 2018-01-05 und 2018-01-23 bereitgestellt werden. Dieses Problem kann sich auch auf lokale Installationen auswirken, wenn Sie das CU3-Update für SQL Server 2017 während des Zeitraums von 2018-01-05 auf 2018-01-23 angewendet haben.

Es wurde eine Dienst Version bereitgestellt, die die richtige Version der R-Installationsdateien enthält.

+ [Kumulatives Update Paket 3 für SQL Server 2017 KB4052987](https://www.microsoft.com/download/details.aspx?id=56128).

Zum Installieren der Komponenten und reparieren SQL Server 2017 CU3 müssen Sie CU3 deinstallieren und die aktualisierte Version neu installieren:

1. Laden Sie die aktualisierte Installationsdatei CU3 herunter, die die R-Installationsprogramme enthält.
2. Deinstallieren Sie CU3. Suchen Sie in der Systemsteuerung nach **Deinstallation eines Updates**, und wählen Sie dann "Hotfix 3015 für SQL Server 2017 (KB4052987) (64-Bit)" aus. Führen Sie die Schritte zur Deinstallation
3. Installieren Sie das CU3-Update neu, indem Sie auf das soeben heruntergeladene Update für KB4052987 doppelklicken `SQLServer2017-KB4052987-x64.exe`:. Befolgen Sie die Installationsanweisungen.

### <a name="6-unable-to-install-python-components-in-offline-installations-of-sql-server-2017-ctp-20-or-later"></a>6. Python-Komponenten können nicht in Offline Installationen von SQL Server 2017 CTP 2,0 oder höher installiert werden.

Wenn Sie eine Vorabversion von SQL Server 2017 auf einem Computer ohne Internet Zugriff installieren, kann das Installationsprogramm möglicherweise die Seite nicht anzeigen, auf der Sie zur Eingabe des Speicher Orts der heruntergeladenen python-Komponenten aufgefordert werden. In einer solchen Instanz können Sie das Machine Learning Services Feature installieren, aber nicht die python-Komponenten.

Dieses Problem wurde in der Releaseversion korrigiert. Außerdem gilt diese Einschränkung nicht für R-Komponenten.

**Gilt für:** SQL Server 2017 mit python

### <a name="bkmk_sqlbindr"></a>Warnung der inkompatiblen Version beim Herstellen einer Verbindung mit einer älteren Version von SQL Server R Services von einem Client mithilfe von[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]

Wenn Sie R-Code in einem SQL Server 2016-computekontext ausführen, wird möglicherweise der folgende Fehler angezeigt:

> *Sie führen Version 9.0.0 von Microsoft R Client auf Ihrem Computer aus. Diese ist nicht mit der Microsoft R Server-Version 8.0.3 kompatibel. Laden Sie eine kompatible Version herunter und installieren Sie sie.*

Diese Meldung wird angezeigt, wenn eine der beiden folgenden Anweisungen den Wert true hat.

+ Sie haben R Server (eigenständig) auf einem Client Computer mithilfe des Setup-Assistenten [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]für installiert.
+ Sie haben Microsoft R Server mithilfe des [separaten Windows Installer](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows)installiert.

Um sicherzustellen, dass der Server und der Client dieselbe Version verwenden, müssen Sie möglicherweise eine _Bindung_verwenden, die für die Versionen Microsoft R Server 9,0 und höher unterstützt wird, um die R-Komponenten in SQL Server 2016-Instanzen zu aktualisieren. Informationen zum ermitteln, ob die Unterstützung für Upgrades für Ihre Version von r Services verfügbar ist, finden Sie unter [Aktualisieren einer Instanz von r Services mithilfe von sqlbindr. exe](install/upgrade-r-and-python.md).

**Gilt für:** SQL Server 2016 R Services mit R Server Version 9.0.0 oder früher

### <a name="7-setup-for-sql-server-2016-service-releases-might-fail-to-install-newer-versions-of-r-components"></a>7. Setup für SQL Server 2016 Service Releases kann unter Umständen keine neueren R-Komponenten installieren

Wenn Sie ein kumulatives Update installieren oder eine Service Pack für SQL Server 2016 auf einem Computer installieren, der nicht mit dem Internet verbunden ist, zeigt der Setup-Assistent möglicherweise nicht die Aufforderung an, mit der Sie die R-Komponenten mithilfe heruntergeladener CAB-Dateien aktualisieren können. Dieser Fehler tritt normalerweise auf, wenn mehrere Komponenten in Verbindung mit der Datenbank-Engine installiert wurden.

Um dieses Problem zu umgehen, können Sie die Dienst Freigabe mithilfe der Befehlszeile installieren und das `MRCACHEDIRECTORY` -Argument angeben, wie im folgenden Beispiel gezeigt, mit dem CU1-Updates installiert werden:

`C:\<path to installation media>\SQLServer2016-KB3164674-x64.exe /Action=Patch /IACCEPTROPENLICENSETERMS /MRCACHEDIRECTORY=<path to CU1 CAB files>`

Informationen zu den neuesten Installationsprogrammen finden Sie unter [Installieren von Machine Learning-Komponenten ohne Internet Zugriff](install/sql-ml-component-install-without-internet-access.md).

**Gilt für:** SQL Server 2016 R Services mit R Server Version 9.0.0 oder früher

### <a name="8-launchpad-services-fails-to-start-if-the-version-is-different-from-the-r-version"></a>8. Launchpad-Dienste können nicht gestartet werden, wenn sich die Version von der R-Version unterscheidet.

Wenn Sie SQL Server R Services getrennt von der Datenbank-Engine installieren und die Buildversionen unterschiedlich sind, wird möglicherweise der folgende Fehler im System Ereignisprotokoll angezeigt:

> *Der SQL Server-Launchpad-Dienst konnte aufgrund des folgenden Fehlers nicht gestartet werden: Der Dienst hat nicht rechtzeitig auf die Start-oder Steuerungs Anforderung geantwortet.*

Dieser Fehler kann z. b. auftreten, wenn Sie die Datenbank-Engine mithilfe der Releaseversion installieren, einen Patch anwenden, um die Datenbank-Engine zu aktualisieren, und dann die R Services-Funktion mithilfe der Releaseversion hinzufügen.

Um dieses Problem zu vermeiden, verwenden Sie ein Hilfsprogramm wie den Datei-Manager, um die Versionen von "launchpad. exe" mit einer Version von SQL-Binärdateien wie "sqldk. dll" zu vergleichen. Alle Komponenten sollten dieselbe Versionsnummer aufweisen. Wenn Sie eine Komponente aktualisieren, müssen Sie dasselbe Upgrade auf alle anderen installierten Komponenten anwenden.

Suchen Sie im `Binn` Ordner für die-Instanz nach launchpad. In einer Standardinstallation von SQL Server 2016 lautet der Pfad `C:\Program Files\Microsoft SQL Server\MSSQL.13.InstanceNameMSSQL\Binn`z. b. 

### <a name="9-remote-compute-contexts-are-blocked-by-a-firewall-in-sql-server-instances-that-are-running-on-azure-virtual-machines"></a>9. Remotecomputekontexte werden von einer Firewall in SQL Server Instanzen blockiert, die auf virtuellen Azure-Computern ausgeführt werden.

Wenn Sie auf einem [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] virtuellen Azure-Computer installiert haben, sind Sie möglicherweise nicht in der Lage, computekontexte zu verwenden, die die Verwendung des Arbeitsbereichs des virtuellen Computers erfordern. Der Grund hierfür ist, dass die Firewall auf virtuellen Azure-Computern standardmäßig eine Regel enthält, die den Netzwerk Zugriff für lokale R-Benutzerkonten blockiert.

Um dieses Problem zu umgehen, öffnen Sie auf der Azure-VM **Windows-Firewall mit**erweiterter Sicherheit, wählen Sie **ausgehende Regeln**aus, und deaktivieren Sie die folgende Regel: **Blockieren Sie den Netzwerk Zugriff für lokale R-Benutzerkonten in SQL Server MSSQLSERVER-Instanz**. Sie können auch die Regel aktiviert lassen, aber die Sicherheits Eigenschaft ändern, um **if Secure zuzulassen**.

### <a name="10-implied-authentication-in-sqlexpress"></a>10. Implizite Authentifizierung in SQLEXPRESS

Wenn Sie R-Aufträge von einer Remote-Data Science-Arbeitsstation mithilfe der integrierten Windows-Authentifizierung ausführen, verwendet SQL Server die *implizite Authentifizierung* , um lokale ODBC-Aufrufe zu generieren, die möglicherweise vom Skript benötigt werden. Im RTM-Build der SQL Server Express Edition funktionierte diese Funktion jedoch nicht.

Um das Problem zu beheben, empfehlen wir die Aktualisierung auf ein neueres Service Release.

Wenn das Upgrade nicht möglich ist, verwenden Sie als Problem Umgehung eine SQL-Anmeldung, um Remote-R-Aufträge auszuführen, die möglicherweise eingebettete ODBC-Aufrufe erfordern.

**Gilt für:** SQL Server 2016 R Services Express Edition

### <a name="11-performance-limits-when-libraries-used-by-sql-server-are-called-from-other-tools"></a>11. Leistungs Limits, wenn von SQL Server verwendete Bibliotheken von anderen Tools aufgerufen werden

Es ist möglich, die Machine Learning-Bibliotheken, die für SQL Server installiert sind, aus einer externen Anwendung (z. b. rgui) aufzurufen. Dies ist möglicherweise die einfachste Möglichkeit, bestimmte Aufgaben zu erledigen, z. b. das Installieren neuer Pakete oder das Ausführen von Ad-hoc-Tests für sehr kurze Codebeispiele. Allerdings kann die Leistung außerhalb der SQL Server beschränkt werden. 

Wenn Sie z. b. die Enterprise Edition von SQL Server verwenden, wird r im Single Thread-Modus ausgeführt, wenn Sie Ihren R-Code mithilfe externer Tools ausführen. Um die Vorteile der Leistung in SQL Server zu erzielen, initiieren Sie eine SQL Server Verbindung, und verwenden Sie [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) , um die externe Skript Laufzeit aufzurufen.

Vermeiden Sie im Allgemeinen das Aufrufen der Machine Learning-Bibliotheken, die von SQL Server von externen Tools verwendet werden. Wenn Sie R-oder python-Code Debuggen müssen, ist es in der Regel einfacher, dies außerhalb der SQL Server zu tun. Zum erhalten derselben Bibliotheken in SQL Server können Sie Microsoft R Client, [SQL Server 2017 Machine Learning Server (eigenständig)](install/sql-machine-learning-standalone-windows-install.md)oder [SQL Server 2016 R Server (eigenständig)](install/sql-r-standalone-windows-install.md)installieren.

### <a name="12-sql-server-data-tools-does-not-support-permissions-required-by-external-scripts"></a>12. SQL Server Data Tools unterstützt keine Berechtigungen, die für externe Skripts erforderlich sind.

Wenn Sie Visual Studio oder SQL Server Data Tools zum Veröffentlichen eines Datenbankprojekts verwenden, erhalten Sie möglicherweise eine Fehlermeldung wie die folgende, wenn ein Prinzipal über Berechtigungen verfügt, die für die Ausführung externer Skripts spezifisch sind:

> *"T"-Modell: Beim Reverse Engineering der Datenbank wurde ein Fehler erkannt. Die Berechtigung wurde nicht erkannt und wurde nicht importiert.*

Das dacpac-Modell unterstützt derzeit nicht die von R Services oder Machine Learning Services verwendeten Berechtigungen, z. b. das erteilen externer Skripts oder das Ausführen externer Skripts. Dieses Problem wird in einer künftigen Version behoben werden.

Um dieses Problem zu umgehen, führen Sie die zusätzlichen GRANT-Anweisungen in einem Skript nach der Bereitstellung aus.

### <a name="13-external-script-execution-is-throttled-due-to-resource-governance-default-values"></a>13. Die externe Skriptausführung wird aufgrund von ressourcengovernance-Standardwerten gedrosselt.

In Enterprise Edition können Sie Ressourcenpools verwenden, um externe Skriptprozesse zu verwalten. In einigen frühen Releasebuilds war der maximale Arbeitsspeicher, der den R-Prozessen zugewiesen werden konnte, 20%. Wenn der Server also 32 GB RAM hat, können die ausführbaren R-Dateien ("RTERM. exe" und "bxlserver. exe") maximal 6,4 GB in einer einzelnen Anforderung verwenden.

Wenn Ressourcenbeschränkungen auftreten, überprüfen Sie die aktuelle Standardeinstellung. Wenn 20 Prozent nicht ausreichen, finden Sie weitere Informationen zum [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ändern dieses Werts in der Dokumentation zu.

**Gilt für:** SQL Server 2016 R Services, Enterprise Edition

## <a name="r-script-execution-issues"></a>Probleme mit der R-Skriptausführung

Dieser Abschnitt enthält bekannte Probleme, die für die Ausführung von r auf SQL Server spezifisch sind, sowie einige Probleme im Zusammenhang mit den R-Bibliotheken und-Tools, die von Microsoft, einschließlich revoscaler, veröffentlicht werden.

Weitere bekannte Probleme, die sich auf R-Lösungen auswirken können, finden Sie auf der [Machine Learning Server](https://docs.microsoft.com/machine-learning-server/resources-known-issues) -Website.

### <a name="1-access-denied-warning-when-executing-r-scripts-on-sql-server-in-a-non-default-location"></a>1. Zugriffs Verweigerungs Warnung beim Ausführen von R-Skripts auf SQL Server an einem nicht standardmäßigen Speicherort

Wenn die Instanz von SQL Server an einem nicht standardmäßigen Speicherort (z. b. außerhalb des `Program Files` Ordners) installiert wurde, wird die Warnung ACCESS_DENIED ausgelöst, wenn Sie versuchen, Skripts auszuführen, mit denen ein Paket installiert wird. Zum Beispiel:

> *In `normalizePath(path.expand(path), winslash, mustWork)` : Pfad [2] = "~ externallibraries/R/8/1": Zugriff verweigert*

Der Grund hierfür ist, dass eine R-Funktion versucht, den Pfad zu lesen, und einen Fehler erzeugt, wenn die integrierte Benutzergruppe **sqlrusergroup**keinen Lesezugriff hat. Die Warnung, die ausgelöst wird, blockiert nicht die Ausführung des aktuellen r-Skripts. die Warnung kann jedoch immer wiederholt auftreten, wenn der Benutzer ein anderes r-Skript ausführt.

Wenn Sie SQL Server am Standard Speicherort installiert haben, tritt dieser Fehler nicht auf, da alle Windows-Benutzer über Leseberechtigungen für `Program Files` den Ordner verfügen.

Dieses Problem wurde in einer bevorstehenden Dienst Version behandelt. Um dieses Problem zu umgehen, stellen Sie die Gruppe **sqlrusergroup**mit Lesezugriff für alle übergeordneten `ExternalLibraries`Ordner von bereit.

### <a name="2-serialization-error-between-old-and-new-versions-of-revoscaler"></a>2. Serialisierungsfehler zwischen alten und neuen Versionen von revoscaler

Wenn Sie ein Modell mit einem serialisierten Format an eine Remote SQL Server-Instanz übergeben, wird möglicherweise der folgende Fehler angezeigt: 

> *Fehler in memdecompress (Data, Type = DECOMPRESS) interner Fehler-3 in memdecompress (2).*

Dieser Fehler wird ausgelöst, wenn Sie das Modell mit einer neueren Version der Serialisierungsfunktion, [rxserializemodel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel), gespeichert haben, aber die SQL Server Instanz, auf der Sie das Modell deserialisieren, über eine ältere Version der revoscaler-APIs verfügt, von SQL Server 2017 Cu2 oder früher.

Um dieses Problem zu umgehen, können Sie die SQL Server 2017-Instanz auf CU3 oder höher aktualisieren.

Der Fehler wird nicht angezeigt, wenn die API-Version identisch ist, oder wenn Sie ein Modell, das mit einer älteren Serialisierungsfunktion gespeichert ist, auf einen Server verschieben, auf dem eine neuere Version der serialisierungsapi verwendet wird.

Mit anderen Worten: Verwenden Sie die gleiche Version von revoscaler für Serialisierungs-und Deserialisierungsvorgänge.

### <a name="3-real-time-scoring-does-not-correctly-handle-the-_learningrate_-parameter-in-tree-and-forest-models"></a>3. Bei der Echtzeitbewertung wird der _learningrate_ -Parameter in Struktur-und Gesamtstruktur Modellen nicht ordnungsgemäß behandelt.

Wenn Sie ein Modell mithilfe einer Entscheidungsstruktur oder Entscheidungsstruktur Methode erstellen und die Lernrate angeben, werden möglicherweise inkonsistente Ergebnisse bei `sp_rxpredict` der Verwendung von `PREDICT` oder der SQL-Funktion im `rxPredict`Vergleich zur Verwendung von angezeigt.

Die Ursache ist ein Fehler in der API, die serialisierte Modelle verarbeitet und auf den `learningRate` Parameter beschränkt ist, z. b. in [rxbtrees](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxbtrees)oder

Dieses Problem wird in einer bevorstehenden Dienst Version behandelt.

### <a name="4-limitations-on-processor-affinity-for-r-jobs"></a>4. Einschränkungen der Prozessoraffinität für R-Aufträge

Im ersten Releasebuild von SQL Server 2016 konnten Sie die Prozessor Affinität nur für CPUs in der ersten k-Gruppe festlegen. Wenn es sich bei dem Server z. b. um einen 2-Socket-Computer mit zwei k-Gruppen handelt, werden nur Prozessoren der ersten k-Gruppe für die R-Prozesse verwendet. Die gleiche Einschränkung gilt, wenn Sie die Ressourcenkontrolle für R-Skript Aufträge konfigurieren.

Dieses Problem wurde in SQL Server 2016 Service Pack 1 behoben. Es wird empfohlen, ein Upgrade auf die neueste Dienst Version durchzuführen.

**Gilt für:** RTM-Version SQL Server 2016 R Services

### <a name="5-changes-to-column-types-cannot-be-performed-when-reading-data-in-a-sql-server-compute-context"></a>5. Änderungen an Spaltentypen nicht möglich, wenn Daten in SQL Server-Rechenkontext gelesen werden

Wenn der Rechenkontext auf die SQL Server-Instanz festgelegt ist, können Sie das Argument _ColClasses_ (oder andere ähnliche Argumente) nicht verwenden, um den Datentyp von Spalten in Ihrem R-Code zu ändern.

Die folgende Anweisung würde beispielsweise zu einem Fehler würden, wenn die Spalte CRSDepTimeStr keine Ganzzahl ist:

```R
data <- RxSqlServerData(
  sqlQuery = "SELECT CRSDepTimeStr, ArrDelay  FROM AirlineDemoSmall", 
  connectionString = connectionString, 
  colClasses = c(CRSDepTimeStr = "integer"))
```

Um dieses Problem zu umgehen, können Sie die SQL-Abfrage so umschreiben, dass Sie CAST oder Convert verwendet und die Daten mithilfe des richtigen Datentyps in R darstellen. Im Allgemeinen ist die Leistung besser, wenn Sie mit SQL arbeiten, anstatt Daten im R-Code zu ändern.

**Gilt für:** SQL Server 2016 R-Dienste

### <a name="6-limits-on-size-of-serialized-models"></a>6. Beschränkung der Größe serialisierter Modelle

Wenn Sie ein Modell in einer SQL Server Tabelle speichern, müssen Sie das Modell serialisieren und es in einem Binärformat speichern. Theoretisch ist die maximale Größe eines Modells, das mit dieser Methode gespeichert werden kann, 2 GB. Dies ist die maximale Größe von varbinary-Spalten in SQL Server.

Wenn Sie größere Modelle verwenden müssen, sind die folgenden Problem Umgehungen verfügbar:

+ Führen Sie Schritte aus, um die Größe des Modells zu verringern. Einige Open Source-R-Pakete enthalten zahlreiche Informationen im Modell Objekt, und viele dieser Informationen können für die Bereitstellung entfernt werden. 
+ Verwenden Sie die Funktionsauswahl, um unnötige Spalten zu entfernen.
+ Wenn Sie einen Open Source-Algorithmus verwenden, sollten Sie eine ähnliche Implementierung verwenden, indem Sie den entsprechenden Algorithmus in microsoftml oder revoscaler verwenden. Diese Pakete wurden für Bereitstellungs Szenarien optimiert.
+ Nachdem das Modell rationalisiert wurde und die Größe mit den vorangehenden Schritten reduziert wurde, finden Sie Informationen dazu, ob die [memcompress](https://www.rdocumentation.org/packages/base/versions/3.4.1/topics/memCompress) -Funktion in Base R verwendet werden kann, um die Größe des Modells zu verringern, bevor es an SQL Server übergeben wird. Diese Option ist am besten geeignet, wenn das Modell in der Nähe des Limits von 2 GB liegt.
+ Bei größeren Modellen können Sie die SQL Server [FILETABLE](../relational-databases/blob/filetables-sql-server.md) -Funktion verwenden, um die Modelle zu speichern, anstatt eine varbinary-Spalte zu verwenden.

    Um filetables verwenden zu können, müssen Sie eine Firewallausnahme hinzufügen, da die in filetables gespeicherten Daten in SQL Server vom FILESTREAM-Dateisystem Treiber verwaltet werden und die standardmäßigen Firewallregeln den Zugriff auf Netzwerkdateien blockieren. Weitere Informationen finden Sie unter Aktivieren der erforderlichen Komponenten [für FILETABLE](../relational-databases/blob/enable-the-prerequisites-for-filetable.md).

    Nachdem Sie FILETABLE aktiviert haben, um das Modell zu schreiben, erhalten Sie mithilfe der FILETABLE-API einen Pfad von SQL, und schreiben Sie dann das Modell aus dem Code in diesen Speicherort. Wenn Sie das Modell lesen müssen, erhalten Sie den Pfad von SQL, und Sie können das Modell mit dem Pfad aus dem Skript abrufen. Weitere Informationen finden Sie unter [zugreifen auf filetables mit Dateieingabe-Ausgabe-APIs](../relational-databases/blob/access-filetables-with-file-input-output-apis.md).

### <a name="7-avoid-clearing-workspaces-when-you-execute-r-code-in-a-includessnoversionincludesssnoversion-mdmd-compute-context"></a>7. Vermeiden Sie das Löschen von Arbeitsbereichen beim Ausführen von R [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Code in einem computekontext.

Wenn Sie einen r-Befehl verwenden, um den Arbeitsbereich von Objekten beim Ausführen von r [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Code in einem computekontext zu löschen, oder wenn Sie den Arbeitsbereich als Teil eines R-Skripts mit dem Namen [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)löschen, wird möglicherweise der folgende Fehler angezeigt: *Arbeitsbereich das Objekt "revoscriptconnection" wurde nicht gefunden* .

`revoScriptConnection` ist ein Objekt im R-Arbeitsbereich, das Informationen über eine R-Sitzung enthält, die aus [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]aufgerufen wird. Wenn Ihr R-Code jedoch einen Befehl zum Löschen des Arbeitsbereichs enthält (wie z.B. `rm(list=ls()))`), werden alle Informationen über die Sitzung und andere Objekte im R-Arbeitsbereich ebenfalls gelöscht.

Um dieses Problem zu umgehen, vermeiden Sie das willkürliche Löschen von Variablen und anderen Objekten während der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Ausführung von R in. Obwohl das Löschen des Arbeitsbereichs bei der Arbeit in der R-Konsole üblich ist, kann dies unbeabsichtigte Folgen haben.

* Um bestimmte Variablen zu löschen, verwenden Sie `remove` die R-Funktion: z. b.`remove('name1', 'name2', ...)`
* Wenn mehrere zu löschende Variablen vorhanden sind, speichern Sie die Namen temporärer Variablen in einer Liste und führen eine regelmäßige automatische Speicherbereinigung durch.

### <a name="8-restrictions-on-data-that-can-be-provided-as-input-to-an-r-script"></a>8. Einschränkungen von Daten, die als Eingabe für ein R-Skript bereitgestellt werden können

Sie können die folgenden Typen von Abfrageergebnissen nicht in einem R-Skript verwenden:

- Daten aus einer [!INCLUDE[tsql](../includes/tsql-md.md)] -Abfrage, die auf „AlwaysEncrypted“-Spalten verweist.
  
- Daten aus einer [!INCLUDE[tsql](../includes/tsql-md.md)] -Abfrage, die auf maskierte Spalten verweist.
  
     Wenn Sie maskierte Daten in einem R-Skript verwenden müssen, ist eine mögliche Problemumgehung das Erstellen einer Kopie der Daten in einer temporären Tabelle und anschließende Verwenden dieser Daten.

### <a name="9-use-of-strings-as-factors-can-lead-to-performance-degradation"></a>9. Die Verwendung von Zeichen folgen als Faktoren kann zu Leistungseinbußen führen.

Die Verwendung von Zeichen folgen-Typvariablen als Faktoren kann die Menge an Arbeitsspeicher für R-Vorgänge erheblich erhöhen. Dies ist ein bekanntes Problem mit R im Allgemeinen, und es gibt viele Artikel zu diesem Thema. Beispiel: [Faktoren sind keine erstklassigen Bürger in r, von John Mount, R-Blogger)](https://www.r-bloggers.com/factors-are-not-first-class-citizens-in-r/) oder [stringsasfactors: Eine nicht autorisierte Biographie von Roger PG](https://simplystatistics.org/2015/07/24/stringsasfactors-an-unauthorized-biography/). 

Obwohl das Problem nicht spezifisch für SQL Server ist, kann sich dies erheblich auf die Leistung von R-Code auswirken, der in SQL Server ausgeführt wird. Zeichen folgen werden in der Regel als "varchar" oder "nvarchar" gespeichert, und wenn eine Spalte mit Zeichen folgen Daten viele eindeutige Werte aufweist, kann der Prozess der internen Typzuordnung in ganze Zahlen und zurück in Zeichen folgen durch R sogar zu Fehlern bei der Speicher Belegung führen.

Wenn Sie nicht unbedingt einen Zeichen folgen-Datentyp für andere Vorgänge benötigen, ist die Zuordnung der Zeichen folgen Werte zu einem numerischen Datentyp (Integer) als Teil der Daten Vorbereitung aus Leistungs-und Skalierungs Perspektive vorteilhaft.

Eine Erörterung dieses Problems und weitere Tipps finden Sie unter [Leistung für R Services-Daten Optimierung](r/r-and-data-optimization-r-services.md).

### <a name="10-arguments-varstokeep-and-varstodrop-are-not-supported-for-sql-server-data-sources"></a>10. Die Argumente *varstokeep* und *varstodrop* werden für SQL Server Datenquellen nicht unterstützt.

Wenn Sie die Funktion rxdatastep verwenden, um Ergebnisse in eine Tabelle zu schreiben, ist die Verwendung von *varstokeep* und *varstodrop* eine praktische Möglichkeit, um die Spalten anzugeben, die als Teil des Vorgangs eingeschlossen oder ausgeschlossen werden sollen. Diese Argumente werden jedoch für SQL Server Datenquellen nicht unterstützt.

### <a name="11-limited-support-for-sql-data-types-in-sp_execute_external_script"></a>11. Eingeschränkte Unterstützung für SQL-Datentypen\_in\_SP\_-Ausführungs externen Skripts

Nicht alle Datentypen, die in SQL unterstützt werden, können in R verwendet werden. Um dieses Problem zu umgehen, sollten Sie den nicht unterstützten Datentyp in einen unterstützten Datentyp umwandeln,\_bevor\_Sie\_die Daten an das externe Skript ausführen.

Weitere Informationen finden Sie unter [R-Bibliotheken und-Datentypen](r/r-libraries-and-data-types.md).

### <a name="12-possible-string-corruption-using-unicode-strings-in-varchar-columns"></a>12. Mögliche Zeichen folgen Beschädigung mithilfe von Unicode-Zeichen folgen in varchar-Spalten

Das übergeben von Unicode-Daten in varchar-Spalten von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] an R/python kann zu einer Beschädigung der Zeichenfolge führen. Dies liegt daran, dass die Codierung für diese Unicode- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Zeichenfolge in Sortierungen möglicherweise nicht mit der in R/python verwendeten standardmäßigen UTF-8-Codierung identisch ist. 

Verwenden Sie die UTF-8-Codierung ( [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] in [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]verfügbar), oder verwenden Sie den nvarchar-Typ für denselben, um nicht-ASCII-Zeichen folgen Daten von an R/python zu senden.

### <a name="13-only-one-value-of-type-raw-can-be-returned-from-sp_execute_external_script"></a>13. Es kann nur ein Wert `raw` des Typs zurückgegeben werden.`sp_execute_external_script`

Wenn ein binärer Datentyp (der r-rohdatentyp) von r zurückgegeben wird, muss der Wert im Ausgabedaten Rahmen gesendet werden.

Bei anderen Datentypen als **RAW**können Sie Parameterwerte zusammen mit den Ergebnissen der gespeicherten Prozedur zurückgeben, indem Sie das OUTPUT-Schlüsselwort hinzufügen. Weitere Informationen finden Sie unter [Parameter](https://docs.microsoft.com/sql/relational-databases/stored-procedures/parameters).

Wenn Sie mehrere Ausgabe Sätze verwenden möchten, die Werte des Typs **RAW**enthalten, besteht eine mögliche Problem Umgehung darin, mehrere Aufrufe der gespeicherten Prozedur auszuführen oder die Resultsets mithilfe von ODBC zurück an zu [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] senden.

### <a name="14-loss-of-precision"></a>14. Genauigkeitsverlust

Da [!INCLUDE[tsql](../includes/tsql-md.md)] und R verschiedene Datentypen unterstützen, kann es bei der Konvertierung bei numerischen Datentypen zu einem Genauigkeits Verlust kommen.

Weitere Informationen zur impliziten Datentyp Konvertierung finden Sie unter [R-Bibliotheken und-Datentypen](r/r-libraries-and-data-types.md).

### <a name="15-variable-scoping-error-when-you-use-the-transformfunc-parameter"></a>15. Variablen Bereichs Fehler bei Verwendung des transformfunc-Parameters

Zum Transformieren von Daten während der Modellierung können Sie ein *transformfunc* -Argument in einer Funktion wie `rxLinmod` oder `rxLogit`übergeben. Allerdings können Aufrufe von in der SQL Server computekontext zu Bereichs Fehlern führen, selbst wenn die Aufrufe im lokalen computekontext ordnungsgemäß funktionieren.

> *Das Beispiel Dataset für die Analyse enthält keine Variablen.*

Angenommen, Sie haben zwei Funktionen definiert `f` , und `g`in Ihrer lokalen globalen Umgebung und `g` rufen `f`auf. Bei `g`verteilten oder Remote Aufrufen von kann der Aufruf von `g` mit diesem Fehler fehlschlagen, da `f` nicht gefunden werden kann, selbst wenn Sie sowohl `f` als `g` auch an den Remote Aufruf übermittelt haben.

Wenn dieses Problem auftritt, können Sie es umgehen, indem Sie die Definition von `f` innerhalb der Definition von `g`an einer Stelle einbetten, vor der `g` normalerweise `f`aufrufen würde.

Zum Beispiel:

```R
f <- function(x) { 2*x * 3 }
g <- function(y) {
              a <- 10 * y
               f(a)
}
```

Um den Fehler zu vermeiden, schreiben Sie die Definition wie folgt um:

```R
g <- function(y){
              f <- function(x) { 2*x +3}
              a <- 10 * y
              f(a)
}
```

### <a name="16-data-import-and-manipulation-using-revoscaler"></a>16. Importieren und Bearbeiten von Daten mithilfe von RevoScaleR

Wenn **varchar** -Spalten aus einer Datenbank gelesen werden, wird Leerraum gekürzt. Um dies zu verhindern, schließen Sie Zeichenfolgen in Zeichen ein, die keine Leerzeichen sind.

Wenn Funktionen wie `rxDataStep` zum Erstellen von Datenbanktabellen mit **varchar** -Spalten verwendet werden, wird die Spaltenbreite basierend auf einer Stichprobe der Daten geschätzt. Wenn die Breite variieren kann, kann es notwendig sein, alle Zeichen folgen auf eine gemeinsame Länge zu auffüllen.

Das Verwenden einer Transformation zum Ändern des Datentyps einer Variablen wird nicht unterstützt, wenn wiederholte Aufrufe von `rxImport` oder `rxTextToXdf` zum Importieren und Anfügen von Zeilen verwendet werden, wobei mehrere Eingabedateien zu einer einzelnen XDF-Datei kombiniert werden.

### <a name="17-limited-support-for-rxexec"></a>17. Eingeschränkte Unterstützung für rxexec

In SQL Server 2016 kann die `rxExec` Funktion, die vom revoscaler-Paket bereitgestellt wird, nur im Single Thread-Modus verwendet werden.

### <a name="18-increase-the-maximum-parameter-size-to-support-rxgetvarinfo"></a>18. Erhöhen Sie die maximale Parameter Größe zur Unterstützung von rxgetvarinfo.

Wenn Sie Datasets mit extrem vielen Variablen verwenden (z. b `max-ppsize` `rxGetVarInfo`. über 40.000), legen Sie das-Flag beim Starten von R fest, um Funktionen wie zu verwenden. Das `max-ppsize` -Flag gibt die maximale Pointer Protection Stack-Größe an.

Wenn Sie die R-Konsole verwenden (z. b. "rgui. exe" oder "RTERM. exe"), können Sie den Wert von " _Max-ppsize_ " auf "500000" festlegen, indem Sie Folgendes eingeben:

```R
R --max-ppsize=500000
```

### <a name="19-issues-with-the-rxdtree-function"></a>19. Probleme mit der rxdtree-Funktion

Die `rxDTree` -Funktion unterstützt derzeit keine formelinternen Transformationen. Insbesondere das Verwenden der `F()` -Syntax zum Erstellen von Faktoren bei laufendem Betrieb wird nicht unterstützt. Numerische Daten werden jedoch automatisch klassifiziert.

Geordnete Faktoren werden in allen RevoScaleR-Analysefunktionen außer `rxDTree`genauso wie Faktoren behandelt.

### <a name="20-datatable-as-an-outputdataset-in-r"></a>20. Data. Table als outputdataset in R

`data.table` Die`OutputDataSet` Verwendung von als in R wird im kumulativen Update 13 (CU13) von SQL Server 2017 und früher nicht unterstützt. Möglicherweise wird die folgende Meldung angezeigt:

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

`data.table`ein `OutputDataSet` in R wird in 2017 SQL Server kumulativem Update 14 (CU14) und höher unterstützt.

## <a name="python-script-execution-issues"></a>Probleme bei der python-Skriptausführung

Dieser Abschnitt enthält bekannte Probleme, die für die Ausführung von python auf SQL Server gelten, sowie Probleme im Zusammenhang mit den von Microsoft veröffentlichten Python-Paketen, einschließlich [revoscalepy](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package) und [microsoftml](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package).

### <a name="1-call-to-pretrained-model-fails-if-path-to-model-is-too-long"></a>1. Der aufzurufende Modell Vorgang schlägt fehl, wenn der Pfad zum Modell zu lang ist.

Wenn Sie die vortrainierten Modelle in einer frühen Version von SQL Server 2017 installiert haben, ist der gesamte Pfad zur trainierten Modelldatei möglicherweise zu lang für das Lesen von Python. Diese Einschränkung wird in einer späteren Dienst Version korrigiert.

Es gibt mehrere mögliche Problem Umgehungen: 

+ Wenn Sie die vorab trainierten Modelle installieren, wählen Sie einen benutzerdefinierten Speicherort aus.
+ Installieren Sie nach Möglichkeit die SQL Server Instanz unter einem benutzerdefinierten Installationspfad mit einem kürzeren Pfad, z. b. c:\sql\mssql14. MSSQLSERVER.
+ Verwenden Sie das Windows-Hilfsprogramm [fsutil](https://technet.microsoft.com/library/cc788097(v=ws.11).aspx) , um einen festen Link zu erstellen, der die Modelldatei einem kürzeren Pfad zuordnet.
+ Aktualisieren Sie auf die neueste Dienst Version.

### <a name="2-error-when-saving-serialized-model-to-sql-server"></a>2. Fehler beim Speichern des serialisierten Modells in SQL Server

Wenn Sie ein Modell an eine Remote SQL Server-Instanz übergeben und versuchen, das binäre Modell mithilfe der `rx_unserialize` -Funktion in [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package)zu lesen, erhalten Sie möglicherweise die folgende Fehlermeldung: 

> *NameError: der Name "rx_unserialize_model" ist nicht definiert.*

Dieser Fehler wird ausgelöst, wenn Sie das Modell mit einer neueren Version der Serialisierungsfunktion gespeichert haben, aber die SQL Server Instanz, auf der Sie das Modell deserialisieren, die serialisierungsapi nicht erkennt.

Um das Problem zu beheben, führen Sie ein Upgrade der SQL Server 2017-Instanz auf CU3 oder höher aus.

### <a name="3-failure-to-initialize-a-varbinary-variable-causes-an-error-in-bxlserver"></a>3. Fehler beim Initialisieren einer varbinary-Variablen verursachen einen Fehler in bxlserver

Wenn Sie Python-Code in SQL Server mit `sp_execute_external_script`ausführen und der Code Ausgabevariablen vom Typ varbinary (max), varchar (max) oder ähnliche Typen aufweist, muss die Variable als Teil des Skripts initialisiert oder festgelegt werden. Andernfalls löst die Datenaustausch Komponente bxlserver einen Fehler aus und funktioniert nicht mehr.

Diese Einschränkung wird in einer bevorstehenden Dienst Version korrigiert. Um dieses Problem zu umgehen, stellen Sie sicher, dass die Variable innerhalb des python-Skripts initialisiert wird. Jeder gültige Wert kann verwendet werden, wie in den folgenden Beispielen:

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

### <a name="4-telemetry-warning-on-successful-execution-of-python-code"></a>4. Telemetriewarnung bei erfolgreicher Ausführung von Python-Code

Ab SQL Server 2017 Cu2 wird möglicherweise die folgende Meldung angezeigt, auch wenn Python-Code anderweitig erfolgreich ausgeführt wird:

> *Stderr-Meldung (en) aus dem externen Skript:* 
>  *~ PYTHON_SERVICES\lib\site-packages\revoscalepy\utils\RxTelemetryLogger*
> *syntaxwarning: telemetry_state wird vor der globalen Deklaration verwendet* .

Dieses Problem wurde in SQL Server kumulativem Update 3 (CU3) von 2017 behoben. 

### <a name="5-numeric-decimal-and-money-data-types-not-supported"></a>5. Numerische, dezimale und Money-Datentypen werden nicht unterstützt.

Ab 2017 SQL Server kumulative Update 12 (CU12), numeric-, Decimal-und Money-Datentypen in mit Resultsets werden bei Verwendung `sp_execute_external_script`von Python mit nicht unterstützt. Möglicherweise werden folgende Meldungen angezeigt:

> *Ordnung 39004, SQL-Status: S1000] ein Python-Skript Fehler ist während der Ausführung of'sp_execute_external_script "mit HRESULT 0x80004004 aufgetreten.*

> *Ordnung 39019, SQL-Status: S1000] ein externer Skript Fehler ist aufgetreten:*
> 
> *Sqlsatellitecallfehler: Nicht unterstützter Typ im Ausgabe Schema. Unterstützte Typen: bit, smallint, int, DateTime, smallmoney, Real und float. Char, varchar wird teilweise unterstützt.*

Dies wurde in SQL Server kumulativen Update 14 (CU14) von 2017 korrigiert.

### <a name="6-bad-interpreter-error-when-installing-python-packages-with-pip-on-linux"></a>6. Ungültiger interpreterfehler beim Installieren von Python-Paketen mit PIP unter Linux. 

Auf SQL Server 2019, wenn Sie versuchen, **PIP**zu verwenden. Zum Beispiel:

```bash
/opt/mssql/mlservices/runtime/python/bin/pip -h
```

Diese Fehlermeldung wird angezeigt:

> *bash:/opt/MSSQL/mlservices/Runtime/python/bin/PIP:/opt/Microsoft/mlserver/9.4.7/bin/python/python: Ungültiger Interpreter: Datei oder Verzeichnis nicht.*

**Problemumgehung**

Installieren von **PIP** von der [Python-Paket Autorität (pypa)](https://www.pypa.io):

```bash
wget 'https://bootstrap.pypa.io/get-pip.py' 
/opt/mssql/mlservices/bin/python/python ./get-pip.py 
```

**Empfehlung**

Weitere Informationen finden Sie [unter Installieren von Python-Paketen mit sqlmlutils](package-management/install-additional-python-packages-on-sql-server.md).

**Gilt für:** SQL Server 2019 unter Linux

## <a name="revolution-r-enterprise-and-microsoft-r-open"></a>Revolution R Enterprise und Microsoft R Open

In diesem Abschnitt werden Probleme aufgelistet, die für R-Konnektivität,-Entwicklung und-Leistungs Tools von Revolution Analytics spezifisch sind. Diese Tools wurden in früheren vorab Versionen von [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]bereitgestellt.

Im Allgemeinen wird empfohlen, dass Sie diese früheren Versionen deinstallieren und die neueste Version von SQL Server oder Microsoft R Server installieren.

### <a name="1-revolution-r-enterprise-is-not-supported"></a>1. Revolution R Enterprise wird nicht unterstützt.

Das parallele Installieren von [!INCLUDE[rsql_productname_md](../includes/rsql-productname-md.md)] Revolution R Enterprise mit einer beliebigen-Version wird nicht unterstützt.

Wenn Sie über eine vorhandene Lizenz für Revolution R Enterprise verfügen, müssen Sie Sie auf einem separaten Computer von der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Instanz und einer beliebigen Arbeitsstation ablegen, die Sie zum Herstellen einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Verbindung mit der Instanz verwenden möchten.

Einige vorab Versionen von [!INCLUDE[rsql_productname](../includes/rsql-productname-md.md)] enthielten eine R-Entwicklungsumgebung für Windows, die von Revolution Analytics erstellt wurde. Dieses Tool wird nicht mehr bereitgestellt und wird nicht unterstützt.

Aus Kompatibilitäts [!INCLUDE[rsql_productname](../includes/rsql-productname-md.md)]Gründen wird empfohlen, stattdessen Microsoft R Client zu installieren. [R Tools für Visual Studio](https://www.visualstudio.com/vs/rtvs/) und [Visual Studio Code](https://code.visualstudio.com/) unterstützt auch Microsoft R-Lösungen.

### <a name="2-compatibility-issues-with-sqlite-odbc-driver-and-revoscaler"></a>2. Kompatibilitätsprobleme mit SQLite-ODBC-Treiber und RevoScaleR

Revision 0,92 des SQLite-ODBC-Treibers ist mit revoscaler nicht kompatibel. Die Revisionen von 0,88-0,91 und 0,93 und höher sind bekanntermaßen kompatibel.

## <a name="next-steps"></a>Nächste Schritte

[Problembehandlung bei Machine Learning in SQL Server](machine-learning-troubleshooting-faq.md)
