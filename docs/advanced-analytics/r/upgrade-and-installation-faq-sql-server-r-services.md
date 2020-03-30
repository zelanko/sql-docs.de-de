---
title: Häufig gestellte Fragen zu Upgrade und Installation
description: Hier finden Sie Antworten auf einige häufig gestellte Fragen zur Installation von Machine Learning-Funktionen in SQL Server.
ms.custom: seo-lt-2019
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/06/2019
ms.topic: conceptual
ms.author: davidph
author: dphansen
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6357f98627842ab790b494cf1b4a1f9b2110ec9c
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "73727344"
---
# <a name="upgrade-and-installation-faq-for-sql-server-machine-learning-or-r-server"></a>Häufig gestellte Fragen zu Upgrade und Installation für SQL Server-Machine Learning oder R Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dieses Thema enthält Antworten auf einige häufig gestellte Fragen zur Installation von Machine Learning-Funktionen in SQL Server. Zudem werden häufig gestellte Fragen zu Upgrades beantwortet.

+ Einige Probleme treten nur bei Upgrades von Vorabversionen auf. Daher sollten Sie sich über die von Ihnen verwendete Version und Edition informieren, bevor Sie mit diesen Hinweisen fortfahren. Führen Sie zum Abrufen der Versionsinformationen in SQL Server Management Studio in einer Abfrage `@@VERSION` aus.
+ Führen Sie so bald wie möglich ein Upgrade auf das aktuelle Release oder Service Release aus, um Probleme zu lösen, die in den neuesten Releases behoben wurden.

**Anwendungsbereich:** SQL Server 2016 R Services, SQL Server Machine Learning Services (datenbankintern)

## <a name="requirements-and-restrictions-on-older-versions-of-sql-server-2016"></a>Anforderungen und Einschränkungen für ältere Versionen von SQL Server 2016 

Je nachdem, welchen Build von SQL Server Sie installieren, gelten möglicherweise einige der folgenden Einschränkungen:

- In frühen Versionen von SQL Server 2016 R Services war auf dem Laufwerk, das das Arbeitsverzeichnis enthält, die 8.3-Notation erforderlich. Wenn Sie eine Vorabversion installiert haben, sollte dieses Problem durch ein Upgrade auf SQL Server 2016 Service Pack 1 behoben werden. Diese Anforderung gilt nicht für Releases nach SP1.

- Sie können [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] nicht auf einem Failovercluster in SQL Server 2016 installieren. SQL Server 2019 stellt dennoch Failoverunterstützung bereit. Weitere Informationen finden Sie unter [Neuerungen](../what-s-new-in-sql-server-machine-learning-services.md).

- Auf einem virtuellen Azure-Computer können einige zusätzliche Konfigurationen erforderlich sein. Beispielsweise kann es erforderlich sein, eine Firewallausnahme für die Unterstützung von Remotezugriff zu erstellen.

- Eine parallele Installation mit einer anderen Version von R oder mit anderen Releases von Revolution Analytics wird nicht unterstützt.

- Deaktivieren Sie den Virenscanner, bevor Sie mit dem Setup beginnen. Nach Abschluss des Setups sollten Sie den Virenscan für die von [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] verwendeten Ordner aussetzen. Vorzugsweise sollten Sie den Scan für die gesamte [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)]-Struktur aussetzen.

 - Installieren von Microsoft R Server in einer Instanz von SQL Server unter Windows Core: Die RTM-Version von SQL Server 2016 wies ein bekanntes Problem beim Hinzufügen von Microsoft R Server zu einer Instanz unter Windows Server Core auf. Dies wurde behoben. Sollte bei Ihnen dieses Problem auftreten, können Sie die in [KB3164398](https://support.microsoft.com/kb/3164398) beschriebene Fehlerbehebung anwenden, um die R-Funktion zur vorhandenen Instanz unter Windows Server Core hinzuzufügen. Weitere Informationen finden Sie unter [Microsoft R Server (eigenständig) kann nicht auf einem Windows Server Core-System installiert werden](https://support.microsoft.com/kb/3168691).


## <a name="offline-installation-of-machine-learning-components-for-a-localized-version-of-sql-server-2016"></a>Offlineinstallation von Machine Learning-Komponenten für eine lokalisierte Version von SQL Server 2016

In frühen Versionen von SQL Server 2016 konnten bei einer Offlineeinrichtung ohne Internetverbindung keine gebietsschemaspezifischen CAB-Dateien installiert werden. Dieses Problem wurde in späteren Releases behoben. Gibt der Installer jedoch die Meldung zurück, dass die richtige Sprache nicht installiert werden kann, können Sie den Dateinamen bearbeiten und das Setup fortsetzen.

+ Bearbeiten Sie die Installationsdatei manuell, um sicherzustellen, dass die richtige Sprache installiert wird. Wenn Sie beispielsweise die japanische Version von SQL Server installieren möchten, ändern Sie den Dateinamen von „SRS_8.0.3.0_**1033**.cab“ in „SRS_8.0.3.0_**1041**.cab“.
+ Die für die Machine Learning-Komponenten verwendete Sprachen-ID muss der SQL Server-Setupsprache entsprechen. Andernfalls können Sie das Setup nicht abschließen.

## <a name="pre-release-versions-support-policies-upgrade-and-known-issues"></a>Vorabversionen: Richtlinien zur Unterstützung, Upgrades und bekannte Probleme

Neue Installationen einer Vorabversion von [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] werden nicht mehr unterstützt. Wenn Sie eine Vorabversion verwenden, führen Sie also so bald wie möglich ein Upgrade durch.

Dieser Abschnitt enthält ausführliche Anweisungen für bestimmte Upgradeszenarios.

### <a name="how-to-upgrade-sql-server"></a>Upgrade von SQL Server

Sie können Ihre Version von SQL Server aktualisieren, indem Sie den Setup-Assistenten erneut ausführen.

+ [Aktualisieren von SQL Server](../../database-engine/install-windows/upgrade-sql-server.md)
+ [Upgrade von SQL Server mithilfe des Installations-Assistenten](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)

Mithilfe einer sogenannten Bindung können Sie auch nur die Machine Learning-Komponenten aktualisieren: 
+ [Verwenden von SqlBindR zum Aktualisieren von Machine Learning-Komponenten](../install/upgrade-r-and-python.md)

### <a name="end-of-support-for-in-place-upgrades-from-prerelease-versions"></a>Supportende für direkte Upgrades von Vorabversionen

Upgrades von Vorabversionen von SQL Server 2016 werden nicht mehr unterstützt. Dies betrifft u. a. SQL Server 2016 CTP3, CTP3.1, CTP3.2, RC0 und RC1.

Die folgenden Versionen wurden mit Vorabversionen von SQL Server 2016 installiert:

| Version | Entwickeln         |
|---------|---------------|
| CTP 3.0 | 13.0.xxx      |
| CTP 3.1 | 13.0.801.12   |
| CTP 3.2 | 13.0.900.73   |
| CTP 3.3 | 13.0.1000.281 |
| RC1     | 13.0.1200.242 |
| RC2     | 13.0.1300.275 |
| RC3     | 13.0.1400.361 |

Wenn Sie sich nicht sicher sind, welche Version Sie verwenden, führen Sie `@@VERSION` in einer Abfrage in SQL Server Management Studio aus.

Der Upgradevorgang läuft in der Regel folgendermaßen ab:

1. Skripts und Daten sichern
2. die Vorabversion deinstallieren
3. eine Releaseversion installieren

Das Deinstallieren einer Vorabversion der SQL Server-Machine Learning-Komponenten kann ein komplexer Vorgang sein, der möglicherweise das Ausführen eines bestimmten Skripts erfordert. Wenden Sie sich an den technischen Support, um Unterstützung zu erhalten.

###  <a name="uninstall-prior-to-upgrading-from-an-older-version-of-microsoft-r-server"></a><a name="bkmk_Uninstall"></a> Deinstallation vor dem Ausführen eines Upgrades von einer älteren Version von Microsoft R Server

Wenn Sie eine Vorabversion von Microsoft R Server installiert haben, müssen Sie diese deinstallieren, bevor Sie auf eine neuere Version aktualisieren können.

1.  Klicken Sie in der **Systemsteuerung**auf **Programme hinzufügen/entfernen**, und wählen Sie `Microsoft SQL Server 2016 <version number>`aus.

2.  Wählen Sie im Dialogfeld mit den Optionen zum **Hinzufügen**, **Reparieren**oder **Entfernen** von Komponenten die Option **Entfernen**aus.
  
3.  Wählen Sie auf der Seite **Funktionen auswählen** unter **Freigegebene Funktionen**die Option **R Server (eigenständig)** aus. Klicken Sie auf **Weiter**, und klicken Sie dann auf **Fertig stellen** , um nur die ausgewählten Komponenten zu deinstallieren.

## <a name="r-services-and-r-server-standalone-side-by-side-errors"></a>Fehler bei der parallelen Installation von R Services und R Server (eigenständig) 

In früheren Versionen von SQL Server 2016 führte die gleichzeitige Installation von R Server (eigenständig) und R Services (datenbankintern) gelegentlich zu einem Setup-Fehler mit der Meldung „Zugriff verweigert“. Dieses Problem wurde in Service Pack 1 für SQL Server 2016 behoben.

Wenn dieser Fehler bei Ihnen auftritt und Sie die Funktionen aktualisieren müssen, führen Sie eine Slipstreaminstallation von SQL Server 2016 mit SP1 aus. Es gibt zwei Möglichkeiten, das Problem zu beheben, und beide erfordern die Deinstallation und Neuinstallation.

1. Deinstallieren Sie R Services (datenbankintern), und stellen Sie dabei sicher, dass die Benutzerkonten für „SQLRUserGroup“ entfernt werden.

2. Starten Sie den Server neu, und installieren Sie R Server (eigenständig) neu.

3. Führen Sie das SQL Server-Setup erneut aus, und aktivieren Sie dieses Mal die Option **Funktionen zu einer vorhandenen SQL Server-Instanz hinzufügen**.

4. Wählen Sie die Instanz aus, und aktivieren Sie dann die Option **R Services (datenbankintern)** , um die Funktion hinzuzufügen.

Sollte das Problem weiter bestehen, versuchen Sie es mit der folgenden Problemumgehung:

1. Deinstallieren Sie gleichzeitig R Services (datenbankintern) und R Server (eigenständig).

2. Entfernen Sie die lokalen Benutzerkonten (SQLRUserGroup).

3. Starten Sie den Server neu.

4. Führen Sie das SQL Server-Setup aus, und fügen Sie nur die Funktion R Services (datenbankintern) hinzu. Wählen Sie nicht die Funktion **R Server (eigenständig)** aus.

R Services (datenbankintern) und R Server (eigenständig) sollten im Allgemeinen nicht auf demselben Computer installiert werden. Verfügt der Server jedoch über eine ausreichende Kapazität, kann R Server (eigenständig) ein nützliches Entwicklungstool darstellen. Ein weiteres mögliches Szenario besteht darin, dass Sie die Operationalisierungsfunktionen von R Server verwenden müssen und gleichzeitig ohne Datenverschiebung auf Daten in SQL Server zugreifen möchten.

## <a name="incompatible-version-of-r-client-and-r-server"></a>Inkompatible Version von R Client und R Server

Wenn Sie Microsoft R Client installieren und anschließend verwenden, um R in einem SQL Server-Remotecomputekontext auszuführen, erhalten Sie möglicherweise eine Fehlermeldung wie die folgende:

*Sie führen Version 9.0.0 von Microsoft R Client auf Ihrem Computer aus. Diese ist nicht mit der Version 8.0.3 von Microsoft R Server kompatibel. Laden Sie eine kompatible Version herunter und installieren Sie sie.*

In SQL Server 2016 musste die in SQL Server R Services ausgeführte Version von R exakt mit den Bibliotheken in Microsoft R Client übereinstimmen. Diese Anforderung wurde in späteren Versionen entfernt. Es wird jedoch empfohlen, dass Sie immer die aktuelle Version der Machine Learning-Komponenten verwenden und alle Service Packs installieren. 

Wenn Sie eine frühere Version von Microsoft R Server verwenden und die Kompatibilität mit Microsoft R Client 9.0.0 sicherstellen möchten, installieren Sie die in diesem [Supportartikel](https://support.microsoft.com/kb/3210262) beschriebenen Updates.


## <a name="installation-fails-with-error-only-one-revolution-enterprise-product-can-be-installed-at-a-time"></a>Installation schlägt fehl mit dem Fehler „Es kann jeweils nur ein Revolution Enterprise-Produkt installiert werden.“

Dieser Fehler kann auftreten, wenn Sie eine ältere Installation von Revolution Analytics-Produkten oder eine Vorabversion von SQL Server R Services verwenden. Sie müssen alle früheren Versionen deinstallieren, bevor Sie eine neuere Version von Microsoft R Server installieren können. Eine parallele Installation mit anderen Versionen der Revolution Enterprise-Tools wird nicht unterstützt.

Parallele Installationen werden jedoch unterstützt, wenn R Server (eigenständig) mit [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] oder SQL Server 2016 verwendet wird.

## <a name="registry-cleanup-to-uninstall-older-components"></a>Bereinigen der Registrierung zum Deinstallieren älterer Komponenten

Wenn Sie Probleme beim Entfernen einer älteren Version haben, müssen Sie unter Umständen die Registrierung bearbeiten, um betroffene Schlüssel zu entfernen.

> [!IMPORTANT]
> Dieses Problem tritt nur auf, wenn Sie eine Vorabversion von Microsoft R Server oder eine CTP-Version von SQL Server 2016 R Services installiert haben.
  
1. Öffnen Sie die Windows-Registrierung, und suchen Sie folgenden Schlüssel: `HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall`.
2. Löschen Sie einen der folgenden Einträge, wenn er vorhanden ist und der Schlüssel nur den Wert `sEstimatedSize2`enthält:
  
    -   E0B2C29E-B8FC-490B-A043-2CAE75634972        (für 8.0.2)
  
    -   46695879-954E-4072-9D32-1CC84D4158F4        (für 8.0.1)
  
    -   2DF16DF8-A2DB-4EC6-808B-CB5A302DA91B        (für 8.0.0)
  
    -   5A2A1571-B8CD-4AAF-9303-8DF463DABE5A        (für 7.5.0)

## <a name="see-also"></a>Weitere Informationen

 [SQL Server Machine Learning Services (datenbankintern)](../r/sql-server-r-services.md)

 [SQL Server-Machine Learning Server (eigenständig)](../r/r-server-standalone.md)
