---
title: Häufig gestellte Fragen zu Upgrade und Installation (FAQ)
ms.custom: sqlseattle
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
ms.author: davidph
author: dphansen
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: fe196a82badcab9ebe05004ee05cd67131942dd1
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715615"
---
# <a name="upgrade-and-installation-faq-for-sql-server-machine-learning-or-r-server"></a>FAQ zu Upgrade und Installation für SQL Server Machine Learning oder R Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dieses Thema enthält Antworten auf einige häufig gestellte Fragen zur Installation von Machine Learning-Features in SQL Server. Außerdem werden häufig gestellte Fragen zu Upgrades behandelt.

+ Einige Probleme treten nur bei Upgrades von vorab Versionen auf. Daher wird empfohlen, dass Sie die Version und die Edition zuerst ermitteln, bevor Sie diese Notizen lesen. Um Versionsinformationen zu erhalten, `@@VERSION` führen Sie in einer Abfrage aus SQL Server Management Studio aus.
+ Führen Sie ein Upgrade auf die aktuellste Version oder Dienst Freigabe so bald wie möglich durch, um Probleme zu beheben, die in den letzten Releases behoben wurden.

**Gilt für:** SQL Server 2016 R Services, SQL Server Machine Learning Services (in-Database)

## <a name="requirements-and-restrictions-on-older-versions-of-sql-server-2016"></a>Anforderungen und Einschränkungen für ältere Versionen von SQL Server 2016 

Abhängig vom Build der SQL Server, die Sie installieren, gelten möglicherweise einige der folgenden Einschränkungen:

- In frühen Versionen von SQL Server 2016 R Services war eine 8.3-Notation auf dem Laufwerk erforderlich, das das Arbeitsverzeichnis enthält. Wenn Sie eine Vorabversion installiert haben, sollte dieses Problem durch ein Upgrade auf SQL Server 2016 Service Pack 1 behoben werden. Diese Anforderung gilt nicht für Releases nach SP1.

- Zurzeit ist es nicht [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] möglich, auf einem Failovercluster zu installieren. SQL Server 2019 Preview bietet jedoch Failoverunterstützung, wenn Sie diese Funktion in einer Testumgebung auswerten möchten. Weitere Informationen finden Sie unter [Neuigkeiten](../what-s-new-in-sql-server-machine-learning-services.md).

- Auf einem virtuellen Azure-Computer sind möglicherweise einige zusätzliche Konfigurationen erforderlich. Beispielsweise kann es erforderlich sein, eine Firewallausnahme zu erstellen, um den Remote Zugriff zu unterstützen.

- Die parallele Installation mit einer anderen Version von R oder mit anderen Versionen von Revolution Analytics wird nicht unterstützt.

- Deaktivieren Sie die Viren Überprüfung, bevor Sie die Installation starten. Nachdem das Setup abgeschlossen ist, wird empfohlen, die Viren Überprüfung für die von [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)]verwendeten Ordner auszusetzen. Vorzugsweise sollten Sie die Überprüfung [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] der gesamten Struktur aussetzen.

 - Installieren von Microsoft R Server auf einer-Instanz, die unter Windows Core installiert SQL Server. In der RTM-Version von SQL Server 2016 gab es ein bekanntes Problem beim Hinzufügen von Microsoft R Server zu einer Instanz unter Windows Server Core Edition. Dies wurde behoben. Wenn dieses Problem auftritt, können Sie die in [KB3164398](https://support.microsoft.com/kb/3164398) beschriebene Korrektur anwenden, um die R-Funktion der vorhandenen Instanz von Windows Server Core hinzuzufügen. Weitere Informationen finden Sie unter [Microsoft R Server (eigenständig) kann nicht auf einem Windows Server Core-System installiert werden](https://support.microsoft.com/kb/3168691).


## <a name="offline-installation-of-machine-learning-components-for-a-localized-version-of-sql-server-2016"></a>Offline Installation von Machine Learning-Komponenten für eine lokalisierte Version von SQL Server 2016

In den frühen Versionen von SQL Server 2016 konnten keine Gebiets Schema spezifischen CAB-Dateien während des Offline-Setups ohne Internetverbindung installiert werden. Dieses Problem wurde in späteren Versionen behoben, aber wenn das Installationsprogramm eine Meldung zurückgibt, die besagt, dass die richtige Sprache nicht installiert werden kann, können Sie den Dateinamen bearbeiten, damit Setup fortgesetzt werden kann.

+ Bearbeiten Sie die Installerdatei manuell, um sicherzustellen, dass die richtige Sprache installiert ist. Um beispielsweise die japanische Version von SQL Server zu installieren, ändern Sie den Namen der Datei von srs_ 8.0.3.0 _**1033**. cab in srs_ 8.0.3.0 _**1041**. cab.
+ Die Sprach-ID, die für die Machine Learning-Komponenten verwendet wird, muss mit der SQL Server Setup Sprache identisch sein, oder Sie können das Setup nicht durchführen.

## <a name="pre-release-versions-support-policies-upgrade-and-known-issues"></a>Vorab Versionen: Support Richtlinien, Upgrade und bekannte Probleme

Neue Installationen einer Vorabversion von [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] werden nicht mehr unterstützt. Wenn Sie eine Vorabversion verwenden, aktualisieren Sie so bald wie möglich.

Dieser Abschnitt enthält ausführliche Anweisungen zu bestimmten Upgradeszenarien.

### <a name="how-to-upgrade-sql-server"></a>Upgraden SQL Server

Sie können Ihre Version von SQL Server aktualisieren, indem Sie den Setup-Assistenten erneut ausführen.

+ [Aktualisieren von SQL Server](../../database-engine/install-windows/upgrade-sql-server.md)
+ [Aktualisieren von SQL Server mithilfe des Installations-Assistenten](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)

Sie können nur die Machine Learning-Komponenten aktualisieren, indem Sie einen Prozess namens Binding verwenden: 
+ [Verwenden von sqlbindr zum Aktualisieren von Machine Learning-Komponenten](../install/upgrade-r-and-python.md)

### <a name="end-of-support-for-in-place-upgrades-from-prerelease-versions"></a>Ende der Unterstützung für direkte Upgrades von vorab Versionen

Upgrades von vorab Versionen von SQL Server 2016 werden nicht mehr unterstützt. Dies umfasst SQL Server 2016 CTP3, CTP 3.1, CTP 3.2, RC0 oder RC1.

Die folgenden Versionen wurden mit vorab Versionen von SQL Server 2016 installiert.

| Version | Build         |
|---------|---------------|
| CTP 3.0 | 13.0.xxx      |
| CTP 3.1 | 13.0.801.12   |
| CTP 3.2 | 13.0.900.73   |
| CTP 3.3 | 13.0.1000.281 |
| RC1     | 13.0.1200.242 |
| RC2     | 13.0.1300.275 |
| RC3     | 13.0.1400.361 |

Wenn Sie sich nicht sicher sind, welche Version Sie verwenden, führen `@@VERSION` Sie in einer Abfrage aus SQL Server Management Studio aus.

Im allgemeinen lautet der Upgradevorgang wie folgt:

1. Sichern Sie Skripts und Daten.
2. Deinstallieren Sie die Vorabversion.
3. Installieren Sie eine Releaseversion.

Das Deinstallieren einer Vorabversion der SQL Server Machine Learning-Komponenten kann komplex sein und das Ausführen eines speziellen Skripts erfordern. Wenden Sie sich an den technischen Support, um Unterstützung zu erhalten.

###  <a name="bkmk_Uninstall"></a>Deinstallieren vor dem Upgrade von einer älteren Version von Microsoft R Server

Wenn Sie eine Vorabversion von Microsoft R Server installiert haben, müssen Sie diese deinstallieren, bevor Sie auf eine neuere Version aktualisieren können.

1.  Klicken Sie in der **Systemsteuerung**auf **Programme hinzufügen/entfernen**, und wählen Sie `Microsoft SQL Server 2016 <version number>`aus.

2.  Wählen Sie im Dialogfeld mit den Optionen zum **Hinzufügen**, **Reparieren**oder **Entfernen** von Komponenten die Option **Entfernen**aus.
  
3.  Wählen Sie auf der Seite **Funktionen auswählen** unter **Freigegebene Funktionen**die Option **R Server (eigenständig)** aus. Klicken Sie auf **Weiter**, und klicken Sie dann auf **Fertig stellen** , um nur die ausgewählten Komponenten zu deinstallieren.

## <a name="r-services-and-r-server-standalone-side-by-side-errors"></a>Parallele Fehler bei R Services und R Server (eigenständig) 

In früheren Versionen von SQL Server 2016 führte die Installation von R Server (eigenständig) und R Services (in-Database) manchmal zu einem Fehler bei Setup mit der Meldung "Zugriff verweigert". Dieses Problem wurde in Service Pack 1 für SQL Server 2016 behoben.

Wenn dieser Fehler aufgetreten ist und Sie ein Upgrade für diese Features ausführen müssen, führen Sie eine Slipstream-Installation von SQL Server 2016 mit SP1 aus. Es gibt zwei Möglichkeiten, das Problem zu beheben, die beide deinstallieren und erneut installieren müssen.

1. Deinstallieren Sie R Services (in-Database), und stellen Sie sicher, dass die Benutzerkonten für sqlrusergroup entfernt wurden.

2. Starten Sie den Server neu, und installieren Sie R Server (eigenständig) neu.

3. Führen Sie SQL Server Setup erneut aus, und wählen Sie dieses Mal **die Option Features zu vorhandenem SQL Server hinzufügen**aus.

4. Wählen Sie die Instanz aus, und wählen Sie dann die Option **R Services (in-Database) aus** , die Sie hinzufügen möchten.

Wenn dieses Verfahren das Problem nicht beheben kann, versuchen Sie es mit der folgenden Problem Umgehung:

1. Deinstallieren Sie R Services (in-Database) und R Server (eigenständig) gleichzeitig.

2. Entfernen Sie die lokalen Benutzerkonten (sqlrusergroup).

3. Starten Sie den Server neu.

4. Führen Sie SQL Server Setup aus, und fügen Sie die Funktion R Services (in-Database) nur hinzu. Wählen Sie nicht **R Server (eigenständig)** aus.

Im Allgemeinen wird empfohlen, nicht gleichzeitig R Services (in-Database) und R Server (eigenständig) auf demselben Computer zu installieren. Wenn der Server jedoch über genügend Kapazität verfügt, können Sie feststellen, dass R Server Standalone als Entwicklungs Tool nützlich ist. Ein weiteres mögliches Szenario besteht darin, dass Sie die operationalisierungsfeatures von R Server verwenden müssen, aber auch ohne Daten Verschiebung auf SQL Server Daten zugreifen möchten.

## <a name="incompatible-version-of-r-client-and-r-server"></a>Inkompatible Version von R Client und R Server

Wenn Sie Microsoft R Client installieren und zum Ausführen von R in einem Remote SQL Server computekontext verwenden, erhalten Sie möglicherweise eine Fehlermeldung wie die folgende:

*Sie führen die Version 9.0.0 von Microsoft R Client auf Ihrem Computer aus, der mit der Microsoft R Server Version 8.0.3 nicht kompatibel ist. Laden Sie eine kompatible Version herunter und installieren Sie sie.*

In SQL Server 2016 war es erforderlich, dass die Version von R, die in SQL Server R Services ausgeführt wurde, exakt mit den Bibliotheken in Microsoft R Client übereinstimmen. Diese Anforderung wurde in späteren Versionen entfernt. Es wird jedoch empfohlen, immer die neuesten Versionen der Machine Learning-Komponenten zu erhalten und alle Service Packs zu installieren. 

Wenn Sie über eine frühere Version von Microsoft R Server verfügen und die Kompatibilität mit Microsoft R Client 9.0.0 sicherstellen müssen, installieren Sie die Updates, die in diesem [Support Artikel](https://support.microsoft.com/kb/3210262)beschrieben werden.


## <a name="installation-fails-with-error-only-one-revolution-enterprise-product-can-be-installed-at-a-time"></a>Installation schlägt fehl mit dem Fehler „Es kann jeweils nur ein Revolution Enterprise-Produkt installiert werden.“

Dieser Fehler kann auftreten, wenn Sie eine ältere Installation von Revolution Analytics-Produkten oder eine Vorabversion von SQL Server R Services verwenden. Sie müssen alle früheren Versionen deinstallieren, bevor Sie eine neuere Version von Microsoft R Server installieren können. Eine parallele Installation mit anderen Versionen der Revolution Enterprise-Tools wird nicht unterstützt.

Parallele Installationen werden jedoch unterstützt, wenn R Server (eigenständig) mit [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] oder SQL Server 2016 verwendet wird.

## <a name="registry-cleanup-to-uninstall-older-components"></a>Registrierungs Bereinigung zum Deinstallieren älterer Komponenten

Wenn Sie Probleme beim Entfernen einer älteren Version haben, müssen Sie unter Umständen die Registrierung bearbeiten, um betroffene Schlüssel zu entfernen.

> [!IMPORTANT]
> Dieses Problem tritt nur auf, wenn Sie eine Vorabversion von Microsoft R Server oder eine CTP-Version von SQL Server 2016 R Services installiert haben.
  
1. Öffnen Sie die Windows-Registrierung, und suchen Sie folgenden Schlüssel: `HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall`.
2. Löschen Sie einen der folgenden Einträge, wenn er vorhanden ist und der Schlüssel nur den Wert `sEstimatedSize2`enthält:
  
    -   E0B2C29E-B8FC-490B-A043-2CAE75634972        (für 8.0.2)
  
    -   46695879-954E-4072-9D32-1CC84D4158F4        (für 8.0.1)
  
    -   2DF16DF8-A2DB-4EC6-808B-CB5A302DA91B        (für 8.0.0)
  
    -   5A2A1571-B8CD-4AAF-9303-8DF463DABE5A        (für 7.5.0)

## <a name="see-also"></a>Siehe auch

 [SQL Server Machine Learning Services (in-Database)](../r/sql-server-r-services.md)

 [SQL Server Machine Learning Server (eigenständig)](../r/r-server-standalone.md)
