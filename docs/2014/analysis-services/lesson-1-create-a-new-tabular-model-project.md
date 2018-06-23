---
title: 'Lektion 1: Erstellen ein neuen Tabellenmodellprojekts | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0d2eb34d-78c8-41ff-b92d-49b62c16b2ac
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.openlocfilehash: 6a5f5c938289963373d09891f20c3a87495a33a1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148495"
---
# <a name="lesson-1-create-a-new-tabular-model-project"></a>Lektion 1: Erstellen eines neuen Tabellenmodellprojekts
  In dieser Lektion erstellen Sie ein neues leeres Tabellenmodellprojekt in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Sobald das neue Projekt erstellt wird, können Sie mithilfe des Tabellenimport-Assistenten Daten hinzufügen. Zusätzlich zum Erstellen eines neuen Projekts bietet diese Lektion auch eine kurze Einführung in die Umgebung zur Tabellenmodellerstellung in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].  
  
 Weitere Informationen zu den verschiedenen Typen von Tabellenmodellprojekten finden Sie unter [Tabellenmodellprojekte &#40;SSAS – tabellarisch&#41;](tabular-models/tabular-model-projects-ssas-tabular.md). Weitere Informationen zu der Umgebung zur tabellenmodellerstellung finden Sie unter [Tabellenmodelldesigners &#40;SSAS – tabellarisch&#41;](tabular-model-designer-ssas-tabular.md).  
  
 Geschätzte Zeit zum Bearbeiten dieser Lektion: **10 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Dieses Thema stellt die erste Lektion in einem Lernprogramm zur Tabellenmodellerstellung dar. Um diese Lektion abzuschließen, benötigen Sie die auf einer SQL Server-Instanz installierte AdventureWorksDW-Datenbank. Weitere Informationen finden Sie unter [Tabellenmodellierung &#40;Adventure Works-Tutorial&#41;](tabular-modeling-adventure-works-tutorial.md).  
  
## <a name="create-a-new-tabular-model-project"></a>Erstellen eines neuen Tabellenmodellprojekts  
  
#### <a name="to-create-a-new-tabular-model-project"></a>So erstellen Sie ein neues Tabellenmodellprojekt  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]auf das Menü **Datei** , auf **Neu**und dann auf **Projekt**.  
  
2.  In der **neues Projekt** Dialogfeld unter **installierte Vorlagen**, klicken Sie auf **Business Intelligence**, klicken Sie dann auf **Analysis Services**, und Klicken Sie dann auf **tabellarischen Analysis Services-Projekts**.  
  
3.  In **Namen**, Typ `AW Internet Sales Tabular Model`, und geben einen Speicherort für die Projektdateien.  
  
     Standardmäßig entspricht der **Projektmappenname** dem Projektnamen. Sie können jedoch auch einen anderen Projektmappennamen eingeben.  
  
4.  Klicken Sie auf **OK**.  
  
## <a name="understanding-the-sql-server-data-tools-tabular-model-authoring-environment"></a>Einblick in die SQL Server Data Tools-Umgebung zur Tabellenmodellerstellung  
 Nachdem Sie ein neues Projekt für tabellarische Modelle erstellt haben, soll nun die Umgebung zur Erstellung tabellarischer Modelle in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] (Visual Studio 2010 oder höher) erkundet werden.  
  
 Nach der Erstellung des Projekts wird es in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] geöffnet. Ein leeres Modell wird im Modell-Designer angezeigt, und die Datei **Model.bim** wird im Fenster des **Projektmappen-Explorers** ausgewählt. Wenn Sie Daten hinzufügen, werden Tabellen und Spalten im Designer angezeigt. Wenn Sie den Designer (das leere Fenster mit der Registerkarte "Model.bim") in sehen **Projektmappen-Explorer**unter `AW Internet Sales Tabular Model`, doppelklicken klicken Sie auf die **Model.bim** Datei.  
  
 Sie können die grundlegenden Eigenschaften für das Projekt im Fenster **Eigenschaften** anzeigen. In **Projektmappen-Explorer**, klicken Sie auf `AW Internet Sales Tabular Model`. Im Fenster **Eigenschaften** unter **Projektdatei**wird **AW Internet Sales Tabular Model.smproj**angezeigt. Dies ist der Projektdateiname, und unter **Projektordner**wird der Projektdateispeicherort angegeben.  
  
 In **Projektmappen-Explorer**, mit der rechten Maustaste die `AW Internet Sales Tabular Model` Projekt, und klicken Sie dann auf **Eigenschaften**. Das Dialogfeld für die **Eigenschaftenseiten des AW Internet Sales-Tabellenmodells** wird angezeigt. Hierbei handelt es sich um die erweiterten Projekteigenschaften. Sie werden später einige dieser Eigenschaften festlegen, wenn Sie für die Bereitstellung des Modells bereit sind.  
  
 Nun sehen wir uns die Modelleigenschaften an. Klicken Sie im **Projektmappen-Explorer**auf **Model.bim**. Im Fenster **Eigenschaften** sehen Sie jetzt die Modelleigenschaften, wobei die wichtigste Eigenschaft die Eigenschaft **DirectQuery-Modus** ist. Diese Eigenschaft gibt an, ob das Modell im InMemory-Modus (Aus) oder im DirectQuery-Modus (Ein) bereitgestellt wird. In diesem Lernprogramm wird das Modell im InMemory-Modus erstellt und bereitgestellt.  
  
 Wenn Sie ein neues Modell erstellen, werden bestimmte Modelleigenschaften automatisch gemäß den Datenmodellierungseinstellungen festgelegt, die im Dialogfeld für Tools und Optionen angegeben werden können. Die Eigenschaften für die Datensicherung, Beibehaltung des Arbeitsbereichs und den Arbeitsbereichsserver geben an, wie und wo die Arbeitsbereichsdatenbank (Datenbank zur Modellerstellung) gesichert, speicherintern beibehalten und erstellt wird. Sie können diese Einstellungen ggf. später ändern. Lassen Sie sie jedoch vorerst unverändert.  
  
 Bei der Installation von [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] wurden der Visual Studio-Umgebung mehrere neue Menüelemente hinzugefügt. Sehen wir die neuen Menüelemente an, die für die Erstellung von Tabellenmodellen konzipiert sind. Klicken Sie auf das Menü **Modell** . Über dieses Menü können Sie den Tabellenimport-Assistenten starten, vorhandene Verbindungen anzeigen und bearbeiten, Arbeitsbereichsdaten aktualisieren, Ihr Modell in [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel mit der Funktion "In Excel analysieren" durchsuchen, Perspektiven und Rollen erstellen, die Modellsicht auswählen und Berechnungsoptionen festlegen.  
  
 Klicken Sie auf das Menü **Tabelle**. Hier können Sie Beziehungen zwischen Tabellen erstellen und verwalten, Datumstabelleneigenschaften festlegen, Partitionen erstellen und Tabelleneigenschaften bearbeiten.  
  
 Klicken Sie auf das Menü **Spalte** . Hier können Sie Spalten in einer Tabelle hinzufügen und löschen, Spalten fixieren und die Sortierreihenfolge angeben. Sie können auch die AutoSumme-Funktion verwenden, um ein Standardaggregationsmeasure für eine ausgewählte Spalte zu erstellen. Weitere Schaltflächen in der Symbolleiste bieten einen schnellen Zugriff auf häufig verwendete Funktionen und Befehle.  
  
 Erkunden Sie einige der Dialogfelder und Positionen für verschiedene Funktionen, die für die Erstellung von Tabellenmodellen konzipiert sind. Obwohl einige Elemente noch nicht aktiv sind, erhalten Sie dennoch einen Einblick in die Umgebung zur Tabellenmodellerstellung.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Wenn Sie mit diesem Tutorial fortfahren möchten, wechseln Sie zur nächsten Lektion: [Lektion 2: Hinzufügen von Daten](lesson-2-add-data.md).  
  
  