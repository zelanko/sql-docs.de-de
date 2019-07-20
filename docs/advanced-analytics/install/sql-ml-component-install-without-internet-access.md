---
title: Installieren von R-Sprache und python-Komponenten ohne Internetzugang
description: Offline oder getrennt Machine Learning R-und python-Setup auf isolierter SQL Server Instanz hinter einer Netzwerk Firewall.
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 1c68ce075c34c6475828e81a66121e21afcf2482
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345022"
---
# <a name="install-sql-server-machine-learning-r-and-python-on-computers-with-no-internet-access"></a>Installieren von SQL Server Machine Learning R und python auf Computern ohne Internet Zugriff
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Standardmäßig stellen Installationsprogramme eine Verbindung mit Microsoft-Download Websites her, um erforderliche und aktualisierte Komponenten für Machine Learning auf SQL Server zu erhalten. Wenn das Installationsprogramm durch Firewalleinschränkungen nicht erreicht werden kann, können Sie mit einem mit dem Internet verbundenen Gerät Dateien herunterladen, Dateien auf einen Offline Server übertragen und dann das Setup ausführen.

Daten bankübergreifende Analysen bestehen aus der Datenbank-Engine-Instanz und zusätzlichen Komponenten für R-und python-Integration, abhängig von der Version von SQL Server. 

+ SQL Server 2017 umfasst R und python. 
+ SQL Server 2016 ist R-only.

Auf einem isolierten Server werden die sprachspezifischen Features von Machine Learning und R/python über CAB-Dateien hinzugefügt. 

## <a name="sql-server-2017-offline-install"></a>SQL Server 2017-Offline Installation

Wenn Sie SQL Server 2017 Machine Learning Services (R und python) auf einem isolierten Server installieren möchten, laden Sie zunächst die erste Version von SQL Server und die entsprechenden CAB-Dateien für R-und Python-Unterstützung herunter. Auch wenn Sie beabsichtigen, den Server umgehend auf das neueste kumulative Update zu aktualisieren, muss zunächst eine erste Version installiert werden.

> [!Note]
> SQL Server 2017 weist keine Service Packs auf. Es ist die erste Version von SQL Server, die erste Version als einzige Basislinie zu verwenden, bei der nur kumulative Updates gewartet werden. 

### <a name="1---download-2017-cabs"></a>1: Herunterladen von 2017-Cabs

Laden Sie auf einem Computer mit Internetverbindung die CAB-Dateien herunter, die R-und Python-Funktionen für die erste Version und die Installationsmedien für SQL Server 2017 bereitstellen. 

Release  |Downloadlink  |
---------|---------------|
Microsoft R Open     |[SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)|
Microsoft R Server      |[SRS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851507)|
Microsoft python Open     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502) |
Microsoft python-Server    |[SPS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851508) |

###  <a name="2---get-sql-server-2017-installation-media"></a>2: Get SQL Server 2017-Installationsmedien

1. Laden Sie auf einem Computer, der über eine Internetverbindung verfügt, das [SQL Server 2017-Setup Programm](https://www.microsoft.com/sql-server/sql-server-downloads)herunter. 

2. Doppelklicken Sie auf Setup, und wählen Sie den Installationstyp **Download Medium** aus. Bei dieser Option wird von Setup eine lokale ISO-Datei (oder. cab) mit den Installationsmedien erstellt.

   ![Wählen Sie den Installationstyp herunterladen] aus. (media/offline-download-tile.png "Medien herunterladen")

## <a name="sql-server-2016-offline-install"></a>SQL Server 2016-Offline Installation

SQL Server 2016-Datenbankanalyse ist r-only, mit nur zwei CAB-Dateien für Produktpakete und der Microsoft-Verteilung von Open Source-r. Installieren Sie zunächst eine der folgenden Versionen: RTM, SP 1, SP 2. Sobald eine Basisinstallation vorhanden ist, können kumulative Updates als nächster Schritt angewendet werden.

Auf einem Computer mit Internetverbindung können Sie die vom Setup verwendeten CAB-Dateien herunterladen, um datenbankübergreifende Analysen auf SQL Server 2016 zu installieren. 

### <a name="1---download-2016-cabs"></a>1: Herunterladen von 2016-Cabs

Release  | Microsoft R Open | Microsoft R Server |
---------|-----------------|---------------------|
**SQL Server 2016 RTM**     | [SRO_3.2.2.803_1033.cab](https://go.microsoft.com/fwlink/?LinkId=761266) |[SRS_8.0.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=735051) |
**SQL Server 2016 SP 1**     | [SRO_3.2.2.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824879) |[SRS_8.0.3.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824881) | 
**SQL Server 2016 SP 2**  |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866039) |[SRS_8.0.3.17000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=850317) |

### <a name="2---get-sql-server-2016-installation-media"></a>2: Get SQL Server 2016-Installationsmedien

Sie können SQL Server 2016 RTM, SP 1 oder SP 2 als erste Installation auf dem Zielcomputer installieren. Jede dieser Versionen kann ein kumulatives Update akzeptieren.

Eine Möglichkeit, eine ISO-Datei mit den Installationsmedien zu erhalten, ist die [Visual Studio dev Essentials](https://visualstudio.microsoft.com/dev-essentials/). Melden Sie sich an, und verwenden Sie dann den Link **Downloads** , um die Version SQL Server 2016 zu finden, die Sie installieren möchten. Der Download erfolgt in Form einer ISO-Datei, die Sie für eine Offline Installation auf den Bereitstellungs Zielcomputer kopieren können.

## <a name="transfer-files"></a>Dateien übertragen

Kopieren Sie die SQL Server-Installationsmedien (ISO-oder CAB-Dateien) und CAB-Dateien in der Datenbankanalyse auf den Zielcomputer. Platzieren Sie die CAB-Dateien und die Installationsmedien Datei im selben Ordner auf dem Zielcomputer, z. b. im Ordner "% Temp *" des Setup Benutzers.

Der Ordner "% Temp%" ist für python-CAB-Dateien erforderlich. Für R können Sie% Temp% verwenden oder den myrcachedirectory-Parameter auf den CAB-Pfad festlegen.

Der folgende Screenshot zeigt SQL Server 2017-CAB-und ISO-Dateien. SQL Server 2016-Downloads sehen anders aus: weniger Dateien (keine python-Datei), und der Name der Installationsmedien Datei ist für 2016.

![Liste der zu übertragenden Dateien](media/offline-file-list.png "Datei Liste")

## <a name="run-setup"></a>Ausführen von 'Setup'

Wenn Sie SQL Server Setup auf einem Computer ausführen, der nicht mit dem Internet getrennt ist, wird vom-Setup eine Seite für die **Offline Installation** hinzugefügt, sodass Sie den Speicherort der CAB-Dateien angeben können, die Sie im vorherigen Schritt kopiert haben.

1. Um die Installation zu starten, doppelklicken Sie auf die ISO-oder. CAB-Datei, um auf das-Installationsmedium zuzugreifen. Die Datei " **Setup. exe** " sollte angezeigt werden.

2. Klicken Sie mit der rechten Maustaste auf **Setup. exe** , und führen Sie als Administrator

3. Wenn der Setup-Assistent die Seite Lizenzierung für Open-Source-R-oder python-Komponenten anzeigt, klicken Sie auf **annehmen**. Wenn Sie die Lizenzbedingungen akzeptieren, können Sie mit dem nächsten Schritt fortfahren.

4. Wenn Sie zur Seite **Offline Installation** gelangen, geben Sie unter **Installationspfad**den Ordner mit den CAB-Dateien an, die Sie zuvor kopiert haben.

   ![Assistenten Seite für die CAB-Ordner Auswahl](media/screenshot-sql-offline-cab-page.png "CAB-Ordner")

5. Befolgen Sie die Anweisungen auf dem Bildschirm, um die Installation abzuschließen.

<a name="apply-cu"></a>

## <a name="apply-cumulative-updates"></a>Anwenden von kumulativen Updates

Es wird empfohlen, dass Sie das neueste kumulative Update sowohl auf die Datenbank-Engine als auch auf die Machine Learning-Komponenten anwenden. Kumulative Updates werden über das-Setup Programm installiert. 

1. Beginnen Sie mit einer Baseline-Instanz. Sie können nur kumulative Updates auf vorhandene Installationen von SQL Server anwenden:

  + SQL Server 2017-erste Version
  + SQL Server 2016, erste Release SQL Server 2016 SP 1 oder SQL Server 2016 SP 2

2. Wechseln Sie auf einem mit dem Internet verbundenen Gerät zur Liste der kumulativen Updates für Ihre Version von SQL Server:

  + [SQL Server 2017 Updates](https://sqlserverupdates.com/sql-server-2017-updates/)
  + [SQL Server 2016 Updates](https://sqlserverupdates.com/sql-server-2016-updates/)

3. Wählen Sie das neueste kumulative Update zum Herunterladen der ausführbaren Datei

4. Sie erhalten entsprechende CAB-Dateien für R und python. Download Links finden Sie unter [CAB-Downloads für kumulative Updates auf SQL Server in-Database-Analyse Instanzen](sql-ml-cab-downloads.md).

5. Übertragen Sie alle Dateien, ausführbaren Dateien und CAB-Dateien in denselben Ordner auf dem Offline Computer.

6. Führen Sie das Setup aus. Akzeptieren Sie die Lizenzbedingungen, und überprüfen Sie auf der Seite Funktionsauswahl die Funktionen, für die kumulative Updates angewendet werden. Es sollte jede installierte Funktion für die aktuelle Instanz angezeigt werden, einschließlich Machine Learning-Features.

  ![Wählen Sie Features aus der Funktionsstruktur aus] . (media/cumulative-update-feature-selection.png "Funktionsliste")

5. Fahren Sie mit dem Assistenten fort, und akzeptieren Sie die Lizenzbedingungen für R-und python-Distributionen. Während der Installation werden Sie aufgefordert, den Speicherort des Ordners mit den aktualisierten CAB-Dateien auszuwählen.

## <a name="set-environment-variables"></a>Umgebungsvariablen festlegen

Für die Integration von R-Funktionen sollten Sie die **MKL_CBWR** -Umgebungsvariable festlegen, um [eine konsistente Ausgabe](https://software.intel.com/articles/introduction-to-the-conditional-numerical-reproducibility-cnr) von MKL-Berechnungen (Intel Math Kernel Library) sicherzustellen.

1. Klicken Sie in der Systemsteuerung auf **System-und Sicherheits** > **System** > **Erweiterte Systemeinstellungen** > **Umgebungsvariablen**.

2. Erstellen Sie eine neue Benutzer-oder System Variable. 

  + Variablenname festlegen auf`MKL_CBWR`
  + Legen Sie den Variablen Wert auf fest.`AUTO`

Für diesen Schritt ist ein Neustart des Servers erforderlich. Wenn Sie im Begriff sind, die Skriptausführung zu aktivieren, können Sie den Neustart anhalten, bis die gesamte Konfigurations Arbeit abgeschlossen ist.

## <a name="post-install-configuration"></a>Konfiguration nach der Installation

Starten Sie nach Abschluss der Installation den Dienst neu, und konfigurieren Sie dann den Server, um die Skriptausführung zu aktivieren:

+ [Externe Skriptausführung aktivieren (SQL Server 2017)](sql-machine-learning-services-windows-install.md#bkmk_enableFeature)
+ [Externe Skriptausführung aktivieren (SQL Server 2016)](sql-r-services-windows-install.md#bkmk_enableFeature)

Eine anfängliche Offline Installation von SQL Server 2017 Machine Learning Services oder SQL Server 2016 R Services erfordert dieselbe Konfiguration wie eine Online Installation:

+ [Überprüfen der Installation](sql-machine-learning-services-windows-install.md#verify-installation)  (Klicken Sie für SQL Server 2016 auf [hier](sql-r-services-windows-install.md#verify-installation)).
+ [Zusätzliche Konfiguration nach Bedarf](sql-machine-learning-services-windows-install.md#additional-configuration)  (Klicken Sie für SQL Server 2016 auf [hier](sql-r-services-windows-install.md#bkmk_FollowUp)).

## <a name="next-steps"></a>Nächste Schritte

Informationen zum Überprüfen des Installationsstatus der-Instanz und zum Beheben von häufigen Problemen finden Sie unter [benutzerdefinierte Berichte für SQL Server R Services](../r/monitor-r-services-using-custom-reports-in-management-studio.md).

Hilfe zu unbekannten Nachrichten oder Protokoll Einträgen finden Sie unter Häufig gestellte Fragen zu [Upgrade und Installation-Machine Learning Services](../r/upgrade-and-installation-faq-sql-server-r-services.md).

