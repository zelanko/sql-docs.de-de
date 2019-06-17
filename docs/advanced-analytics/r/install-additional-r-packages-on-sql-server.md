---
title: 'Installieren Sie neuer R-Sprache-Pakete: SQL Server Machine Learning Services'
description: Fügen Sie neue R-Pakete auf SQL Server 2016 R Services oder SQL Server 2017-Machine Learning Services (Datenbankintern)
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: fb8e5512a9b623a3e97d80289b928d66314f9d72
ms.sourcegitcommit: a91c3f4fe2587d474cd4d470bda93239ba2693bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/14/2019
ms.locfileid: "67140589"
---
# <a name="install-new-r-packages-on-sql-server"></a>Installieren Sie neuer R-Pakete unter SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel beschreibt, wie Sie neue R-Pakete mit einer Instanz von SQL Server installieren, Machine Learning aktiviert ist. Es gibt mehrere Methoden zum Installieren neuer R-Pakete, je nachdem, welche Version von SQL Server haben und gibt an, ob der Server über eine Internetverbindung verfügt. Die folgenden Methoden zum neuen Paketinstallation sind möglich.

| Vorgehensweise                           | Berechtigungen               | Remote/lokale |
|------------------------------------|---------------------------|--------------|
| [Verwenden von herkömmlichen R-Paket-Manager](use-r-package-managers-on-sql-server.md)  | Admin | Lokal |
| [Verwenden von RevoScaleR](use-revoscaler-to-manage-r-packages.md) |  Danach Datenbankrollen Admin-aktiviert | both|
| [Verwenden von T-SQL (CREATE EXTERNAL LIBRARY)](install-r-packages-tsql.md) | Danach Datenbankrollen Admin-aktiviert | both 

## <a name="who-installs-permissions"></a>Wer (Berechtigungen) installiert

Die R-Paket-Bibliothek befindet sich physisch im Ordner "Programme" Ihrer SQL Server-Instanz, in einem sicheren Ordner mit eingeschränktem Zugriff. Das Schreiben in diesen Speicherort sind Administratorberechtigungen erforderlich.

Nicht-Administratoren können Pakete installieren. dazu sind jedoch zusätzliche Konfiguration und die Funktion in der ersten Installationen nicht verfügbar. Es gibt zwei Ansätze für die Paket-Installationen ohne Administratorrechte: RevoScaleR, die mit Version 9.0.1 und höher, oder mit CREATE EXTERNAL LIBRARY (nur SQL Server 2017). In SQL Server 2017 **Dbo_owner** oder einem anderen Benutzer mit der CREATE EXTERNAL LIBRARY-Berechtigung kann R-Pakete installieren, auf die aktuelle Datenbank.

R-Entwickler sind daran gewöhnt, zum Erstellen von benutzerbibliotheken für die Pakete, die sie benötigen, wenn-einstellungspakete Bibliotheken Hardwarefeatures sind. Diese Vorgehensweise ist problematisch für R-Code in einer Instanz von SQL Server-Datenbank-Engine ausgeführt. SQL Server können keine externen Bibliotheken Laden von Paketen aus, selbst wenn diese Bibliothek, auf dem gleichen Computer ist. Nur Pakete aus der Instanz-Bibliothek können in R-Code, die unter SQL Server verwendet werden.

Dateisystemzugriff ist in der Regel beschränkt, auf dem Server und auch wenn Sie über Administratorrechte und Zugriff in einem Dokument Benutzerordner auf dem Server verfügen, nicht die externen Skript-Runtime, die in SQL Server ausgeführt wird alle Pakete, die außerhalb der Standardinstanz installiert verfügbar -Bibliothek. 

## <a name="considerations-for-package-installation"></a>Überlegungen zur Paketinstallation

Installieren neuer Pakete, berücksichtigen Sie, ob die neuen Funktionen von einem bestimmten Paket in einer SQL Server-Umgebung geeignet sind. In einer SQL Server-Umgebung mit verstärkter Sicherheit empfiehlt es sich um Folgendes zu vermeiden:

+ Pakete, die Zugriff auf das Netzwerk erfordern.
+ Pakete, die mit erhöhten Rechten Dateisystemzugriff erfordern
+ Paket wird für die Webentwicklung oder andere Aufgaben, die durch die Ausführung in SQL Server profitieren nicht verwendet.

## <a name="offline-installation-no-internet-access"></a>Offline-Installation (ohne Internetzugriff)

Im Allgemeinen blockieren Servern, die für die Produktion hosten internetverbindungen. Installieren neuer R oder Python-Pakete in solchen Umgebungen erfordert, dass Sie Pakete und Abhängigkeiten im Voraus vorbereiten und kopieren Sie die Dateien in einen Ordner auf dem Server für die Offlineinstallation.

Identifizieren alle Abhängigkeiten kompliziert. Für R, empfehlen wir die Verwendung von [MiniCRAN zum Erstellen eines lokalen Repositorys](create-a-local-package-repository-using-minicran.md) übertragen und dann das vollständig definierte Repository an eine isolierte Instanz von SQL Server.

Alternativ können Sie diese Schritte manuell ausführen:

1. Identifizieren Sie alle paketabhängigkeiten an. 
2. Überprüfen Sie, ob alle erforderlichen Pakete bereits auf dem Server installiert sind. Wenn das Paket installiert ist, stellen Sie sicher, dass die Version korrekt ist.
3. Laden Sie das Paket und alle Abhängigkeiten in einem separaten Computer herunter.
4. Verschieben Sie die Dateien in einen Ordner zugegriffen werden kann, durch den Server.
5. Führen Sie einen unterstützten Installation-Befehl oder DDL-Anweisung, um das Paket in die Instanz-Bibliothek zu installieren.

### <a name="download-the-package-as-a-zipped-file"></a>Das Paket als ZIP-Datei herunterladen

Für die Installation auf einem Server ohne Internetzugriff müssen Sie eine Kopie des Pakets im Format einer ZIP-Datei für offline-Installation herunterladen. **Entzippen Sie das Paket nicht.**

Z. B. das folgende Verfahren beschreibt jetzt, um die richtige Version von der [FISHalyseR](https://bioconductor.org/packages/release/bioc/html/FISHalyseR.html) Paket von Bioconductor, sofern der Computer über Internetzugriff verfügt.

1.  Suchen Sie in der Liste der **Paketarchive** die **Windows-Binärdateiversion** .

2.  Mit der rechten Maustaste in des Links, um die. ZIP-Datei, und wählen **Ziel speichern unter**.

3.  Navigieren Sie zu den lokalen Ordner, in dem komprimierten Pakete gespeichert werden, und klicken Sie auf **speichern**.

    Dieser Vorgang erstellt eine lokale Kopie des Pakets. 

4. Wenn Sie einen Downloadfehler erhalten, versuchen Sie eine andere gespiegelte Site aus.

5. Nach dem das Archiv Paket heruntergeladen wurde, können Sie das Paket installieren oder kopieren das ZIP-Paket auf einen Server, der keinen Zugriff auf das Internet.

> [!TIP]
> Wenn Sie versehentlich das Paket nicht die Binärdateien heruntergeladen installieren, wird eine Kopie der heruntergeladenen ZIP-Datei auch auf Ihrem Computer gespeichert. Sehen Sie die statusmeldungen an, wie das Paket installiert wird, um den Dateispeicherort zu ermitteln. Sie können diese ZIP-Datei an den Server kopieren, die keinen Zugriff auf das Internet.
> 
> Wenn Sie Pakete, die mit dieser Methode zu erhalten, sind die Abhängigkeiten nicht enthalten. 


## <a name="side-by-side-installation-with-standalone-r-or-python-servers"></a>Seite-an-Seite-Installation mit Standalone R oder Python-Server

R und Python-Funktionen sind in verschiedenen Microsoft-Produkten, enthalten, die alle auf dem gleichen Computer gleichzeitig vorhanden.

Wenn Sie SQL Server 2017 Microsoft Machine Learning Server (eigenständig) oder SQL Server 2016 R Server (eigenständig) zusätzlich zum in-Database-Analyse (SQL Server 2017-Machine Learning Services und SQL Server 2016 R Services) installiert haben, sind für Ihren Computer separate Installationen von R für jeden, ohne Duplikate, der alle R-Tools und Bibliotheken.

In der Bibliothek R_SERVER installierte Pakete werden nur von einem eigenständigen Server verwendet und können nicht von einer Instanz von SQL Server (Datenbankintern) zugegriffen werden. Verwenden Sie immer die `R_SERVICES` Bibliothek beim Installieren von Paketen, die Sie in der Datenbank auf SQL Server verwenden möchten. Weitere Informationen zu Pfaden finden Sie unter [Bibliothek Paketspeicherort](../package-management/default-packages.md).

## <a name="see-also"></a>Siehe auch

+ [Neue Python-Pakete installieren](../python/install-additional-python-packages-on-sql-server.md)
+ [Tutorials, Beispiele, Lösungen](../tutorials/machine-learning-services-tutorials.md)
