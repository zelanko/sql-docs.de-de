---
title: 'Lektion 1: Erstellen eines neuen Projekts für tabellarische Modelle | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0d2eb34d-78c8-41ff-b92d-49b62c16b2ac
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fb9ca011cdbbe32ebd6c71cb9ca64967cfbccb9e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66079308"
---
# <a name="lesson-1-create-a-new-tabular-model-project"></a>Lektion 1: Erstellen eines neuen Tabellenmodellprojekts
  In dieser Lektion erstellen Sie ein neues leeres Tabellenmodellprojekt in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Sobald das neue Projekt erstellt wird, können Sie mithilfe des Tabellenimport-Assistenten Daten hinzufügen. Zusätzlich zum Erstellen eines neuen Projekts bietet diese Lektion auch eine kurze Einführung in die Umgebung zur Tabellenmodellerstellung in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].  
  
 Weitere Informationen zu den verschiedenen Typen von Tabellenmodellprojekten finden Sie unter [Tabellenmodellprojekte &#40;SSAS – tabellarisch&#41;](tabular-models/tabular-model-projects-ssas-tabular.md). Weitere Informationen zur Umgebung für die Erstellung von tabellarischen Modellen finden Sie unter tabellarischer [Modell-Designer &#40;SSAS ](tabular-model-designer-ssas-tabular.md)-Tabellen&#41;.  
  
 Geschätzte Zeit zum Bearbeiten dieser Lektion: **10 Minuten**  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Dieses Thema stellt die erste Lektion in einem Lernprogramm zur Tabellenmodellerstellung dar. Um diese Lektion abzuschließen, benötigen Sie die auf einer SQL Server-Instanz installierte AdventureWorksDW-Datenbank. Weitere Informationen finden Sie unter [Tabellenmodellierung &#40;Adventure Works-Tutorial&#41;](tabular-modeling-adventure-works-tutorial.md).  
  
## <a name="create-a-new-tabular-model-project"></a>Erstellen eines neuen Tabellenmodellprojekts  
  
#### <a name="to-create-a-new-tabular-model-project"></a>Erstellen eines neuen tabellarischen Modellprojekts  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]auf das Menü **Datei** , auf **Neu**und dann auf **Projekt**.  
  
2.  Klicken Sie im Dialogfeld **Neues Projekt** unter **installierte Vorlagen**auf **Business Intelligence**, und klicken Sie dann auf **Analysis Services**und dann auf **Analysis Services tabellarische Projekt**.  
  
3.  Geben Sie unter Name `AW Internet Sales Tabular Model`den **Namen**ein, und geben Sie einen Speicherort für die Projektdateien an.  
  
     Standardmäßig entspricht der **Projektmappenname** dem Projektnamen; Sie können aber einen anderen Projektmappennamen erfassen.  
  
4.  Klicken Sie auf **OK**.  
  
## <a name="understanding-the-sql-server-data-tools-tabular-model-authoring-environment"></a>Einblick in die SQL Server Data Tools-Umgebung zur Tabellenmodellerstellung  
 Nachdem Sie nun ein neues Projekt für tabellarische Modelle erstellt haben, nehmen wir uns einen Moment Zeit, um die Umgebung für [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] das Erstellen von tabellarischen Modellen in (Visual Studio 2010 oder höher) zu untersuchen.  
  
 Nach der Erstellung des Projekts wird es in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]geöffnet. Ein leeres Modell wird im Modell-Designer angezeigt, und die Datei **Model.bim** wird im Fenster des **Projektmappen-Explorers** ausgewählt. Wenn Sie Daten hinzufügen, werden Tabellen und Spalten im Designer angezeigt. Wenn der Designer (das leere Fenster mit der Registerkarte Model. BIM) nicht angezeigt wird, **Solution Explorer**Doppelklicken Sie `AW Internet Sales Tabular Model`in Projektmappen-Explorer auf die Datei **Model. BIM** .  
  
 Sie können die grundlegenden Eigenschaften für das Projekt im Fenster **Eigenschaften** anzeigen. Klicken **Solution Explorer**Sie `AW Internet Sales Tabular Model`in Projektmappen-Explorer auf. Im Fenster **Eigenschaften** unter **Projektdatei**wird **AW Internet Sales Tabular Model.smproj**angezeigt. Dies ist der Projektdateiname, und unter **Projektordner**wird der Projektdateispeicherort angegeben.  
  
 Klicken Sie in **Projektmappen-Explorer**mit der rechten `AW Internet Sales Tabular Model` Maustaste auf das Projekt, und klicken Sie dann auf **Eigenschaften**. Das Dialogfeld für die **Eigenschaftenseiten des AW Internet Sales-Tabellenmodells** wird angezeigt. Hierbei handelt es sich um die erweiterten Projekteigenschaften. Sie werden später einige dieser Eigenschaften festlegen, wenn Sie für die Bereitstellung des Modells bereit sind.  
  
 Nun sehen wir uns die Modell Eigenschaften an. Klicken Sie im **Projektmappen-Explorer**auf **Model.bim**. Im Fenster **Eigenschaften** sehen Sie jetzt die Modelleigenschaften, wobei die wichtigste Eigenschaft die Eigenschaft **DirectQuery-Modus** ist. Diese Eigenschaft gibt an, ob das Modell im In-Memory-Modus (Aus) oder im DirectQuery-Modus (Ein) bereitgestellt wird. In diesem Lernprogramm wird das Modell im InMemory-Modus erstellt und bereitgestellt.  
  
 Wenn Sie ein neues Modell erstellen, werden bestimmte Modelleigenschaften automatisch gemäß den Datenmodellierungseinstellungen festgelegt, die im Dialogfeld für Tools und Optionen angegeben werden können. Die Eigenschaften für die Datensicherung, Beibehaltung des Arbeitsbereichs und den Arbeitsbereichsserver geben an, wie und wo die Arbeitsbereichsdatenbank (Datenbank zur Modellerstellung) gesichert, speicherintern beibehalten und erstellt wird. Sie können diese Einstellungen später ändern, falls erforderlich, aber vorläufig lassen Sie diese Eigenschaften bitte unverändert.  
  
 Bei der Installation von [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]wurden der Visual Studio-Umgebung mehrere neue Menüelemente hinzugefügt. Sehen wir uns die neuen Menü Elemente an, die für das Erstellen von tabellarischen Modellen spezifisch sind. Klicken Sie in das Menü **Modell**. Über dieses Menü können Sie den Tabellenimport-Assistenten starten, vorhandene Verbindungen anzeigen und bearbeiten, Arbeitsbereichsdaten aktualisieren, Ihr Modell in [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel mit der Funktion "In Excel analysieren" durchsuchen, Perspektiven und Rollen erstellen, die Modellsicht auswählen und Berechnungsoptionen festlegen.  
  
 Klicken Sie auf das Menü **Tabelle** . Hier können Sie Beziehungen zwischen Tabellen erstellen und verwalten, Datumstabelleneigenschaften festlegen, Partitionen erstellen und Tabelleneigenschaften bearbeiten.  
  
 Klicken Sie auf das Menü **Spalte** . Hier können Sie Spalten in einer Tabelle hinzufügen und löschen, Spalten fixieren und die Sortierreihenfolge angeben. Sie können auch die AutoSumme-Funktion verwenden, um ein Standardaggregationsmeasure für eine ausgewählte Spalte zu erstellen. Weitere Schaltflächen in der Symbolleiste bieten einen schnellen Zugriff auf häufig verwendete Funktionen und Befehle.  
  
 Erkunden Sie einige der Dialogfelder und Positionen für verschiedene Funktionen, die für die Erstellung von Tabellenmodellen konzipiert sind. Obwohl einige Elemente noch nicht aktiv sind, erhalten Sie dennoch einen Einblick in die Umgebung zur Tabellenmodellerstellung.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Wenn Sie mit diesem Tutorial fortfahren möchten, wechseln Sie zur nächsten Lektion: [Lektion 2: Hinzufügen von Daten](lesson-2-add-data.md).  
  
  
