---
title: Installieren ohne Internetzugang
description: Installieren Sie SQL Server Machine Learning in R und Python auf Computern, die sich isoliert hinter einer Netzwerkfirewall befinden.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/04/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e966406a20df723c453a5c8083f00f2e4989d9d0
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "74064128"
---
# <a name="install-sql-server-machine-learning-r-and-python-on-computers-with-no-internet-access"></a>Installieren von Machine Learning in R und Python auf SQL Server-Computern ohne Internetzugang
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Standardmäßig stellen Installationsprogramme eine Verbindung mit Microsoft-Downloadwebsites her, um erforderliche und aktualisierte Komponenten für Machine Learning auf SQL Server-Instanzen zu erhalten. Wenn Firewallbeschränkungen den Zugriff des Installationsprogramms auf diese Websites verhindern, können Sie über ein mit dem Internet verbundenes Gerät Dateien herunterladen, die Dateien auf einen Offlineserver übertragen und dann das Setup ausführen.

Die datenbankinterne Analysefunktion umfasst die Instanz der Datenbank-Engine sowie zusätzliche Komponenten für die R- und Python-Integration, abhängig von der Version der SQL Server-Instanz. 

+ SQL Server 2019 umfasst R, Python und Java
+ SQL Server 2017 umfasst R und Python
+ SQL Server 2016 umfasst ausschließlich R

Auf einem isolierten Server werden Machine Learning-Funktionen und spezifische Funktionen für die R- bzw. Python-Programmiersprache über CAB-Dateien hinzugefügt. 

::: moniker range="=sql-server-ver15||=sqlallproducts-allversions"
## <a name="sql-server-2019-offline-install"></a>Offlineinstallation von SQL Server 2019

Um SQL Server Machine Learning Services (R und Python) auf einem isolierten Server zu installieren, laden Sie zunächst das erste Release von SQL Server und die entsprechenden CAB-Dateien für R- und Python-Unterstützung herunter. Auch wenn der Server sofort aktualisiert werden soll, damit er das neueste kumulative Update verwendet, muss zuerst ein erstes Release installiert werden.

> [!Note]
> Für SQL Server 2019 gibt es keine Service Packs. Nur für das erste Release erfolgt die Wartung ausschließlich über kumulative Updates.

### <a name="1---download-2019-cabs"></a>1: Herunterladen der CAB-Dateien für 2019

Laden Sie auf einem Computer mit Internetverbindung die CAB-Dateien mit den R- und Python-Funktionen für das erste Release und die Installationsmedien für SQL Server 2019 herunter.

Release  |Downloadlink  |
---------|---------------|
Microsoft R Open        | [SRO_3.5.2.125_1033.cab](https://go.microsoft.com/fwlink/?linkid=2085686) |
Microsoft R Server      | [SRS_9.4.7.25_1033.cab](https://go.microsoft.com/fwlink/?linkid=2085792) |
Microsoft Python Open   | [SPO_4.5.12.120_1033.cab](https://go.microsoft.com/fwlink/?linkid=2085793) |
Microsoft Python Server | [SPS_9.4.7.25_1033.cab](https://go.microsoft.com/fwlink/?linkid=2085685) |

> [!NOTE]
> Für die Java-Funktion ist keine separate CAB-Datei erforderlich, da sie auf dem SQL Server-Installationsmedium enthalten ist.

###  <a name="2---get-sql-server-2019-installation-media"></a>2: Herunterladen des Installationsmediums für SQL Server 2019

1. Laden Sie auf einem Computer mit Internetverbindung das [SQL Server 2019-Setupprogramm](https://www.microsoft.com/sql-server/sql-server-downloads) herunter. 

2. Doppelklicken Sie auf die Setupdatei, und wählen Sie den Installationstyp **Medien herunterladen** aus. Mit dieser Option wird beim Setup eine lokale ISO-Datei (oder CAB-Datei) erstellt, in der die Installationsdateien enthalten sind.

   ![Auswahl des Installationstyps beim Herunterladen des Mediums](media/2019offline-download-tile.png "Medien herunterladen")

::: moniker-end

::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
## <a name="sql-server-2017-offline-install"></a>Offlineinstallation von SQL Server 2017

Um SQL Server Machine Learning Services (R und Python) auf einem isolierten Server zu installieren, laden Sie zunächst das erste Release von SQL Server und die entsprechenden CAB-Dateien für R- und Python-Unterstützung herunter. Auch wenn der Server sofort aktualisiert werden soll, damit er das neueste kumulative Update verwendet, muss zuerst ein erstes Release installiert werden.

> [!Note]
> Für SQL Server 2017 gibt es keine Service Packs. Nur für das ursprüngliche Release der ersten SQL Server-Version erfolgt die Wartung ausschließlich über kumulative Updates. 

### <a name="1---download-2017-cabs"></a>1: Herunterladen der CAB-Dateien für 2017

Laden Sie auf einem Computer mit Internetverbindung die CAB-Dateien mit den R- und Python-Funktionen für das erste Release und die Installationsmedien für SQL Server 2017 herunter. 

Release  |Downloadlink  |
---------|---------------|
Microsoft R Open     |[SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)|
Microsoft R Server      |[SRS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851507)|
Microsoft Python Open     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502) |
Microsoft Python Server    |[SPS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851508) |

###  <a name="2---get-sql-server-2017-installation-media"></a>2: Herunterladen des Installationsmediums für SQL Server 2017

1. Laden Sie auf einem Computer mit Internetverbindung das [SQL Server 2017-Setupprogramm](https://www.microsoft.com/sql-server/sql-server-downloads) herunter. 

2. Doppelklicken Sie auf die Setupdatei, und wählen Sie den Installationstyp **Medien herunterladen** aus. Mit dieser Option wird beim Setup eine lokale ISO-Datei (oder CAB-Datei) erstellt, in der die Installationsdateien enthalten sind.

   ![Auswahl des Installationstyps beim Herunterladen des Mediums](media/offline-download-tile.png "Medien herunterladen")

::: moniker-end

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"

## <a name="sql-server-2016-offline-install"></a>Offlineinstallation von SQL Server 2016

Für die datenbankinterne Analysefunktion von SQL Server 2016 wird ausschließlich R verwendet. Es gibt nur zwei CAB-Dateien und zwar für Produktpakete und die Distribution der Open-Source-Programmiersprache R durch Microsoft. Installieren Sie zunächst eine der folgenden Releases: RTM, SP 1, SP 2. Sobald eine Basisinstallation vorhanden ist, können im nächsten Schritt kumulative Updates aufgespielt werden.

Laden Sie auf einem Computer mit Internetverbindung die CAB-Dateien herunter, die für das Setup benötigt werden, um die datenbankinterne Analysefunktion für SQL Server 2016 zu installieren. 

### <a name="1---download-2016-cabs"></a>1: Herunterladen der CAB-Dateien für 2016

Release  | Microsoft R Open | Microsoft R Server |
---------|-----------------|---------------------|
**SQL Server 2016 RTM**     | [SRO_3.2.2.803_1033.cab](https://go.microsoft.com/fwlink/?LinkId=761266) |[SRS_8.0.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=735051) |
**SQL Server 2016 SP 1**     | [SRO_3.2.2.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824879) |[SRS_8.0.3.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824881) | 
**SQL Server 2016 SP 2**  |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866039) |[SRS_8.0.3.17000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=850317) |

### <a name="2---get-sql-server-2016-installation-media"></a>2: Herunterladen des Installationsmediums für SQL Server 2016

Als Erstinstallation auf dem Zielcomputer können Sie SQL Server 2016 RTM, SP 1 oder SP 2 installieren. Für jede dieser Versionen kann ein kumulatives Update ausgeführt werden.

Eine Möglichkeit, eine ISO-Datei mit dem Installationsmedium zu erhalten, ist [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/). Melden Sie sich an, und verwenden Sie dann den Link **Download**, um nach der gewünschten SQL Server 2016-Version zu suchen. Die Downloaddatei liegt im ISO-Format vor, sodass Sie diese für eine Offlineinstallation auf den Zielcomputer kopieren können.

::: moniker-end

## <a name="transfer-files"></a>Übertragen der Dateien

Kopieren Sie die SQL Server-Installationsmedien (ISO- oder CAB-Dateien) und die CAB-Dateien der datenbankinternen Analysefunktion auf den Zielcomputer. Speichern Sie die CAB-Dateien und die Installationsdatei im selben Ordner auf dem Zielcomputer, z. B. im Ordner „% Temp%“ des Setupbenutzers.

Für Python-CAB-Dateien muss der Ordner „%Temp%“ verwendet werden. Für R können Sie „%Temp%“ verwenden oder den `myrcachedirectory`-Parameter auf den CAB-Pfad festlegen.

## <a name="run-setup"></a>Ausführen von 'Setup'

Wenn Sie das SQL Server-Setup auf einem vom Internet getrennten Computer ausführen, wird im Assistenten eine zusätzliche Seite **Offlineinstallation** hinzugefügt, damit Sie den Speicherort der CAB-Dateien angeben können, die Sie im vorherigen Schritt kopiert haben.

1. Doppelklicken Sie zur Installation auf die ISO- oder CAB-Datei, um so auf das Installationsmedium zuzugreifen. Die Datei **setup.exe** wird angezeigt.

2. Klicken Sie mit der rechten Maustaste auf **setup.exe**, und führen Sie sie als Administrator aus.

3. Wenn der Setup-Assistent die Lizenzseite für Open-Source-R- oder Python-Komponenten anzeigt, klicken Sie auf **Akzeptieren**. Durch die Bestätigung der Lizenzbedingungen können Sie mit dem nächsten Schritt fortfahren.

4. Wenn Sie auf die Seite **Offlineinstallation** gelangen, geben Sie unter **Installationspfad** den Ordner mit den CAB-Dateien an, die Sie zuvor kopiert haben.

5. Befolgen Sie die Anweisungen auf dem Bildschirm, um die Installation abzuschließen.

<a name="apply-cu"></a>

## <a name="apply-cumulative-updates"></a>Anwenden kumulativer Updates

Es wird empfohlen, dass Sie das neueste kumulative Update sowohl auf die Datenbank-Engine als auch auf die Machine Learning-Komponenten anwenden. Kumulative Updates werden über das Setupprogramm installiert. 

::: moniker range="=sql-server-ver15||=sqlallproducts-allversions"
1. Beginnen Sie mit einer Baselineinstanz. Sie können kumulative Updates nur auf vorhandene Installationen des ersten Releases von SQL Server anwenden:

2. Klicken Sie auf einem mit dem Internet verbundenen Gerät auf die Liste für das kumulative Update für Ihre SQL Server-Version:

   + SQL Server 2019-Updates *(es sind noch keine Updates für 2019 verfügbar)* .
::: moniker-end

::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
1. Beginnen Sie mit einer Baselineinstanz. Sie können kumulative Updates nur auf vorhandene Installationen des ersten Releases von SQL Server anwenden:

2. Klicken Sie auf einem mit dem Internet verbundenen Gerät auf die Liste für das kumulative Update für Ihre SQL Server-Version:

   + [SQL Server 2017-Updates](https://sqlserverupdates.com/sql-server-2017-updates/)
::: moniker-end

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
1. Beginnen Sie mit einer Baselineinstanz. Sie können kumulative Updates nur auf vorhandene Installationen des ersten Releases von SQL Server 2016, SQL Server 2016 SP 1 oder SQL Server 2016 SP 2 anwenden:

2. Klicken Sie auf einem mit dem Internet verbundenen Gerät auf die Liste für das kumulative Update für Ihre SQL Server-Version:

   + [SQL Server 2016-Updates](https://sqlserverupdates.com/sql-server-2016-updates/)
::: moniker-end

3. Wählen Sie das neueste kumulative Update aus, um die ausführbare Datei herunterzuladen.

4. Rufen Sie entsprechende CAB-Dateien für R und Python ab. Downloadlinks finden Sie unter [CAB-Dateidownloads für kumulative Updates für SQL Server-Instanzen für datenbankinterne Analysen](sql-ml-cab-downloads.md).

5. Übertragen Sie alle Dateien, die ausführbare Datei und CAB-Dateien, in denselben Ordner auf dem Offlinecomputer.

6. Führen Sie das Setup aus. Akzeptieren Sie die Lizenzbedingungen, und überprüfen Sie auf der Seite für die Funktionsauswahl die Funktionen, für die kumulative Updates angewendet werden. Es sollte jede für die aktuelle Instanz installierte Funktion einschließlich Machine Learning-Funktionen angezeigt werden.

   ![Auswählen der Funktionen aus der Funktionsstruktur](media/cumulative-update-feature-selection.png "Funktionsliste")

5. Folgen Sie den weiteren Anweisungen des Assistenten, und akzeptieren Sie die Lizenzbedingungen für die R- und Python-Distributionen. Während der Installation werden Sie aufgefordert, den Speicherort des Ordners mit den aktualisierten CAB-Dateien auszuwählen.

## <a name="set-environment-variables"></a>Festlegen von Umgebungsvariablen

Wenn Sie nur das R-Feature integrieren möchten, sollten Sie die Umgebungsvariable **MKL_CBWR** über die Intel Math Kernel Library-Berechnungen auf [ensure consistent output](https://software.intel.com/articles/introduction-to-the-conditional-numerical-reproducibility-cnr) (Konsistente Ausgabe sicherstellen) festlegen.

1. Klicken Sie in der Systemsteuerung auf **System und Sicherheit** > **System** > **Erweiterte Systemeinstellungen** > **Umgebungsvariablen**.

2. Erstellen Sie eine neue Benutzer- oder Systemvariable. 

   + Legen Sie den Variablenname auf `MKL_CBWR` fest.
   + Legen Sie den Variablenwert auf `AUTO` fest.

Für diesen Schritt ist ein Neustart des Servers erforderlich. Wenn Sie im Begriff sind, die Skriptausführung zu aktivieren, können Sie den Neustart anhalten, bis die gesamte Konfiguration abgeschlossen ist.

## <a name="post-install-configuration"></a>Konfiguration nach der Installation

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
Starten Sie nach Abschluss der Installation den Dienst neu, und konfigurieren Sie dann den Server, um die Skriptausführung zu aktivieren:

+ [Aktivieren der Ausführung des externen Skripts](sql-machine-learning-services-windows-install.md#bkmk_enableFeature)

Eine erste Offlineinstallation von SQL Server Machine Learning Services erfordert die gleiche Konfiguration wie eine Onlineinstallation:

+ [Überprüfen der Installation](sql-machine-learning-services-windows-install.md#verify-installation)
+ [Zusätzliche Konfiguration bei Bedarf](sql-machine-learning-services-windows-install.md#additional-configuration)
::: moniker-end

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
Starten Sie nach Abschluss der Installation den Dienst neu, und konfigurieren Sie dann den Server, um die Skriptausführung zu aktivieren:

+ [Aktivieren der Ausführung des externen Skripts](sql-r-services-windows-install.md#bkmk_enableFeature)

Eine anfängliche Offlineinstallation von SQL Server R Services erfordert die gleiche Konfiguration wie eine Onlineinstallation:

+ [Überprüfen der Installation](sql-r-services-windows-install.md#verify-installation)
+ [Zusätzliche Konfiguration bei Bedarf](sql-r-services-windows-install.md#bkmk_FollowUp)
::: moniker-end

## <a name="next-steps"></a>Nächste Schritte

Informationen zum Überprüfen des Installationsstatus der Instanz und zum Beheben häufiger Probleme finden Sie im Artikel zu [benutzerdefinierten Berichten für SQL Server](../r/monitor-r-services-using-custom-reports-in-management-studio.md).

Hilfe zu unbekannten Meldungen oder Protokolleinträgen finden Sie unter [Häufig gestellte Fragen zu Upgrade und Installation – Machine Learning Services](../r/upgrade-and-installation-faq-sql-server-r-services.md).
