---
title: Open-Methode (ADO MD) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Open
- Cellset::Open
helpviewer_keywords:
- Open method [ADO MD]
ms.assetid: a87d8080-a238-45e5-bc80-9a8625b3810f
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 49d811ed0eb60bb02767579c604a6a4be3c5b337
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2018
ms.locfileid: "38982632"
---
# <a name="open-method-ado-md"></a>Open Sie-Methode (ADO MD)
Ruft die Ergebnisse von einer mehrdimensionalen Abfrage ab und gibt die Ergebnisse in einem [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Cellset.Open Source, ActiveConnection  
```  
  
#### <a name="parameters"></a>Parameter  
 *Quelle*  
 Optional. Ein **Variant** , die an einen gültigen MDX-Abfrage, z. B. eine Abfrage (Multidimensional Expressions) ausgewertet wird. Die *Quelle* Argument entspricht der [Quelle](../../../ado/reference/ado-md-api/source-property-ado-md.md) Eigenschaft. Weitere Informationen zu MDX finden Sie unter den [OLE DB für Online Analytical Processing (OLAP)](http://msdn.microsoft.com/8a7673c6-3ca1-4411-9f1e-adf1e47df4f3) Dokumentation in der Microsoft Data Access Components SDK.  
  
 *ActiveConnection*  
 Optional. Ein **Variant** , ausgewertet wird, in eine Zeichenfolge, die dabei wird entweder ein gültige ADO [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) Objekt Variablenname oder eine Definition für eine Verbindung. Die *ActiveConnection* Argument gibt an, die Verbindung für das Öffnen der [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) Objekt. Wenn Sie eine Definition der Serververbindung für dieses Argument übergeben, wird von ADO mit den angegebenen Parametern eine neue Verbindung geöffnet. Die *ActiveConnection* Argument entspricht der [ActiveConnection](../../../ado/reference/ado-md-api/activeconnection-property-ado-md.md) Eigenschaft.  
  
## <a name="remarks"></a>Hinweise  
 Die **öffnen** Methode wird ein Fehler generiert, wenn einer der Parameter ausgelassen wird und der entsprechenden Eigenschaftswert nicht festgelegt wurde vor dem Öffnen der **Cellset**.  
  
## <a name="applies-to"></a>Gilt für  
 [Cellset-Objekt (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Cellset-Beispiel (VB)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [ActiveConnection-Eigenschaft (ADO MD)](../../../ado/reference/ado-md-api/activeconnection-property-ado-md.md)   
 [Close-Methode (ADO MD)](../../../ado/reference/ado-md-api/close-method-ado-md.md)   
 [Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Source-Eigenschaft (ADO MD)](../../../ado/reference/ado-md-api/source-property-ado-md.md)   
 [State-Eigenschaft (ADO MD)](../../../ado/reference/ado-md-api/state-property-ado-md.md)
