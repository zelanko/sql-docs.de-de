---
title: Hinzufügen von Spalten zu einer Miningstruktur | Microsoft-Dokumentation
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4c09d4b263dc4e4274888f6cbd8bf1f27103dd8b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68210217"
---
# <a name="add-columns-to-a-mining-structure"></a>Hinzufügen von Spalten zu einer Miningstruktur
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
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
 [Tasks und Anweisungen für Miningstrukturen](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)  
  
  
