---
title: Hinzufügen von Spalten zu einer Miningstruktur | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- mining structures [Analysis Services], columns
- columns [data mining], mining structure columns
- adding columns
ms.assetid: 3f879344-9f66-4178-851a-e8c5ccccf4cb
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: a13e3216ff7d4209331fb5cbc062b62908283140
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049994"
---
# <a name="add-columns-to-a-mining-structure"></a>Hinzufügen von Spalten zu einer Miningstruktur
  Mit dem Data Mining-Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] können Sie einer Miningstruktur Spalten hinzufügen, nachdem Sie die Miningstruktur im Data Mining-Assistenten erstellt haben. Sie können jede Spalte hinzufügen, die in der zum Definieren der Miningstruktur verwendeten Datenquellensicht vorhanden ist.  
  
> [!NOTE]  
>  Sie können einer Miningstruktur mehrere Kopien von Spalten hinzufügen. Sie sollten jedoch nicht mehrere Instanzen der Spalte innerhalb desselben Modells verwenden, um falsche Korrelationen zwischen der Quelle und der abgeleiteten Spalte zu vermeiden.  
  
### <a name="to-add-a-column-to-a-mining-structure"></a>So fügen Sie einer Miningstruktur eine Spalte hinzu  
  
1.  Wählen Sie im Data Mining-Designer die Registerkarte **Miningstruktur** aus.  
  
2.  Klicken Sie mit der rechten Maustaste auf die Miningstruktur, und klicken Sie anschließend auf **Spalte hinzufügen**.  
  
     Das Dialogfeld **Spalte auswählen** wird geöffnet.  
  
3.  Wählen Sie unter **Quelltabelle**die Tabelle in der Datenquellensicht aus, in der sich die Spalte befindet.  
  
4.  Wählen Sie unter **Quellspalte**die Spalte aus, die Sie der Miningstruktur hinzufügen möchten.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
> [!NOTE]  
>  Wenn Sie eine bereits vorhandene Spalte hinzufügen, wird eine Kopie in die Struktur einbezogen, und dem Namen der Spalte wird dabei eine "1" angehängt. Sie können den Namen der kopierten Spalte in einen aussagekräftigeren Namen ändern, indem Sie einen neuen Namen in die **Name** -Eigenschaft der Miningstruktur-Spalte eingeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Tasks und Anweisungen für Miningstrukturen](mining-structure-tasks-and-how-tos.md)  
  
  