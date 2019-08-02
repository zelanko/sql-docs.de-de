---
title: Tipps zur Verwendung von R-Paketen, die in Benutzer Bibliotheken installiert sind
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 16f3ae10c7a05529c86bea5684182c7805f9f54b
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715673"
---
# <a name="tips-for-using-r-packages-in-sql-server"></a>Tipps für die Verwendung von R-Paketen in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dieser Artikel enthält separate Abschnitte für Datenbankadministratoren, die mit R und erfahrenen r-Entwicklern, die keinen unbekannten Paket Zugriff in einer SQL Server-Instanz haben, nicht vertraut sind.

## <a name="new-to-r"></a>Neu bei R

Als Administrator, der r-Pakete zum ersten Mal installiert, können Sie sich mit einigen Grundlagen zur Verwaltung von r-Paketen beim Einstieg informieren.

### <a name="package-dependencies"></a>Paketabhängigkeiten

R-Pakete sind häufig von mehreren anderen Paketen abhängig, von denen einige möglicherweise nicht in der von der-Instanz verwendeten Standard-R-Bibliothek verfügbar sind. Manchmal erfordert ein Paket eine andere Version eines abhängigen Pakets, das bereits installiert ist. Paketabhängigkeiten werden in einer Beschreibungsdatei vermerkt, die in das Paket eingebettet ist, aber manchmal unvollständig sind. Sie können ein Paket mit dem Namen [igraph](https://igraph.org/r/) verwenden, um das Abhängigkeits Diagramm vollständig zu formulieren.

Wenn Sie mehrere Pakete installieren müssen oder sicherstellen möchten, dass jeder in Ihrer Organisation den richtigen Pakettyp und die richtige Version erhält, empfiehlt es sich, das [minicran](https://mran.microsoft.com/package/miniCRAN) -Paket zum Analysieren der vollständigen Abhängigkeits Kette zu verwenden. minicran erstellt ein lokales Repository, das von mehreren Benutzern oder Computern gemeinsam genutzt werden kann. Weitere Informationen finden Sie unter [Erstellen eines lokalen paketrepositorys mit minicran](create-a-local-package-repository-using-minicran.md).

### <a name="package-sources-versions-and-formats"></a>Paketquellen, Versionen und Formate

Es gibt mehrere Quellen für R-Pakete, z. b. [cran](https://cran.r-project.org/) und [BioConductor](https://www.bioconductor.org/). Auf der offiziellen Website für die R-<https://www.r-project.org/>Sprache () sind viele dieser Ressourcen aufgeführt. Microsoft bietet [mran](https://mran.microsoft.com/) für seine Verteilung von Open Source-R ([MRO](https://mran.microsoft.com/open)) und anderen Paketen an. Viele Pakete werden auf GitHub veröffentlicht, wo Entwickler den Quellcode abrufen können.

R-Pakete werden auf mehreren Computerplattformen ausgeführt. Stellen Sie sicher, dass es sich bei den installierten Versionen um Windows-Binärdateien handelt.

### <a name="know-which-library-you-are-installing-to-and-which-packages-are-already-installed"></a>Informieren Sie sich darüber, welche Bibliothek Sie installieren und welche Pakete bereits installiert sind.

Wenn Sie zuvor die r-Umgebung auf dem Computer geändert haben, müssen Sie vor dem Installieren von nichts sicherstellen `.libPath` , dass die r-Umgebungsvariable nur einen Pfad verwendet.

Dieser Pfad sollte auf den Ordner R_SERVICES für die-Instanz verweisen. Weitere Informationen, einschließlich Informationen zum Ermitteln der bereits installierten Pakete, finden Sie [unter Standard-R-und Python-Pakete in SQL Server](../package-management/default-packages.md).

## <a name="new-to-sql-server"></a>Neu bei SQL Server

Wenn Sie ein R-Entwickler an Code arbeiten, der auf SQL Server ausgeführt wird, schränken die Sicherheitsrichtlinien, die den Server schützen, die Steuerung der R-Umgebung ein.

### <a name="r-user-libraries-not-supported-on-sql-server"></a>R-Benutzer Bibliotheken: wird auf SQL Server nicht unterstützt.

R-Entwickler, die neue R-Pakete installieren müssen, sind daran gewöhnt, Pakete zu installieren, wobei eine private Benutzer Bibliothek verwendet wird, wenn die Standardbibliothek nicht verfügbar ist oder wenn der Entwickler kein Administrator auf dem Computer ist. Beispielsweise würde der Benutzer in einer typischen r-Entwicklungsumgebung den Speicherort des Pakets zur r-Umgebungsvariablen `libPath`hinzufügen oder wie folgt auf den vollständigen Paketpfad verweisen:

```R
library("c:/Users/<username>/R/win-library/packagename")
```

Dies funktioniert nicht, wenn r-Lösungen in SQL Server ausgeführt werden, da r-Pakete in einer bestimmten Standardbibliothek installiert werden müssen, die der Instanz zugeordnet ist. Wenn ein Paket in der Standardbibliothek nicht verfügbar ist, erhalten Sie diesen Fehler, wenn Sie versuchen, das Paket aufzurufen:

*Fehler in Bibliothek (xxx): Es ist kein Paket mit dem Namen "Paketname" vorhanden.*

### <a name="avoid-package-not-found-errors"></a>Fehler "Paket nicht gefunden" vermeiden

+ Entfernen Sie Abhängigkeiten von Benutzer Bibliotheken. 

    Es ist eine schlechte Entwicklungs Übung, erforderliche R-Pakete in einer benutzerdefinierten Benutzer Bibliothek zu installieren, da dies zu Fehlern führen kann, wenn eine Projekt Mappe von einem anderen Benutzer ausgeführt wird, der keinen Zugriff auf den Speicherort der Bibliothek hat.

    Wenn ein Paket in der Standardbibliothek installiert ist, lädt die r-Laufzeit außerdem das Paket aus der Standardbibliothek, auch wenn Sie eine andere Version im R-Code angeben.

+ Ändern Sie den Code, um ihn in einer freigegebenen Umgebung auszuführen.

+ Vermeiden Sie das Installieren von Paketen als Teil einer Lösung. Wenn Sie nicht über die Berechtigung zum Installieren von Paketen verfügen, schlägt der Code fehl. Auch wenn Sie über Berechtigungen zum Installieren von Paketen verfügen, sollten Sie dies separat von anderem Code tun, den Sie ausführen möchten.

+ Stellen Sie sicher, dass im Code keine Aufrufe von nicht installierten Paketen enthalten sind.

+ Aktualisieren Sie Ihren Code, um direkte Verweise auf die Pfade von r-Paketen oder r-Bibliotheken zu entfernen. 

+ Wissen Sie, welche paketbibliothek der-Instanz zugeordnet ist. Weitere Informationen finden Sie unter [Standard-R-und Python-Pakete in SQL Server](../package-management/default-packages.md).

## <a name="see-also"></a>Siehe auch

+ [Neue R-Pakete installieren](install-additional-r-packages-on-sql-server.md)
+ [Neue Python-Pakete installieren](../python/install-additional-python-packages-on-sql-server.md)
+ [Tutorials, Beispiele, Lösungen](../tutorials/machine-learning-services-tutorials.md)