---
title: Szenarios für Data Science und Lösungsvorlagen – SQL Server-Machine Learning
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 936bc010838b3869c567117a9e87cdc2c4ce6d52
ms.sourcegitcommit: 33712a0587c1cdc90de6dada88d727f8623efd11
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2018
ms.locfileid: "53596124"
---
# <a name="data-science-scenarios-and-solution-templates"></a>Szenarios für Data Science und Lösungsvorlagen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Vorlagen sind Beispiellösungen, die bewährte Methoden veranschaulichen und Bausteine für die schnelle Implementierung einer Lösung bereitstellen. Jede Vorlage wurde entwickelt, um ein bestimmtes Problem, für einen bestimmten vertikal oder Branche zu lösen. Die Tasks in jeder Vorlage reichen von der Datenvorbereitung und Featureentwicklung bis hin zum Modelltraining und zur Bewertung. Mithilfe dieser Vorlagen erfahren, wie [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] funktioniert. Klicken Sie dann gerne die Vorlage, passen Ihr eigenes Szenario an, und erstellen Sie eine benutzerdefinierte Lösung anpassen. 

Jede Lösung enthält Beispieldaten, R-Code oder Python-Code und SQL gespeicherten Prozeduren aus, falls zutreffend. Der Code kann in Ihrer bevorzugten Entwicklungsumgebung R oder Python zusammen mit Berechnungen in SQL Server ausgeführt werden. In einigen Fällen können Sie Code direkt mithilfe von T-SQL und SQL-Clienttool, wie z. B. SQL Server Management Studio ausführen.

> [!TIP]
> 
> Die meisten der Vorlagen gibt es mehrere Versionen unterstützen sowohl für lokale und cloud-Plattformen für Machine Learning. Beispielsweise können Sie die Projektmappe, die mit nur SQL Server erstellen, oder Sie können die Lösung in Microsoft R Server oder in Azure Machine Learning erstellen.

+ Weitere Informationen und Updates finden Sie unter dieser Ankündigung: [Interessante neue Vorlagen in Azure ML](https://blogs.technet.microsoft.com/machinelearning/2015/04/09/exciting-new-templates-in-azure-ml/)

+ Für den Download und installationsanweisungen finden Sie unter [Gewusst wie: Verwenden Sie die Vorlagen](#bkmk_HowTo).

## <a name="fraud-detection"></a>Betrugserkennung

[Online Fraud Detection Template-Vorlage (SQL Server R Services)](https://github.com/Microsoft/r-server-fraud-detection)

**Was:** Die Möglichkeit, betrügerische Transaktionen zu erkennen ist wichtig für Onlineunternehmen. Um verbrauchsbasierte kostenzuteilung Verluste zu verringern, müssen Unternehmen Transaktionen, die vorgenommen wurden, entweder über gestohlene Zahlungsmittel oder Anmeldeinformationen schnell zu identifizieren. Wenn die betrügerische Transaktionen erkannt werden, ergreifen Unternehmen in der Regel Maßnahmen, um bestimmte Konten so früh wie möglich zu blockieren, um weitere Verluste zu vermeiden. In diesem Szenario erfahren Sie, wie Sie Daten von online-kaufvorgängen verwenden, um die möglichen Betrug zu erkennen.

**So geht's:**  Die Betrugserkennung wird als binäres Klassifizierungsproblem gelöst. Die Methodik, die in dieser Vorlage verwendet wird, kann problemlos auf die Betrugserkennung in anderen Domänen angewendet werden.


## <a name="campaign-optimization"></a>Kampagnenoptimierung

[Vorhersagen, wie und wann Leads kontaktieren](https://microsoft.github.io/r-server-campaign-optimization/)

**Was:** Diese Lösung verwendet die Versicherungsbranche Daten zur Vorhersage von Leads basierend auf demografischen Daten, die historische Antwortdaten und produktspezifische Details.  Empfehlungen werden auch generiert, um anzugeben, den besten Kanal und Zeitpunkt Ansatz Benutzer Kaufverhalten zu beeinflussen.

**So geht's:** Die Lösung erstellt und mehrere Modelle verglichen. Die Lösung zeigt auch, automatisierte datenintegrations- und Verwenden von gespeicherten Prozeduren datenvorbereitung. Beispiele für parallele werden für SQL Server in der Datenbank, in Azure und HDInsight Spark bereitgestellt. 

## <a name="health-care-predict-length-of-stay-in-hospital"></a>Gesundheitswesen: prognostizieren der Länge des Aufenthalts im Krankenhaus 

[Prognostizieren der Aufenthaltsdauer in Kliniken](https://gallery.cortanaintelligence.com/Solution/Predicting-Length-of-Stay-in-Hospitals-1)

**Was:** Genau Vorhersagen der Patienten langfristige ein Krankenhausaufenthalt notwendig ist, möglicherweise ist ein wichtiger Teil sowohl Sorgfalt und Planung. Administratoren müssen in der Lage, um zu bestimmen, welche Einrichtungen mehr Ressourcen benötigen, und Pflegekräfte entsprechende sicherstellen möchten, dass sie die Anforderungen von Patienten erfüllen können.

**So geht's:** Diese Lösung verwendet die Data Science-VM, und eine Instanz von SQL Server mit Machine Learning aktiviert. Darüber hinaus eine Reihe von Power BI-Berichten, die Sie für die Interaktion mit einem bereitgestellten Modell verwenden können.

## <a name="customer-churn"></a>Kundenabwanderung

[Kundenabwanderung Vorhersagen Debitorenvorlage (SQL Server R Services)](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/Churn/Introduction.md)

**Was:** Analysieren und Vorhersagen von kundenabwanderung ist wichtig für jede Branche, in denen der Verlust von Kunden an Wettbewerber verwaltet und verhindert werden muss: Banking, Telekommunikation und im Einzelhandel, um nur einige zu nennen. Das Ziel der Abwanderungsanalyse ist es, zu identifizieren, welche Kunden möglicherweise abwandern und anschließend angemessene Maßnahmen einzuleiten, um diese Kunden zu behalten und weiterhin Geschäfte mit ihnen zu machen.

**So geht's:** Diese Vorlage formuliert, das Problem der kundenabwanderung als eine **binärklassifizierung** Problem. Es werden Beispieldaten aus zwei Quellen verwendet, Kundendemografie und Kundentransaktionen, um zu klassifizieren, ob Kunden wahrscheinlich oder eher unwahrscheinlich abwandern.
  
## <a name="predictive-maintenance"></a>Vorbeugende Wartung

[Vorlage zur vorbeugenden Wartung (SQL Server 2016)](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/PredictiveMaintenance/Introduction.md)

**Was:** Vorbeugende Wartung zielt darauf ab, erhöhen Sie die Effizienz von Wartungstasks, indem der Vergangenheit aufgetretene Fehler gesammelt, und verwenden diese Informationen, um vorherzusagen, wann oder wo bei einem Gerät möglicherweise Fehler auftreten. Die Möglichkeit Veraltung von Geräten vorherzusagen, ist besonders nützlich für Anwendungen, die auf verteilten Daten oder Sensoren basieren. Diese Methode kann auch zum Überwachen oder Vorhersagen Fehler in IoT (Internet of Things)-Geräte angewendet werden.

Finden Sie unter dieser Ankündigung Weitere Informationen: [Neue Vorlage zur vorbeugenden Wartung](https://blogs.technet.microsoft.com/machinelearning/2015/04/09/exciting-new-templates-in-azure-ml/)

**So geht's:** Diese Lösung konzentriert sich auf die Beantwortung der Frage "Wann wird ein in Betrieb genommener Computer einen Fehler?" Die Eingabedaten stellen simulierte Sensormessungen für Flugzeugtriebwerke dar. Daten aus der Überwachung der Engine aktuellen betriebsbedingungen, z. B. die aktuelle Arbeitszyklus, Einstellungen und sensormessungen, werden zum Erstellen von drei Typen von Vorhersagemodellen verwendet:

-   **Regressionsmodelle**, um vorherzusagen, wie viel länger ein Triebwerk arbeitet, bis es ausfällt. Das Beispielmodell prognostiziert die Metrik "Restlebensdauer" (RUL), auch als "Zeit zum Fehler" (TTF) bezeichnet.
  
-   **Klassifizierungsmodelle**, um vorherzusagen, ob ein Triebwerk womöglich ausfällt.
  
    Die **binäres klassifizierungsmodell** prognostiziert, ob ein Triebwerk innerhalb eines bestimmten Zeitraums ausfällt.

    Die **mehrklassige klassifikationsmodell** vorhersagt, ob ein bestimmtes Triebwerk möglicherweise fehl, und ein wahrscheinliches Zeitfenster des Fehlers bietet. Für einen bestimmten Tag können Sie z.B. vorhersagen, ob ein Gerät an diesem bestimmten Tag womöglich ausfallen wird oder innerhalb einer Zeitspanne ab diesem bestimmten Tag.

## <a name="energy-demand-forecasting"></a>Vorhersagen des Energiebedarfs

[Vorhersage des Energiebedarfs-Vorlage mit der SQL Server R Services](https://gallery.cortanaintelligence.com/Tutorial/Energy-Demand-Forecast-Template-with-SQL-Server-R-Services-1)

**Was:**: Für die nachfragevorhersage ist ein wichtiges Problem in verschiedenen Domänen, einschließlich der Energie, Verkaufs- und -Dienste. Genaue Vorhersage hilft Unternehmen, die eine bessere Planung, ressourcenzuweisung, Produktion durchführen und andere wichtige geschäftsentscheidungen zu treffen. Im Energiesektor ist die nachfragevorhersage für Energie Speicherkosten zu verringern und Ausgleichen von Angebot und Nachfrage entscheidend.

**So geht's:** Diese Vorlage verwendet SQL Server R Services, um den Bedarf an Strom vorherzusagen. Das Modell für die Vorhersage verwendet wird, eine random Forest-Regression-Modell basierend auf **RxDForest**, eine hohe Leistung Machine learning-Algorithmus, die in Microsoft R Server enthalten. Die Lösung umfasst einen Bedarfs-Simulator sowie alle erforderlichen R- und T-SQL-Codes, um ein Modell zu trainieren sowie gespeicherte Prozeduren, die Sie zum Generieren und Melden von Vorhersagen verwenden können. 


## <a name="bkmk_HowTo"></a>Gewusst wie: Verwenden Sie die Vorlagen

Zum Herunterladen der Dateien in den einzelnen Vorlagen können Sie GitHub-Befehle verwenden, oder Sie öffnen den Link und klicken auf **Download Zip** (Herunterladen der ZIP-Dateien), um alle Dateien auf Ihrem Computer zu speichern.  Wenn die Projektmappe heruntergeladen wurde, enthält sie in der Regel folgende Ordner:
  
-   **Daten**: Enthält die Beispieldaten für jede Anwendung.
  
-   **R**: Enthält alle Entwicklungscodes von, die Sie für die Lösung benötigen. Die Projektmappe benötigt die Bibliotheken, die von Microsoft R Server bereitgestellt werden, doch sie kann in jeder beliebigen R-IDE geöffnet und bearbeitet werden. Der R-Code wurde optimiert, sodass Berechnungen „datenbankintern“ durch Festlegen des Computekontexts auf eine SQL Server-Instanz ausgeführt werden.
  
-   **"SQLR"**: Enthält mehrere SQL-Dateien, die Sie z. B. in einer SQL-Umgebung ausführen können [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] um die gespeicherten Prozeduren zu erstellen, die Aufgaben im Zusammenhang mit wie Datenverarbeitung, Featureentwicklung und modellbereitstellung.
  
    Der Ordner enthält außerdem ein PowerShell-Skript, das Sie ausführen können, um alle Skripts aufzurufen und die Ende-zu-Ende-Umgebung zu erstellen. Denken Sie daran, das Skript an Ihre Umgebung anzupassen.

## <a name="next-steps"></a>Nächste Schritte

+ [SQL Server Machine Learning-Tutorial](machine-learning-services-tutorials.md)




