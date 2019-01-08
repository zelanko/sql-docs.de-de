---
title: 'Upgrade und Installation gestellte häufig Fragen (FAQ): SQL Server Machine Learning Services'
ms.custom: sqlseattle
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/15/2018
ms.topic: conceptual
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.openlocfilehash: dd92ba0e080da0dd8ed387ae0a9f3d431232c896
ms.sourcegitcommit: 85bfaa5bac737253a6740f1f402be87788d691ef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2018
ms.locfileid: "53432853"
---
# <a name="upgrade-and-installation-faq-for-sql-server-machine-learning-or-r-server"></a>Upgrade und Installation – häufig gestellte Fragen für SQL Server-Machine-Learning oder R-Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieses Thema enthält Antworten auf einige häufig gestellte Fragen zur Installation von Machine learning-Funktionen in SQL Server. Außerdem werden häufige gestellte Fragen zu Upgrades behandelt.

+ Einige Probleme auftreten, nur für Upgrades von Vorabversionen. Aus diesem Grund empfehlen wir, dass Sie die Version und-Edition zunächst identifizieren vor dem Lesen die Anmerkungen zu dieser. Führen Sie zum Abrufen von Versionsinformationen `@@VERSION` in einer Abfrage von SQL Server Management Studio.
+ Aktualisieren Sie auf die aktuellste Version oder die Dienstversion so bald wie möglich auf die Behandlung von Problemen, die in neueren Versionen behoben wurden.

**Gilt für:** SQL Server 2016 R Services, SQL Server 2017-Machine-Learning-Services (Datenbankintern)

## <a name="requirements-and-restrictions-on-older-versions-of-sql-server-2016"></a>Anforderungen und Einschränkungen bei älteren Versionen von SQL Server 2016 

Abhängig von der Build von SQL Server, die Sie installieren, können einige der folgenden Einschränkungen gelten:

- In frühen Versionen von SQL Server 2016 R Services wurde der 8.3-Notation auf dem Laufwerk erforderlich, die das Arbeitsverzeichnis enthält. Wenn Sie eine Vorabversion installiert haben, sollte dieses Problems ein Upgrade auf SQL Server 2016 Service Pack 1 behoben werden. Diese Anforderung gilt nicht für Versionen nach SP1.

- Sie können derzeit nicht installieren [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] in einem Failovercluster installieren. Vorschau der SQL Server-2019 bietet Failoverunterstützung jedoch wenn Sie diese Capablity in einer testumgebung zu evaluieren möchten. Weitere Informationen finden Sie unter [neues](../what-s-new-in-sql-server-machine-learning-services.md).

- Klicken Sie auf eine Azure-VM kann einige zusätzliche Konfigurationsschritte erforderlich sein. Beispielsweise müssen Sie eine Firewallausnahme zur Unterstützung von remote-Zugriff erstellen.

- Seite-an-Seite-Installation mit einer anderen Version von R oder mit anderen Versionen von Revolution Analytics, wird nicht unterstützt.

- Deaktivieren Sie die virenprüfung vor dem Setup. Nach dem Abschluss der Installation sollten Sie anhalten virenüberprüfung für die Ordner ein, die [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)]. Vorzugsweise anhalten Scannen der gesamten [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] Struktur.

 - Installieren Microsoft R Server in einer Instanz von SQL Server auf Windows Core installiert. In der RTM-Version von SQL Server 2016 wies ein bekanntes Problem beim Hinzufügen von Microsoft R Server für eine Instanz auf Windows Server Core-Edition. Dies wurde behoben. Wenn Sie dieses Problem auftritt, können, wenden Sie das Update, die in beschriebenen [KB3164398](https://support.microsoft.com/kb/3164398) um die R-Funktion zu einer vorhandenen Instanz unter Windows Server Core hinzuzufügen. Weitere Informationen finden Sie unter [Microsoft R Server (eigenständig) kann nicht auf einem Windows Server Core-System installiert werden](https://support.microsoft.com/kb/3168691).


## <a name="offline-installation-of-machine-learning-components-for-a-localized-version-of-sql-server-2016"></a>Offline-Installation von Machine Learning-Komponenten eine lokalisierte Version von SQL Server 2016

Frühe Veröffentlichung-Versionen von SQL Server 2016 konnte gebietsschemaspezifische CAB-Dateien während der offline-Installation ohne Internetverbindung zu installieren. Dieses Problem wurde in späteren Versionen behoben, aber wenn das Installationsprogramm eine Meldung, die darauf hinweist, dass sie nicht die richtige Sprache installieren kann gibt, können Sie bearbeiten, einen Dateinamen, um die Installation fortgesetzt werden.

+ Manuell bearbeiten Sie, die Installer-Datei, um sicherzustellen, dass die richtige Sprache installiert ist. Z. B. um die japanische Version von SQL Server zu installieren, ändern Sie den Namen der Datei von SRS_8.0.3.0_**1033**.cab in SRS_8.0.3.0_**1041**CAB.
+ Die Sprachen-ID, die für die Machine learning-Komponenten verwendet, muss die SQL Server-Setupsprache identisch sein, oder Sie das Setup nicht abschließen.

## <a name="pre-release-versions-support-policies-upgrade-and-known-issues"></a>Vorabversionen: unterstützen von Richtlinien, Upgrade und bekannte Probleme

Neue Installationen von einer Vorabversion von [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] wird nicht mehr unterstützt. Wenn Sie eine Vorabversion verwenden, aktualisieren Sie so bald wie möglich.

Dieser Abschnitt enthält detaillierte Anweisungen für bestimmte Szenarien.

### <a name="how-to-upgrade-sql-server"></a>Gewusst wie: upgrade von SQL Server

Sie können Ihre Version von SQL Server aktualisieren, indem Sie den Setup-Assistenten erneut ausführen.

+ [Aktualisieren von SQL Server](../../database-engine/install-windows/upgrade-sql-server.md)
+ [Upgrade von SQLServer mithilfe des Installations-Assistenten](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)

Sie können nur für den Computer learning-Komponenten mithilfe eines Prozesses, der als Bindung bezeichnet aktualisieren: 
+ [Verwenden von SqlBindR zum Aktualisieren von Machine Learning-Komponenten](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)

### <a name="end-of-support-for-in-place-upgrades-from-prerelease-versions"></a>Ende des Supports für direkte Upgrades von Vorabversionen

Upgrades von Vorabversionen von SQL Server 2016 werden nicht mehr unterstützt. Dies schließt SQL Server 2016 CTP3, CTP3. 1, CTP3.2, RC0 oder RC1.

Die folgenden Versionen wurden mit Vorabversionen von SQL Server 2016 installiert.

| Version | Erstellen         |
|---------|---------------|
| CTP 3.0 | 13.0.xxx      |
| CTP 3.1 | 13.0.801.12   |
| CTP 3.2 | 13.0.900.73   |
| CTP 3.3 | 13.0.1000.281 |
| RC1     | 13.0.1200.242 |
| RC2     | 13.0.1300.275 |
| RC3     | 13.0.1400.361 |

Wenn Sie nicht sicher sind, haben, welche Version Sie verwenden, führen Sie `@@VERSION` in einer Abfrage von SQL Server Management Studio.

In der Regel lautet wie folgt der Prozess für das Upgrade:

1. Sichern Sie die Skripts und Daten.
2. Deinstallieren Sie die Vorabversion.
3. Installieren Sie eine Releaseversion.

Deinstallieren eine Vorabversion von SQL Server Machine Learning-Komponenten können komplex sein und eventuell ein spezielles Skript ausführen. Wenden Sie sich an den technischen Support, um Unterstützung zu erhalten.

###  <a name="bkmk_Uninstall"></a> Deinstallieren Sie vor dem Upgrade von einer älteren Version von Microsoft R Server

Wenn Sie eine Vorabversion von Microsoft R Server installiert haben, müssen Sie diese deinstallieren, bevor Sie auf eine neuere Version aktualisieren können.

1.  Klicken Sie in der **Systemsteuerung**auf **Programme hinzufügen/entfernen**, und wählen Sie `Microsoft SQL Server 2016 <version number>`aus.

2.  Wählen Sie im Dialogfeld mit den Optionen zum **Hinzufügen**, **Reparieren**oder **Entfernen** von Komponenten die Option **Entfernen**aus.
  
3.  Wählen Sie auf der Seite **Funktionen auswählen** unter **Freigegebene Funktionen**die Option **R Server (eigenständig)** aus. Klicken Sie auf **Weiter**, und klicken Sie dann auf **Fertig stellen** , um nur die ausgewählten Komponenten zu deinstallieren.

## <a name="r-services-and-r-server-standalone-side-by-side-errors"></a>R Services und R Server (eigenständig)-Seite-an-Seite-Fehler 

In früheren Versionen von SQL Server 2016 verursacht das Installieren von R Server (eigenständig) und R Services (Datenbankintern) zur gleichen Zeit manchmal Setup mit einer Meldung "Zugriff verweigert" fehlschlägt. Dieses Problem wurde in Service Pack 1 für SQL Server 2016 behoben.

Wenn Sie dieser Fehler auftritt, und diese Funktionen aktualisieren möchten, führen Sie eine Slipstream-Installation von SQL Server 2016 mit SP1. Es gibt zwei Möglichkeiten zum Beheben des Problems, die beide, deinstallieren und erneut installieren müssen.

1. Deinstallieren Sie R Services (Datenbankintern), und stellen Sie sicher, dass die Benutzerkonten für SQLRUserGroup entfernt werden.

2. Starten Sie den Server neu, und R Server (eigenständig) installieren.

3. Zur SQL Server-setup einmal mehr, und wählen Sie dieses Mal **Hinzufügen von Funktionen zu einer vorhandenen SQL Server**.

4. Wählen Sie die Instanz, und wählen Sie dann die **R Services (Datenbankintern)** Option zum Hinzufügen.

Wenn diese Prozedur nicht das Problem zu beheben, versuchen Sie die folgende Schritte zur problemumgehung aus:

1. Deinstallieren Sie R Services (Datenbankintern) und R Server (eigenständig) zur gleichen Zeit ein.

2. Entfernen Sie die lokalen Benutzerkonten (SQLRUserGroup).

3. Starten Sie den Server neu.

4. Führen Sie SQL Server-Setup aus, und fügen Sie nur das Feature für R Services (Datenbankintern). Aktivieren Sie nicht **R Server (eigenständig)**.

Im Allgemeinen empfehlen wir, dass Sie nicht sowohl für R Services (Datenbankintern) als auch für R Server (eigenständig) installieren auf dem gleichen Computer. Vorausgesetzt, dass der Server über genügend Kapazität verfügt, können Sie jedoch feststellen, dass R-Server (eigenständig) als ein Entwicklungstool von Nutzen sein kann. Ein anderes mögliches Szenario ist, dass Sie benötigen, verwenden Sie die Funktionen der operationalisierung von R Server, aber auch auf SQL Server-Daten ohne gleichzeitige datenverschiebung zugreifen möchten.

## <a name="incompatible-version-of-r-client-and-r-server"></a>Inkompatible Version von R Client und R Server

Wenn Sie Microsoft R Client installieren und verwenden, um R in einem remote SQL Server-rechenkontext ausführen, erhalten Sie möglicherweise einen Fehler wie folgt:

*Sie führen Version 9.0.0 von Microsoft R Client auf Ihrem Computer führen aus ist nicht mit der Microsoft R Server-Version 8.0.3 kompatibel. Laden Sie eine kompatible Version herunter und installieren Sie sie.*

In SQL Server 2016 war es erforderlich, dass die Version von R, die in SQL Server R Services ausgeführt wurde als die Bibliotheken in Microsoft R Client identisch sein. Diese Anforderung wurde in höheren Versionen entfernt. Allerdings empfiehlt es sich, dass Sie immer die neuesten Versionen der Machine learning-Komponenten zu erhalten, und installieren Sie alle Servicepacks. 

Wenn Sie eine frühere Version von Microsoft R Server aufweisen, und Sicherstellen der Kompatibilität mit Microsoft R Client 9.0.0 müssen, installieren Sie die Updates, die beschrieben werden, in diesem [Support-Artikel](https://support.microsoft.com/kb/3210262).


## <a name="installation-fails-with-error-only-one-revolution-enterprise-product-can-be-installed-at-a-time"></a>Installation schlägt fehl mit dem Fehler „Es kann jeweils nur ein Revolution Enterprise-Produkt installiert werden.“

Dieser Fehler kann auftreten, wenn Sie eine ältere Installation von Revolution Analytics-Produkten oder eine Vorabversion von SQL Server R Services verwenden. Sie müssen alle früheren Versionen deinstallieren, bevor Sie eine neuere Version von Microsoft R Server installieren können. Eine parallele Installation mit anderen Versionen der Revolution Enterprise-Tools wird nicht unterstützt.

Parallele Installationen werden jedoch unterstützt, wenn R Server (eigenständig) mit [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] oder SQL Server 2016 verwendet wird.

## <a name="registry-cleanup-to-uninstall-older-components"></a>Registrierung bereinigen deinstallieren ältere Komponenten

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

 [SQL Server Machine Learning-Dienste (Datenbankintern)](../r/sql-server-r-services.md)

 [SQL Server Machine Learning Server (eigenständig)](../r/r-server-standalone.md)
