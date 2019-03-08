---
title: 'Lektion 1: Erstellen ein neuen tabellarischen Modellprojekts | Microsoft-Dokumentation'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 988a091fa7d536386cadd2ed3412213a2e608564
ms.sourcegitcommit: 8bc5d85bd157f9cfd52245d23062d150b76066ef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/07/2019
ms.locfileid: "57579430"
---
# <a name="lesson-1-create-a-new-tabular-model-project"></a>Lektion 1: Erstellen eines neuen Tabellenmodellprojekts
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

In dieser Lektion erstellen Sie ein neues leeres Tabellenmodellprojekt in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Sobald das neue Projekt erstellt wird, können Sie mithilfe des Tabellenimport-Assistenten Daten hinzufügen. In dieser Lektion erhalten Sie eine kurze Einführung in die tabellarische modellerstellungsumgebung in SSDT.  
  
Geschätzte Zeit zum Bearbeiten dieser Lektion: **10 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
Dieses Thema stellt die erste Lektion in einem Lernprogramm zur Tabellenmodellerstellung dar. Um diese Lektion abschließen zu können, müssen Sie auf einer SQL Server-Instanz installierte AdventureWorksDW-Beispieldatenbank. Weitere Informationen finden Sie unter [Tabellenmodellierung &#40;Adventure Works-Tutorial&#41;](../analysis-services/tabular-modeling-adventure-works-tutorial.md).  
  
## <a name="create-a-new-tabular-model-project"></a>Erstellen eines neuen Tabellenmodellprojekts  
  
#### <a name="to-create-a-new-tabular-model-project"></a>So erstellen Sie ein neues Tabellenmodellprojekt  
  
1.  In SSDT auf das **Datei** Menü klicken Sie auf **neu** > **Projekt**.  
  
2.  In der **neues Projekt** Dialogfeld erweitern Sie **installiert** > **Business Intelligence** > **Analysis Services**, und klicken Sie dann auf **tabellarischen Analysis Services-Projekts**.  
  
3.  In **Namen**, Typ **AW-Internetverkäufe**, und geben Sie dann einen Speicherort für die Projektdateien.  
  
    Standardmäßig entspricht der **Projektmappenname** dem Projektnamen. Sie können jedoch auch einen anderen Projektmappennamen eingeben.  
  
4.  Klicken Sie auf **OK**.  
  
5.  In der **Designer für tabellarische Modelle** wählen Sie im Dialogfeld **integrierten Arbeitsbereich**.  
  
    Der Arbeitsbereich wird eine Datenbank für tabellarische Modelle mit dem gleichen Namen wie das Projekt während der Modellerstellung gehostet werden. Integrierter Arbeitsbereich bedeutet, dass SSDT eine eingebaute Instanz verwendet wird, und Sie müssen eine separate Instanz der Analysis Services-Server nur für die Modellerstellung zu installieren. Weitere Informationen finden Sie unter [Arbeitsbereichsdatenbank](../analysis-services/tabular-models/workspace-database-ssas-tabular.md).
      
6.  Überprüfen Sie im Listenfeld **Kompatibilitätsgrad**, ob **SQL Server 2016 (1200)** ausgewählt ist, und klicken Sie anschließend auf **OK**.   
 
    ![as-tabular-lesson1-tmd](../analysis-services/media/as-tabular-lesson1-tmd.png)
      
    Wenn Sie SQL Server 2016 RTM (1200) im Kompatibilitätsgrad-Listenfeld nicht angezeigt wird, verwenden Sie nicht die neueste Version von SQL Server Data Tools. Sie können die neueste Version unter [Installieren von SQL Server Data Tools](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt)herunterladen.  

    Wenn Sie die neueste Version von SSDT verwenden, können Sie auch auswählen, auf SQL Server 2017 (1400). Allerdings für Lektion 13: Bereitstellen, benötigen Sie eine SQL Server 2017 oder eine Azure-Server für die Bereitstellung auf.
      
    Auswählen eines früheren Kompatibilitätsgrads wird nur empfohlen, wenn Sie Ihr abgeschlossene tabellarische Modell in einer anderen Analysis Services-Instanz, die eine frühere Version von SQL Server bereitstellen möchten. Integrierter Arbeitsbereich wird bei niedrigeren Kompatibilitätsgraden nicht unterstützt. Weitere Informationen finden Sie unter [Kompatibilitätsgrad für tabellarische Modelle in Analysis Services](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md).   
  
## <a name="understanding-the-ssdt-tabular-model-authoring-environment"></a>Grundlegendes zu den tabellarische SSDT modellerstellungsumgebung  
Nun, dass Sie ein neues tabellarisches Modellprojekt erstellt haben, werfen wir kurz die tabellarische modellerstellungsumgebung in SSDT ansehen.  
  
Nachdem das Projekt erstellt wurde, werden sie in SSDT geöffnet. Klicken Sie auf der rechten Seite in **tabellarischer Modell-Explorer**, sehen Sie eine Strukturansicht der Objekte in Ihrem Modell. Da Sie noch Daten importiert haben, werden der Ordner leer sein. Sie können einen Objekt-Ordner, um Aktionen ausführen, auf der Menüleiste ähnlich wie mit der Maustaste. Während Sie in diesem Tutorial durchlaufen, verwenden Sie das tabellarische Modell-Explorer, um die verschiedenen Objekte in Ihrem Modellprojekt zu navigieren.

![as-tabular-lesson1-tme](../analysis-services/media/as-tabular-lesson1-tme.png)

Klicken Sie auf die **Projektmappen-Explorer** Registerkarte. Hier sehen Sie Ihre **Model.bim** Datei. Wenn Sie nicht in das Designer-Fenster auf der linken Seite (das leere Fenster mit der Registerkarte Model.bim), sehen **Projektmappen-Explorer**unter **AW Internet-Verkaufsprojekt**, doppelklicken Sie auf die **Model.bim** Datei. Die Datei "Model.bim" enthält alle Metadaten für Ihr Modellprojekt. 

![as-tabular-lesson1-se](../analysis-services/media/as-tabular-lesson1-se.png)
  
Wir sehen uns die Modelleigenschaften. Klicken Sie auf **Model.bim**. In der **Eigenschaften** Fenster sehen Sie die [Modelleigenschaften](../analysis-services/tabular-models/model-properties-ssas-tabular.md)wichtigste davon ist die **DirectQuery-Modus** Eigenschaft. Diese Eigenschaft gibt an, ob das Modell im InMemory-Modus (Aus) oder im DirectQuery-Modus (Ein) bereitgestellt wird. In diesem Lernprogramm wird das Modell im InMemory-Modus erstellt und bereitgestellt.

![as-tabular-lesson1-properties](../analysis-services/media/as-tabular-lesson1-properties.png)
  
Wenn Sie ein neues Modell erstellen, bestimmte Modelleigenschaften gemäß den datenmodellierungseinstellungen, die in angegeben werden können automatisch festgelegt sind das **Tools** > **Optionen** Dialogfeld. Die Eigenschaften für die Datensicherung, Beibehaltung des Arbeitsbereichs und den Arbeitsbereichsserver geben an, wie und wo die Arbeitsbereichsdatenbank (Datenbank zur Modellerstellung) gesichert, speicherintern beibehalten und erstellt wird. Sie können diese Einstellungen ggf. später ändern. Lassen Sie sie jedoch vorerst unverändert.  

In **Projektmappen-Explorer**, mit der rechten Maustaste **AW-Internetverkäufe** (Projekt), und klicken Sie dann auf **Eigenschaften**. Die **Eigenschaftenseiten des AW Internet Sales** Dialogfeld wird angezeigt. Hierbei handelt es sich um den erweiterten [Projekteigenschaften](../analysis-services/tabular-models/project-properties-ssas-tabular.md). Sie werden später einige dieser Eigenschaften festlegen, wenn Sie für die Bereitstellung des Modells bereit sind.  
  
Wenn Sie SSDT installiert haben, wurden der Visual Studio-Umgebung mehrere neue Menüelemente hinzugefügt. Betrachten wir nun, die nur für die Erstellung tabellarischer Modelle. Klicken Sie auf das Menü **Modell** . Von hier aus können Sie den Tabellenimport-Assistenten zu starten, anzeigen und Bearbeiten vorhandener Verbindungen, Arbeitsbereichsdaten aktualisieren, Durchsuchen des Modells in Excel mit der Funktion in Excel analysieren, Perspektiven und Rollen erstellen, die Modellansicht auswählen und Berechnungsoptionen festlegen.  
  
Klicken Sie auf das Menü **Tabelle** . Hier können Sie Beziehungen zwischen Tabellen erstellen und verwalten, Datumstabelleneigenschaften festlegen, Partitionen erstellen und Tabelleneigenschaften bearbeiten.  
  
Klicken Sie auf das Menü **Spalte** . Hier können Sie Spalten in einer Tabelle hinzufügen und löschen, Spalten fixieren und die Sortierreihenfolge angeben. Sie können auch die AutoSumme-Funktion verwenden, um ein Standardaggregationsmeasure für eine ausgewählte Spalte zu erstellen. Weitere Schaltflächen in der Symbolleiste bieten einen schnellen Zugriff auf häufig verwendete Funktionen und Befehle.  
  
Erkunden Sie einige der Dialogfelder und Positionen für verschiedene Funktionen, die für die Erstellung von Tabellenmodellen konzipiert sind. Obwohl einige Elemente noch nicht aktiv sind, erhalten Sie dennoch einen Einblick in die Umgebung zur Tabellenmodellerstellung.  


## <a name="additional-resources"></a>Zusätzliche Ressourcen
Mehr über die verschiedenen Typen von tabellenmodellprojekten finden Sie unter [Projekte für tabellarische Modelle](../analysis-services/tabular-models/tabular-model-projects-ssas-tabular.md). Weitere Informationen zu der Umgebung für die tabellenmodellerstellung finden Sie unter [Designer für tabellarische Modelle](../analysis-services/tabular-models/tabular-model-designer-ssas.md).  
  

## <a name="whats-next"></a>Wie geht es weiter?
Wechseln Sie zur nächsten Lektion: [Lektion 2: Hinzufügen von Daten](../analysis-services/lesson-2-add-data.md).

  
  
  
