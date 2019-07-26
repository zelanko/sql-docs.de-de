---
title: Leistungsoptimierung für SQL Server R Services
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 9d6dbc55281a725dea0373f2a4d61293b2ddb9c0
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469932"
---
# <a name="performance-tuning-for-r-in-sql-server"></a>Leistungsoptimierung für R in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dieser Artikel ist der erste in einer Reihe von vier Artikeln, in denen die Leistungsoptimierung für R Services basierend auf zwei Fallstudien beschrieben wird:

- Leistungstests, die vom Produkt Entwicklungsteam durchgeführt werden, um das Leistungsprofil von R-Lösungen zu validieren

- Leistungsoptimierung durch das Microsoft Data Science-Team für ein bestimmtes Machine Learning-Szenario, das häufig von Kunden angefordert wird.

Das Ziel dieser Reihe besteht darin, Anleitungen zu den Typen von Leistungs Optimierungstechniken bereitzustellen, die für die Ausführung von R-Aufträgen in SQL Server am nützlichsten sind.

+ Dieses (erste) Thema bietet einen Überblick über die Architektur und einige häufige Probleme bei der Optimierung von Data Science Tasks.
+ Im zweiten Artikel werden bestimmte Hardware-und SQL Server Optimierungen behandelt.
+ Der dritte Artikel behandelt Optimierungen in R-Code und Ressourcen für die Operationalisierung.
+ Im vierten Artikel werden die Testmethoden ausführlich beschrieben und Ergebnisse und Schlussfolgerungen berichtet.

**Gilt für:** SQL Server 2016 R Services, SQL Server 2017 Machine Learning Services

## <a name="performance-goals-and-targeted-scenarios"></a>Leistungsziele und gezielte Szenarien

Die r Services-Funktion wurde in SQL Server 2016 eingeführt, um die Ausführung von r-Skripts durch SQL Server zu unterstützen. Wenn Sie dieses Feature verwenden, wird die R-Laufzeit in einem separaten Prozess von der Datenbank-Engine betrieben, aber die Daten werden mithilfe von Server Ressourcen und-Diensten, die mit SQL Server interagieren, wie z. b. dem vertrauenswürdigen Launchpad, sicher mit der Datenbank-Engine ausgetauscht.

In SQL Server 2017 wurde die Unterstützung für die Ausführung von python-Skripts mit der gleichen Architektur angekündigt, wobei in Zukunft zusätzliche Sprache befolgt werden muss.

Wenn die Anzahl unterstützter Versionen und Sprachen zunimmt, ist es wichtig, dass der Datenbankadministrator und der Daten Bank Architekt das Potenzial von Ressourcenkonflikten aufgrund von Machine Learning-Aufträgen erkennen und den Server für die Unterstützung von konfigurieren können. die neuen Arbeits Auslastungen. Obwohl Analysen in der Nähe der Daten bleiben, werden unsichere Daten Verschiebungen vermieden. Außerdem werden analytische Workloads von dem Laptop des Datenanalysten und zurück auf den Server verschoben, auf dem die Daten gehostet werden.

Die Leistungsoptimierung für Machine Learning ist offensichtlich kein eindimensionales Angebot. Die folgenden allgemeinen Aufgaben haben möglicherweise sehr unterschiedliche Leistungsprofile:

- Schulungs Aufgaben: Erstellen und Trainieren eines Regressionsmodells im Vergleich zum Trainieren eines neuronalen Netzwerks
- Featureentwicklung mithilfe von R und featureextraktion mit T-SQL
- Bewertung von einzelnen Zeilen oder kleinen Batches im Vergleich zur Massen Bewertung mithilfe von Tabellen Eingaben
- Ausführen der Bewertung in R und Bereitstellen von Modellen in der Produktion auf SQL Server in gespeicherten Prozeduren
- Ändern von R-Code zum Minimieren der Datenübertragung oder entfernen kostspieliger Daten Transformationen
- Aktivieren von automatischem testen und erneuten trainieren von Modellen

Da die Auswahl der Optimierungstechniken davon abhängt, welche Aufgabe für Ihre Anwendung oder Ihren Anwendungsfall entscheidend ist, werden die Fallstudien sowohl allgemeine Tipps zur Leistung als auch eine Anleitung zur Optimierung der Batch Bewertung behandelt.

+ **Individuelle Optimierungs Optionen in SQL Server**

    In der ersten Leistungs Fallstudie wurden mehrere Tests in einem einzelnen Dataset mit einem einzigen Modelltyp ausgeführt. Der rxlinmod-Algorithmus in revoscaler wurde verwendet, um ein Modell zu erstellen und Ergebnisse daraus zu erstellen, aber der Code und die zugrunde liegenden Datentabellen wurden systematisch geändert, um die Auswirkungen der einzelnen Änderungen zu testen.

    Beispielsweise wurde in einem Testlauf der R-Code so geändert, dass ein Vergleich zwischen der Featureentwicklung mit einer Transformations Funktion und dem vorab Berechnen der Features und dem anschließenden Laden von Features aus einer Tabelle vorgenommen werden kann. Bei einem anderen Testlauf wurde die Modell Trainingsleistung zwischen der Verwendung einer indizierten Standardtabelle im Vergleich zu Daten in einer Tabelle mit verschiedenen Komprimierungs Typen oder neuen Index Typen verglichen.

+ **Optimierung für ein bestimmtes Bewertungs Szenario mit hohem Volumen**

    Die Machine Learning-Aufgabe in der zweiten Fallstudie umfasst die Verarbeitung von vielen Fortsetzungen, die für mehrere Positionen übermittelt wurden, und die Suche nach dem besten Kandidaten für die einzelnen Auftragspositionen. Das Machine Learning-Modell selbst ist als binäres Klassifizierungs Problem formuliert: Es führt eine Fortsetzung und eine Auftrags Beschreibung als Eingabe aus und generiert die Wahrscheinlichkeit für jedes Resume-Job-Paar. Da das Ziel darin besteht, die beste Übereinstimmung zu finden, wird ein benutzerdefinierter Wahrscheinlichkeits Schwellenwert zum weiteren Filtern und Abrufen der passenden Übereinstimmungen verwendet.

    Für diese Lösung war das Hauptziel, bei der Bewertung eine geringe Latenz zu erzielen. Diese Aufgabe ist aber auch während des Bewertungsprozesses Rechen intensiv, da jeder neue Auftrag innerhalb eines angemessenen Zeitraums mit Millionen von Fort Läufen abgeglichen werden muss. Außerdem erzeugt der featureentwicklungsprozess mehr als 2000 Features pro Fortsetzung oder Auftrag und stellt einen erheblichen Leistungsengpass dar.

Es wird empfohlen, dass Sie alle Ergebnisse aus der ersten Fallstudie überprüfen, um zu ermitteln, welche Techniken auf Ihre Lösung anwendbar sind, und Ihre potenziellen Auswirkungen zu wiegen.

Überprüfen Sie dann die Ergebnisse der Fallstudie zur Bewertungs Optimierung, um zu sehen, wie der Autor verschiedene Techniken angewendet und den Server für die Unterstützung einer bestimmten Arbeitsauslastung optimiert hat.

## <a name="performance-optimization-process"></a>Leistungs Optimierungsprozess

Für die Konfiguration und Optimierung der Leistung muss eine solide Basis erstellt werden, auf der Optimierungen für bestimmte Arbeits Auslastungen erstellt werden:

- Wählen Sie einen geeigneten Server zum Hosten von Analytics aus. Normalerweise wird ein sekundäres Berichterstattungs-, Data Warehouse-oder anderer Server, der bereits für andere Berichte oder Analysen verwendet wird, bevorzugt. In einer Hybridlösung für die Transaktions analytische Verarbeitung (HTAP) können jedoch operative Daten als Eingabe für R für die schnelle Bewertung verwendet werden.

- Konfigurieren Sie die SQL Server Instanz, um Datenbank-Engine-Vorgänge und die Ausführung von R-oder python-Skripts auf angemessenen Ebenen auszugleichen Dies kann das ändern SQL Server Standardwerte für die Arbeitsspeicher-und CPU-Auslastung, die NUMA-und Prozessor Affinitäts Einstellungen und die Erstellung von Ressourcengruppen einschließen.

- Optimieren Sie den Server Computer, um die effiziente Verwendung externer Skripts zu unterstützen. Dies kann das Erhöhen der Anzahl von Konten, die für die Ausführung externer Skripts verwendet werden, das Aktivieren der Paketverwaltung und das Zuweisen von Benutzern zu verwandten Sicherheitsrollen umfassen.

- Anwenden spezieller Optimierungen für die Datenspeicherung und-Übertragung in SQL Server, einschließlich der Indizierungs-und Statistik Strategien, des Abfrage Entwurfs und der Abfrageoptimierung sowie des Entwurfs von Tabellen, die für Maschinelles Lernen verwendet werden. Sie können auch Datenquellen und Datentransport Methoden analysieren oder ETL-Prozesse ändern, um die featureextraktion zu optimieren.

- Optimieren Sie das analytische Modell, um Ineffizienzen zu vermeiden. Der Umfang der Optimierungen, die möglich sind, hängt von der Komplexität des R-Codes und den von Ihnen verwendeten Paketen und Daten ab. Zu den Hauptaufgaben zählen das eliminieren kostspieliger Daten Transformationen oder das Auslagern von Datenvorbereitungs-oder featureentwicklungsaufgaben von R oder python zu ETL-Prozessen oder Sie können auch Skripts umgestalten, Inline-Paketinstallationen entfernen, R-Code in separate Verfahren zum trainieren, bewerten und auswerten aufteilen oder Code so vereinfachen, dass er effizienter als gespeicherte Prozedur funktioniert.

## <a name="articles-in-this-series"></a>Artikel in dieser Reihe

+ [Leistungsoptimierung für R in SQL Server-Hardware](../r/sql-server-configuration-r-services.md)

    Enthält Anleitungen zum Konfigurieren der Hardware [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] , die auf installiert ist, sowie zum Konfigurieren der SQL Server Instanz zur besseren Unterstützung externer Skripts. Dies ist besonders nützlich für **Datenbankadministratoren**.

+ [Leistungsoptimierung für R in SQL Server-Code-und Daten Optimierung](../r/r-and-data-optimization-r-services.md)

    Bietet spezifische Tipps zur Optimierung des externen Skripts, um bekannte Probleme zu vermeiden. Es ist besonders nützlich für **Daten**Analysten.

    > [!NOTE]
    > Obwohl viele der Informationen in diesem Abschnitt Allgemein auf R zutreffen, sind einige Informationen spezifisch für die revoscaler-Analysefunktionen. Ausführliche Leistungs Hinweise sind für **revoscalepy** und andere unterstützte python-Bibliotheken nicht verfügbar.
    >

+ [Leistungsoptimierung für R in SQL Server-Methoden und-Ergebnissen](../r/performance-case-study-r-services.md)

    Fasst zusammen, welche Daten für die beiden Fallstudien verwendet wurden, wie die Leistung getestet wurde und wie sich die Optimierungen auf die Ergebnisse ausgewirkt haben.
