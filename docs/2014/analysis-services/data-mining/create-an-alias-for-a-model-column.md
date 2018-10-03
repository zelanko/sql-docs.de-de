---
title: Erstellen eines Alias für eine Modellspalte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], how-to topics
- mining models [Analysis Services], columns
- column names [Analysis Services]
ms.assetid: c80ebe66-a8f8-4f24-9fe8-8288de9d13bc
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ae3e9f2d0ecf1a5a4fe41f053d8c6cc582663857
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48148760"
---
# <a name="create-an-alias-for-a-model-column"></a>Erstellen eines Alias für eine Modellspalte
  In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]können Sie einen Alias für eine Modellspalte erstellen. Dies kann hilfreich sein, wenn der Miningstrukturname zu lang ist, um mühelos damit zu arbeiten, oder wenn Sie der Spalte einen aussagekräftigeren Namen im Hinblick auf Inhalt oder Verwendung im Modell geben möchten. Beispiel: wenn Sie eine Kopie einer Strukturspalte erstellen und die Spalte dann für ein bestimmtes Modell unterschiedlich diskretisieren, können Sie die Spalte umbenennen, um den Inhalt genauer anzugeben.  
  
 Zum Erstellen eines Alias für eine Modellspalte verwenden Sie den Bereich **Eigenschaften** und legen [Name](../scripting/properties/name-element-assl.md) -Eigenschaft der Spalte fest.  
  
 Auf der Registerkarte **Miningmodelle** im Data Mining Designer wird der Alias in Klammern neben der Beschriftung zur Spaltenverwendung angezeigt.  
  
 Informationen zum Festlegen der Eigenschaften eines Miningmodells finden Sie unter [Miningmodellspalten](mining-model-columns.md).  
  
### <a name="to-add-an-alias-to-a-mining-model-column"></a>So fügen Sie einen Alias einer Miningmodellspalte hinzu  
  
1.  Klicken Sie im Data Mining Designer auf der Registerkarte **Miningmodelle** mit der rechten Maustaste auf die Zelle im Miningmodell für die Miningspalte, die Sie ändern möchten, und wählen Sie dann **Eigenschaften**aus.  
  
2.  Klicken Sie anschließend im Fenster **Eigenschaften** auf der rechten Seite des Fensters auf die Zelle neben der Name-Eigenschaft, und löschen Sie den aktuellen Wert. Geben Sie einen neuen Namen für die Spalte ein.  
  
## <a name="see-also"></a>Siehe auch  
 [Miningmodelltasks und Anweisungen Mining](mining-model-tasks-and-how-tos.md)   
 [Miningmodelleigenschaften](mining-model-properties.md)  
  
  
