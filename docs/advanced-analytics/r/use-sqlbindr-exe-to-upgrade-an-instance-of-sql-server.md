---
title: Upgrade von R und Python-Komponenten – SQL Server Machine Learning Services
description: Aktualisieren Sie R- und Python in SQL Server 2016-Services oder SQL Server 2017 Machine Learning Services verwenden von sqlbindr.exe zum Binden an Machine Learning-Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/30/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: da28d6f0ae423ce9cca0c6d571af944a2d7acd3d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62642063"
---
# <a name="upgrade-machine-learning-r-and-python-components-in-sql-server-instances"></a>Aktualisieren von Machine learning (R- und Python) Komponenten in SQL Server-Instanzen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

R und Python-Integration in SQL Server enthält Open Source- und Microsoft-eigenes Pakete. Unter der standardmäßigen SQL Server-Wartung, werden die Pakete entsprechend im Veröffentlichungszyklus von SQL Server mit Fehlerbehebungen, um vorhandene Pakete an die aktuelle Version, aber keine Upgrades von Hauptversionen aktualisiert. 

Es gibt jedoch viele Datenanalysten daran gewöhnt, mit der Arbeit mit neueren Pakete, sobald sie verfügbar sind. Für SQL Server 2017-Machine Learning Services (Datenbankintern) und SQL Server 2016 R Services (Datenbankintern), erhalten Sie [neuere Versionen von R und Python](#version-map) von *Bindung* zu **Microsoft Machine Learning-Server**. 

## <a name="what-is-binding"></a>Was ist Datenbindung?

Bindung ist ein Installationsprozess, die tauscht den Inhalt der Ordner R_SERVICES und PYTHON_SERVICES mit neueren ausführbare Dateien, Bibliotheken und tools von [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/index).

Zusammen mit aktualisierten Komponenten an, einen Switch im Wartungsmodus Modelle enthält. Anstelle von der [Produktlebenszyklus für SQL Server](https://support.microsoft.com/lifecycle/search?alpha=SQL%20Server%202017), mit [kumulativen Updates für SQL Server](https://support.microsoft.com/help/4047329/sql-server-2017-build-versions), Ihre Dienstupdates entsprechen nun die [support-Ablauffristen für Microsoft R Server und Computer Erlernen von Server](https://docs.microsoft.com/machine-learning-server/resources-servicing-support) auf die [modernen Lebenszyklus](https://support.microsoft.com/help/30881/modern-lifecycle-policy).

Mit Ausnahme der Versionen einer Komponente und Dienstupdates wird die Bindung nicht die Grundlagen der Installation geändert: Integration von R und Python gehört immer noch zu einer Datenbank-Engine-Instanz, Lizenzierung, bleibt unverändert (keine zusätzlichen Kosten Bindung) und SQL Server-Support-Richtlinien enthalten jedoch weiterhin für die Datenbank-Engine. Im weiteren Verlauf dieses Artikels wird der Mechanismus für die Bindung und deren Funktionsweise für jede Version von SQL Server erläutert.

> [!NOTE]
> Bindung gilt für (In-Database)-Instanzen, die mit SQL Server-Instanz gebunden sind. Bindung ist nicht relevant, für die Installation (Standalone).

**Überlegungen zu SQL Server 2017-Bindung**

Für SQL Server 2017 Machine Learning-Dienste würden Sie in Betracht ziehen Bindung nur, wenn Microsoft Machine Learning Server beginnt, um zusätzliche Pakete bieten oder neuere Versionen auf, was Sie bereits verfügen.

**Überlegungen zu SQL Server 2016-Bindung**

Für SQL Server 2016 R Services-Kunden, Bindung bietet aktualisierte R-Pakete, neue Pakete nicht Teil der ursprünglichen Installation ([MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)), und [pretrained Modelle](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models), alle können weitere sein. in jeder neuen Haupt- und Nebenversionen der Version von aktualisiert [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/index). Binden damit Sie Python-Unterstützung, keinen SQL Server 2017-Funktion. 

<a name="version-map"></a>

## <a name="version-map"></a>Version-Karte

Die folgende Tabelle enthält die Version Karte, Paketversionen über veröffentlichungswege zur, sodass Sie potenzielle Upgradepfade, beim Binden an Microsoft Machine Learning Server ermitteln können (vormals bekannt als R-Server, bevor Sie das Hinzufügen von Python-Unterstützung ab in 9.2.1 MLS) Vergleichbaren. 

Beachten Sie, dass die Bindung nicht mit die neueste Version von R oder Anaconda garantiert. Wenn Sie zu Microsoft Machine Learning Server (MLS) binden, erhalten Sie die R- oder Python-Version, die Setup installiert, die möglicherweise nicht die neueste Version sind im Web verfügbar.

[**SQL Server 2016 R Services**](../install/sql-r-services-windows-install.md)

Komponente |Erste Version | [R Server 9.0.1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows) | [R Server 9.1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows) | [MLS 9.2.1](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) | [MLS 9.3](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) |
----------|----------------|----------------|--------------|---------|-------|
Microsoft R Open (MRO) über R | R 3.2.2     | R 3.3.2   |R 3.3.3   | R 3.4.1  | R 3.4.3 |
[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) | 8.0.3  | 9.0.1 |  9.1 |  9.2.1 |  9.3 |
[MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)| Niederländische Antillen | 9.0.1 |  9.1 |  9.2.1 |  9.3 |
[vortrainierte Modelle](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models)| Niederländische Antillen | 9.0.1 |  9.1 |  9.2.1 |  9.3 |
[sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)| Niederländische Antillen | 1,0 |  1,0 |  1,0 |  1,0 |
[olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | Niederländische Antillen | 1,0 |  1,0 |  1,0 |  1,0 |


[**SQL Server 2017-Machine Learning-Dienste**](../install/sql-machine-learning-services-windows-install.md)

Komponente |Erste Version | MLS 9.3 | | | |
----------|----------------|---------|-|-|-|-|
Microsoft R Open (MRO) über R | R 3.3.3 | R 3.4.3 | | | |
[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) |   9.2 |  9.3 | | | |
[MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) | 9.2  | 9.3| | | |
[sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)| 1,0 |  1,0 | | | |
[olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | 1,0 |  1,0 | | | |
Anaconda 4.2 über Python 3.5  | 4.2/3.5.2 | 4.2/3.5.2 | | | |
[revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | 9.2  | 9.3| | | |
 [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | 9.2  | 9.3| | | |
[vortrainierte Modelle](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models) | 9.2 | 9.3| | | |

## <a name="how-component-upgrade-works"></a>Funktionsweise der Komponentenupgrade 

R und Python-Bibliotheken und ausführbaren Dateien werden aktualisiert, wenn Sie eine vorhandene Installation von R und Python, Machine Learning Server binden. Bindung wird ausgeführt, indem die [Microsoft Machine Learning Server-Installationsprogramm](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) beim Ausführen von Setup auf einer vorhandenen SQL Server-Datenbank-Engine-Instanz, entweder 2016 oder 2017, dass R oder Python-Integration. Setup erkennt die vorhandenen Features und fordert Sie auf, um Machine Learning Server erneut zu binden. 

Während der Bindung, die Inhalte von C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\R_SERVICES und \PYTHON_SERVICES wird mit dem neueren ausführbare Dateien und Bibliotheken mit c:\programme\microsoft\ml Server\R_SERVER und \PYTHON_SERVER überschrieben.

Zur gleichen Zeit wird der Dienstmodell auch aus SQL Server-Update-Mechanismen, häufiger Haupt- und Nebenversionsnummern Releasezyklus der Microsoft Machine Learning Server gespiegelt. Richtlinien zur Unterstützung der Wechsel ist, einer attraktiven Option für Data Science-Teams, die benötigen jüngere Generation R und Python-Module für ihre Lösungen. 

+ Ohne Bindung werden R und Python-Paketen für Fehlerbehebungen gepatcht, bei der Installation einer SQL Server Servicepack oder Kumulatives Update (CU). 
+ Bei der Bindung neuere Versionen des Pakets können angewendet werden, Ihre Instanz, unabhängig vom Zeitplan CU-Version unter der [Modern Lifecycle-Richtlinie](https://support.microsoft.com/help/30881/modern-lifecycle-policy) und Microsoft Machine Learning Server-Versionen. Die Modern Lifecycle-Richtlinie bietet häufigere Aktualisierungen über ein kürzere, ein Jahr lang gültig. Nach der Bindung, würden Sie weiterhin das Installationsprogramm MLS für zukünftige Updates von R und Python zu verwenden, sobald sie auf Microsoft-Download-Websites verfügbar sind.

Bindung gilt für nur R und Python-Funktionen. Nämlich Open-Source-Pakete für R und Python-Funktionen (mit Microsoft R Open, Anaconda), und der proprietären Pakete RevoScaleR, Revoscalepy und So weiter. Bindung ändert sich nicht auf das unterstützungsmodell für die Datenbank-Engine-Instanz und nicht die Version von SQL Server geändert.

Bindung kann rückgängig gemacht werden. Können Sie SQL Server-Service durch Wiederherstellen [Aufheben der Bindung der Instanz](#bkmk_Unbind) und reparing Ihrer SQL Server-Datenbank-Engine-Instanz.

Schritte für die Bindung sind wie folgt zusammengefasst werden:

+ Beginnen Sie mit einer vorhandenen, konfigurierten Installation von SQL Server 2016 R Services (oder SQL Server 2017-Machine Learning Services).
+ Bestimmen Sie, welche Version von Microsoft Machine Learning Server die aktualisierten Komponenten verfügt, die Sie verwenden möchten.
+ Herunterladen und Ausführen von Setup für diese Version. Setup erkennt die vorhandene Instanz, fügt eine Bindungsoption hinzu, und gibt eine Liste der kompatiblen Instanzen zurück.
+ Wählen Sie die Instanz, die Sie binden, und schließen Sie dann Setup aus, um die Bindung ausführen möchten.

Im Hinblick auf benutzerfreundlichkeit die Technologie und wie Sie damit arbeiten bleibt unverändert. Der einzige Unterschied ist das Vorhandensein von neueren mit versionsverwaltung durch das Pakete und eventuell weitere Pakete, die ursprünglich nicht mit SQL Server (z. B. MicrosoftML für Kunden von SQL Server 2016 R Services) verfügbar.

## <a name="bkmk_BindWizard"></a>Binden Sie an MLS mithilfe des Setups

Setup für Microsoft Machine Learning erkennt die vorhandenen Features und die SQL Server-Version und ruft ein Hilfsprogramm SqlBindR.exe zum Ändern der Bindungs aufgerufen. Intern ist SqlBindR verkettet mit der Einrichtung und indirekt verwendet. Später können Sie SqlBindR direkt über die Befehlszeile an bestimmten Befehlsoptionen aufrufen.

1. Führen Sie in SSMS `SELECT @@version` um zu überprüfen, ob der Server die minimalen Anforderungen erfüllt. 

   Für SQL Server 2016 R Services, der Mindestwert beträgt [Service Pack 1](https://www.microsoft.com/download/details.aspx?id=54276) und [CU3](https://support.microsoft.com/help/4019916/cumulative-update-3-for-sql-server-2016-sp1).

1. Überprüfen Sie die Version von R-Basis "und" RevoScaleR-Pakete ", um zu bestätigen, dass die vorhandenen Versionen sind kleiner, was durch die sie ersetzt werden sollen. Klicken Sie für SQL Server 2016 R Services R-Base-Paket ist 3.2.2, und RevoScaleR ist 8.0.3 kompatibel.

    ```sql
    EXECUTE sp_execute_external_script
    @language=N'R'
    ,@script = N'str(OutputDataSet);
    packagematrix <- installed.packages();
    Name <- packagematrix[,1];
    Version <- packagematrix[,3];
    OutputDataSet <- data.frame(Name, Version);'
    , @input_data_1 = N''
    WITH RESULT SETS ((PackageName nvarchar(250), PackageVersion nvarchar(max) ))
    ```

1. Schließen Sie SSMS, und von anderen Tools müssen eine offene Verbindung zur SQL Server aus. Bindung überschreibt die Programmdateien. Wenn SQL Server geöffneten Sitzungen hat, fehl Bindung mit dem Fehlercode "Bind" 6.

1. Laden Sie Microsoft Machine Learning Server, auf dem Computer mit der Instanz, die Sie aktualisieren möchten. Wir empfehlen die [neueste Version](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install#download-machine-learning-server-installer).

1. Entzippen Sie den Ordner, und starten Sie ServerSetup.exe, befindet sich im MLSWIN93.

   ![Microsoft Machine Learning Server-Setup-Assistenten](media/mls-921-installer-start.PNG)

1. Auf **konfigurieren Sie die Installation**, bestätigen Sie die Komponenten aktualisieren, und überprüfen Sie die Liste der kompatiblen Instanzen. 

   Dieser Schritt ist sehr wichtig.

   Wählen Sie auf der linken Seite jedes Feature, das Sie verwenden möchten, behalten oder aktualisieren. Sie können nicht einige Funktionen und andere nicht aktualisieren. Ist das Kontrollkästchen entfernt dieses Feature, vorausgesetzt, dass sie derzeit installiert ist. Der Screenshot zeigt, wenn eine Instanz von SQL Server 2016 R Services (MSSQL13) werden R und die R-Version der vorab trainierten Modelle ausgewählt. Diese Konfiguration ist gültig, da SQL Server 2016 R jedoch nicht in Python unterstützt.

   Wenn Sie auf SQL Server 2016 R Services-Komponenten aktualisieren, wählen Sie die Python-Funktion nicht. Sie können keine SQL Server 2016 R Services Python hinzufügen.

   Wählen Sie auf der rechten Seite das Kontrollkästchen neben den Namen der Instanz ein. Wenn keine Instanzen aufgelistet werden, müssen Sie eine Kombination nicht kompatibel. Wenn Sie keine Instanz auswählen, wird eine neue eigenständige Installation von Machine Learning Server erstellt, und die SQL Server-Bibliotheken sind unverändert. Wenn Sie eine Instanz nicht auswählen, möglicherweise nicht auf [SP1 CU3](https://support.microsoft.com/help/4019916/cumulative-update-3-for-sql-server-2016-sp1). 

    ![Schritt bei der Installation konfigurieren](media/mls-931-installer-mssql13.png)

1. Auf der **-Lizenzvertrag** Seite **ich akzeptiere diese Lizenzbedingungen** , akzeptieren die Lizenzbedingungen für Machine Learning-Server. 

1. Geben Sie auf den nachfolgenden Seiten Zustimmung zur weiteren Lizenzierung Bedingungen für Open-Source-Komponenten, die Sie ausgewählt haben, z. B. Microsoft R Open oder die Python-Anaconda-Distribution.

1. Auf der **fast** Seite, notieren Sie sich den Installationsordner. Der Standardordner ist \Program Files\Microsoft\ML Server.

    Wenn Sie den Installationsordner nicht ändern möchten, klicken Sie auf **erweitert** zurückzugebenden zur ersten Seite des Assistenten. Allerdings müssen Sie alle zuvor vorgenommenen Auswahlen wiederholen.

Während der Installation alle von SQL Server verwendeten R oder Python-Bibliotheken werden ersetzt, und Launchpad wird aktualisiert, um die Verwendung der neueren Komponenten. Daher werden, wenn die Instanz im Standardordner R_SERVICES zuvor Bibliotheken verwendet, diese Bibliotheken werden nach dem Upgrade entfernt, und die Eigenschaften für den Launchpad-Dienst geändert werden, um die Bibliotheken in den neuen Speicherort zu verwenden.

Bindung wirkt sich auf den Inhalt dieser Ordner: C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\R_SERVICES\library wird mit dem Inhalt der c:\programme\microsoft\ml Server\R_SERVER ersetzt. Der zweite Ordner und dessen Inhalt werden von Microsoft Machine Learning Server-Setup erstellt. 

Wenn Sie Upgrades ein Fehler auftritt, überprüfen Sie [SqlBindR-Fehlercodes](#sqlbindr-error-codes) für Weitere Informationen.

## <a name="confirm-binding"></a>Bestätigen der Bindung

Überprüfen Sie die Version von R "und" RevoScaleR ", um zu bestätigen, dass Sie neuere Versionen haben. Verwenden Sie die R-Konsole mit der R-Pakete in der Datenbank-Engine-Instanz verteilt, um die Paketinformationen abzurufen:

```sql
EXECUTE sp_execute_external_script
@language=N'R'
,@script = N'str(OutputDataSet);
packagematrix <- installed.packages();
Name <- packagematrix[,1];
Version <- packagematrix[,3];
OutputDataSet <- data.frame(Name, Version);'
, @input_data_1 = N''
WITH RESULT SETS ((PackageName nvarchar(250), PackageVersion nvarchar(max) ))
```

Für SQL Server 2016 R Services an Machine Learning Server 9.3 gebunden R-Base-Paket muss 3.4.3, RevoScaleR muss 9.3 und Sie sollten auch MicrosoftML 9.3 haben. 

Wenn Sie die vorab trainierte Modelle hinzugefügt, die Modelle werden in der Bibliothek MicrosoftML eingebettet, und Sie können diese aufrufen, MicrosoftML-Funktionen. Weitere Informationen finden Sie unter [R-Beispiele für MicrosoftML](https://docs.microsoft.com/machine-learning-server/r/sample-microsoftml).

## <a name="offline-binding-no-internet-access"></a>Offline-Bindung (kein Internet-Zugriff)

Für Systeme ohne Internetverbindung können Sie die Installationsprogramm und CAB-Dateien auf einem Computer mit Internetverbindung herunterladen und übertragen Sie die Dateien dann an den Server isoliert. 

Das Installationsprogramm (ServerSetup.exe) enthält die Microsoft-Pakete (RevoScaleR, MicrosoftML, OlapR, SqlRUtils). Die CAB-Dateien bieten andere Kernkomponenten. Beispielsweise stellt das Cab "SRO" R öffnen, die Microsoft-Distribution von Open-Source-R.

Die folgenden Anweisungen wird erläutert, wie die Dateien für eine Offlineinstallation zu platzieren.

1. Herunterladen des Installationsprogramms von MLS an. Es werden als eine einzelne ZIP-Datei heruntergeladen. Es wird empfohlen die [neueste Version](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install#download-machine-learning-server-installer), aber Sie können auch installieren [früher](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows-offline#download-required-components).

1. Laden Sie die CAB-Dateien herunter. Die folgenden Links sind für die Version 9.3. Wenn Sie frühere Versionen benötigen, weitere Links befinden sich [R Server 9.1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows-offline#download-required-components). Denken Sie daran, dass Python/Anaconda kann nur mit einer SQL Server 2017-Machine Learning Services-Instanz hinzugefügt werden. Vortrainierte Modelle vorhanden für R und Python. die CAB-Datei enthält Modelle, die in den Sprachen, die Sie verwenden.

    | Funktion | Herunterladen |
    |---------|----------|
    | R       | [SRO_3.4.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=867186&clcid=1033) |
    | Python  | [SPO_9.3.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=859054) | 
    | Vortrainierte Modelle | [MLM_9.3.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=859053) |

1. Übertragen Sie ZIP und CAB-Dateien auf den Zielserver.

1. Geben Sie auf dem Server `%temp%` in den Befehl "ausführen", um den physischen Speicherort des temp-Verzeichnisses abzurufen. Der physische Pfad hängt vom Computer ab, aber dies ist normalerweise `C:\Users\<your-user-name>\AppData\Local\Temp`.

1. Platzieren Sie die CAB-Dateien im Ordner "% Temp%".

1. Entzippen Sie das Installationsprogramm aus.

1. ServerSetup.exe ausgeführt, und befolgen Sie die angezeigten aufforderungen, um die Installation abzuschließen.

## <a name="bkmk_BindCmd"></a>Über die Befehlszeile-Vorgänge

Nach dem Ausführen von Microsoft Machine Learning Server wird ein Befehlszeilendienstprogramm namens SqlBindR.exe verfügbar, die Sie verwenden können, für die weiteren Vorgänge zu binden. Beispielsweise müssen Sie entscheiden, um eine Bindung umzukehren, Sie können Setup erneut ausführen oder mithilfe des Befehlszeilendienstprogramms. Darüber hinaus können Sie dieses Tool verwenden, um Kompatibilität und Verfügbarkeit für die Instanz zu überprüfen.

> [!TIP]
> Gefunden SqlBindR wurde nicht? Sie haben wahrscheinlich Setup nicht ausgeführt. SqlBindR steht erst nach der Machine Learning Server-Setup ausführen.

1. Öffnen Sie als Administrator eine Eingabeaufforderung und navigieren Sie zum Ordner, der „sqlbindr.exe“ enthält. Der Standardspeicherort ist c:\Programme\Microsoft Files\Microsoft\MLServer\Setup

2. Geben Sie den folgenden Befehl ein, um eine Liste der verfügbaren Instanzen anzuzeigen: `SqlBindR.exe /list`
  
   Merken Sie sich den vollständigen aufgelisteten Namen der Instanz. Zum Beispiel möglicherweise den Namen der Instanz MSSQL14. MSSQLSERVER für eine Standardinstanz oder ähnlich SERVERNAME. MYNAMEDINSTANCE.

3. Führen Sie die **SqlBindR.exe** -Befehl mit der */bind* -Argument, und geben Sie den Namen der Instanz zu aktualisieren, verwenden den Namen der Instanz, die im vorherigen Schritt zurückgegeben wurde.

   Geben Sie beispielsweise, um die Standardinstanz zu aktualisieren:  `SqlBindR.exe /bind MSSQL14.MSSQLSERVER`

4. Wenn das Upgrade abgeschlossen ist, starten Sie den Launchpad-Dienst verknüpft mit jeder Instanz, die geändert wurde neu.

## <a name="bkmk_Unbind"></a>Wiederherstellen oder Aufheben der Bindung einer Instanz

Sie können eine gebundene Instanz zu einer anfänglichen Installation der R und Python-Komponenten hergestellt, indem SQL Server-Setup wiederherstellen. Es gibt drei Teile beim Wiederherstellen auf der SQL Server-Wartung.

+ [Schritt 1: Trennt die Verbindung von Microsoft Machine Learning Server](#step-1-unbind)
+ [Schritt 2: Die Instanz zum ursprünglichen Zustand wiederherstellen](#step-2-restore)
+ [Schritt 3: Installieren Sie alle Pakete, die Sie die Installation hinzugefügt](#step-3-reinstall-packages)

<a name="step-1-unbind"></a> 

### <a name="step-1-unbind"></a>Schritt 1: Aufheben der Bindung

Sie haben zwei Optionen für ein Rollback für die Bindung: Führen Sie Setup erneut erneut aus, oder verwenden Sie SqlBindR-Befehlszeilen-Hilfsprogramm.

#### <a name="bkmk_wizunbind"></a> Aufheben der Bindung mithilfe des Setups

1. Suchen Sie das Installationsprogramm für Machine Learning Server aus. Wenn Sie das Installationsprogramm entfernt haben, müssen Sie möglicherweise erneut herunterladen oder von einem anderen Computer kopieren.
2. Achten Sie darauf, dass Sie das Installationsprogramm auf dem Computer ausgeführt wird, die die Instanz, die Sie die Bindung aufheben möchten.
2. Das Installationsprogramm identifiziert lokale Instanzen, die für das Aufheben der Bindung in Frage kommen.
3. Deaktivieren Sie das Kontrollkästchen neben der Instanz, die die ursprüngliche Konfiguration wiederhergestellt werden soll.
4. Akzeptieren Sie den Lizenzvertrag. Sie müssen die Annahme der Lizenzbedingungen, die auch angeben, bei der Installation.
5. Klicken Sie auf **Fertig stellen**. Der Vorgang dauert eine Weile.

#### <a name="bkmk_cmdunbind"></a> Aufheben der Bindung über die Befehlszeile

1. Öffnen Sie eine Eingabeaufforderung, und navigieren Sie zu dem Ordner, der **sqlbindr.exe** enthält, wie im vorherigen Abschnitt beschrieben.

2. Führen Sie den Befehl **SqlBindR.exe** mit dem */unbind*-Argument aus, und geben Sie die Instanz an.

   Der folgende Befehl stellt z. B. die Standardinstanz wieder her:
   
    `SqlBindR.exe /unbind MSSQL14.MSSQLSERVER`

<a name="step-2-restore"></a> 

###  <a name="step-2-repair-the-sql-server-instance"></a>Schritt 2: Reparieren Sie die SQL Server-Instanz

Führen Sie SQL Server-Setup, um die Datenbank-Engine-Instanz müssen die R und Python-Funktionen zu reparieren. Vorhandene Updates werden beibehalten, aber wenn Sie eine SQL Server-Wartungsupdates für R und Python-Pakete verpasst haben, wird dieser Schritt gilt Patches.

Sie können auch dies mehr Arbeit ist, aber Sie könnten auch vollständig deinstallieren und installieren Sie die Datenbank-Engine-Instanz neu und wenden Sie alle Serviceupdates.

<a name="step-3-reinstall-packages"></a> 

### <a name="step-3-add-any-third-party-packages"></a>Schritt 3: Fügen Sie alle Pakete von Drittanbietern

Sie können andere Pakete Open Source- oder von Drittanbietern Ihre paketbibliothek hinzugefügt haben. Da die Bindung umkehren den Speicherort des Standard-paketbibliothek wechselt, müssen Sie die Pakete in der Bibliothek neu installieren, die R- und Python jetzt verwenden. Weitere Informationen finden Sie unter [Pakete standardmäßig](installing-and-managing-r-packages.md), [Installieren neuer R-Pakete](install-additional-r-packages-on-sql-server.md), und [Installieren neuer Python-Pakete](../python/install-additional-python-packages-on-sql-server.md).

## <a name="sqlbindrexe-command-syntax"></a>SqlBindR.exe-Befehlssyntax

### <a name="usage"></a>Verwendung

`sqlbindr [/list] [/bind <SQL_instance_ID>] [/unbind <SQL_instance_ID>]`

### <a name="parameters"></a>Parameter

|Name|Description|
|------|------|
|*list*| Zeigt eine Liste aller SQL-Datenbankinstanz-IDs auf dem aktuellen Computer an|
|*bind*| Aktualisiert die angegebene SQL-Datenbankinstanz auf die neueste Version von R Server und stellt sicher, dass die Instanz automatisch zukünftige Upgrades von R Server erhält|
|*unbind*|Die neueste Version von R Server wird auf der angegebenen SQL-Datenbankinstanz deinstalliert, und es wird verhindert, dass zukünftige R Server-Upgrades auf die Instanz angewandt werden|

<a name="sqlbindr-error-codes"><a/>

## <a name="binding-errors"></a>Bindungsfehler

MLS Installer und SqlBindR Geben Sie die folgenden Fehlercodes und Meldungen zurück.

|Fehlercode  | MessageBox           | Details               |
|------------|-------------------|-----------------------|
|Fehler: 0 binden | OK (Erfolg) | Bindung übergeben, ohne Fehler. |
|Fehler 1 binden | Ungültige Argumente. | Syntaxfehler. |
|Binden Sie Fehler 2 | Ungültige Aktion | Syntaxfehler. |
|Fehler: 3 binden | Ungültige Instanz | Eine Instanz vorhanden, aber es gilt nicht für die Bindung. |
|Fehler 4 binden | Nicht bindbar. | |
|Binden Sie Fehler 5 | Bereits gebunden | Sie haben den *bind* -Befehl ausgeführt, die angegebene Instanz ist aber bereits gebunden. |
|Binden Sie Fehler 6 | Fehler beim Binden | Fehler beim Aufheben der Bindung der Instanz. Dieser Fehler kann auftreten, wenn Sie das MLS-Installationsprogramm ausführen, ohne alle Features auszuwählen. Bindung erfordert, dass die Auswahl einer MSSQL-Instanz und die R und Python, wenn die Instanz ist SQL Server 2017. Dieser Fehler tritt auch auf, wenn SqlBindR nicht in den Ordner "Programme" schreiben konnte. Offenen Sitzungen oder Handles für SQL Server werden zum Auftreten dieses Fehlers führen. Wenn Sie diesen Fehler erhalten, starten Sie den Computer neu, und wiederholen Sie die Schritte für die Bindung vor dem Starten der neuen Sitzungen, die aus.|
|Binden Sie Fehler 7 | Nicht gebunden | Die Datenbank-Engine-Instanz verfügt über R-Services oder SQL Server-Machine Learning-Dienste. Die Instanz ist nicht an Microsoft Machine Learning Server gebunden. |
|Binden Sie Fehler 8 | Aufheben der Bindung Fehler | Fehler beim Aufheben der Bindung der Instanz. |
|Bindung Fehler 9 | Keine Instanzen gefunden | Keine Datenbank-Engine-Instanzen wurden auf diesem Computer gefunden. |

## <a name="known-issues"></a>Bekannte Probleme

Dieser Abschnitt enthält bekannte Probleme im Zusammenhang, verwenden Sie das Hilfsprogramm SqlBindR.exe oder Upgrades von Machine Learning-Server, die SQL Server-Instanzen auswirken.

### <a name="restoring-packages-that-were-previously-installed"></a>Wiederherstellen von Paketen, die zuvor installiert wurden

Wenn Sie mit Microsoft R Server 9.0.1 aktualisiert, die Version des SqlBindR.exe für diese Version konnte nicht die ursprünglichen Pakete wiederhergestellt oder R-Komponenten vollständig zu erfordern, dass der Benutzer Repair für SQL Server in der Instanz ausführen, gelten alle Service-Versionen, und starten Sie die Instanz.

Höhere Version von SqlBindR automatisch die ursprüngliche R-Funktionen, und beseitigt die Notwendigkeit der erneuten Installation von R-Komponenten wiederherstellen oder patch erneut auf den Server. Allerdings müssen Sie alle Aktualisierungen der R-Paket installieren, die möglicherweise nach der ersten Installation hinzugefügt wurden.

Wenn Sie zum Installieren und Freigeben des Pakets die Paket-Verwaltungsrollen verwendet haben, ist diese Aufgabe viel einfacher: Sie können R-Befehle verwenden, installierten Pakete im Dateisystem mithilfe von Datensätzen in der Datenbank zu synchronisieren und umgekehrt. Weitere Informationen finden Sie unter [R-paketverwaltung für SQL Server](install-additional-r-packages-on-sql-server.md).

### <a name="problems-with-multiple-upgrades-from-sql-server"></a>Probleme mit der mehrere Upgrades von SQL Server

Wenn Sie beim Ausführen von des neuen Installers für Microsoft R Server 9.1.0 bereits eine Instanz von SQL Server 2016 R Services auf 9.0.1, aktualisiert haben, zeigt eine Liste aller gültigen Instanzen, und wählt dann standardmäßig bereits gebundene Instanzen. Wenn Sie fortfahren, werden die Instanzen bereits gebundenen aufgehoben. Als Ergebnis der früheren 9.0.1 Installation entfernt wird, einschließlich aller Pakete verknüpft, aber die neue Version von Microsoft R Server (9.1.0) ist nicht installiert.

Dieses Problem zu umgehen können Sie die vorhandene Installation von R Server wie folgt ändern:
1. Öffnen Sie in der Systemsteuerung **Software**.
2. Suchen Sie Microsoft R Server, und klicken Sie auf **ändern**.
3. Wenn das Installationsprogramm gestartet wird, wählen Sie die Instanzen, die Sie an 9.1.0 binden möchten.

Microsoft Machine Learning Server 9.2.1 und 9.3, verfügen nicht über dieses Problem.

### <a name="binding-or-unbinding-leaves-multiple-temporary-folders"></a>Binden bzw. Aufheben der Bindung bewirkt, dass mehrere temporärer Ordner

Gelegentlich sogar die Bindung und die Bindung Vorgänge zum Bereinigen von temporären Ordner.
Wenn Sie Ordner mit einem Namen wie folgt zu finden, können Sie diese entfernen, nachdem die Installation abgeschlossen ist: R_SERVICES_<guid>

> [!NOTE]
> Achten Sie darauf warten, bis die Installation abgeschlossen ist. Es dauert sehr lange zum Entfernen von R-Bibliotheken, die mit einer bestimmten Version verknüpft ist, und fügen Sie dann die neuen R-Bibliotheken hinzu. Wenn der Vorgang abgeschlossen ist, werden die temporären Ordner entfernt.

## <a name="see-also"></a>Siehe auch

+ [Installieren von Machine Learning Server für Windows (Internetverbindung)](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)
+ [Installieren von Machine Learning Server für Windows (offline)](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-offline)
+ [Bekannte Probleme in Machine Learning Server](https://docs.microsoft.com/machine-learning-server/resources-known-issues)
+ [Ankündigungen von Funktionen aus der vorherigen Version von R Server](https://docs.microsoft.com/r-server/whats-new-in-r-server)
+ [Veraltete, nicht mehr unterstützte oder geänderten features](https://docs.microsoft.com/machine-learning-server/resources-deprecated-features)
