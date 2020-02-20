---
title: Data-Science-Lösungsvorlagen
description: In diesem Artikel werden branchenspezifischen Vorlagen beschrieben, die bewährte Methoden veranschaulichen und Bausteine für die Implementierung einer Machine Learning-Lösung bereitstellen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/29/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6d87fbbb60f70292075d4f24080798d017ee5288
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "74947278"
---
# <a name="data-science-scenarios-and-solution-templates"></a>Szenarios für Data Science und Lösungsvorlagen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Artikel werden verschiedene Vorlagen für Machine Learning-Lösungen in SQL Server beschrieben. Diese Vorlagen veranschaulichen die bewährten Methoden und stellen Bausteine für die schnelle Implementierung einer Machine Learning-Lösung bereit. Jede Vorlage ist für die Lösung eines bestimmten Data-Science-Problems in einer bestimmten Branche oder einem bestimmten Nischenmarkt konzipiert.
Die Tasks in jeder Vorlage reichen von der Datenvorbereitung und Featureentwicklung bis hin zum Modelltraining und zur Bewertung. 

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
Arbeiten Sie sich mithilfe dieser Vorlagen in die Funktionsweise von [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] ein. Dann können Sie die Vorlage an Ihr eigenes Szenario anpassen und so eine benutzerdefinierte Lösung erstellen.
::: moniker-end

::: moniker range=">=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions"
Mit diesen Vorlagen können Sie sich mit der Funktionsweise von SQL Server Machine Learning Services vertraut machen. Dann können Sie die Vorlage an Ihr eigenes Szenario anpassen und so eine benutzerdefinierte Lösung erstellen.
::: moniker-end

Jede Lösung umfasst Beispieldaten, R- oder Python-Code und gespeicherte SQL-Prozeduren (falls vorhanden). Der Code kann in Ihrer bevorzugten R- oder Python-Entwicklungsumgebung ausgeführt werden, wobei die Berechnungen in SQL Server durchgeführt werden. In einigen Fällen können Sie Code direkt mit T-SQL und einem beliebigen SQL-Clienttool wie SQL Server Management Studio ausführen.

> [!TIP]
> 
> Die meisten Vorlagen sind in mehreren Versionen vorhanden, sodass lokale Umgebungen und Cloudplattformen für Machine Learning unterstützt werden. Sie können beispielsweise nur mit SQL Server Lösungen erstellen, oder Sie können die Lösung in Microsoft R Server oder Azure Machine Learning erstellen.

+ Anweisungen zum Download und zum Setup finden Sie unter [Verwenden der Vorlagen](#bkmk_HowTo).

## <a name="fraud-detection"></a>Betrugserkennung

[Onlinevorlage zur Betrugserkennung (SQL Server R Services)](https://github.com/Microsoft/r-server-fraud-detection)

**Beschreibung:** Für online agierende Unternehmen ist es wichtig, dass betrügerische Transaktionen erkannt werden. Unternehmen müssen Transaktionen, die mit gestohlenen Zahlungsmitteln oder Anmeldeinformationen durchgeführt wurden, schnell erkennen, um Verluste durch Rückbuchungskosten gering zu halten. Wenn die betrügerische Transaktionen erkannt werden, ergreifen Unternehmen in der Regel Maßnahmen, um bestimmte Konten so früh wie möglich zu blockieren, um weitere Verluste zu vermeiden. In diesem Szenario erfahren Sie, wie Sie Daten von Onlinekaufvorgängen verwenden, um möglichen Betrug zu erkennen.

**Anwendung:**  Die Betrugserkennung wird als binäres Klassifizierungsproblem gelöst. Die Methodik, die in dieser Vorlage verwendet wird, kann problemlos auf die Betrugserkennung in anderen Domänen angewendet werden.


## <a name="campaign-optimization"></a>Kampagnenoptimierung

[Wann und wie werden Leads kontaktiert](https://microsoft.github.io/r-server-campaign-optimization/)

**Beschreibung:** In dieser Lösung werden Daten aus der Versicherungsbranche verwendet, um die Notwendigkeit, Leads zu kontaktieren, anhand von demografischen Daten, Verlaufsantwortdaten oder produktspezifischen Details vorherzusagen.  Auch Empfehlungen werden generiert, um den Kanal und Zeitpunkt für das Kontaktieren der Benutzer zu bestimmen, über den bzw. zu dem das Kaufverhalten möglichst positiv beeinflusst werden kann.

**Anwendung:** Die Lösung erstellt und vergleicht mehrere Modelle. Die Lösung veranschaulicht auch die automatisierte Datenintegration und Datenaufbereitung mithilfe gespeicherter Prozeduren. Es werden auch Parallelbeispiele für SQL Server (In-Database), Azure und HDInsight Spark bereitgestellt. 

## <a name="health-care-predict-length-of-stay-in-hospital"></a>Gesundheitswesen: Vorhersagen der Dauer von Krankenhausaufenthalten 

[Vorhersagen der Dauer von Krankenhausaufenthalten](https://gallery.cortanaintelligence.com/Solution/Predicting-Length-of-Stay-in-Hospitals-1)

**Beschreibung:** Für die Pflege und Planung ist es wichtig, genau vorhersagen zu können, ob Patienten langfristig im Krankenhaus bleiben müssen. Das Verwaltungspersonal muss bestimmen, welche Abteilungen mehr Ressourcen benötigen, und das Pflegepersonal muss die bedarfsorientierte Versorgung der Patienten sicherstellen.

**Anwendung:** Diese Lösung verwendet Data Science Virtual Machine mit einer Instanz von SQL Server, in der Machine Learning verwendet wird. Es sind auch einige Power BI-Berichte enthalten, die Sie zur Interaktion mit einem bereitgestellten Modell einsetzen können.

## <a name="customer-churn"></a>Kundenabwanderung

[Onlinevorlage zur Kundenabwanderung (SQL Server R Services)](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/Churn/README.md)

**Beschreibung:** Die Analyse und die Vorhersage von Kundenabwanderung ist für jede Branche wichtig, in der der Verlust von Kunden an Wettbewerber verwaltet und verhindert werden muss, z. B. im Bankwesen, in der Telekommunikation und im Einzelhandel. Das Ziel der Abwanderungsanalyse ist es, zu identifizieren, welche Kunden möglicherweise abwandern und anschließend angemessene Maßnahmen einzuleiten, um diese Kunden zu behalten und weiterhin Geschäfte mit ihnen zu machen.

**Anwendung:** In dieser Vorlage wird das Abwanderungsproblem als **Binärklassifizierung** dargestellt. Es werden Beispieldaten aus zwei Quellen verwendet, Kundendemografie und Kundentransaktionen, um zu klassifizieren, ob Kunden wahrscheinlich oder eher unwahrscheinlich abwandern.
  
## <a name="predictive-maintenance"></a>Predictive Maintenance

[Vorlage zu Predictive Maintenance (SQL Server 2016)](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/PredictiveMaintenance/README.md)

**Beschreibung:** Predictive Maintenance ist dafür vorgesehen, die Effizienz von Wartungstasks zu verbessern, indem in der Vergangenheit aufgetretene Fehler gesammelt und diese Informationen genutzt werden, um vorherzusagen, wann oder wo bei einem Gerät möglicherweise Fehler auftreten. Die Obsoleszenz eines Geräts vorhersagen zu können ist insbesondere für Anwendungen wichtig, die von verteilten Daten oder Sensoren abhängig sind. Diese Methode kann auch für die Überwachung oder Vorhersage von Fehlern bei IoT-Geräten (Internet der Dinge) eingesetzt werden.

**Anwendung:** Diese Lösung konzentriert sich auf die Beantwortung der Frage „Wann erzeugt ein in Betrieb genommener Computer einen Fehler?“. Die Eingabedaten stellen simulierte Sensormessungen für Flugzeugtriebwerke dar. Daten, die aus der Überwachung der aktuellen Betriebsbedingungen des Triebwerks stammen, z. B. der aktuelle Arbeitszyklus, Einstellungen oder Sensormessungen, werden zur Erstellung von drei verschiedenen Vorhersagemodellen verwendet:

-   **Regressionsmodelle**, um vorherzusagen, wie viel länger ein Triebwerk arbeitet, bis es ausfällt. Das Beispielmodell prognostiziert die Metrik „Remaining Useful Life“ (RUL, Verbleibende Nutzungsdauer), die auch „Time to Failure“ (TTF, Zeit bis zum Ausfall) genannt wird.
  
-   **Klassifizierungsmodelle**, um vorherzusagen, ob ein Triebwerk womöglich ausfällt.
  
    Das **binäre Klassifizierungsmodell** sagt vorher, ob ein Triebwerk innerhalb eines bestimmten Zeitraums ausfällt.

    Das **mehrklassige Klassifizierungsmodell** sagt vorher, ob ein bestimmtes Triebwerk ausfallen könnte und gibt das wahrscheinliche Zeitfenster des Ausfalls an. Für einen bestimmten Tag können Sie z.B. vorhersagen, ob ein Gerät an diesem bestimmten Tag womöglich ausfallen wird oder innerhalb einer Zeitspanne ab diesem bestimmten Tag.

## <a name="energy-demand-forecasting"></a>Prognose des Energiebedarfs

[Vorlage zur Prognose des Energiebedarfs mit SQL Server R Services](https://gallery.cortanaintelligence.com/Tutorial/Energy-Demand-Forecast-Template-with-SQL-Server-R-Services-1)

**Beschreibung:** Der Bedarf für Prognosen stellt ein Problem in verschiedenen Bereichen dar, zum Beispiel in der Energiebranche, im Einzelhandel und unter Dienstleistern. Eine genaue Prognose der Nachfrage unterstützt Unternehmen dabei, die Produktionsplanung und Ressourcenzuordnung zu verbessern und wichtige geschäftliche Entscheidungen zu treffen. In der Energiebranche ist die Vorhersage der Nachfrage entscheidend, um die Kosten für die Energiespeicherung zu senken und Versorgung und Nachfrage auszugleichen.

**Anwendung:** Diese Vorlage nutzt SQL Server R Services, um den Elektrizitätsbedarf vorherzusagen. Das für die Vorhersage verwendete Modell ist ein zufälliges Regressionsmodell mit Gesamtstruktur. Dieses basiert auf **rxDForest**, einem hochleistungsfähigen Machine-Learning-Algorithmus, der in Microsoft R Server enthalten ist. Die Lösung umfasst einen Bedarfs-Simulator sowie alle erforderlichen R- und T-SQL-Codes, um ein Modell zu trainieren sowie gespeicherte Prozeduren, die Sie zum Generieren und Melden von Vorhersagen verwenden können. 


## <a name="bkmk_HowTo"></a>Verwenden der Vorlagen

Zum Herunterladen der Dateien in den einzelnen Vorlagen können Sie GitHub-Befehle verwenden, oder Sie öffnen den Link und klicken auf **Download Zip** (Herunterladen der ZIP-Dateien), um alle Dateien auf Ihrem Computer zu speichern.  Wenn die Projektmappe heruntergeladen wurde, enthält sie in der Regel folgende Ordner:
  
-   **Data:** enthält die Beispieldaten für jede Anwendung
  
-   **R:** enthält alle Entwicklungscodes von R, die Sie für die Projektmappe benötigen Die Projektmappe benötigt die Bibliotheken, die von Microsoft R Server bereitgestellt werden, doch sie kann in jeder beliebigen R-IDE geöffnet und bearbeitet werden. Der R-Code wurde optimiert, sodass Berechnungen „datenbankintern“ durch Festlegen des Computekontexts auf eine SQL Server-Instanz ausgeführt werden.
  
-   **SQLR**: enthält mehrere SQL-Dateien, die Sie in einer SQL-Umgebung wie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ausführen können, um die gespeicherten Prozeduren zu erstellen, die verwandte Tasks wie Datenverarbeitung, Featureentwicklung und Modellbereitstellung ausführen
  
    Der Ordner enthält außerdem ein PowerShell-Skript, das Sie ausführen können, um alle Skripts aufzurufen und die Ende-zu-Ende-Umgebung zu erstellen. Denken Sie daran, das Skript an Ihre Umgebung anzupassen.

## <a name="next-steps"></a>Nächste Schritte

+ [SQL Server-Machine-Learning-Tutorial](machine-learning-services-tutorials.md)




