---
title: Erweiterte Modellierung (Data Mining-Add-ins für Excel) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- mining structures, creating
ms.assetid: 042270a3-6ec7-4b52-b2ba-2adb6c4740d5
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: de7eea9099b458a9f16e6928c1535dc4a03eb81a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049598"
---
# <a name="advanced-modeling-data-mining-add-ins-for-excel"></a>Erweiterte Modellierung (Data Mining-Add-Ins für Excel)
  Sie können die **erweitert** datenmodellierungsoptionen benutzerdefinierten Datamining-Strukturen und-Modelle mit Parametern sich von denen von den Assistenten erstellten erstellen. Mit den beiden in diesem Abschnitt beschriebenen Assistenten können Sie eine völlig neue Data Mining-Struktur und ein neues Miningmodell erstellen, das auf eine vorhandene Data Mining-Struktur angewendet wird.  
  
## <a name="create-mining-structure"></a>Miningstruktur erstellen  
 ![Miningstruktur-Schaltfläche "erstellen", Data Mining-Menüband](media/dmc-createstruct.gif "Create Mining Structure-Schaltfläche, Data Mining-Menüband")  
  
 Die **Strukturerstellungs-Assistenten** hilft, die Sie erstellen eine neue Datamining-Struktur. Eine Struktur ist eine Sammlung von Daten, die aus einer bestimmten Datenquelle extrahiert wurden.  Eine Miningstruktur kann anhand neuer Daten aus der Quelle aktualisiert werden; beim Erstellen der Miningstruktur definieren Sie jedoch Datentypen und Namen, die festlegen, wie die Daten zu Analysezwecken verwendet werden.  
  
 Zum Erstellen der Struktur können Sie die folgenden Datenquellen verwenden: eine Excel-Tabelle, einen Excel-Bereich oder Daten aus einer externen Datenquelle, die bereits als [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Datenquellensicht definiert wurden.  
  
 Für jede Struktur können Sie einige Daten bestimmen, die zum Testen und Überprüfen verwendet werden sollen. Durch das Erstellen dieser *zurückhaltungsdataset* , wenn Sie Ihre Datenquellen eingerichtet haben, können Sie sicherstellen, dass alle Modelle, die abhängig von der Struktur ein konsistentes DataSet zu Testzwecken verwenden können.  
  
 Nachdem Sie eine Miningstruktur erstellt haben, können Sie mehrere Modelle hinzufügen, um verschiedene Analysemethoden anzuwenden.  
  
 Weitere Informationen zur Verwendung der **Strukturerstellungs-Assistenten**, finden Sie unter [Create Mining Structure &#40;SQL Server Data Mining-Add-ins&#41;](create-mining-structure-sql-server-data-mining-add-ins.md).  
  
## <a name="add-model-to-structure"></a>Hinzufügen eines Modells zu einer Struktur  
 ![Hinzufügen eines Modells zu Struktur Schaltfläche](media/dmc-addmodel.gif "Modell einer Struktur Schaltfläche hinzufügen")  
  
 Wenn Sie einer Struktur ein neues Modell hinzufügen, analysieren Sie die Daten mithilfe eines anderen Algorithmus oder mit anderen Parametern. Diese Option ist insbesondere dann hilfreich, wenn Sie ein Modell mithilfe eines der Algorithmen erstellen möchten, die nicht über Tools des Data Mining-Clients verfügbar gemacht werden.  
  
 Beispielsweise können Sie einen beliebigen, von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]unterstützten Algorithmus verwenden, z. B.:  
  
-   Lineare Regression  
  
-   Sequenzclustering  
  
-   Zuordnungsanalyse für geschachtelte Datasets  
  
 Um festzustellen, welche Art von Miningstrukturen sind verfügbar, Sie können zum Durchsuchen der Modelle und Strukturen, die in gespeicherten [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Optionen **Modelle verwalten** oder **Durchsuchen**.  
  
 Dabei sind Sie auf die Data Mining-Strukturen beschränkt, die während der aktuellen Sitzung erstellt wurden, bzw. die Miningstrukturen, die in einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] gespeichert wurden.  
  
 Weitere Informationen finden Sie unter [Modell einer Struktur hinzufügen &#40;Data Mining-Add-ins für Excel&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Modellen &#40;SQL Server Data Mining-Add-ins&#41;](manage-models-sql-server-data-mining-add-ins.md)   
 [Durchsuchen von Modellen in Excel &#40;SQL Server Data Mining-Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  