---
title: Leistungsoptimierung für R
description: In diesem Artikel wird die Leistungsoptimierung für R Services beschrieben.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 04/15/2018
ms.topic: how-to
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 991f9f0ddbe58e5591a89ff16bf8455d5a5cdca4
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85756478"
---
# <a name="performance-tuning-for-r-in-sql-server"></a>Leistungsoptimierung für R in SQL Server
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Dieser Artikel ist der erste in einer Reihe von vier Artikeln, in denen die Leistungsoptimierung für R Services basierend auf zwei Fallstudien beschrieben wird:

- Leistungstests, die vom Produktentwicklungsteam durchgeführt werden, um das Leistungsprofil von R-Lösungen zu überprüfen

- Leistungsoptimierung durch das Microsoft Data Science-Team für ein bestimmtes Machine Learning-Szenario, das häufig von Kunden angefordert wird

Das Ziel dieser Reihe ist es, Anleitungen für die Techniken zur Leistungsoptimierung bereitzustellen, die für das Ausführen von R-Aufträgen in SQL Server am nützlichsten sind.

+ Dieses (erste) Thema bietet eine Übersicht über die Architektur und einige häufige Probleme bei der Optimierung für Data Science-Aufgaben.
+ Im zweiten Artikel werden bestimmte Hardware- und SQL Server-Optimierungen behandelt.
+ Der dritte Artikel behandelt Optimierungen in R-Code und Ressourcen für die Operationalisierung.
+ Im vierten Artikel werden die Testmethoden ausführlich beschrieben sowie Ergebnisse und Schlussfolgerungen genannt.

**Anwendungsbereich:** SQL Server 2016 R Services, SQL Server Machine Learning Services

## <a name="performance-goals-and-targeted-scenarios"></a>Leistungsziele und Zielszenarien

Das R Services-Feature wurde in SQL Server 2016 eingeführt, um die Ausführung von R-Skripts durch SQL Server zu unterstützen. Bei Verwendung dieses Features wird die R-Laufzeit in einem separaten Prozess von der Datenbank-Engine betrieben. Die Daten werden jedoch mithilfe von Serverressourcen und -diensten, die mit SQL Server interagieren (z.B. Trusted Launchpad), auf sichere Weise mit der Datenbank-Engine ausgetauscht.

In SQL Server 2017 wurde Unterstützung für das Ausführen von Python-Skripts mithilfe der gleichen Architektur angekündigt, wobei in Zukunft noch weitere Sprachen folgen werden.

Mit zunehmender Anzahl unterstützter Versionen und Sprachen ist es wichtig, dass sich der Datenbankadministrator und der Datenbankarchitekt des Potenzials von Ressourcenkonflikten durch Machine Learning-Aufträge bewusst sind und den Server zur Unterstützung der neuen Workloads konfigurieren können. Obwohl durch datennahe Analysen unsichere Datenverschiebungen vermieden werden, werden Analyseworkloads vom Laptop des Datenanalysten zurück auf den Server verschoben, auf dem die Daten gehostet werden.

Die Leistungsoptimierung für Machine Learning ist eindeutig keine Einheitslösung. Die folgenden allgemeinen Aufgaben können sehr unterschiedliche Leistungsprofile aufweisen:

- Trainingsaufgaben: Erstellen und Trainieren eines Regressionsmodells gegenüber dem Trainieren eines neuronalen Netzwerks
- Featureentwicklung mithilfe von R gegenüber Featureextraktion mit T-SQL
- Bewertung von einzelnen Zeilen oder kleinen Batches gegenüber Massenbewertung mithilfe von Tabelleneingaben
- Ausführen der Bewertung in R gegenüber Bereitstellen von Modellen in der Produktion auf SQL Server in gespeicherten Prozeduren
- Ändern von R-Code zum Minimieren der Datenübertragung oder Entfernen kostenintensiver Datentransformationen
- Aktivieren von automatischem Testen und erneutem Trainieren von Modellen

Da die Auswahl der Optimierungstechniken davon abhängt, welche Aufgabe für Ihre Anwendung oder Ihren Anwendungsfall entscheidend ist, umfassen die Fallstudien sowohl allgemeine Tipps zur Leistung als auch Anleitungen zur Optimierung für ein bestimmtes Szenario, die Optimierung für die Batchbewertung.

+ **Individuelle Optimierungsoptionen in SQL Server**

    In der ersten Fallstudie zur Leistung wurden mehrere Tests für ein einzelnes Dataset mit einem einzigen Modelltyp ausgeführt. Mithilfe des rxLinMod-Algorithmus in RevoscaleR wurde ein Modell zum Erstellen von Bewertungen erstellt, doch wurden der Code und die zugrunde liegenden Datentabellen systematisch geändert, um die Auswirkungen der einzelnen Änderungen zu testen.

    Beispielsweise wurde in einem Testlauf der R-Code so geändert, dass ein Vergleich zwischen der Featureentwicklung mithilfe einer Transformationsfunktion gegenüber dem Vorausberechnen der Features und dem anschließenden Laden der Features aus einer Tabelle vorgenommen werden konnte. In einem weiteren Testlauf wurde die Leistung des Modelltrainings bei Verwendung einer indizierten Standardtabelle gegenüber Daten in einer Tabelle mit verschiedenen Komprimierungstypen oder neuen Indextypen verglichen.

+ **Optimierung für ein bestimmtes Bewertungsszenario mit hohem Volumen**

    Die Machine Learning-Aufgabe in der zweiten Fallstudie umfasst die Verarbeitung vieler Lebensläufe, die für mehrere Positionen eingesandt wurden, und die Ermittlung des besten Kandidaten für die jeweilige Position. Das Machine Learning-Modell selbst ist als ein binäres Klassifizierungsproblem formuliert: Es nimmt einen Lebenslauf und eine Stellenbeschreibung als Eingabe und generiert die Wahrscheinlichkeit für jedes Lebenslauf-Stelle-Paar. Da es das Ziel ist, die beste Übereinstimmung zu finden, wird ein benutzerdefinierter Wahrscheinlichkeitsschwellenwert verwendet, um weiter zu filtern und nur die passenden Übereinstimmungen zu erhalten.

    Bei dieser Lösung war es das Hauptziel, eine geringe Latenz bei der Bewertung zu erreichen. Diese Aufgabe ist aber auch während des Bewertungsprozesses rechenintensiv, da jede neue Stelle innerhalb eines angemessenen Zeitraums mit Millionen von Lebensläufen abgeglichen werden muss. Außerdem werden im Featureentwicklungsschritt mehr als 2000 Features pro Lebenslauf oder Stelle erzeugt, was einen erheblichen Leistungsengpass darstellt.

Es wird empfohlen, alle Ergebnisse der ersten Fallstudie zu überprüfen, um festzustellen, welche Techniken für Ihre Lösung geeignet sind, und deren potenziellen Auswirkungen abzuwägen.

Dann überprüfen Sie die Ergebnisse der Fallstudie zur Bewertungsoptimierung, um zu sehen, wie der Autor verschiedene Techniken angewendet und den Server zur Unterstützung einer bestimmten Workload optimiert hat.

## <a name="performance-optimization-process"></a>Leistungsoptimierungsprozess

Zum Konfigurieren und Optimieren für Leistung muss eine solide Basis erstellt werden, auf der Optimierungen für bestimmte Workloads aufbauen:

- Wählen Sie einen geeigneten Server zum Hosten von Analysen aus. Normalerweise wird ein sekundärer Berichtsserver, Data Warehouse-Server oder ein anderer Server bevorzugt, der bereits für andere Berichte oder Analysen verwendet wird. In einer HTAP-Lösung (Hybrid Transactional-Analytical Processing) können jedoch operative Daten als Eingabe für R für eine schnelle Bewertung verwendet werden.

- Konfigurieren Sie die SQL Server-Instanz, um Datenbank-Engine-Vorgänge und die Ausführung von R- oder Python-Skripts in geeigneter Form auszugleichen. Dies kann das Ändern von SQL Server-Standardwerten für die Arbeitsspeicher- und CPU-Auslastung, die Einstellungen für NUMA und Prozessoraffinität sowie die Erstellung von Ressourcengruppen umfassen.

- Optimieren Sie den Servercomputer, um eine effiziente Verwendung externer Skripts zu unterstützen. Dies kann das Erhöhen der Anzahl von Konten, die für die Ausführung externer Skripts verwendet werden, das Aktivieren der Paketverwaltung und das Zuweisen von Benutzern zu verwandten Sicherheitsrollen umfassen.

- Wenden Sie spezielle Optimierungen für die Datenspeicherung und -übertragung in SQL Server an, einschließlich Indizierungs- und Statistikstrategien, Abfrageentwurf und Abfrageoptimierung sowie den Entwurf von Tabellen, die für Machine Learning verwendet werden. Sie können auch Datenquellen und Datentransportmethoden analysieren oder ETL-Prozesse ändern, um die Featureextraktion zu optimieren.

- Optimieren Sie das Analysemodell, um Ineffizienzen zu vermeiden. Der Umfang der möglichen Optimierungen hängt von der Komplexität des R-Codes und den verwendeten Paketen und Daten ab. Zu den Hauptaufgaben gehören das Beseitigen kostenintensiver Datentransformationen oder das Auslagern von Aufgaben zur Datenvorbereitung oder Featureentwicklung von R oder Python zu ETL-Prozessen oder SQL. Sie können auch Skripts umgestalten, Inline-Paketinstallationen entfernen, R-Code in separate Verfahren zum Trainieren, Bewerten und Evaluieren unterteilen oder Code so vereinfachen, dass er effizienter als gespeicherte Prozedur funktioniert.

## <a name="articles-in-this-series"></a>Artikel in dieser Reihe

+ [Leistungsoptimierung für R in SQL Server – Hardware](../r/sql-server-configuration-r-services.md)

    Enthält Anleitungen zum Konfigurieren der Hardware, auf der [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] installiert ist, sowie zum Konfigurieren der SQL Server-Instanz für bessere Unterstützung externer Skripts. Dies ist besonders nützlich für **Datenbankadministratoren**.

+ [Leistungsoptimierung für R in SQL Server – Code- und Datenoptimierung](../r/r-and-data-optimization-r-services.md)

    Enthält spezifische Tipps zur Optimierung des externen Skripts, um bekannte Probleme zu vermeiden. Dies ist besonders nützlich für **Datenanalysten**.

    > [!NOTE]
    > Während ein Großteil der Informationen in diesem Abschnitt für R im Allgemeinen gilt, sind einige Informationen spezifisch für analytische RevoScaleR-Funktionen vorgesehen. Ein ausführlicher Leitfaden zur Leistung für **revoscalepy** und andere unterstützte Python-Bibliotheken ist nicht verfügbar.
    >

+ [Leistungsoptimierung für R in SQL Server – Methoden und Ergebnisse](../r/performance-case-study-r-services.md)

    Fasst zusammen, welche Daten für die beiden Fallstudien verwendet wurden, wie die Leistung getestet wurde und wie sich die Optimierungen auf die Ergebnisse ausgewirkt haben.
