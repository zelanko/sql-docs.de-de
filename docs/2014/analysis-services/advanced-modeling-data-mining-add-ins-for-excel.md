---
title: Erweiterte Modellierung (Data Mining-Add-Ins für Excel) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures, creating
ms.assetid: 042270a3-6ec7-4b52-b2ba-2adb6c4740d5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 669fa1fcd9e4802a4d4102120a373dd615741017
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66062735"
---
# <a name="advanced-modeling-data-mining-add-ins-for-excel"></a>Erweiterte Modellierung (Data Mining-Add-Ins für Excel)
  Mithilfe der **erweiterten** Optionen für die Datenmodellierung können Sie benutzerdefinierte Data Mining Strukturen und Modelle mit Parametern erstellen, die sich von den von den Assistenten erstellten Parametern unterscheiden. Mit den beiden in diesem Abschnitt beschriebenen Assistenten können Sie eine völlig neue Data Mining-Struktur und ein neues Miningmodell erstellen, das auf eine vorhandene Data Mining-Struktur angewendet wird.  
  
## <a name="create-mining-structure"></a>Erstellen einer Miningstruktur  
 ![Miningstruktur erstellen (Schaltfläche auf Data Mining-Menüband)](media/dmc-createstruct.gif "Miningstruktur erstellen (Schaltfläche auf Data Mining-Menüband)")  
  
 Der **Assistent zum Erstellen von Mining Strukturen** unterstützt Sie beim Erstellen einer neuen Data Mining Struktur. Eine Struktur ist eine Sammlung von Daten, die aus einer bestimmten Datenquelle extrahiert wurden.  Eine Miningstruktur kann anhand neuer Daten aus der Quelle aktualisiert werden; beim Erstellen der Miningstruktur definieren Sie jedoch Datentypen und Namen, die festlegen, wie die Daten zu Analysezwecken verwendet werden.  
  
 Zum Erstellen der Struktur können Sie die folgenden Datenquellen verwenden: eine Excel-Tabelle, einen Excel-Bereich oder Daten aus einer externen Datenquelle, die bereits als [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Datenquellensicht definiert wurden.  
  
 Für jede Struktur können Sie einige Daten bestimmen, die zum Testen und Überprüfen verwendet werden sollen. Wenn Sie dieses Dataset für zurück *gehaltene Daten erstellen* , wenn Sie Ihre Datenquellen einrichten, können Sie sicherstellen, dass alle Modelle, die auf der Struktur basieren, ein konsistentes DataSet zum Testen verwenden können.  
  
 Nachdem Sie eine Miningstruktur erstellt haben, können Sie mehrere Modelle hinzufügen, um verschiedene Analysemethoden anzuwenden.  
  
 Weitere Informationen zur Verwendung des **Assistenten zum Erstellen von Mining Strukturen**finden Sie unter [Erstellen einer Mining Struktur &#40;SQL Server Data Mining-Add-ins&#41;](create-mining-structure-sql-server-data-mining-add-ins.md).  
  
## <a name="add-model-to-structure"></a>Hinzufügen eines Modells zu einer Struktur  
 ![Schaltfläche "Modell einer Struktur hinzufügen"](media/dmc-addmodel.gif "Schaltfläche "Modell einer Struktur hinzufügen"")  
  
 Wenn Sie einer Struktur ein neues Modell hinzufügen, analysieren Sie die Daten mithilfe eines anderen Algorithmus oder mit anderen Parametern. Diese Option ist insbesondere dann hilfreich, wenn Sie ein Modell mithilfe eines der Algorithmen erstellen möchten, die nicht über Tools des Data Mining-Clients verfügbar gemacht werden.  
  
 Beispielsweise können Sie einen beliebigen, von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]unterstützten Algorithmus verwenden, z. B.:  
  
-   Lineare Regression  
  
-   Sequenzclustering  
  
-   Zuordnungsanalyse für geschachtelte Datasets  
  
 Um zu sehen, welche Art von Mining Strukturen verfügbar ist, können Sie die in gespeicherten Modelle und [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Strukturen durchsuchen, indem Sie entweder auf **Modelle verwalten** oder auf **Durchsuchen**klicken.  
  
 Dabei sind Sie auf die Data Mining-Strukturen beschränkt, die während der aktuellen Sitzung erstellt wurden, bzw. die Miningstrukturen, die in einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] gespeichert wurden.  
  
 Weitere Informationen finden Sie unter [Hinzufügen eines Modells zu einer Struktur &#40;Data Mining-Add-Ins für Excel&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten von Modellen &#40;SQL Server Data Mining-Add-ins&#41;](manage-models-sql-server-data-mining-add-ins.md)   
 [Durchsuchen von Modellen in Excel &#40;SQL Server Data Mining-Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
