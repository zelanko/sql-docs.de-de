---
title: Data Science-Szenarien und Lösungs Vorlagen
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/29/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: cb144eb5c766b417884f6f1adb67dc0ac48504a5
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469779"
---
# <a name="data-science-scenarios-and-solution-templates"></a>Data Science-Szenarien und Lösungs Vorlagen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Vorlagen sind Beispiellösungen, die bewährte Methoden veranschaulichen und Bausteine für die schnelle Implementierung einer Lösung bereitstellen. Jede Vorlage ist so konzipiert, dass ein bestimmtes Problem für eine bestimmte vertikale oder Branche gelöst wird. Die Tasks in jeder Vorlage reichen von der Datenvorbereitung und Featureentwicklung bis hin zum Modelltraining und zur Bewertung. Verwenden Sie diese Vorlagen, um [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] zu erfahren, wie funktioniert. Dann können Sie die Vorlage so anpassen, dass Sie Ihrem eigenen Szenario entspricht, und eine benutzerdefinierte Lösung erstellen. 

Jede Lösung umfasst Beispiel Daten, R-Code oder python-Code und ggf. gespeicherte SQL-Prozeduren. Der Code kann in Ihrer bevorzugten R-oder python-Entwicklungsumgebung ausgeführt werden, wobei Berechnungen in SQL Server durchgeführt werden. In einigen Fällen können Sie Code direkt mit T-SQL und einem beliebigen SQL-Client Tool, wie z. b. SQL Server Management Studio, ausführen.

> [!TIP]
> 
> Die meisten Vorlagen sind in mehreren Versionen enthalten, die sowohl lokale als auch cloudbasierte Plattformen für Machine Learning unterstützen. Beispielsweise können Sie die Projekt Mappe nur mit SQL Server erstellen, oder Sie können die Projekt Mappe in Microsoft R Server oder Azure Machine Learning erstellen.

+ Anweisungen zum herunterladen und einrichten finden Sie unter [How to use the Templates](#bkmk_HowTo).

## <a name="fraud-detection"></a>Betrugserkennung

[Vorlage für die Online Betrugserkennung (SQL Server R Services)](https://github.com/Microsoft/r-server-fraud-detection)

**Worüber** Die Fähigkeit zum Erkennen betrügerischer Transaktionen ist wichtig für Online Unternehmen. Um die Kosten Verluste zu verringern, müssen Unternehmen Transaktionen schnell ermitteln, die mithilfe von gestohlenen Zahlungsinstrumenten oder Anmelde Informationen erstellt wurden. Wenn die betrügerische Transaktionen erkannt werden, ergreifen Unternehmen in der Regel Maßnahmen, um bestimmte Konten so früh wie möglich zu blockieren, um weitere Verluste zu vermeiden. In diesem Szenario erfahren Sie, wie Sie Daten aus Online Kauf Transaktionen verwenden, um wahrscheinliche Betrugsfälle zu ermitteln.

**Dass**  Die Betrugserkennung wird als binäres Klassifizierungsproblem gelöst. Die Methodik, die in dieser Vorlage verwendet wird, kann problemlos auf die Betrugserkennung in anderen Domänen angewendet werden.


## <a name="campaign-optimization"></a>Kampagnen Optimierung

[Vorhersagen, wie und wann Sie Leads kontaktieren sollten](https://microsoft.github.io/r-server-campaign-optimization/)

**Worüber** Diese Lösung verwendet Versicherungs Industrie-Daten, um Leads basierend auf demografischen Daten, Verlaufs Daten und produktspezifischen Details vorherzusagen.  Außerdem werden Empfehlungen generiert, um den besten Kanal und die beste Zeit für die Benutzer zu beeinflussen, um das Kaufverhalten zu beeinflussen.

**Dass** Mit der Lösung werden mehrere Modelle erstellt und verglichen. Die Lösung veranschaulicht auch die automatisierte Datenintegration und die Daten Vorbereitung mithilfe gespeicherter Prozeduren. Parallele Beispiele werden für SQL Server in-Database, in Azure und hdinsight Spark bereitgestellt. 

## <a name="health-care-predict-length-of-stay-in-hospital"></a>Gesundheitswesen: Vorhersage der Länge des Aufenthalts im Krankenhaus 

[Vorhersagen der Länge des Aufenthalts in Krankenhäusern](https://gallery.cortanaintelligence.com/Solution/Predicting-Length-of-Stay-in-Hospitals-1)

**Worüber** Die genaue Vorhersage, welche Patienten die langfristige Hospitalisierung benötigen, ist ein wichtiger Bestandteil der Pflege und Planung. Administratoren müssen in der Lage sein, zu bestimmen, welche Einrichtungen mehr Ressourcen benötigen, und die Betreuer möchten sicherstellen, dass Sie die Anforderungen von Patienten erfüllen können.

**Dass** Diese Lösung verwendet die Data Science Virtual Machine und enthält eine Instanz von SQL Server mit aktiviertem Machine Learning. Sie enthält auch eine Reihe von Power BI-Berichten, die Sie für die Interaktion mit einem bereitgestellten Modell verwenden können.

## <a name="customer-churn"></a>Kunden Abwanderung

[Vorhersage Vorlage für Kunden Abwanderung (SQL Server R Services)](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/Churn/README.md)

**Worüber** Das analysieren und Vorhersagen der Kunden Abwanderung ist in jeder Branche wichtig, in der der Verlust der Kunden an Mitbewerber verwaltet und verhindert werden muss: Banking, Telekommunikation und Einzelhandel, um nur einige zu nennen. Das Ziel der Abwanderungsanalyse ist es, zu identifizieren, welche Kunden möglicherweise abwandern und anschließend angemessene Maßnahmen einzuleiten, um diese Kunden zu behalten und weiterhin Geschäfte mit ihnen zu machen.

**Dass** Diese Vorlage formuliert das Änderungs Problem als **binäres Klassifizierungs** Problem. Es werden Beispieldaten aus zwei Quellen verwendet, Kundendemografie und Kundentransaktionen, um zu klassifizieren, ob Kunden wahrscheinlich oder eher unwahrscheinlich abwandern.
  
## <a name="predictive-maintenance"></a>Vorbeugende Wartung

[Vorlage für vorbeugende Wartung (SQL Server 2016)](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/PredictiveMaintenance/README.md)

**Worüber** Bei der vorbeugenden Wartung soll die Effizienz von Wartungs Tasks gesteigert werden, indem frühere Ausfälle aufgezeichnet werden und diese Informationen verwendet werden, um vorherzusagen, wann oder wo ein Gerät ausfällt. Die Möglichkeit zur Vorhersage der Geräte Alterung ist besonders nützlich für Anwendungen, die auf verteilten Daten oder Sensoren basieren. Diese Methode kann auch zum Überwachen oder Vorhersagen von Fehlern in IOT-Geräten (Internet der Dinge) angewendet werden.

**Dass** Diese Lösung konzentriert sich auf die Beantwortung der Frage "Wann wird ein Dienst interner Computer nicht ausgeführt?". Die Eingabedaten stellen simulierte Sensormessungen für Flugzeugtriebwerke dar. Die Daten, die aus der Überwachung der aktuellen Vorgangs Bedingungen der Engine abgerufen werden, z. b. der aktuelle Arbeitszyklen, die Einstellungen und die Sensormessungen, werden verwendet, um drei Typen von Vorhersagemodellen zu erstellen:

-   **Regressionsmodelle**, um vorherzusagen, wie viel länger ein Triebwerk arbeitet, bis es ausfällt. Das Beispielmodell sagt die Metrik "verbleibende nutzbare Lebensdauer" (rul), die auch als "Time to Failure" (ttf) bezeichnet wird.
  
-   **Klassifizierungsmodelle**, um vorherzusagen, ob ein Triebwerk womöglich ausfällt.
  
    Das **binäre Klassifizierungs Modell** prognostiziert, ob ein Modul innerhalb eines bestimmten Zeitrahmens ausfällt.

    Das **Multi-Class-Klassifizierungs Modell** prognostiziert, ob ein bestimmtes Modul möglicherweise fehlschlägt, und stellt ein wahrscheinliches Zeitfenster des Fehlers bereit. Für einen bestimmten Tag können Sie z.B. vorhersagen, ob ein Gerät an diesem bestimmten Tag womöglich ausfallen wird oder innerhalb einer Zeitspanne ab diesem bestimmten Tag.

## <a name="energy-demand-forecasting"></a>Vorhersagen des Energiebedarfs

[Vorhersage Vorlage für Energienachfrage mit SQL Server R Services](https://gallery.cortanaintelligence.com/Tutorial/Energy-Demand-Forecast-Template-with-SQL-Server-R-Services-1)

**Was:** : Die Bedarfs Vorhersage ist ein wichtiges Problem in verschiedenen Domänen, einschließlich Energie, Einzelhandel und Diensten. Die genaue Nachfrage nach Bedarf hilft Unternehmen, eine bessere Produktionsplanung und Ressourcen Zuordnung durchzuführen und andere wichtige geschäftliche Entscheidungen zu treffen. Im Energiesektor ist die Bedarfs Vorhersage wichtig, um die Energiespeicher Kosten zu senken und die Versorgung und Nachfrage auszugleichen.

**Dass** Diese Vorlage verwendet SQL Server R Services, um die Nachfrage nach Strom vorherzusagen. Das für Vorhersagen verwendete Modell ist ein zufälliges Gesamtstruktur-Regressionsmodell, das auf **rxdforest**basiert, einem hochleistungsfähigen Machine Learning-Algorithmus, der in Microsoft R Server enthalten ist. Die Lösung umfasst einen Bedarfs-Simulator sowie alle erforderlichen R- und T-SQL-Codes, um ein Modell zu trainieren sowie gespeicherte Prozeduren, die Sie zum Generieren und Melden von Vorhersagen verwenden können. 


## <a name="bkmk_HowTo"></a>Verwenden der Vorlagen

Zum Herunterladen der Dateien in den einzelnen Vorlagen können Sie GitHub-Befehle verwenden, oder Sie öffnen den Link und klicken auf **Download Zip** (Herunterladen der ZIP-Dateien), um alle Dateien auf Ihrem Computer zu speichern.  Wenn die Projektmappe heruntergeladen wurde, enthält sie in der Regel folgende Ordner:
  
-   **Daten**: Enthält die Beispiel Daten für jede Anwendung.
  
-   **R**: Enthält den gesamten R-Entwicklungscode, den Sie für die Lösung benötigen. Die Projektmappe benötigt die Bibliotheken, die von Microsoft R Server bereitgestellt werden, doch sie kann in jeder beliebigen R-IDE geöffnet und bearbeitet werden. Der R-Code wurde optimiert, sodass Berechnungen „datenbankintern“ durch Festlegen des Computekontexts auf eine SQL Server-Instanz ausgeführt werden.
  
-   **SQLR**: Enthält mehrere SQL-Dateien, die Sie in einer SQL-Umgebung ausführen können [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , z. b., um die gespeicherten Prozeduren zu erstellen, die verwandte Tasks wie Datenverarbeitung, Featureentwicklung und Modell Bereitstellung ausführen.
  
    Der Ordner enthält außerdem ein PowerShell-Skript, das Sie ausführen können, um alle Skripts aufzurufen und die Ende-zu-Ende-Umgebung zu erstellen. Denken Sie daran, das Skript an Ihre Umgebung anzupassen.

## <a name="next-steps"></a>Nächste Schritte

+ [Lernprogramme zum SQL Server Machine Learning](machine-learning-services-tutorials.md)




