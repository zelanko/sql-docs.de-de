---
title: Aktualisieren Sie R und Python-Komponenten in SQL Server-R-Instanzen (Machine Learning-Dienste) | Microsoft Docs
description: Aktualisieren Sie R und Python in SQL Server 2016 R Services oder SQL Server 2017 Machine Learning Services mithilfe von sqlbindr.exe zum Binden an Machine Learning-Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/05/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: f58eb498843c259c4bc9ac9a5d453456dac21b54
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="upgrade-machine-learning-r-and-python-components-in-sql-server-instances"></a>Aktualisieren des Machine learning (R und Python) Komponenten in SQL Server-Instanzen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

R und Python-Integration in SQL Server enthält, Open Source- und Microsoft-proprietäre Pakete. R und Python-Pakete werden unter der standardmäßigen SQL Server-Wartung, entsprechend den SQL Server-Freigabezyklus mit Fehlerbehebungen für vorhandene Pakete an die aktuelle Version aktualisiert. 

Die meisten Datenanalysten sind Erfahrung beim Arbeiten mit neueren Pakete, sobald sie verfügbar sind. Für SQL Server 2017 Machine Learning Services (Datenbankintern) und SQL Server 2016 R Services (Datenbankintern), erhalten Sie neuere Versionen von R und Python durch Ändern der *Bindung* aus SQL Server-Wartung [Microsoft Machine Learning-Servers](https://docs.microsoft.com/en-us/machine-learning-server/index) und [Supportrichtlinie für moderne Lebenszyklus](https://support.microsoft.com/help/30881/modern-lifecycle-policy).

Bindung ändert sich nicht auf die Grundlagen der Installation: R und Python-Integration ist immer noch Teil einer Datenbank-Modulinstanz Lizenzierung nicht geändert wird (keine zusätzlichen Kosten Bindung), und SQL Server-Support-Richtlinien enthalten jedoch weiterhin für die Datenbank Modul. Ändert sich jedoch das erneute Binden wie R und Python-Pakete bedient werden. Im weiteren Verlauf dieses Artikels erläutert Bindungsmechanismus und deren Funktionsweise für jede Version von SQL Server.

> [!NOTE]
> Bindung gilt für nur Instanzen (In-Database). Bindung ist nicht für eine Installation (eigenständig) relevant.

**SQL Server 2017**

Für SQL Server 2017 Machine Learning Services würden Sie in Betracht ziehen Bindung nur, wenn Microsoft Machine Learning-Server beginnt, um zusätzliche Pakete oder neuere Versionen über was Sie bereits verfügen.

**SQL Server 2016**

Für Kunden, die SQL Server 2016-R-Services, es gibt zwei Pfade für die erste neue und aktualisierte R-Pakete. Eine Methode besteht im aktualisieren auf SQL Server-2017; die zweite, binden an Microsoft Machine Learning-Server.

Upgrade auf SQL Server-2017 ruft Sie R-Pakete auf die Versionen, die in dieser Version sowie die Python-Features enthalten. Bindung ruft aktualisiert auch R-Pakete, mit denen weiter in jeder neuen Haupt- und Nebenversionsnummern-Version von Microsoft Machine Learning-Server aktualisiert werden können. 

Bindung ist nicht Ihnen Python-Unterstützung, weshalb eine SQL Server-2017-Funktion ist. 

**Upgrades bei den Komponenten über Microsoft Machine Learning-Server zur Verfügung.**

Die folgende Tabelle ist eine Version-Zuordnung, mit der Version, die mit SQL Server installiert, mit möglichen Upgrades beim Binden an Microsoft Machine Learning-Server (vormals bekannt als R-Server vor dem Hinzufügen der Unterstützung der Python MLS 9.2.1 ab). 

Beachten Sie, dass die Bindung nicht mit die neueste Version von R oder Anaconda garantiert. Wenn Sie sich an Microsoft Machine Learning-Server binden, erhalten Sie die R oder Python-Version installiert, über das Setupprogramm aus, die nicht unbedingt die neueste Version sind im Web verfügbar.

[**SQL Server 2016 R Services**](../install/sql-r-services-windows-install.md)

Komponente |Erste Version | R Server 9.0.1 | R Server 9.1 | MLS 9.2.1 | MLS 9.3 |
----------|----------------|----------------|--------------|---------|-------|
Microsoft R Open (MRO) über R | R 3.2.2     | R 3.3.2   |R 3.3.3   | R 3.4.1  | R 3.4.3 |
[RevoScaleR](https://docs.microsoft.com/achine-learning-server/r-reference/revoscaler/revoscaler) | 8.0.3  | 9.0.1 |  9.1 |  9.2.1 |  9.3 |
[MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)| entfällt | 9.0.1 |  9.1 |  9.2.1 |  9.3 |
[vortrainierte Modelle](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models)| entfällt | 9.0.1 |  9.1 |  9.2.1 |  9.3 |
[sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)| entfällt | 1,0 |  1,0 |  1,0 |  1,0 |
[olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | entfällt | 1,0 |  1,0 |  1,0 |  1,0 |


[**SQL Server 2017 Machine Learning-Dienste**](../install/sql-machine-learning-services-windows-install.md)

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

## <a name="how-component-upgrade-works"></a>Funktionsweise des Upgrades der Komponente

Upgrade von Integrationskomponenten erfolgt über *Bindung* Instanz von SQL Server 2016 R Services (oder eine Instanz von SQL Server 2017 Machine Learning Services) zum [Microsoft Machine Learning-Server](https://docs.microsoft.com/machine-learning-server/index). 

Microsoft Machine Learning-Server ist ein lokaler Server-Produkt von SQL Server, jedoch mit dem gleichen Interpreter und Pakete zu trennen. Binden von Swaps out der Aktualisierungsmechanismus für SQL Server-Dienst, damit Sie die R und Python-Pakete, die mit Microsoft Machine Learning-Server kann den Protokollversand verwenden können, die häufig neuer als die von SQL Server installiert sind. Wechseln Unterstützung für Richtlinien ist einer attraktiven Option für Data Science-Teams, die neuere Generation R erfordern und Python-Module für ihre Lösungen. 

Bindung wird ausgeführt, indem die [MLS Installer](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install). Das Installationsprogramm aktualisiert bestimmte R und Python-Pakete, ersetzt jedoch nicht Ihre SQL Server-Instanz in der Datenbank mit einem eigenständigen Computer mit nicht verbundenen Server installieren.

+ Ohne Bindung sind R und Python-Pakete für Fehlerkorrekturen gepatcht, bei der Installation einer SQL Server Servicepack oder Kumulatives Update (CU). 
+ Mit der Bindung die, neuere Versionen können angewendet werden auf der Instanz, unabhängig vom Zeitplan CU Version unter dem [moderne Lifecycle-Richtlinie](https://support.microsoft.com/help/30881/modern-lifecycle-policy) und Versionen von Microsoft Machine Learning-Server. Die Supportrichtlinie für moderne Lebenszyklus bietet häufiger Updates über eine kürzere und einjähriges Lebensdauer. Nach der Bindung, würden Sie weiterhin MLS-Installationsprogramm für zukünftige Updates von R und Python stehen im Microsoft Machine Learning-Server verwenden.

Bindung gilt für R und Python-Funktionen. Open-Source-Pakete für Funktionen, die R und Python (Anaconda, Microsoft R Open) und der proprietäre Pakete, nämlich "revoscaler" Revoscalepy und So weiter. Bindung ändert sich nicht auf das Modell Unterstützung für die Instanz des Datenbankmoduls und die Version von SQL Server nicht geändert.

Bindung kann rückgängig gemacht. Sie können in SQL Server nach Wartung wiederherstellen [Aufheben der Bindung der Instanz](#bkmk_Unbind) und Ihre SQL Server-Datenbankmodulinstanz reparing.

Werden addiert, Schritte für die Bindung wie folgt:

+ Beginnen Sie mit einer vorhandenen, konfigurierten Installation von SQL Server 2016 R Services (oder SQL Server 2017 Machine Learning Services).
+ Bestimmen Sie, welche Version von Microsoft Machine Learning-Server die aktualisierten Komponenten enthält, die Sie verwenden möchten.
+ Herunterladen und Ausführen von Setup für die jeweilige Version. Setup erkennt die vorhandene Instanz, fügt eine Bindungsoption und eine Liste der kompatiblen Instanzen zurückgegeben.
+ Wählen Sie die Instanz, die Sie binden, und beenden Sie dann Setup aus, um die Bindung ausführen möchten.

Im Hinblick auf die benutzerfreundlichkeit bleibt die Technologie und Ihre Arbeitsweise mit er unverändert. Der einzige Unterschied ist das Vorhandensein der neueren Version Pakete und eventuell weitere Pakete, die ursprünglich nicht mit SQL Server (z. B. MicrosoftML für Kunden, die SQL Server 2016 R Services) verfügbar.

## <a name="bkmk_BindWizard"></a>Binden Sie an MLS mithilfe von Setup

Setup für Microsoft Machine Learning erkennt die vorhandenen Funktionen und SQL Server-Version und ruft von einem Dienstprogramm mit dem Namen SqlBindR.exe um die Bindung zu ändern. Intern wird SqlBindR mit Setup verkettet und indirekt verwendet. Später können Sie SqlBindR direkt über die Befehlszeile, um spezifische Optionen Übung aufrufen.

1. Führen Sie in SSMS `SELECT @@version` um zu überprüfen, ob der Server die minimalen Buildanforderungen erfüllt. 

   Für SQL Server 2016-R-Services, der Mindestwert beträgt [Service Pack 1](https://www.microsoft.com/download/details.aspx?id=54276) und [CU3](https://support.microsoft.com/help/4019916/cumulative-update-3-for-sql-server-2016-sp1).

1. Überprüfen Sie die Version der R-Basis und "revoscaler"-Pakete, um zu bestätigen, dass die vorhandenen Versionen sind kleiner, was durch die sie ersetzt werden sollen. Für SQL Server 2016 R Services Base R-Paket ist 3.2.2 und "revoscaler" ist 8.0.3.

    ```SQL
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

1. Laden Sie Microsoft Machine Learning-Server herunter, auf dem Computer mit der Instanz, die Sie aktualisieren möchten. Es wird empfohlen die [neueste Version](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install#download-machine-learning-server-installer).

1. Entpacken Sie den Ordner, und starten Sie ServerSetup.exe, befindet sich im MLSWIN93.

   ![Microsoft Machine Learning-Server-Setup-Assistenten](media/mls-921-installer-start.PNG)

1. Auf **konfigurieren Sie die Installation**, bestätigen Sie die Komponenten aktualisieren, und überprüfen Sie die Liste der kompatiblen Instanzen. 

   Wählen Sie jede Funktion, die Sie beibehalten oder aktualisieren möchten, auf der linken Seite. Sie können nicht einige Funktionen und andere nicht aktualisieren. Ein leeres Kontrollkästchen entfernt diese Funktion, vorausgesetzt, dass sie derzeit installiert ist. Im Screenshot, der eine Instanz von SQL Server 2016 R Services (MSSQL13) angegeben, werden R und R-Version der Pre-tained Modelle ausgewählt. Diese Konfiguration ist ungültig, da SQL Server 2016 R jedoch nicht für Python unterstützt.

   Aktivieren Sie das Kontrollkästchen neben dem Instanznamen, auf der rechten Seite. Wenn keine Instanzen aufgelistet werden, müssen Sie eine Kombination nicht kompatibel. Wenn Sie keine Instanz auswählen, wird eine neue eigenständige Installation von Machine Learning-Server erstellt, und die SQL Server-Bibliotheken sind dieselben wie. Wenn Sie eine Instanz auswählen können, möglicherweise nicht am [SP1 CU3](https://support.microsoft.com/help/4019916/cumulative-update-3-for-sql-server-2016-sp1). 

    ![Microsoft Machine Learning-Server-Setup-Assistenten](media/mls-931-installer-mssql13.png)

1. Auf der **Lizenzvertrag** Seite **ich akzeptiere diese Lizenzbedingungen** für Machine Learning-Server die Lizenzbedingungen akzeptieren. 

1. Geben Sie auf den nachfolgenden Seiten seine Zustimmung zur weiteren Lizenzierung Bedingungen für Open Source-Komponenten, die Sie ausgewählt haben, z. B. Microsoft R Open oder die Python-Anaconda-Verteilung.

1. Auf der **beinahe** Seite, notieren Sie sich den Installationsordner. Der Standardordner ist \Program Files\Microsoft\ML Server.

    Wenn Sie den Installationsordner nicht ändern möchten, klicken Sie auf **erweitert** um zur ersten Seite des Assistenten zurückzukehren. Allerdings müssen Sie alle vorherigen Auswahl wiederholen.

Klicken Sie während der Installation alle R oder Python-Bibliotheken, die von SQL Server verwendeten ersetzt werden, und Launchpad wird aktualisiert, um die neueren Komponenten verwenden. Daher wird, wenn die Instanz zuvor Bibliotheken im Standardordner R_SERVICES verwendet, nach dem Upgrade werden diese Bibliotheken entfernt und die Eigenschaften für den Launchpad-Dienst werden geändert, um die Bibliotheken am neuen Speicherort zu verwenden.

Bindung wirkt sich auf den Inhalt dieser Ordner: C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\R_SERVICES\library wird mit dem Inhalt des c:\Programme\Microsoft Files\Microsoft\ML Server\R_SERVER ersetzt. Den zweiten Ordner und seinen Inhalt werden vom Setup für Microsoft Machine Learning-Server erstellt. 

Wenn das Upgrade fehlschlägt, überprüfen Sie [SqlBindR Fehlercodes](#sqlbindr-error-codes) für Weitere Informationen.

## <a name="confirm-binding"></a>Bestätigen der Bindung

Überprüfen Sie die Version von R und "revoscaler", um zu bestätigen, dass Sie neuere Versionen aufweisen. Verwenden Sie die R-Konsole mit der R-Pakete in der Datenbank-Modulinstanz verteilt, um Paketinformationen abzurufen:

```SQL
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

Für SQL Server 2016 R Services zu Machine Learning Server 9.3 gebunden Base R-Paket muss 3.4.1, "revoscaler" 9.3 werden soll und Sie sollten außerdem MicrosoftML 9.3 haben. 

Wenn Sie die vorab trainierten Modelle hinzugefügt haben, werden die Modelle in der Bibliothek MicrosoftML eingebettet und über MicrosoftML Funktionen aufrufen. Weitere Informationen finden Sie unter [R-Beispiele für MicrosoftML](https://docs.microsoft.com/machine-learning-server/r/sample-microsoftml).

## <a name="offline-binding-no-internet-access"></a>Offline-Bindung (keinen Internetzugang)

Bei Systemen ohne Internetverbindung können Sie das Installationsprogramm und CAB-Dateien auf einem Computer mit Internetzugang heruntergeladen und Dateien dann mit dem isolierten Server übertragen. 

Das Installationsprogramm (ServerSetup.exe) enthält die Microsoft-Pakete ("revoscaler", MicrosoftML, OlapR, SqlRUtils). Die CAB-Dateien geben Sie andere Kernkomponenten. Beispielsweise bietet die "SRO" CAB-Datei ein R Open, Microsofts Verteilung der Open-Source-r

Die folgenden Anweisungen wird erläutert, wie die Dateien für eine Offlineinstallation abgelegt wird.

1. Laden Sie das Installationsprogramm MLS herunter. Es werden als eine einzelne ZIP-Datei heruntergeladen. Es wird empfohlen die [neueste Version](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install#download-machine-learning-server-installer), aber Sie können auch installieren [Vorgängerversionen](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows-offline#download-required-components).

1. Laden Sie die CAB-Dateien herunter. Die folgenden Links sind für die 9.3 Version. Wenn Sie frühere Versionen benötigen, zusätzliche Links finden Sie in [R Server 9.1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows-offline#download-required-components). Beachten Sie, dass Python/Anaconda kann nur mit einer Instanz von SQL Server 2017 Machine Learning Services hinzugefügt werden. Pre-tained Modelle, die für R und Python vorhanden sind; die CAB-Datei enthält die Modelle in den Sprachen, die Sie verwenden.

    | Funktion | Herunterladen |
    |---------|----------|
    | R       | [SRO_3.4.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=867186&clcid=1033) |
    | Python  | [SPO_9.3.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=859054) | 
    | Pre-tained Modelle | [MLM_9.3.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=859053) |

1. ZIP und CAB-Dateien auf dem Zielserver zu übertragen.

1. Geben Sie auf dem Server `%temp%` in den Befehl ausführen, um den physischen Speicherort des temp-Verzeichnisses abzurufen. Der physische Pfad variiert je nach Computer, jedoch ist dies normalerweise `C:\Users\<your-user-name>\AppData\Local\Temp`.

1. Platzieren Sie die CAB-Dateien im Ordner "% Temp%".

1. Entpacken Sie das Installationsprogramm an.

1. ServerSetup.exe ausgeführt, und befolgen Sie die aufforderungen, um die Installation abzuschließen.

## <a name="bkmk_BindCmd"></a>Vorgänge über die Befehlszeile

Nach dem Ausführen von Microsoft Machine Learning-Server wird ein Befehlszeilen-Dienstprogramm SqlBindR.exe verfügbar, die Sie für weitere Vorgänge Binden verwenden können. Beispielsweise sollten Sie entscheiden, um eine Bindung umzukehren, können entweder führen Sie Setup erneut aus. oder verwenden Sie das Befehlszeile-Hilfsprogramm. Darüber hinaus können Sie dieses Tool verwenden, um Kompatibilität und höchste Verfügbarkeit für die Instanz zu überprüfen.

> [!TIP]
> Gefunden SqlBindR wurde nicht? Setup haben Sie wahrscheinlich nicht ausgeführt. SqlBindR steht erst nach der Machine Learning-Server-Setup ausführen.

1. Öffnen Sie als Administrator eine Eingabeaufforderung und navigieren Sie zum Ordner, der „sqlbindr.exe“ enthält. Der Standardspeicherort ist c:\Programme\Microsoft Files\Microsoft\MLServer\Setup

2. Geben Sie den folgenden Befehl ein, um eine Liste der verfügbaren Instanzen anzuzeigen: `SqlBindR.exe /list`
  
   Merken Sie sich den vollständigen aufgelisteten Namen der Instanz. Der Instanzname kann z. B. MSSQL14 sein. MSSQLSERVER für eine Standardinstanz oder etwa SERVERNAME. MYNAMEDINSTANCE.

3. Führen Sie die **SqlBindR.exe** -Befehl mit der */bind* Argument, und geben Sie den Namen der Instanz für ein upgrade auf die Verwendung des Instanznamens, die im vorherigen Schritt zurückgegeben wurde.

   Um die Standardinstanz zu aktualisieren, z. B. Folgendes ein:  `SqlBindR.exe /bind MSSQL14.MSSQLSERVER`

4. Starten Sie nach Abschluss des Upgrades den Launchpad-Dienst verknüpft sind mit jeder Instanz, die geändert wurde.

## <a name="bkmk_Unbind"></a>REVERT oder Aufheben der Bindung einer Instanz

Sie können eine Erstinstallation R und Python-Komponenten durch die SQL Server-Setup eine gebundene Instanz wiederherstellen. Es gibt drei Komponenten zum Zurücksetzen auf die SQL Server-Wartung.

+ [Schritt 1: Aufheben der Bindung von Microsoft-Machine Learning-Server](#step-1-unbind)
+ [Schritt 2: Wiederherstellen der Instanz den ursprünglichen status](#step-2-restore)
+ [Schritt 3: Installieren Sie alle Pakete, die Sie hinzugefügt haben, um die Installation neu](#step-3-reinstall-packages)

<a name="step-1-unbind"></a> 

### <a name="step-1-unbind"></a>Schritt 1: Aufheben der Bindung

Sie haben zwei Optionen für ein Rollback für die Bindung: Führen Sie Setup erneut erneut aus, oder verwenden Sie SqlBindR-Befehlszeilen-Hilfsprogramm.

#### <a name="bkmk_wizunbind"></a> Aufheben der Bindung mithilfe von Setup

1. Suchen Sie das Installationsprogramm für Machine Learning-Server. Wenn Sie das Installationsprogramm entfernt haben, müssen Sie möglicherweise erneut herunterladen oder von einem anderen Computer zu kopieren.
2. Achten Sie darauf, dass Sie das Installationsprogramm auf dem Computer ausführen, der die Instanz verfügt, die Bindung aufgehoben werden soll.
2. Der Installer gibt die lokale Instanzen, die für die Bindung aufgehoben werden.
3. Deaktivieren Sie das Kontrollkästchen neben der Instanz, die die ursprüngliche Konfiguration wiederhergestellt werden soll.
4. Akzeptieren Sie den Lizenzvertrag. Sie müssen die Annahme der Lizenzbedingungen auch angeben, bei der Installation.
5. Klicken Sie auf **Fertig stellen**. Der Vorgang dauert eine Weile.

#### <a name="bkmk_cmdunbind"></a> Aufheben der Bindung über die Befehlszeile

1. Öffnen Sie eine Eingabeaufforderung, und navigieren Sie zu dem Ordner, der **sqlbindr.exe** enthält, wie im vorherigen Abschnitt beschrieben.

2. Führen Sie den Befehl **SqlBindR.exe** mit dem */unbind*-Argument aus, und geben Sie die Instanz an.

   Der folgende Befehl stellt z. B. die Standardinstanz wieder her:
   
    `SqlBindR.exe /unbind MSSQL14.MSSQLSERVER`

<a name="step-2-restore"></a> 

###  <a name="step-2-repair-the-sql-server-instance"></a>Schritt 2: Reparieren Sie die SQL Server-Instanz

Führen Sie SQL Server-Setup, um der Datenbankmodulinstanz, dass die R und Python-Funktionen zu reparieren. Vorhandene Updates werden beibehalten, aber wenn Sie alle SQL Server-Wartungsupdates R und Python-Pakete fehlen, wird dieser Schritt gilt Patches.

Alternativ können Sie dies mehr Arbeit ist, aber Sie könnten auch vollständig deinstallieren und Installieren der Instanz des Datenbankmoduls und wenden Sie alle Serviceupdates.

<a name="step-3-reinstall-packages"></a> 

### <a name="step-3-add-any-third-party-packages"></a>Schritt 3: Hinzufügen von Drittanbieter-Pakete

Sie können andere Open Source- oder Drittanbieter-Pakete für die Paket-Bibliotheksfreigabe hinzugefügt haben. Da den Speicherort des Pakets Standardbibliothek Umkehren der Bindungsnamens gewechselt wird, müssen Sie die Pakete in der Bibliothek, die R und Python jetzt verwenden, neu installieren. Weitere Informationen finden Sie unter [Standard Pakete](installing-and-managing-r-packages.md), [neue R-Pakete installieren](install-additional-r-packages-on-sql-server.md), und [neue Python Installationspakete](../python/install-additional-python-packages-on-sql-server.md).

## <a name="known-issues"></a>Bekannte Probleme

Dieser Abschnitt enthält bekannte Probleme im Zusammenhang Verwendung des Hilfsprogramms SqlBindR.exe oder für Upgrades von Machine Learning-Server, die SQL Server-Instanzen beeinträchtigen können.

### <a name="restoring-packages-that-were-previously-installed"></a>Wiederherstellen von Paketen, die zuvor installiert wurden

Wenn Sie auf Microsoft R Server 9.0.1 aktualisiert, die Version des SqlBindR.exe für die jeweilige Version konnte nicht die ursprünglichen Pakete wiederhergestellt oder R-Komponenten vollständig zu erfordern, dass der Benutzer auf der Instanz, SQL Server-Reparatur Ausführen aller Service Releases gelten, und starten Sie die Instanz.

Folgeversion von SqlBindR automatisch die ursprüngliche R-Funktionen, entfällt das Erfordernis Neuinstallation des R-Komponenten wiederherstellen oder erneut Patch für den Server. Allerdings müssen Sie alle Updates der R-Paket installieren, die nach der Erstinstallation hinzugefügt wurden.

Wenn Sie zum Installieren und Freigeben von Paket die Paket-Verwaltungsrollen verwendet haben, ist diese Aufgabe sehr viel einfacher: Sie können R-Befehle verwenden, mit dem installierten Pakete im Dateisystem verwenden die Datensätze in der Datenbank synchronisiert und umgekehrt. Weitere Informationen finden Sie unter [paketverwaltung für SQL Server R](r-package-management-for-sql-server-r-services.md).

### <a name="problems-with-multiple-upgrades-from-sql-server"></a>Probleme bei mehreren Upgrades von SQL Server

Wenn Sie beim Ausführen von mit dem neuen Installers für Microsoft R Server 9.1.0 zuvor eine Instanz von SQL Server 2016 R Services zu 9.0.1 aktualisiert haben, zeigt eine Liste aller gültigen Instanzen und wählt dann standardmäßig bereits gebundenen Instanzen aus. Wenn Sie den Vorgang fortsetzen, sind die zuvor gebundenen Instanzen aufgehoben. Als Ergebnis der früheren 9.0.1 Installation entfernt wird, einschließlich aller Pakete verknüpft, aber die neue Version von Microsoft R Server (9.1.0) ist nicht installiert.

Dieses Problem zu umgehen können Sie die vorhandene Installation von R-Server wie folgt ändern:
1. Öffnen Sie in der Systemsteuerung **Software**.
2. Suchen von Microsoft R Server, und klicken Sie auf **ändern "/" ändern**.
3. Wenn das Installationsprogramm gestartet wird, wählen Sie die Instanzen, die Sie an 9.1.0 binden möchten.

Microsoft Machine Learning Server 9.2.1 und 9.3 verfügen nicht über dieses Problem.

### <a name="binding-or-unbinding-leaves-multiple-temporary-folders"></a>Binden oder Aufheben der Bindung bewirkt, dass mehrere temporären Ordner

Treten ggf. Fehler bei der Bindung und Aufheben der Bindung Vorgänge zum Bereinigen von temporären Ordner.
Wenn Sie den Ordner mit einem Namen wie folgt finden, können Sie diesen entfernen, nachdem die Installation abgeschlossen ist: R_SERVICES_<guid>

> [!NOTE]
> Achten Sie darauf warten, bis die Installation abgeschlossen ist. Es dauert sehr lange zum Entfernen von R-Bibliotheken, die eine Version zugeordnet, und fügen Sie dann die neuen R-Bibliotheken. Wenn der Vorgang abgeschlossen ist, werden temporäre Ordner entfernt.

## <a name="sqlbindrexe-command-syntax"></a>SqlBindR.exe Befehlssyntax

### <a name="usage"></a>Verwendung

`sqlbindr [/list] [/bind <SQL_instance_ID>] [/unbind <SQL_instance_ID>]`

### <a name="parameters"></a>Parameter

|Name|Description|
|------|------|
|*list*| Zeigt eine Liste aller SQL-Datenbankinstanz-IDs auf dem aktuellen Computer an|
|*bind*| Aktualisiert die angegebene SQL-Datenbankinstanz auf die neueste Version von R Server und stellt sicher, dass die Instanz automatisch zukünftige Upgrades von R Server erhält|
|*unbind*|Die neueste Version von R Server wird auf der angegebenen SQL-Datenbankinstanz deinstalliert, und es wird verhindert, dass zukünftige R Server-Upgrades auf die Instanz angewandt werden|

<a name="sqlbinder-error-codes"><a/>

### <a name="errors"></a>Fehler

Die Abfrage gibt die folgenden Fehlermeldungen zurück:

|Fehlercode  | MessageBox           | Details               |
|------------|-------------------|-----------------------|
|Fehler 0 binden | OK (Erfolg) | Bindung übergeben, ohne Fehler abgeschlossen. |
|Binden Sie Fehler 1 | Ungültige Argumente | Syntaxfehler. |
|Binden Sie Fehler 2 | Ungültige Aktion | Syntaxfehler. |
|Binden Sie Fehler 3 | Ungültige Instanz | Eine Instanz vorhanden ist, jedoch ist für die Bindung ungültig. |
|Binden Sie Fehler 4 | Nicht bindbar. | |
|Fehler: 5 binden | Bereits gebunden. | Sie haben den *bind* -Befehl ausgeführt, die angegebene Instanz ist aber bereits gebunden. |
|Fehler: 6 binden | Fehler beim Binden | Fehler beim Aufheben der Bindung der Instanz. Dieser Fehler kann auftreten, wenn Sie das MLS-Installationsprogramm ausführen, ohne Sie alle Funktionen auswählen.|
|Binden Sie Fehler 7 | Nicht gebunden | Die Datenbank-Modulinstanz verfügt über R Services oder SQL Server-Machine Learning-Services. Die Instanz ist nicht an Microsoft Machine Learning-Server gebunden. |
|Binden Sie Fehler 8 | Aufheben der Bindung fehlgeschlagen | Fehler beim Aufheben der Bindung der Instanz. |
|Binden Sie Fehler 9 | Keine Instanzen gefunden | Auf diesem Computer wurden keine Datenbank-Engine-Instanzen gefunden. |


## <a name="see-also"></a>Siehe auch

+ [Installieren Sie Machine Learning-Server für Windows (mit dem Internet verbundenen)](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)
+ [Installieren Sie Machine Learning-Server für Windows (offline)](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-offline)
+ [Bekannte Probleme in Machine Learning-Server](https://docs.microsoft.com/machine-learning-server/resources-known-issues)
+ [Ankündigungen von Funktionen aus der vorherigen Version von R-Server](https://docs.microsoft.com/r-server/whats-new-in-r-server)
+ [Als veraltet markierte oder geänderten nicht mehr unterstützte Funktionen](https://docs.microsoft.com/machine-learning-server/resources-deprecated-features)