---
title: Close-Methode (ADO MD) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Close
- Cellset::Close
helpviewer_keywords:
- Close method [ADO MD]
ms.assetid: a3aa594d-f9d4-4654-8625-ec20153ff5d9
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 4f01845752c0ee1f9187ea3d209a97509f87a5a9
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66709575"
---
# <a name="close-method-ado-md"></a>Close-Methode (ADO MD)
Schließt einen geöffneten Cellset.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Cellset.Close  
```  
  
## <a name="remarks"></a>Hinweise  
 Mithilfe der **schließen** Methode zum Schließen einer [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) Freigeben des Objekts werden die zugehörigen Daten, einschließlich der Daten in allen verknüpften [Zelle](../../../ado/reference/ado-md-api/cell-object-ado-md.md), [Achse](../../../ado/reference/ado-md-api/axis-object-ado-md.md), [Position](../../../ado/reference/ado-md-api/position-object-ado-md.md), oder [Member](../../../ado/reference/ado-md-api/member-object-ado-md.md) Objekte. Schließen einer **Cellset** wird nicht aus dem Arbeitsspeicher entfernt Sie die Einstellungen ändern und öffnen sie es später noch mal. Um ein Objekt vom Arbeitsspeicher vollständig zu vermeiden, legen Sie die Objektvariable auf **nichts**.  
  
 Sie können später aufrufen, die [öffnen](../../../ado/reference/ado-md-api/open-method-ado-md.md) Methode, um erneut zu öffnen der **Cellset** über das gleiche oder eine andere Datenquelle Zeichenfolge. Während der **Cellset** -Objekt geschlossen ist, Abrufen von Eigenschaften oder durch Aufrufen von Methoden, die auf die zugrunde liegenden Daten verweisen oder Metadaten wird ein Fehler generiert.  
  
## <a name="applies-to"></a>Gilt für  
 [Cellset-Objekt (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Axis-Objekt (ADO MD)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)   
 [Cell-Objekt (ADO MD)](../../../ado/reference/ado-md-api/cell-object-ado-md.md)   
 [Member-Objekt (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)   
 [Open Sie-Methode (ADO MD)](../../../ado/reference/ado-md-api/open-method-ado-md.md)   
 [Position-Objekt (ADO MD)](../../../ado/reference/ado-md-api/position-object-ado-md.md)   
 [State-Eigenschaft (ADO MD)](../../../ado/reference/ado-md-api/state-property-ado-md.md)
