---
title: Abfrage Bindungs Detail (Dialog Feld ' Partitions Quelle ') (Analysis Services-Mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.partitions.partitionfilterexpression.f1
ms.assetid: 697874d4-3f7a-4126-96f5-37cc8e2ee306
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 604a42cc0b3519f1034733e12f72dc1a7c969ce6
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66070565"
---
# <a name="query-binding-detail-partition-source-dialog-box-analysis-services---multidimensional-data"></a>Abfragebindungsdetail (Dialogfeld 'Partitionsquelle') (Analysis Services – Mehrdimensionale Daten)
  Mithilfe der Option **Abfragebindung** im Dialogfeld **Partitionsquelle** können Sie die Abfrage angeben, die die Daten für die Partition bereitstellt. Sie können dieses Fenster anzeigen, indem Sie im Dialogfeld **Partitionsquelle** unter der Option **Bindungstyp****Abfragebindung** auswählen.  
  
## <a name="options"></a>Optionen  
 **Datenquelle**  
 Wählen Sie die Datenquelle aus, für die die Abfrage ausgeführt wird, um Daten für die Partition bereit zu stellen.  
  
 **Abfrage**  
 Geben Sie die SQL-Anweisung ein, die während der Verarbeitung der Partition zum Abrufen von Faktendaten verwendet wird, oder ändern Sie diese.  
  
> [!IMPORTANT]  
>  Wenn Sie eine WHERE-Klausel angeben, kann für diese Partition eine Teilmenge von Datensätzen verwendet werden. Dies ist von wesentlicher Bedeutung, um das Duplizieren von Daten zu verhindern, wenn mehrere Partitionen auf einer einzigen Faktentabelle basieren. Weitere Informationen finden Sie unter [Partition Source Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](partition-source-dialog-box-analysis-services-multidimensional-data.md).  
  
 **Kontroll**  
 Klicken Sie auf diese Option, um zu überprüfen, dass es sich bei der Anweisung in **Abfrage** um eine gültige SQL-Anweisung handelt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dialog Feld ' Partitions Quelle ' &#40;Analysis Services Mehrdimensionale Daten&#41;](partition-source-dialog-box-analysis-services-multidimensional-data.md)  
  
  
