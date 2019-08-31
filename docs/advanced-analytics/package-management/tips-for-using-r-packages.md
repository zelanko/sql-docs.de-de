---
title: Tipps für die Verwendung von R-Paketen
description: Hier finden Sie hilfreiche Tipps zur Verwendung von r-Paketen in SQL Server für Benutzer, die mit r oder SQL Server noch nicht vertraut sind.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/06/2019
ms.topic: conceptual
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 5e283ab478a6d65243e9962fd5c26f5f91d87c15
ms.sourcegitcommit: 00350f6ffb73c2c0d99beeded61c5b9baa63d171
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2019
ms.locfileid: "70196343"
---
# <a name="tips-for-using-r-packages"></a>Tipps für die Verwendung von R-Paketen

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dieser Artikel bietet hilfreiche Tipps zur Verwendung von R-Paketen in SQL Server. Diese Tipps sind für DBAs gedacht, die mit r nicht vertraut sind, und erfahrene R-Entwickler, die mit dem Paket Zugriff in einer SQL Server-Instanz nicht vertraut sind.

## <a name="if-youre-new-to-r"></a>Wenn Sie noch nicht mit R vertraut sind

Als Administrator, der r-Pakete zum ersten Mal installiert, können Sie sich mit einigen Grundlagen zur Verwaltung von r-Paketen beim Einstieg informieren.

### <a name="package-dependencies"></a>Paketabhängigkeiten

R-Pakete sind häufig von mehreren anderen Paketen abhängig, von denen einige möglicherweise nicht in der von der-Instanz verwendeten Standard-R-Bibliothek verfügbar sind. Manchmal erfordert ein Paket eine andere Version eines abhängigen Pakets als das, was bereits installiert ist. Paketabhängigkeiten werden in einer Beschreibungsdatei vermerkt, die in das Paket eingebettet ist, aber manchmal unvollständig sind. Sie können ein Paket mit dem Namen [igraph](https://igraph.org/r/) verwenden, um das Abhängigkeits Diagramm vollständig zu formulieren.

Wenn Sie mehrere Pakete installieren müssen oder sicherstellen möchten, dass jeder in Ihrer Organisation den richtigen Pakettyp und die richtige Version erhält, empfiehlt es sich, das [minicran](https://mran.microsoft.com/package/miniCRAN) -Paket zum Analysieren der vollständigen Abhängigkeits Kette zu verwenden. minicran erstellt ein lokales Repository, das von mehreren Benutzern oder Computern gemeinsam genutzt werden kann. Weitere Informationen finden Sie unter [Erstellen eines lokalen paketrepositorys mit minicran](create-a-local-package-repository-using-minicran.md).

### <a name="package-sources-versions-and-formats"></a>Paketquellen, Versionen und Formate

Es gibt mehrere Quellen für R-Pakete, z. b. [cran](https://cran.r-project.org/) und [BioConductor](https://www.bioconductor.org/). Auf der offiziellen Website für die R-<https://www.r-project.org/>Sprache () sind viele dieser Ressourcen aufgeführt. Microsoft bietet [mran](https://mran.microsoft.com/) für seine Verteilung von Open Source-R ([MRO](https://mran.microsoft.com/open)) und anderen Paketen an. Viele Pakete werden auf GitHub veröffentlicht, wo Entwickler den Quellcode abrufen können.

::: moniker range=">=sql-server-2016||=sqlallproducts-allversions"
R-Pakete werden auf mehreren Computerplattformen ausgeführt. Stellen Sie sicher, dass es sich bei den installierten Versionen um Windows-Binärdateien handelt.
::: moniker-end

::: moniker range=">=sql-server-linux-ver15||=sqlallproducts-allversions"
R-Pakete werden auf mehreren Computerplattformen ausgeführt. Stellen Sie sicher, dass es sich bei den installierten Versionen um Linux-Binärdateien handelt.
::: moniker-end

### <a name="know-which-library-youre-installing-to-and-which-packages-are-already-installed"></a>Die Bibliothek, in der Sie installieren, und welche Pakete bereits installiert sind

Wenn Sie zuvor die r-Umgebung auf dem Computer geändert haben, müssen Sie vor dem Installieren von etwas sicher `.libPath` stellen, dass die r-Umgebungsvariable nur einen Pfad verwendet.

Dieser Pfad sollte auf den Ordner R_SERVICES für die-Instanz verweisen. Weitere Informationen, einschließlich Informationen zum Ermitteln der bereits installierten Pakete, finden Sie unter [Get R Package Information](../package-management/r-package-information.md).

## <a name="if-youre-new-to-sql-server"></a>Wenn Sie noch nicht mit SQL Server vertraut sind

Wenn Sie ein R-Entwickler an Code arbeiten, der auf SQL Server ausgeführt wird, schränken die Sicherheitsrichtlinien, die den Server schützen, die Steuerung der R-Umgebung ein. In den folgenden Tipps werden typische Situationen beschrieben und Vorschläge zum Arbeiten in dieser Umgebung bereitgestellt.

### <a name="r-user-libraries-not-supported-on-sql-server"></a>R-Benutzer Bibliotheken: wird auf SQL Server nicht unterstützt.

R-Entwickler, die neue R-Pakete installieren müssen, sind daran gewöhnt, Pakete zu installieren, wobei eine private Benutzer Bibliothek verwendet wird, wenn die Standardbibliothek nicht verfügbar ist oder wenn der Entwickler kein Administrator auf dem Computer ist. Beispielsweise würde der Benutzer in einer typischen r-Entwicklungsumgebung den Speicherort des Pakets zur r-Umgebungsvariablen `libPath`hinzufügen oder wie folgt auf den vollständigen Paketpfad verweisen:

```R
library("c:/Users/<username>/R/win-library/packagename")
```

Dies funktioniert nicht, wenn r-Lösungen in SQL Server ausgeführt werden, da r-Pakete in einer bestimmten Standardbibliothek installiert werden müssen, die der Instanz zugeordnet ist. Wenn ein Paket in der Standardbibliothek nicht verfügbar ist, erhalten Sie diesen Fehler, wenn Sie versuchen, das Paket aufzurufen:

*Fehler in Bibliothek (xxx): Es ist kein Paket mit dem Namen "Paketname" vorhanden.*

Informationen zum Installieren von r-Paketen in SQL Server finden Sie unter [Installieren neuer r-Pakete auf SQL Server Machine Learning Services oder SQL Server R Services](install-additional-r-packages-on-sql-server.md).

### <a name="how-to-avoid-package-not-found-errors"></a>Vermeiden von Fehlern "Paket nicht gefunden"

Mithilfe der folgenden Richtlinien können Sie die Fehler "Paket nicht gefunden" vermeiden.

+ Entfernen Sie Abhängigkeiten von Benutzer Bibliotheken.

    Es ist eine schlechte Entwicklungs Übung, erforderliche R-Pakete in einer benutzerdefinierten Benutzer Bibliothek zu installieren. Dies kann zu Fehlern führen, wenn eine Projekt Mappe von einem anderen Benutzer ausgeführt wird, der keinen Zugriff auf den Speicherort der Bibliothek hat.

    Wenn ein Paket in der Standardbibliothek installiert ist, lädt die r-Laufzeit außerdem das Paket aus der Standardbibliothek, auch wenn Sie eine andere Version im R-Code angeben.

+ Stellen Sie sicher, dass Ihr Code in einer freigegebenen Umgebung ausgeführt werden kann.

+ Vermeiden Sie das Installieren von Paketen als Teil einer Lösung. Wenn Sie nicht über die Berechtigung zum Installieren von Paketen verfügen, schlägt der Code fehl. Auch wenn Sie über Berechtigungen zum Installieren von Paketen verfügen, sollten Sie dies separat von anderem Code tun, den Sie ausführen möchten.

+ Stellen Sie sicher, dass im Code keine Aufrufe von nicht installierten Paketen enthalten sind.

+ Aktualisieren Sie Ihren Code, um direkte Verweise auf die Pfade von r-Paketen oder r-Bibliotheken zu entfernen.

+ Wissen Sie, welche paketbibliothek der-Instanz zugeordnet ist. Weitere Informationen finden Sie unter [Get R Package Information](../package-management/r-package-information.md).

## <a name="see-also"></a>Siehe auch

+ [Neue R-Pakete installieren](install-additional-r-packages-on-sql-server.md)
+ [Neue Python-Pakete installieren](../python/install-additional-python-packages-on-sql-server.md)
+ [Tutorials, Beispiele, Lösungen](../tutorials/machine-learning-services-tutorials.md)