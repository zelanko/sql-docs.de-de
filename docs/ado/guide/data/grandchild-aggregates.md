---
description: Untergeordnete Aggregate
title: Aggregierte untergeordnete Aggregate | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: a1ea79e0246585898f068dfb55fa2a120ea2e6b9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88453342"
---
# <a name="grandchild-aggregates"></a>Untergeordnete Aggregate
Der in einer-Klausel eines Shape-Befehls erstellten Kapitel-Spalte kann ein *Kapitel-Alias-Name* zugewiesen werden (in der Regel mit dem As-Schlüsselwort). Sie können jede Spalte in einem beliebigen Kapitel des geformten **Recordsets** mit einem voll qualifizierten Namen identifizieren, der das untergeordnete Element identifiziert, das die Spalte enthält. Wenn das übergeordnete Kapitel chap1 beispielsweise ein untergeordnetes Kapitel chap2 enthält, das eine Spalte Amount (Amt) aufweist, lautet der qualifizierte Name chap1. chap2. Amt. Der qualifizierte Name kann dann als Argument für eine der Aggregatfunktionen (Sum, AVG, Max, min, count, StDev oder any) verwendet werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenstrukturierung – Beispiel](../../../ado/guide/data/data-shaping-example.md)
