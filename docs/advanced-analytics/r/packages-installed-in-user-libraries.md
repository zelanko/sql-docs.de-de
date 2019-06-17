---
title: Tipps zur Verwendung von R-Pakete in benutzerbibliotheken – SQL Server Machine Learning Services installiert
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: bb354e1a0a7f7f22a39b690fdd0c0f4ae7778b8f
ms.sourcegitcommit: a91c3f4fe2587d474cd4d470bda93239ba2693bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/14/2019
ms.locfileid: "67140505"
---
# <a name="tips-for-using-r-packages-in-sql-server"></a>Tipps zur Verwendung von R-Pakete in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel enthält einen eigenen Abschnitt für DBAs, die mit R und erfahrenen R-Entwickler, die unbekannte Paketzugriff in einer SQL Server-Instanz sind nicht vertraut sind.

## <a name="new-to-r"></a>Keine Erfahrung mit R

Als Administrator beim Installieren von R beginnen Sie Pakete zum ersten Mal wissen, dass einige Grundlagen zur Verwaltung von R-Paketen, die Ihnen helfen können.

### <a name="package-dependencies"></a>Paketabhängigkeiten

R-Pakete hängen häufig mehrere andere Pakete, von die einige möglicherweise nicht verfügbar in der R-Standardbibliothek, die von der Instanz verwendet. In einigen Fällen erfordert ein Paket eine andere Version ein abhängiges Paket, das bereits installiert ist. Paketabhängigkeiten werden in einer Beschreibungsdatei, die im Paket eingebettete erwähnt, aber manchmal nicht vollständig sind. Sie können ein Paket namens [iGraph](https://igraph.org/r/) auf das Abhängigkeitsdiagramm vollständig zu formulieren.

Wenn Sie möchten mehrere Pakete zu installieren, oder möchten, stellen Sie sicher, dass jeder in Ihrer Organisation, den richtigen Pakettyp und die Version erhält, wir empfehlen die Verwendung der [MiniCRAN](https://mran.microsoft.com/package/miniCRAN) Paket, um die vollständige Abhängigkeitskette zu analysieren. MinicRAN erstellt ein lokales Repository, das von mehreren Benutzern oder Computern gemeinsam genutzt werden kann. Weitere Informationen finden Sie unter [erstellen ein lokalen paketrepositorys mit MiniCRAN](create-a-local-package-repository-using-minicran.md).

### <a name="package-sources-versions-and-formats"></a>Paketquellen, Versionen und Formate

Es gibt mehrere Quellen für R-Pakete, z.B. [CRAN](https://cran.r-project.org/) und [Bioconductor](https://www.bioconductor.org/). Die offizielle Website für die R-Sprache (<https://www.r-project.org/>) sind viele dieser Ressourcen aufgeführt. Microsoft bietet [MRAN](https://mran.microsoft.com/) für die Verteilung der Open-Source-Sprache R ([MRO](https://mran.microsoft.com/open)) und andere Pakete. Viele Pakete werden in GitHub veröffentlicht, in denen sich Entwickler auf den Quellcode erhalten können.

R-Pakete, die auf mehreren computing-Plattformen ausgeführt werden. Achten Sie darauf, dass die Versionen, die Sie installieren Windows-Binärdateien befinden.

### <a name="know-which-library-you-are-installing-to-and-which-packages-are-already-installed"></a>Wissen, welcher Bibliothek, die Sie installieren, und welche Pakete bereits installiert sind.

Wenn Sie vor der Installation alle zuvor auf dem Computer, die R-Umgebung geändert haben, stellen sicher, dass die R-Umgebungsvariable `.libPath` nur einen Pfad verwendet.

Dieser Pfad sollte auf den Ordner R_SERVICES für die Instanz verweisen. Weitere Informationen einschließlich Informationen, um zu bestimmen, welche Pakete bereits installiert sind, finden Sie unter [standardmäßige R und Python-Paketen in SQL Server](../package-management/default-packages.md).

## <a name="new-to-sql-server"></a>Neues in SQLServer

Als ein R-Entwickler, die zur codeausführung von in SQL Server arbeiten einschränken, die Sicherheitsrichtlinien, die Schutz des Servers die Möglichkeit zum Steuern der R-Umgebung.

### <a name="r-user-libraries-not-supported-on-sql-server"></a>R-Benutzer-Bibliotheken: in SQL Server nicht unterstützt.

R-Entwickler, die zum Installieren neuer R-Pakete müssen sind daran gewöhnt, für die Installation von Paketen werden eine Private, Benutzerbibliothek verwenden, wenn die Standardbibliothek nicht verfügbar ist oder wenn der Entwickler kein Administrator auf dem Computer ist. Z. B. in einer typischen R-Entwicklungsumgebung, die Benutzer würden hinzufügen den Speicherort des Pakets der R-Umgebungsvariable `libPath`, oder verweisen Sie auf den vollständigen Paketpfad wie folgt:

```R
library("c:/Users/<username>/R/win-library/packagename")
```

Dies funktioniert nicht bei der Ausführung von R-Lösungen in SQL Server, da R-Pakete auf eine bestimmte Standard-Bibliothek installiert werden müssen, die der Instanz zugeordnet ist. Wenn ein Paket in der Standardbibliothek nicht verfügbar ist, erhalten Sie diesen Fehler, wenn Sie versuchen, das Paket abgerufen:

*Fehler in library(xxx): ist kein Paket namens "Paket-Name"*

### <a name="avoid-package-not-found-errors"></a>"Paket wurde nicht gefunden"-Fehler zu vermeiden

+ Beseitigen Sie Abhängigkeiten von benutzerbibliotheken. 

    Es ist eine fehlerhafte Entwicklung-Methode, die erforderlichen R-Pakete in einer benutzerdefinierten Bibliothek zu installieren, da es zu Fehlern führen kann, wenn eine Lösung von einem anderen Benutzer ausgeführt wird, die keinen Zugriff auf den Bibliotheksspeicherort.

    Auch wenn ein Paket in der Standardbibliothek installiert ist, lädt die R-Laufzeit das Paket aus der Standardbibliothek, auch wenn Sie eine andere Version im R-Code angeben.

+ Ändern Sie Ihren Code in einer freigegebenen Umgebung ausgeführt.

+ Vermeiden Sie die Installation von Paketen als Teil einer Lösung. Wenn Sie nicht über die Berechtigungen zum Installieren von Paketen verfügen, wird der Code nicht. Auch wenn Sie Berechtigungen zum Installieren von Paketen haben, sollten Sie also getrennt von anderem Code tun, die Sie ausführen möchten.

+ Stellen Sie sicher, dass im Code keine Aufrufe von nicht installierten Paketen enthalten sind.

+ Aktualisieren Sie Ihren Code, um direkte Verweise auf die Pfade der R-Pakete oder R-Bibliotheken zu entfernen. 

+ Wissen Sie, welche paketbibliothek, die der Instanz zugeordnet ist. Weitere Informationen finden Sie unter [standardmäßige R und Python-Paketen in SQL Server](../package-management/default-packages.md).

## <a name="see-also"></a>Siehe auch

+ [Neue R-Pakete installieren](install-additional-r-packages-on-sql-server.md)
+ [Neue Python-Pakete installieren](../python/install-additional-python-packages-on-sql-server.md)
+ [Tutorials, Beispiele, Lösungen](../tutorials/machine-learning-services-tutorials.md)