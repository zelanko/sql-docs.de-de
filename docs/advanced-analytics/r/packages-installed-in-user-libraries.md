---
title: Tipps zur Verwendung von R-Paketen in benutzerbibliotheken auf SQL Server installiert | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/30/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: e52a6f4a9a3830aab01e54819804785a7069c9d2
ms.sourcegitcommit: 2d93cd115f52bf3eff3069f28ea866232b4f9f9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/01/2018
ms.locfileid: "34708468"
---
# <a name="tips-for-using-r-packages-in-sql-server"></a>Tipps zur Verwendung von R-Pakete in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel enthält einen eigenen Abschnitt für Datenbankadministratoren, die mit R und erfahrenen R Entwickler, die in einer SQL Server-Instanz nicht vertraut Paketzugriff nicht vertraut sind.

## <a name="new-to-r"></a>Noch nicht mit R

Als Administrator Installieren von R beginnen Sie Pakete zum ersten Mal zu wissen, dass einige Grundlagen zur Verwaltung der R-Paket, die Ihnen helfen können.

### <a name="package-dependencies"></a>Paketabhängigkeiten

R-Pakete hängen häufig mehrere andere Pakete, von die einige möglicherweise nicht verfügbar in der Standardeinstellung R-Bibliothek, die von der Instanz verwendet. In einigen Fällen erfordert ein Paket eine andere Version von ein abhängiges Paket, das bereits installiert ist. Paketabhängigkeiten werden in einer Beschreibungsdatei in das Paket eingebettet notiert haben, aber manchmal unvollständig sind. Sie können ein Paket aufgerufen [iGraph](http://igraph.org/r/) um das Abhängigkeitsdiagramm vollständig zu formulieren.

Wenn Sie müssen zum Installieren mehrerer Pakete, oder möchten, stellen Sie sicher, dass jeder einzelne in Ihrem Unternehmen die richtigen Pakettyp und Version erhält, wir empfehlen die Verwendung der [MiniCRAN](https://mran.microsoft.com/package/miniCRAN) Paket, um die vollständige Abhängigkeitskette zu analysieren. MinicRAN erstellt ein lokales Repository, das für mehrere Benutzer oder Computer freigegeben werden kann. Weitere Informationen finden Sie unter [erstellen Sie ein lokales Paket-Repository mit MiniCRAN](create-a-local-package-repository-using-minicran.md).

### <a name="package-sources-versions-and-formats"></a>Paketquellen, Versionen und Formate

Es gibt mehrere Quellen für R-Pakete, wie [CRAN](https://cran.r-project.org/) und [Bioconductor](https://www.bioconductor.org/). Die offizielle Website für die Sprache "R" (<https://www.r-project.org/>) sind viele dieser Ressourcen aufgeführt. Microsoft bietet [MRAN](https://mran.microsoft.com/) für die Verteilung der Open-Source-R ([MRO](https://mran.microsoft.com/open)) und anderen Paketen. Viele Pakete werden in GitHub veröffentlicht, in denen Entwickler den Quellcode erhalten können.

R-Pakete, die auf mehrere Computerplattformen ausgeführt werden. Achten Sie darauf, dass die Versionen, die Sie installieren Windows-Binärdateien sind.

### <a name="know-which-library-you-are-installing-to-and-which-packages-are-already-installed"></a>Wissen, welche Bibliothek, die Sie zum Installieren und die Pakete sind bereits installiert.

Wenn Sie vor der Installation von alles zuvor die R-Umgebung auf dem Computer geändert haben, sicherstellen, dass die R-Umgebungsvariable `.libPath` nur ein Pfad verwendet.

Dieser Pfad sollte auf den Ordner R_SERVICES für die Instanz verweisen. Weitere Informationen, einschließlich Informationen zum bestimmen, welche Pakete bereits installiert sind, finden Sie unter [Standard R und Python-Paketen in SQL Server](installing-and-managing-r-packages.md).

## <a name="new-to-sql-server"></a>Erfahrung mit SQLServer

Als ein R-Entwickler Code ausführt, auf SQL Server arbeiten beschränken die Sicherheitsrichtlinien, die den Server zu schützen sind Ihre Möglichkeiten zur Steuerung der R-Umgebung.

### <a name="r-user-libraries-not-supported-on-sql-server"></a>R-Benutzer-Bibliotheken: auf SQL Server nicht unterstützt.

R-Entwickler, die neue R-Pakete installieren müssen, sind beim Installieren von Paketen werden, eine Private, Benutzerbibliothek verwenden, wenn die Standardbibliothek nicht verfügbar ist, oder wenn der Entwickler kein Administrator auf dem Computer ist. Z. B. in einer typischen R-Entwicklungsumgebung, die Benutzer würde Hinzufügen der Speicherort des Pakets der R-Umgebungsvariable `libPath`, oder verweisen Sie den vollständigen Paketpfad wie folgt:

```R
library("c:/Users/<username>/R/win-library/packagename")
```

Dies funktioniert nicht bei der Ausführung von R-Lösungen in SQL Server, da R-Pakete in einer spezifischen Bibliothek installiert werden müssen, die mit der Instanz verknüpft ist. Wenn ein Paket in der Standardbibliothek nicht verfügbar ist, erhalten Sie diesen Fehler, wenn Sie versuchen, das Paket abgerufen:

*Fehler in library(xxx): ist kein Paket namens "Paketname"*

### <a name="avoid-package-not-found-errors"></a>Vermeiden von Fehlern "Paket wurde nicht gefunden"

+ Beseitigen Sie Abhängigkeiten von benutzerbibliotheken. 

    Es ist eine fehlerhafte Entwicklung Vorgehensweise zum Installieren der erforderlichen R-Pakete in einer benutzerdefinierten-Bibliothek, da es zu Fehlern führen kann, wenn eine Lösung von einem anderen Benutzer ausgeführt wird, die keinen Zugriff auf den BibliothekenSpeicherort.

    Auch, wenn ein Paket in der Standardbibliothek installiert ist, lädt die R-Laufzeit des Pakets aus der Bibliothek standardmäßig auch wenn Sie eine andere Version in der R-Code angeben.

+ Ändern Sie den Code in einer freigegebenen Umgebung ausgeführt.

+ Vermeiden Sie die Installation von Paketen als Teil einer Lösung. Wenn Sie nicht über Berechtigungen zum Installieren der Pakete verfügen, schlägt der Code fehl. Auch wenn Sie Berechtigungen zum Installieren der Pakete haben, sollten Sie daher separat aus anderem Code durchführen, die Sie ausführen möchten.

+ Stellen Sie sicher, dass im Code keine Aufrufe von nicht installierten Paketen enthalten sind.

+ Aktualisieren Sie den Code um direkte Verweise auf die Pfade der R-Pakete oder R-Bibliotheken zu entfernen. 

+ Wissen Sie, welche Bibliothek Paket mit der Instanz verknüpft ist. Weitere Informationen finden Sie unter [Standard R und Python-Paketen in SQL Server](installing-and-managing-r-packages.md).

## <a name="see-also"></a>Siehe auch

+ [Neue R-Pakete installieren](install-additional-r-packages-on-sql-server.md)
+ [Neue Python-Pakete installieren](../python/install-additional-python-packages-on-sql-server.md)
+ [Tutorials, Beispiele, Lösungen](../tutorials/machine-learning-services-tutorials.md)