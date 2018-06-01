---
title: Installieren Sie neue R-Pakete auf SQL Server-Machine Learning-Services | Microsoft Docs
description: Hinzufügen von neuen R-Pakete auf SQL Server 2016 R Services oder SQL Server 2017 Machine Learning Services (Datenbankintern)
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/29/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: e05842a8e8a5a1d2454dbbe500b4d5aa95fca660
ms.sourcegitcommit: 2d93cd115f52bf3eff3069f28ea866232b4f9f9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/01/2018
ms.locfileid: "34707078"
---
# <a name="install-new-r-packages-on-sql-server"></a>Installieren Sie neue R-Pakete unter SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel beschreibt, wie neue R-Pakete mit einer Instanz von SQL Server installieren, Machine Learning aktiviert ist. Es gibt mehrere Methoden für die Installation von neuen R-Pakete, je nach von Ihnen installierten Version von SQL Server, und gibt an, ob der Server über eine Internetverbindung verfügt. Die folgenden Ansätze für die Neuinstallation des Pakets sind möglich.

| Vorgehensweise                           | Berechtigungen               | Remote/Local |
|------------------------------------|---------------------------|--------------|
| [Verwenden Sie herkömmliche R-Paket-Manager](use-r-package-managers-on-sql-server.md)  | Admin | Lokal |
| [Verwenden von RevoScaleR](use-revoscaler-to-manage-r-packages.md) |  Im Anschluss daran Datenbankrollen Admin aktiviert | both|
| [Verwenden von T-SQL (externe Bibliothek erstellen)](install-r-packages-tsql.md) | Im Anschluss daran Datenbankrollen Admin aktiviert | both 

## <a name="who-installs-permissions"></a>Wer (Berechtigungen) installiert

Die R-Paket-Bibliothek befindet sich physisch im Ordner "Programme" Ihrer SQL Server-Instanz in einem sicheren Ordner mit eingeschränktem Zugriff. Das Schreiben in diesen Speicherort sind Administratorberechtigungen erforderlich.

Nicht-Administratoren können Installationspakete dazu sind jedoch zusätzliche Konfiguration und Funktionalität, die im ersten Installationen nicht verfügbar. Es gibt zwei Ansätze zum ohne Administratorrechte für die Paketinstallation: "revoscaler" verwenden Version 9.0.1 und später erneut, oder mit EXTERNEN Bibliothek erstellen (nur SQL Server 2017). In SQL Server 2017 **Dbo_owner** oder ein anderer Benutzer mit Berechtigung für externe Bibliothek erstellen kann R-Pakete installieren, auf die aktuelle Datenbank.

R-Entwickler sind daran gewöhnt, Erstellen von benutzerbibliotheken für die Pakete, die sie benötigen, wenn zentral Bibliotheken off-limits sind. Diese Vorgehensweise ist problematisch für R-Code in eine SQL Server-Datenbankmodulinstanz ausgeführt. SQL Server kann nicht von externen Bibliotheken Pakete laden, selbst wenn diese Bibliothek auf demselben Computer ist. Nur Pakete aus der Instanz-Bibliothek können in R-Code ausgeführt wird, in SQL Server verwendet werden.

Dateisystemzugriff ist in der Regel auf dem Server beschränkt und auch wenn Sie in einen Benutzer Dokumentordner auf dem Server Administratorrechte sowie über Zugriff verfügt, nicht externes Skript-Laufzeit, die in SQL Server ausgeführt wird Pakete außerhalb der Standardinstanz installiert verfügbar Bibliothek. 

## <a name="considerations-for-package-installation"></a>Überlegungen für die Paketinstallation

Berücksichtigen Sie vor der Installation von neuen Paketen können, ob es sich bei die von einem bestimmten Paket aktivierten Funktionen in einer SQL Server-Umgebung geeignet sind. Auf eine gesicherte SQL Server-Umgebung empfiehlt es sich um Folgendes zu vermeiden:

+ Pakete, die Zugriff auf das Netzwerk erfordern.
+ Pakete, die Java oder andere Frameworks, die üblicherweise nicht in einer SQL Server-Umgebung verwendet erfordern
+ Pakete, die mit erhöhten Rechten Dateisystemzugriff erfordern
+ Paket wird für die Webentwicklung oder andere Aufgaben, die durch die Ausführung innerhalb von SQL Server profitieren nicht verwendet.

## <a name="offline-installation-no-internet-access"></a>Offline-Installation (keinen Internetzugang)

Im Allgemeinen blockieren auf Servern, Produktionsdatenbanken hosten, Internet-Verbindungen. Installieren von neuen R oder Python-Pakete in solchen Umgebungen erfordert, dass Sie Pakete und Abhängigkeiten im Voraus vorbereiten, und kopieren Sie die Dateien in einen Ordner auf dem Server für offline-Installation.

Identifizieren alle Abhängigkeiten komplizierter. Für R, empfehlen wir die Verwendung [MiniCRAN So erstellen ein lokales Repository](create-a-local-package-repository-using-minicran.md) übertragen und dann das vollständig definierte Repository an eine isolierte SQL Server-Instanz.

Wahlweise können Sie diese Schritte manuell ausführen:

1. Identifizieren Sie alle Abhängigkeiten des Pakets an. 
2. Überprüfen Sie, ob alle erforderlichen Pakete auf dem Server bereits installiert sind. Wenn das Paket installiert ist, stellen Sie sicher, dass die Version richtig ist.
3. Laden Sie das Paket und alle Abhängigkeiten auf einen separaten Computer herunter.
4. Verschieben Sie die Dateien vom Server in einen Ordner zugegriffen werden kann.
5. Führen Sie eine unterstützte Installationsbefehl oder DDL-Anweisung, zum Installieren des Pakets in die Bibliothek für die Instanz.

### <a name="download-the-package-as-a-zipped-file"></a>Das Paket als ZIP-Datei herunterladen

Für die Installation auf einem Server ohne Internetzugriff müssen Sie eine Kopie des Pakets in das Format einer ZIP-Datei für die Offlineinstallation herunterladen. **Entzippen Sie das Paket nicht.**

Z. B. das folgende Verfahren beschreibt jetzt, um die richtige Version von den [FISHalyseR](http://bioconductor.org/packages/release/bioc/html/FISHalyseR.html) Paket von Bioconductor, vorausgesetzt, der Computer über Internetzugriff verfügt.

1.  Suchen Sie in der Liste der **Paketarchive** die **Windows-Binärdateiversion** .

2.  Mit der rechten Maustaste des Links, um die. ZIP-Datei, und wählen **Ziel speichern unter**.

3.  Navigieren Sie zu den lokalen Ordner, in dem komprimierten Pakete gespeichert sind, und klicken Sie auf **speichern**.

    Dieser Vorgang erstellt eine lokale Kopie des Pakets. 

4. Wenn Sie einen Download-Fehler erhalten, versuchen Sie eine andere gespiegelte Site aus.

5. Nachdem das Archiv Paket heruntergeladen wurde, können Sie installieren Sie das Paket oder kopieren das ZIP-Paket auf einen Server, die über keinen Zugriff auf das Internet.

> [!TIP]
> Wenn versehentlich des Pakets installieren anstelle eines Downloads von Binärdateien wird eine Kopie der heruntergeladene ZIP-Datei auch auf Ihrem Computer gespeichert. Beobachten Sie die statusmeldungen aus, während das Paket installiert wird, um den Dateispeicherort zu bestimmen. Sie können diese ZIP-Datei an den Server kopieren, die über keinen Zugriff auf das Internet.
> 
> Wenn Sie Pakete, die mit dieser Methode abgerufen haben, sind die Abhängigkeiten nicht enthalten. 


## <a name="side-by-side-installation-with-standalone-r-or-python-servers"></a>Seite-an-Seite-Installation mit Standalone R oder Python-Servern

R und Python-Funktionen sind in zahlreichen Microsoft-Produkten, enthalten, die alle auf demselben Computer koexistieren konnte.

Wenn Sie SQL Server 2017 Microsoft Machine Learning-Server (eigenständig) oder SQL Server 2016 R Server (eigenständig) zusätzlich zu den in der Datenbank Analytics (SQL Server 2017 Machine Learning Services und SQL Server 2016 R Services) installiert haben, sind für Ihren Computer separate Installationen von R für die einzelnen Duplikate aller R-Tools und Bibliotheken.

Pakete, die in der Bibliothek R_SERVER installiert sind, werden nur von einem eigenständigen Server verwendet und können nicht zugegriffen werden, indem Sie eine Instanz von SQL Server (In-Database). Verwenden Sie immer die `R_SERVICES` Bibliothek Installieren von Paketen, die Sie in der Datenbank auf SQL Server verwenden möchten. Weitere Informationen zu Pfaden finden Sie unter [Bibliothek Paketspeicherort](installing-and-managing-r-packages.md#package-library-location).


## <a name="see-also"></a>Siehe auch

+ [Neue Python-Pakete installieren](../python/install-additional-python-packages-on-sql-server.md)
+ [Tutorials, Beispiele, Lösungen](../tutorials/machine-learning-services-tutorials.md)