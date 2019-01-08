---
title: 'Analysis Services-Tutorial – Lektion 1: Erstellen ein neuen tabellarischen modellprojekts | Microsoft-Dokumentation'
ms.date: 08/27/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9135df30afcec9bdae307d9b12aec6810baa98ec
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52417231"
---
# <a name="create-a-tabular-model-project"></a>Erstellen Sie ein Projekt für tabellarische Modelle

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

In dieser Lektion verwenden Sie Visual Studio mit SQL Server Data Tools (SSDT) oder Visual Studio 2017 mit Microsoft Analysis Services-Projekten VSIX-Methode, um ein neues Projekt für tabellarische Modelle mit Kompatibilitätsgrad 1400 zu erstellen. Nachdem das neue Projekt erstellt wurde, können Sie beginnen das Modell erstellen und Daten hinzuzufügen. In dieser Lektion erhalten Sie eine kurze Einführung in die tabellarische modellerstellungsumgebung in Visual Studio.  
  
Geschätzte Zeit zum Bearbeiten dieser Lektion: **10 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten

Dieser Artikel ist die erste Lektion in ein Lernprogramm zur tabellenmodellerstellung. Um diese Lektion abschließen zu können, gibt es mehrere Voraussetzungen erfüllt sein, dass Sie ein direktes haben müssen. Weitere Informationen finden Sie unter [Analysis Services – Adventure Works-Tutorial](../tutorial-tabular-1400/as-adventure-works-tutorial.md).  
  
## <a name="create-a-new-tabular-model-project"></a>Erstellen eines neuen Tabellenmodellprojekts  
  
#### <a name="to-create-a-new-tabular-model-project"></a>So erstellen Sie ein neues Tabellenmodellprojekt  
  
1.  In Visual Studio auf die **Datei** Menü klicken Sie auf **neu** > **Projekt**.  
  
2.  In der **neues Projekt** Dialogfeld erweitern Sie **installiert** > **Business Intelligence** > **Analysis Services**, und klicken Sie dann auf **tabellarischen Analysis Services-Projekts**.  
  
3.  In **Namen**, Typ **AW-Internetverkäufe**, und geben Sie dann einen Speicherort für die Projektdateien.  
  
    In der Standardeinstellung **Projektmappenname** ist identisch mit dem Projektnamen; Sie können jedoch einen anderen Projektmappennamen eingeben.  
  
4.  Klicken Sie auf **OK**.  
  
5.  In der **Designer für tabellarische Modelle** wählen Sie im Dialogfeld **integrierten Arbeitsbereich**.  
  
    Der Arbeitsbereich umfasst eine tabellarische Modelldatenbank mit dem gleichen Namen wie das Projekt während der Modellerstellung an. Integrierter Arbeitsbereich bedeutet, dass Visual Studio eine integrierte Instanz verwendet und Sie müssen eine separate Instanz der Analysis Services-Server nur für die Modellerstellung zu installieren.
      
6.  In **Kompatibilitätsgrad**Option **SQL Server 2017 / Azure Analysis Services (1400)**.   
 
    ![Tmd als Lektion 1](../tutorial-tabular-1400/media/as-lesson1-tmd.png)
      
    Wenn Sie SQL Server 2017 / Azure Analysis Services (1400) im Kompatibilitätsgrad-Listenfeld nicht sehen, verwenden Sie nicht die neueste Version von SQL Server Data Tools. Sie können die neueste Version unter [Installieren von SQL Server Data Tools](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt)herunterladen.  
      
  
## <a name="understanding-the-ssdt-tabular-model-authoring-environment"></a>Grundlegendes zu den tabellarische SSDT modellerstellungsumgebung  

Nun, dass Sie ein neues tabellarisches Modellprojekt erstellt haben, werfen wir kurz die tabellarische modellerstellungsumgebung in Visual Studio ansehen.  
  
Nachdem das Projekt erstellt wurde, wird es in Visual Studio geöffnet. Klicken Sie auf der rechten Seite in **tabellarischer Modell-Explorer**, Sie sehen eine Strukturansicht der Objekte in Ihrem Modell. Die Ordner sind leer, da Sie noch Daten importiert haben. Sie können einen Objekt-Ordner, um Aktionen ausführen, auf der Menüleiste ähnlich wie mit der Maustaste. Während Sie in diesem Tutorial durchlaufen, verwenden Sie im tabellarischen Modell-Explorer, um die verschiedenen Objekte in Ihrem Modellprojekt zu navigieren.

![Tme als Lektion 1](../tutorial-tabular-1400/media/as-lesson1-tme.png)

Klicken Sie auf die **Projektmappen-Explorer** Registerkarte. Hier sehen Sie Ihre **Model.bim** Datei. Wenn Sie nicht in das Designer-Fenster auf der linken Seite (das leere Fenster mit der Registerkarte Model.bim), sehen **Projektmappen-Explorer**unter **AW Internet-Verkaufsprojekt**, doppelklicken Sie auf die **Model.bim** Datei. Die Datei "Model.bim" enthält die Metadaten für Ihr Modellprojekt. 

![Se als Lektion 1](../tutorial-tabular-1400/media/as-lesson1-se.png)
  
Klicken Sie auf **Model.bim**. In der **Eigenschaften** Sie angezeigt wird, die Modelleigenschaften, die wichtigste davon ist, die **DirectQuery-Modus** Eigenschaft. Diese Eigenschaft gibt an, ob das Modell im In-Memory-Modus (aus) oder DirectQuery-Modus (ein) bereitgestellt wird. In diesem Tutorial erstellen und Bereitstellen Ihres Modells im In-Memory-Modus.

![als – Lektion 1-Eigenschaften](../tutorial-tabular-1400/media/as-lesson1-properties.png)
  
Wenn Sie ein Modellprojekt erstellen, bestimmte Modelleigenschaften gemäß den datenmodellierungseinstellungen, die in angegeben werden können automatisch festgelegt sind das **Tools** Menü > **Optionen** im Dialogfeld. Die Eigenschaften für die Datensicherung, Beibehaltung des Arbeitsbereichs und den Arbeitsbereichsserver geben an, wie und wo die Arbeitsbereichsdatenbank (Datenbank zur Modellerstellung) gesichert, speicherintern beibehalten und erstellt wird. Sie können diese Einstellungen später ändern, falls erforderlich, aber vorläufig lassen Sie diese Eigenschaften unverändert.  

In **Projektmappen-Explorer**, mit der rechten Maustaste **AW-Internetverkäufe** (Projekt), und klicken Sie dann auf **Eigenschaften**. Die **Eigenschaftenseiten des AW Internet Sales** Dialogfeld wird angezeigt. Sie festlegen einige dieser Eigenschaften später, wenn Sie das Modell bereitstellen.  
  
Wenn Sie SSDT installiert haben, wurden der Visual Studio-Umgebung mehrere neue Menüelemente hinzugefügt. Klicken Sie auf die **Modell** Menü. Hier können können Sie Daten importieren, Arbeitsbereichsdaten aktualisieren, Durchsuchen des Modells in Excel, Perspektiven und Rollen erstellen, die Modellansicht auswählen und Berechnungsoptionen festlegen. Klicken Sie auf die **Tabelle** Menü. Von hier aus können Sie zu erstellen und Verwalten von Beziehungen, Einstellungen für Datentabellen festlegen, Partitionen erstellen und Tabelleneigenschaften bearbeiten. Wenn Sie auf die **Spalte** Menü, Sie können hinzufügen und Löschen von Spalten in einer Tabelle, Fixieren von Spalten und Sortierreihenfolge angeben. SSDT fügt auch einige Schaltflächen hinzu, auf die Leiste. Besonders nützlich ist die AutoSumme-Funktion, um ein standardaggregationsmeasure für eine ausgewählte Spalte zu erstellen. Weitere Schaltflächen in der Symbolleiste bieten einen schnellen Zugriff auf häufig verwendete Funktionen und Befehle.  
  
Erkunden Sie einige der Dialogfelder und Positionen für verschiedene Funktionen, die für die Erstellung von Tabellenmodellen konzipiert sind. Während einige Elemente noch nicht aktiv sind, erhalten Sie eine gute Vorstellung von der Umgebung zur tabellenmodellerstellung.  
  

## <a name="whats-next"></a>Wie geht es weiter?

[Lektion 2: Abrufen von Daten](../tutorial-tabular-1400/as-lesson-2-get-data.md).

  
  
  
