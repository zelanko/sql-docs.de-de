---
title: Installieren neuer R-Sprachpakete
description: Hinzufügen neuer R-Pakete zu SQL Server 2016 R Services oder SQL Server Machine Learning Services (in-Database)
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 1048dc6ef0a43c5fa41dd5398a5b3dced4a5ebe8
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715102"
---
# <a name="install-new-r-packages-on-sql-server"></a>Installieren neuer R-Pakete auf SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Artikel wird beschrieben, wie Sie neue R-Pakete in einer Instanz von SQL Server installieren, auf der Machine Learning aktiviert ist. Es gibt mehrere Methoden zum Installieren neuer R-Pakete, je nachdem, welche Version von SQL Server Sie haben und ob der Server über eine Internetverbindung verfügt. Die folgenden Vorgehensweisen für die Installation eines neuen Pakets sind möglich.

| Ansatz                           | Berechtigungen               | Remote/lokal |
|------------------------------------|---------------------------|--------------|
| [Verwenden von herkömmlichen R-Paket-Managern](use-r-package-managers-on-sql-server.md)  | Admin | Lokal |
| [Verwenden von RevoScaleR](use-revoscaler-to-manage-r-packages.md) |  Für den Administrator aktivierte Daten bankrollen anschließend | both|
| [Verwenden von T-SQL (externe Bibliothek erstellen)](install-r-packages-tsql.md) | Für den Administrator aktivierte Daten bankrollen anschließend | both 

## <a name="who-installs-permissions"></a>Wer installiert (Berechtigungen)

Die R-paketbibliothek befindet sich physisch im Ordner "Programme" Ihrer SQL Server Instanz, in einem sicheren Ordner mit eingeschränktem Zugriff. Zum Schreiben an diesen Speicherort sind Administrator Berechtigungen erforderlich.

Nicht-Administratoren können Pakete installieren. hierfür sind jedoch zusätzliche Konfigurationsschritte erforderlich, die in erst Installationen nicht verfügbar sind. Es gibt zwei Ansätze für Installationen von nicht-Administrator Paketen: Revoscaler mit Version 9.0.1 und höher oder mit CREATE externe Library (nur SQL Server 2017). In SQL Server 2017 können R-Pakete von **dbo_owner** oder einem anderen Benutzer mit der Berechtigung CREATE extern Library in der aktuellen Datenbank installiert werden.

R-Entwickler sind daran gewöhnt, Benutzer Bibliotheken für die Pakete zu erstellen, die Sie benötigen, wenn sich zentral lokalisierte Bibliotheken außerhalb der Grenzen befinden. Diese Vorgehensweise ist problematisch für R-Code, der in einer SQL Server Datenbank-Engine-Instanz ausgeführt wird. SQL Server können Pakete nicht aus externen Bibliotheken laden, auch wenn sich diese Bibliothek auf demselben Computer befindet. Nur Pakete aus der instanzbibliothek können in R-Code verwendet werden, der in SQL Server ausgeführt wird.

Der Dateisystem Zugriff wird in der Regel auf dem Server eingeschränkt, und auch wenn Sie über Administratorrechte und Zugriff auf einen Benutzer Dokument Ordner auf dem Server verfügen, kann die externe Skript Laufzeit, die in SQL Server ausgeführt wird, nicht auf Pakete zugreifen, die außerhalb der Standard Instanz installiert sind. fern. 

## <a name="considerations-for-package-installation"></a>Überlegungen zur Paketinstallation

Berücksichtigen Sie vor der Installation neuer Pakete, ob die von einem bestimmten Paket aktivierten Funktionen in einer SQL Server Umgebung geeignet sind. In einer SQL Server Umgebung mit verstärkter Sicherheit sollten Sie Folgendes vermeiden:

+ Pakete, für die Netzwerk Zugriff erforderlich ist
+ Pakete, für die ein erhöhter Dateisystem Zugriff erforderlich ist
+ Das Paket wird für die Webentwicklung oder andere Aufgaben verwendet, die von der Ausführung innerhalb SQL Server nicht profitieren.

## <a name="offline-installation-no-internet-access"></a>Offline Installation (kein Internet Zugriff)

Im allgemeinen blockieren Server, die Produktionsdatenbanken hosten, Internetverbindungen. Die Installation neuer R-oder python-Pakete in solchen Umgebungen erfordert, dass Sie Pakete und Abhängigkeiten vorab vorbereiten und die Dateien für die Offline Installation in einen Ordner auf dem Server kopieren.

Das Identifizieren aller Abhängigkeiten wird kompliziert. Für R empfiehlt es sich, dass Sie [minicran verwenden, um ein lokales Repository zu erstellen](create-a-local-package-repository-using-minicran.md) , und dann das vollständig definierte Repository auf eine isolierte SQL Server Instanz übertragen.

Alternativ können Sie diese Schritte auch manuell ausführen:

1. Identifizieren aller Paketabhängigkeiten. 
2. Überprüfen Sie, ob alle erforderlichen Pakete bereits auf dem Server installiert sind. Wenn das Paket installiert ist, überprüfen Sie, ob die Version korrekt ist.
3. Laden Sie das Paket und alle Abhängigkeiten auf einen separaten Computer herunter.
4. Verschieben Sie die Dateien in einen Ordner, auf den der Server zugreifen kann.
5. Führen Sie einen unterstützten Installations Befehl oder eine DDL-Anweisung aus, um das Paket in der instanzbibliothek zu installieren

### <a name="download-the-package-as-a-zipped-file"></a>Paket als ZIP-Datei herunterladen

Für die Installation auf einem Server ohne Internet Zugriff müssen Sie eine Kopie des Pakets im Format einer ZIP-Datei für die Offline Installation herunterladen. **Entpacken Sie das Paket nicht.**

Im folgenden Verfahren wird z. b. beschrieben, wie Sie die richtige Version des [fishalyser](https://bioconductor.org/packages/release/bioc/html/FISHalyseR.html) -Pakets von BioConductor abrufen können, vorausgesetzt, der Computer hat Zugriff auf das Internet.

1.  Suchen Sie in der Liste der **Paketarchive** die **Windows-Binärdateiversion** .

2.  Klicken Sie mit der rechten Maustaste auf den Link zum. ZIP-Datei, und wählen Sie **Ziel speichern**unter aus.

3.  Navigieren Sie zum lokalen Ordner, in dem die komprimierten Pakete gespeichert sind, und klicken Sie auf **Speichern**.

    Dieser Vorgang erstellt eine lokale Kopie des Pakets. 

4. Wenn Sie einen Download Fehler erhalten, versuchen Sie es mit einer anderen Spiegelungs Site.

5. Nach dem Herunterladen des Paket Archivs können Sie das Paket installieren oder das ZIP-Paket auf einen Server kopieren, der nicht über Internet Zugriff verfügt.

> [!TIP]
> Wenn Sie versehentlich das Paket installieren, anstatt die Binärdateien herunterzuladen, wird auch eine Kopie der heruntergeladenen ZIP-Datei auf dem Computer gespeichert. Sehen Sie sich die Statusmeldungen während der Paketinstallation an, um den Datei Speicherort zu ermitteln. Sie können diese ZIP-Datei auf den Server kopieren, der nicht über Internet Zugriff verfügt.
> 
> Wenn Sie jedoch Pakete mithilfe dieser Methode abrufen, werden die Abhängigkeiten nicht eingeschlossen. 


## <a name="side-by-side-installation-with-standalone-r-or-python-servers"></a>Parallele Installation mit eigenständigen R-oder python-Servern

R-und Python-Funktionen sind in mehreren Microsoft-Produkten enthalten, die alle auf dem gleichen Computer vorhanden sein können.

Wenn Sie SQL Server 2017 Microsoft Machine Learning Server (eigenständig) oder SQL Server 2016 R Server (eigenständig) zusätzlich zur Datenbankanalyse (SQL Server Machine Learning Services und SQL Server 2016 R Services) installiert haben, hat der Computer separate Installationen von r für jede, mit Duplikaten aller r-Tools und-Bibliotheken.

Pakete, die in der R_SERVER-Bibliothek installiert werden, werden nur von einem eigenständigen Server verwendet, und es kann nicht von einer SQL Server-Instanz (in der Datenbank) darauf zugegriffen werden. Verwenden Sie die `R_SERVICES` Bibliothek immer beim Installieren von Paketen, die Sie in-Database auf SQL Server verwenden möchten. Weitere Informationen zu Pfaden finden Sie unter [Speicherort der paketbibliothek](../package-management/default-packages.md).

## <a name="see-also"></a>Siehe auch

+ [Neue Python-Pakete installieren](../python/install-additional-python-packages-on-sql-server.md)
+ [Tutorials, Beispiele, Lösungen](../tutorials/machine-learning-services-tutorials.md)
