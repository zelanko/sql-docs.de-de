---
title: SQL Server Data Mining-Add-Ins für Office | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c9021a19-2c19-4f0a-a293-5f7e0ac2524c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 10015ac40948c95f8c912ba6fdb71147e50bb880
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66082891"
---
# <a name="sql-server-data-mining-add-ins-for-office"></a>SQL Server Data Mining-Add-Ins für Office
  
  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Bei den Data Mining-Add-Ins für Office handelt es sich um ein kompaktes Set von Tools für Vorhersageanalysen, mit denen Sie auf der Grundlage von Daten in Excel analytische Modelle für Vorhersagezwecke, Empfehlungen oder Untersuchungen erstellen können.  
  
 Die Assistenten und die Datenverwaltungstools in den Add-Ins bieten schrittweise Anleitungen für die folgenden gängigen Data Mining-Tasks:  
  
-   **Organisieren und Bereinigen der Daten vor der Modellierung.** Dabei können Daten verwendet werden, die in Excel oder einer beliebigen Excel-Datenquelle gespeichert sind. Sie können Verbindungen erstellen und speichern, um Datenquellen wiederzuverwenden, Experimente zu wiederholen oder Modelle erneut zu trainieren.  
  
-   **Profilerstellung, Stichprobenentnahme und Vorbereitung.** Viele erfahrenen Data Mining-Benutzer sagen, dass 70 bis 90 Prozent eines Data Mining-Projekts auf die Datenvorbereitung entfallen. Die Add-Ins können diesen Task beschleunigen, da sie Visualisierungen in Excel und Assistenten bereitstellen, die Sie bei diesen gängigen Tasks unterstützen:  
  
    -   Erstellen von Datenprofilen und Verstehen ihrer Verteilung und Merkmale.  
  
    -   Erstellen von Trainings- und Testsätzen über zufällige Stichproben oder Überquotierung.  
  
    -   Erkennen, Entfernen oder Ersetzen von Ausreißern.  
  
    -   Neubezeichnen von Daten, um die Qualität der Analyse zu verbessern.  
  
-   **Analysieren von Mustern durch überwachtes oder Unüberwachtes Lernen.** Befolgen Sie die schrittweisen Anweisungen benutzerfreundlicher Assistenten, um einige der gängigsten Data Mining-Aufgaben wie Clusteringanalyse, Warenkorbanalyse und Planung auszuführen.  
  
     In den Add-Ins sind bewährte Computerlernalgorithmen wie Naive Bayes, Logistic Regression, Clustering, Zeitreihen und Neural Networks enthalten.  
  
     Wenn Sie über keine Erfahrungen mit dem Data Mining verfügen, werden Sie durch den Abfrage-Assistenten **** beim Erstellen von Vorhersageabfragen unterstützt.  
  
     Erfahrene Benutzer können benutzerdefinierte DMX-Abfragen mit dem **erweiterten Abfrage-Editor**per Drag &amp; Drop erstellen oder mit Excel VBA Vorhersagen automatisieren.  
  
-   **Dokumentieren und verwalten.** Nachdem Sie ein DataSet erstellt und einige Modelle erstellt haben, dokumentieren Sie Ihre Arbeit und ihre Erkenntnisse, indem Sie eine statistische Zusammenfassung der Daten und Modellparameter erstellen.  
  
-   **Untersuchen und visualisieren.** Data Mining ist keine Aktivität, die vollständig automatisiert werden kann. Sie müssen die Ergebnisse untersuchen und verstehen, um sinnvolle Maßnahmen ergreifen zu können. Die Add-Ins unterstützen Sie bei der Untersuchung. Sie bieten interaktive Viewer in Excel, Visio-Vorlagen, mit denen Sie Modelldiagramme anpassen können, sowie die Möglichkeit, Diagramme und Tabellen in Excel für weiteres Filtern oder Ändern zu exportieren.  
  
-   **Bereitstellen und integrieren.** Wenn Sie ein nützliches Modell erstellt haben, können Sie das Modell in die Produktion versetzen, indem Sie die Verwaltungs Tools verwenden, um das Modell von Ihrem experimentellen Server [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]in eine andere Instanz von zu exportieren.  
  
     Sie können das Modell auch auf dem Server belassen, auf dem es erstellt wurde, sollten aber die Trainingsdaten aktualisieren und Vorhersagen mithilfe von Integration Services- oder DMX-Skripts ausführen.  
  
     Poweruser schätzen die Funktionen der **Ablaufverfolgung** , mit der Sie die an den Server gesendeten XMLA- und DMX-Anweisungen anzeigen können.  
  
## <a name="getting-started"></a>Erste Schritte  
 Informationen zu den Tools und ersten Schritten erhalten Sie in folgenden Themen:  
  
-   [Data Mining-Client für Excel &#40;SQL Server Data Mining-Add-ins&#41;](../data-mining-client-for-excel-sql-server-data-mining-add-ins.md)  
  
-   [Tabellenanalysetools für Excel](../table-analysis-tools-for-excel.md)  
  
-   [Data Mining-Shapes für Visio](../data-mining-shapes-for-visio.md)  
  
-   [Herstellen einer Verbindung mit einem Data Mining-Server](../connect-to-a-data-mining-server.md)  
  
## <a name="support-and-requirements"></a>Unterstützung und Anforderungen  
 Die SQL Server Data Mining-Add-Ins für Office werden kostenlos als Download zur Verfügung gestellt. Sie müssen eine der folgenden Versionen von Office bereits installiert haben, um diese Tools verwenden zu können:  
  
-   Office 2010, 32-Bit- oder 64-Bit-Version  
  
-   Office 2013, 32-Bit- oder 64-Bit-Version  
  
> [!WARNING]  
>  Achten Sie darauf, dass Sie die Version der Add-Ins herunterladen, die auf Ihre Excel-Version ausgelegt ist.  
  
 Die Data Mining-Add-Ins erfordern eine Verbindung mit einer der folgenden Editionen von SQL Server Analysis Services:  
  
-   Enterprise  
  
-   Business Intelligence  
  
-   Standard  
  
 Je nach der Edition der SQL Server Analysis Services, mit denen Sie eine Verbindung herstellen, sind einige erweiterte Algorithmen u. U. nicht verfügbar. Weitere Informationen finden Sie [unter von den Editionen von SQL Server 2014 unterstützte Funktionen](https://msdn.microsoft.com/library/cc645993.aspx).  
  
 Weitere Hilfe zur Installation finden Sie auf dieser Seite im Download Center:[https://www.microsoft.com/download/details.aspx?id=29061](https://www.microsoft.com/download/details.aspx?id=29061)  
  
  
