---
title: Installieren von SQL Server-Machine Learning-Komponenten ohne Internetzugang | Microsoft-Dokumentation
description: Offline oder getrennt Machine Learning-R und Pytyon Setup für SQL Server-Instanz isoliert.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/02/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 56624d2a5fcc97035f434cb1ee1d4fdee4dedeba
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2018
ms.locfileid: "39546260"
---
# <a name="install-sql-server-machine-learning-r-and-python-features-on-computers-with-no-internet-access"></a>Installieren von SQL Server-Machine learning-R und Python-Funktionen auf Computern ohne Internetzugang
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Standardmäßig Installationsprogramme Verbindung mit Microsoft-Download-Websites zum Abrufen der erforderlichen und aktualisierte Komponenten für machine Learning in SQL Server. Wenn firewalleinschränkungen verhindern, dass das Installationsprogramm diese Websites zu erreichen, können Sie ein Gerät mit Internetzugang Herunterladen von Dateien, Dateien mit einem offline-Server übertragen, und führen Sie Setup.

In-Database-Analyse bestehen aus der Datenbank-Engine-Instanz sowie zusätzliche Komponenten für die Integration von R und Python, abhängig von der Version von SQL Server. 

+ SQL Server 2017 enthält R und Python. 
+ SQL Server 2016 ist nur für R. 

Auf einem Server isoliert werden Machine Learning und R/Python-Sprache-spezifischen Funktionen über CAB-Dateien hinzugefügt. 

## <a name="sql-server-2017-offline-install"></a>SQL Server 2017-offline-Installation

Um SQL Server 2017 Machine Learning Services (R- und Python) auf einem isolierten-Server zu installieren, starten Sie durch Herunterladen der ersten Version von SQL Server, und die entsprechenden CAB-Dateien für R und Python unterstützt. Auch wenn Sie planen, den Server, um Sie verwenden das aktuelle kumulative Update sofort zu aktualisieren, muss zunächst eine erste Version installiert werden.

> [!Note]
> SQL Server 2017 besitzt keine Servicepacks. Es ist die erste Version von SQL Server die erste Version als die einzige Basis-Zeile, für die Verarbeitung durch nur kumulative Updates verwenden. 

### <a name="1---download-2017-cabs"></a>1 – herunterladen von 2017-CAB-Dateien

Auf einem Computer, die über einen Internetzugang verfügen Laden Sie die CAB-Dateien, die Bereitstellung von R und Python-Funktionen für die erste Version und die Installationsmedien für SQL Server 2017 herunter. 

Release  |Downloadlink  |
---------|---------------|
Microsoft R Open     |[SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)|
Microsoft R Server      |[SRS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851507)|
Öffnen Sie Microsoft-Python     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502) |
Microsoft Python-Server    |[SPS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851508) |

###  <a name="2---get-sql-server-2017-installation-media"></a>2: Abrufen von SQL Server 2017-Installationsmedien

1. Laden Sie auf einem Computer, die über einen Internetzugang verfügen, die [SQL Server 2017-Setup-Programm](https://www.microsoft.com/sql-server/sql-server-downloads). 

2. Doppelklicken Sie auf Setup aus, und wählen Sie die **Medien herunterladen** Installationstyp. Mit dieser Option erstellt Setup eine lokale ISO (oder .cab) Datei, die mit den Installationsmedien.

   ![Wählen Sie die Medien herunterladen Installationstyp](media/offline-download-tile.png "Medien herunterladen")

## <a name="sql-server-2016-offline-install"></a>SQL Server 2016-offline-Installation

SQL Server 2016-in-Database-Analyse ist R ausschließlich mit nur zwei CAB-Dateien für die Produktpakete und die Microsoft-Distribution von Open-Source-R bzw. Starten, indem Sie eine dieser Versionen installieren: RTM, SP 1, SP 2 ausgeführt wird. Sobald eine Basisinstallation vorhanden ist, können die kumulativen Updates als Nächstes angewendet werden.

Laden Sie auf einem Computer, die über einen Internetzugang verfügen die CAB-Dateien von Setup verwendet werden, um die datenbankinternen Analysen auf SQL Server 2016 zu installieren. 

### <a name="1---download-2016-cabs"></a>1 – herunterladen von 2016 CAB-Dateien

Release  | Microsoft R Open | Microsoft R Server |
---------|-----------------|---------------------|
**SQL Server 2016 RTM**     | [SRO_3.2.2.803_1033.cab](https://go.microsoft.com/fwlink/?LinkId=761266) |[SRS_8.0.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=735051) |
**SQL Server 2016 SP 1**     | [SRO_3.2.2.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824879) |[SRS_8.0.3.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824881) | 
**SQL Server 2016 SP2**  |[SRO_3.2.2.20000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866039) |[SRS_8.0.3.20000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866038) |

### <a name="2---get-sql-server-2016-installation-media"></a>2: Abrufen von SQL Server 2016-Installationsmedien

Sie können SQL Server 2016 RTM, SP 1 oder SP 2 als die Installation des ersten auf dem Zielcomputer installieren. Einer dieser Versionen kann ein kumulatives Update akzeptieren.

Eine Möglichkeit zum Abrufen von einer ISO-Datei mit den Installationsmedien ist über [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/). Melden Sie sich, und verwenden Sie dann die **Downloads** Link zu die SQL Server 2016-Version finden Sie installieren möchten. Der Download erfolgt in Form von einer ISO-Datei, die Sie auf den Zielcomputer für eine Offlineinstallation kopieren können.

## <a name="transfer-files"></a>Übertragen von Dateien

Kopieren Sie die SQL Server-Installationsmedien (ISO oder .cab) und in-Database-Analyse CAB-Dateien auf den Zielcomputer an. Platzieren Sie die CAB-Dateien und Medien-Installationsdatei in denselben Ordner auf dem Zielcomputer, z. B. **Downloads** oder Setup im Ordner des Benutzers % Temp *.

Der folgende Screenshot zeigt das CAB-Datei von SQL Server 2017 und ISO-Dateien. SQL Server 2016-Downloads sehen anders: weniger Dateien (keine Python), und die Installationsmedien Dateiname ist für 2016.

![Liste der zu übertragenden Dateien](media/offline-file-list.png "Dateiliste")

## <a name="run-setup"></a>Ausführen von 'Setup'

Wenn Sie SQL Server-Setup auf einem Computer, die vom Internet getrennt ausführen, fügt Setup eine **Offline-Installation** Seite des Assistenten, damit Sie den Speicherort der CAB-Dateien angeben können, die Sie im vorherigen Schritt kopiert haben.

1. Um die Installation zu starten, doppelklicken Sie auf die ISO oder CAB-Datei für den Zugriff auf den Installationsmedien. Daraufhin sollte die **setup.exe** Datei.

2. Mit der rechten Maustaste **setup.exe** und als Administrator ausführen.

3. Wenn der Setup-Assistent die lizenzierungsseite für Open Source-R oder Python-Komponenten angezeigt wird, klicken Sie auf **Accept**. Akzeptieren der Lizenzbedingungen können Sie mit dem nächsten Schritt fortfahren.

4. Wenn Sie sich zum erhalten der **Offline-Installation** auf der Seite **Installationspfad**, geben Sie den Ordner, enthält die CAB-Dateien, die Sie zuvor kopiert haben.

   ![Seite des Assistenten für die Auswahl der Cab-Ordner](media/screenshot-sql-offline-cab-page.png "CAB-Ordner")

5. Weiterhin folgenden die angezeigten aufforderungen, um die Installation abzuschließen.

## <a name="post-install-configuration"></a>Konfiguration nach der Installation

Nachdem die Installation abgeschlossen ist, starten Sie den Dienst neu, und konfigurieren Sie dann auf den Server, um die Ausführung des Skripts zu aktivieren:

+ [Aktivieren Sie die Ausführung des externen Skripts (SQL Server 2017)](sql-machine-learning-services-windows-install.md#bkmk_enableFeature)
+ [Aktivieren Sie die Ausführung des externen Skripts (SQL Server 2016)](sql-r-services-windows-install.md#bkmk_enableFeature)

Eine ersten offline-Installation von SQL Server 2017-Machine Learning Services oder SQL Server 2016 R Services ist die gleiche Konfiguration wie eine online-Installation erforderlich:

+ [Überprüfen der Installation](sql-machine-learning-services-windows-install.md#verify-installation) (für SQL Server 2016, klicken Sie auf [hier](sql-r-services-windows-install.md#verify-installation)).
+ [Zusätzliche Konfiguration nach Bedarf](sql-machine-learning-services-windows-install.md#additional-configuration) (für SQL Server 2016, klicken Sie auf [hier](sql-r-services-windows-install.md#bkmk_FollowUp)).

<a name="slipstream-upgrades"></a>

## <a name="slipstream-upgrades"></a>Slipstream-upgrades

Als Slipstream-Einrichtung wird die Möglichkeit bezeichnet, einen Patch oder ein Update auf eine fehlgeschlagene Installation einer Instanz anzuwenden, um vorhandene Probleme zu beheben. Diese Methode hat den Vorteil, dass SQL Server während der Einrichtung aktualisiert wird, sodass Sie später nur einmal einen Neustart durchführen müssen.

Wenn ein Server nicht über Internetzugriff verfügt, gelten Dienstupdates durch Herunterladen einer aktualisierten SQL Server-Installer und die entsprechenden Versionen der sprachspezifische CAB-Dateien. 

1. Beginnen Sie mit einer Baseline-Instanz. Slipstream-Upgrades werden für diese Versionen von SQL Server unterstützt:

  + Erste Version von SQL Server 2017
  + Erste Version von SQL Server 2016
  + SQL Server 2016 SP1.
  + SQL Server 2016 SP2

2. Erhalten Sie eine aktualisierte Version der SQL Server-Installationsprogramm für eine angegebene kumulative Update an. Ein Update auf die Machine learning (R- und Python)-Funktionen ist zusammen mit einem kumulativen Update von der zugrunde liegenden Datenbank-Engine-Instanz.

  + [Updates für SQL Server 2016](https://sqlserverupdates.com/sql-server-2016-updates/)
  + [SQL Server 2017-updates](https://sqlserverupdates.com/sql-server-2017-updates/)

3. Erhalten Sie entsprechende CAB-Dateien für R und Python. Downloadlinks finden Sie unter [CAB-downloads für kumulative Updates auf SQL Server in-Database-Analyse für Instanzen](sql-ml-cab-downloads.md).

4. Platzieren Sie alle Dateien im selben Ordner, führen Sie Setup aus. Während der Installation werden Sie aufgefordert, den Speicherort des Ordners für die aktualisierten CAB-Dateien auszuwählen.

## <a name="next-steps"></a>Nächste Schritte

Überprüfen Sie den Installationsstatus der Instanz, und beheben häufig auftretende Probleme, finden Sie unter [benutzerdefinierte Berichte für SQL Server R Services](../r/monitor-r-services-using-custom-reports-in-management-studio.md).

Hilfe mit unbekannten Nachrichten oder Protokolleinträge, finden Sie unter [Upgrade und Installation – häufig gestellte Fragen – Machine Learning Services](../r/upgrade-and-installation-faq-sql-server-r-services.md).

