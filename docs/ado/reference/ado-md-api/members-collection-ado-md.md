---
title: Members-Auflistung (ADO MD) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Level::Members
- Members
- Position::Members
helpviewer_keywords:
- Members collection [ADO MD]
ms.assetid: 3a647cde-efdc-4394-b1b9-8cbb1b9d689f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 541e1098dfd18210e7c07a0718ecd3add758c8a4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47616948"
---
# <a name="members-collection-ado-md"></a>Members-Collection (ADO MD)
Enthält die [Member](../../../ado/reference/ado-md-api/member-object-ado-md.md) Objekte aus einer Ebene oder eine Position auf einer Achse.  
  
## <a name="remarks"></a>Hinweise  
 Ein **Mitglieder** Sammlung wird verwendet, um die folgenden Arten von Elementen enthalten:  
  
-   Die Elemente, aus denen eine Ebene in einem Cube besteht. Diese befinden sich die **Mitglieder** Auflistung von einem [Ebene](../../../ado/reference/ado-md-api/level-object-ado-md.md) Objekt. Verwenden Sie beispielsweise aus das Beispiel [Übersicht über multidimensionale Schemas und Daten](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md), sind die vier Elemente der Ebene Ländern, Kanada, USA, Vereinigtes Königreich und Deutschland.  
  
-   Die Elemente, die die untergeordneten Elemente eines bestimmten Elements innerhalb einer Hierarchie sind. Diese Elemente werden zurückgegeben, durch die [untergeordneten](../../../ado/reference/ado-md-api/children-property-ado-md.md) Eigenschaft des übergeordneten Elements **Member** Objekt. Beispielsweise sind die erneut mit dem gleichen Beispiel an, die beiden untergeordneten Elemente dem Kanada-Element, Kanada-Ostküste und Kanada-West.  
  
-   Die Elemente, die eine bestimmte Position auf einer Achse der definieren eine [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md). Mit dem Cellset aus [arbeiten mit mehrdimensionalen Daten](../../../ado/guide/multidimensional/working-with-multidimensional-data.md) als Beispiel sind die beiden Elemente der ersten Position auf der x-Achse Valentine und Seattle. Diese Elemente enthalten sind die **Mitglieder** Auflistung von einem [Position](../../../ado/reference/ado-md-api/position-object-ado-md.md) Objekt.  
  
 **Mitglieder** ist eine standard-ADO-Auflistung. Mit den Eigenschaften und Methoden einer Sammlung können Sie Folgendes tun:  
  
-   Erhalten Sie die Anzahl der Objekte in der Auflistung mit den [Anzahl](../../../ado/reference/ado-api/count-property-ado.md) Eigenschaft.  
  
-   Geben Sie ein Objekt zurück, aus der Auflistung mit der standardmäßigen [Element](../../../ado/reference/ado-api/item-property-ado.md) Eigenschaft.  
  
-   Aktualisieren Sie die Objekte in der Auflistung über den Anbieter mit der [aktualisieren](../../../ado/reference/ado-api/refresh-method-ado.md) Methode.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Eigenschaften, Methoden und Ereignisse](../../../ado/reference/ado-md-api/members-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Member-Beispiel (VBScript)](../../../ado/reference/ado-md-api/members-example-vbscript.md)   
 [Member-Objekt (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)
