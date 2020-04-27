---
title: Aus Power Pivot importieren (SSAS-tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.importfromppt.f1
ms.assetid: ac1a6a79-bda3-4122-a717-8b1e2f77da02
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 941155a5e434457cdf9c79bd25c653c7207937a9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66067018"
---
# <a name="import-from-powerpivot-ssas-tabular"></a>Aus Power Pivot importieren (SSAS-tabellarisch)
  In diesem Thema wird beschrieben, wie Sie ein neues Projekt für tabellarische Modelle erstellen, indem Sie die Metadaten und Daten aus einer Power Pivot-Arbeitsmappe mithilfe der Projekt [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]Vorlage aus Power Pivot importieren in importieren.  
  
## <a name="create-a-new-tabular-model-from-a-powerpivot-for-excel-file"></a>Erstellen eines neuen tabellarischen Modells aus einer PowerPivot für Excel-Datei  
 Wenn Sie ein neues Projekt für tabellarische Modelle erstellen, indem Sie Daten aus einer PowerPivot-Arbeitsmappe importieren, werden die Metadaten zur Definition der Arbeitsmappenstruktur verwendet, um die Struktur des tabellarischen Modellprojekts in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] zu erstellen und zu definieren. Objekte, wie Tabellen, Spalten, Measures und Beziehungen werden beibehalten und im tabellarischen Modellprojekt genauso dargestellt wie in der PowerPivot-Arbeitsmappe. An der XLSX-Arbeitsmappendatei werden keine Änderungen vorgenommen.  
  
> [!NOTE]  
>  Verknüpfte Tabellen werden in tabellarischen Modellen nicht unterstützt. Wenn Daten aus einer PowerPivot-Arbeitsmappe importiert werden, die eine verknüpfte Tabelle enthält, werden die Daten der verknüpften Tabelle wie kopierte/eingefügte Daten behandelt und in der Datei Model.bim gespeichert. Wenn Sie Eigenschaften für eine kopierte/eingefügte Tabelle anzeigen, sind die Eigenschaft **Quelldaten** und das Dialogfeld **Tabelleneigenschaften** im Menü **Tabelle** deaktiviert.  
>   
>  Die Anzahl der Zeilen, die den im Modell eingebetteten Daten hinzugefügt werden können, ist auf 10.000 Zeilen beschränkt. Wenn Sie ein Modell aus Power Pivot importieren und der Fehler "Daten wurden abgeschnitten" angezeigt. Eingefügte Tabellen dürfen nicht mehr als 10000 Zeilen enthalten. "Sie sollten das Power Pivot-Modell überarbeiten, indem Sie die eingebetteten Daten in eine andere Datenquelle verschieben, z. b. eine Tabelle in SQL Server und dann erneut importieren.  
  
 Abhängig davon, ob die Arbeitsbereichsdatenbank auf einer Analysis Services-Instanz auf demselben Computer (lokal) wie [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] oder auf einer Analysis Services-Remoteinstanz gespeichert ist, müssen bestimmte Punkte berücksichtigt werden.  
  
 Wenn die Arbeitsbereichsdatenbank auf einer lokalen Instanz von Analysis Services gespeichert ist, können Sie sowohl die Metadaten als auch die Daten aus der PowerPivot-Arbeitsmappe importieren. Die Metadaten werden aus der Arbeitsmappe kopiert und zum Erstellen des tabellarischen Modellprojekts verwendet. Anschließend werden die Daten aus der Arbeitsmappe kopiert und in der Arbeitsbereichs Datenbank des Projekts gespeichert (mit Ausnahme von kopierten/eingefügten Daten, die in der Datei Model. BIM gespeichert sind).  
  
 Wenn die Arbeitsbereichsdatenbank auf einer Analysis Services-Remoteinstanz gespeichert ist, können Sie keine Daten aus einer PowerPivot für Excel-Arbeitsmappe importieren. Sie können jedoch die Metadaten der Arbeitsmappe importieren. Zu diesem Zweck wird ein Skript auf der Analysis Services-Remoteinstanz ausgeführt. Sie sollten nur Metadaten aus einer vertrauenswürdigen PowerPivot-Arbeitsmappe importieren. Die Daten müssen aus den in den Datenquellenverbindungen definierten Quellen importiert werden. Kopierte/eingefügte Daten und Daten aus verknüpften Tabellen in der PowerPivot-Arbeitsmappe müssen kopiert und in das tabellarische Modellprojekt eingefügt werden.  
  
#### <a name="to-create-a-new-tabular-model-project-from-a-powerpivot-for-excel-file"></a>So erstellen Sie ein neues tabellarisches Modellprojekt aus einer Power Pivot für Excel-Datei  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]auf das Menü **Datei** , auf **Neu**und dann auf **Projekt**.  
  
2.  Klicken Sie im Dialogfeld **Neues Projekt** unter **installierte Vorlagen**auf **Business Intelligence**, und klicken Sie dann auf **aus Power Pivot importieren**.  
  
3.  Geben Sie unter  **Name**einen Namen für das Projekt ein. Geben Sie dann einen Speicherort und einen Projektmappennamen an, und klicken Sie auf **OK**.  
  
4.  Wählen Sie im Dialogfeld **Öffnen** die [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] -Datei aus, die die zu importierenden Modellmetadaten und -daten enthält, und klicken Sie dann auf **Öffnen**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Arbeitsbereichs Datenbank &#40;tabellarischen SSAS-&#41;](workspace-database-ssas-tabular.md)   
 [Kopieren und Einfügen von Daten &#40;SSAS – tabellarisch&#41;](../copy-and-paste-data-ssas-tabular.md)  
  
  
