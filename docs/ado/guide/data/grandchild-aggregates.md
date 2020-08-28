---
description: Untergeordnete Aggregate
title: Aggregierte untergeordnete Aggregate | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- grandchild aggregates [ADO]
- data shaping [ADO], grandchild aggregates
ms.assetid: 4162d35f-2ce1-4218-80a5-b6933348837e
author: rothja
ms.author: jroth
ms.openlocfilehash: 02d481e55fa8fc41e022d41b88c9dcd6c4777dfe
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88980711"
---
# <a name="grandchild-aggregates"></a>Untergeordnete Aggregate
Der in einer-Klausel eines Shape-Befehls erstellten Kapitel-Spalte kann ein *Kapitel-Alias-Name* zugewiesen werden (in der Regel mit dem As-Schlüsselwort). Sie können jede Spalte in einem beliebigen Kapitel des geformten **Recordsets** mit einem voll qualifizierten Namen identifizieren, der das untergeordnete Element identifiziert, das die Spalte enthält. Wenn das übergeordnete Kapitel chap1 beispielsweise ein untergeordnetes Kapitel chap2 enthält, das eine Spalte Amount (Amt) aufweist, lautet der qualifizierte Name chap1. chap2. Amt. Der qualifizierte Name kann dann als Argument für eine der Aggregatfunktionen (Sum, AVG, Max, min, count, StDev oder any) verwendet werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenstrukturierung – Beispiel](./data-shaping-example.md)