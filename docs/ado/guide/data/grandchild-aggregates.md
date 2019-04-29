---
title: Untergeordnete Aggregate | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- grandchild aggregates [ADO]
- data shaping [ADO], grandchild aggregates
ms.assetid: 4162d35f-2ce1-4218-80a5-b6933348837e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f1bff3c8a155e1e9378acbb659f00817f478382e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63161607"
---
# <a name="grandchild-aggregates"></a>Untergeordnete Aggregate
In einer Klausel ein Shape-Befehl erstellte Kapitelspalte zugewiesen werden kann eine *Kapitel-Aliasnamen* (in der Regel mit dem AS-Schlüsselwort). Sie können eine beliebige Spalte in den Kapiteln des der geformten identifizieren **Recordset** mit einem vollständig qualifizierten Namen, der das untergeordnete Element mit der Spalte identifiziert. Angenommen, wenn das übergeordnete Kapitel Kap1, untergeordnete Kapitel chap2, enthält, die eine Mengenspalte "Amt" hat und dann der qualifizierte Name wäre chap1.chap2.amt. Der qualifizierte Name kann dann als Argument für einen der Aggregatfunktionen (SUM, AVG, MAX, MIN, COUNT, STDEV oder alle) verwendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Data Shaping Example (Beispiele der Datenstrukturierung)](../../../ado/guide/data/data-shaping-example.md)
