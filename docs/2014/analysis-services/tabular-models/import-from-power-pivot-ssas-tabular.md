---
title: Importieren aus PowerPivot (SSAS – tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.importfromppt.f1
ms.assetid: ac1a6a79-bda3-4122-a717-8b1e2f77da02
caps.latest.revision: 23
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3f6480cf0b577a0faa48691a85248efb77a84531
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37245740"
---
# <a name="import-from-powerpivot-ssas-tabular"></a>Importieren aus PowerPivot (SSAS – tabellarisch)
  In diesem Thema wird beschrieben, wie So erstellen Sie ein neues tabellarisches Modellprojekt Importieren von Metadaten und Daten aus einer PowerPivot-Arbeitsmappe mit dem Import aus PowerPivot-Projektvorlage in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
## <a name="create-a-new-tabular-model-from-a-powerpivot-for-excel-file"></a>Erstellen eines neuen tabellarischen Modells aus einer PowerPivot für Excel-Datei  
 Wenn Sie ein neues Projekt für tabellarische Modelle erstellen, indem Sie Daten aus einer PowerPivot-Arbeitsmappe importieren, werden die Metadaten zur Definition der Arbeitsmappenstruktur verwendet, um die Struktur des tabellarischen Modellprojekts in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] zu erstellen und zu definieren. Objekte, wie Tabellen, Spalten, Measures und Beziehungen werden beibehalten und im tabellarischen Modellprojekt genauso dargestellt wie in der PowerPivot-Arbeitsmappe. An der XLSX-Arbeitsmappendatei werden keine Änderungen vorgenommen.  
  
> [!NOTE]  
>  Verknüpfte Tabellen werden in tabellarischen Modellen nicht unterstützt. Wenn Daten aus einer PowerPivot-Arbeitsmappe importiert werden, die eine verknüpfte Tabelle enthält, werden die Daten der verknüpften Tabelle wie kopierte/eingefügte Daten behandelt und in der Datei Model.bim gespeichert. Wenn Sie Eigenschaften für eine kopierte/eingefügte Tabelle anzeigen, sind die Eigenschaft **Quelldaten** und das Dialogfeld **Tabelleneigenschaften** im Menü **Tabelle** deaktiviert.  
>   
>  Die Anzahl der Zeilen, die den im Modell eingebetteten Daten hinzugefügt werden können, ist auf 10.000 Zeilen beschränkt. Wenn Sie ein Modell aus PowerPivot importieren und der Fehler "Daten wurden abgeschnitten. Eingefügte Tabellen dürfen nicht mehr als 10000 Zeilen umfassen" angezeigt wird, überprüfen Sie das PowerPivot-Modell, indem Sie die eingebetteten Daten in eine andere Datenquelle, beispielsweise eine Tabelle in SQL Server, verschieben und einen Neuimport ausführen.  
  
 Abhängig davon, ob die Arbeitsbereichsdatenbank auf einer Analysis Services-Instanz auf demselben Computer (lokal) wie [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] oder auf einer Analysis Services-Remoteinstanz gespeichert ist, müssen bestimmte Punkte berücksichtigt werden.  
  
 Wenn die Arbeitsbereichsdatenbank auf einer lokalen Instanz von Analysis Services gespeichert ist, können Sie sowohl die Metadaten als auch die Daten aus der PowerPivot-Arbeitsmappe importieren. Die Metadaten werden aus der Arbeitsmappe kopiert und zum Erstellen des tabellarischen Modellprojekts verwendet. Anschließend werden die Daten aus der Arbeitsmappe kopiert und in der Arbeitsbereichsdatenbank des Projekts gespeichert (mit Ausnahme von kopierten/eingefügten Daten, die in der Datei Model.bim gespeichert werden).  
  
 Wenn die Arbeitsbereichsdatenbank auf einer Analysis Services-Remoteinstanz gespeichert ist, können Sie keine Daten aus einer PowerPivot für Excel-Arbeitsmappe importieren. Sie können jedoch die Metadaten der Arbeitsmappe importieren. Zu diesem Zweck wird ein Skript auf der Analysis Services-Remoteinstanz ausgeführt. Sie sollten nur Metadaten aus einer vertrauenswürdigen PowerPivot-Arbeitsmappe importieren. Die Daten müssen aus den in den Datenquellenverbindungen definierten Quellen importiert werden. Kopierte/eingefügte Daten und Daten aus verknüpften Tabellen in der PowerPivot-Arbeitsmappe müssen kopiert und in das tabellarische Modellprojekt eingefügt werden.  
  
#### <a name="to-create-a-new-tabular-model-project-from-a-powerpivot-for-excel-file"></a>Um ein neues tabellarisches Modellprojekt aus einer PowerPivot für Excel-Datei zu erstellen.  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]auf das Menü **Datei** , auf **Neu**und dann auf **Projekt**.  
  
2.  In der **neues Projekt** Dialogfeld **installierte Vorlagen**, klicken Sie auf **Business Intelligence**, und klicken Sie dann auf **importieren aus PowerPivot**.  
  
3.  Geben Sie unter  **Name**einen Namen für das Projekt ein. Geben Sie dann einen Speicherort und einen Projektmappennamen an, und klicken Sie auf **OK**.  
  
4.  Wählen Sie im Dialogfeld **Öffnen** die [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] -Datei aus, die die zu importierenden Modellmetadaten und -daten enthält, und klicken Sie dann auf **Öffnen**.  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeitsbereichsdatenbank &#40;SSAS – tabellarisch&#41;](workspace-database-ssas-tabular.md)   
 [Kopieren und Einfügen von Daten &#40;SSAS – tabellarisch&#41;](../copy-and-paste-data-ssas-tabular.md)  
  
  
