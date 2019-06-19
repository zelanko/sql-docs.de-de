---
title: Name-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::Name
- Field20::Name
helpviewer_keywords:
- Name property [ADO]
ms.assetid: cfd0e29c-8310-44ab-85c3-5761184b865d
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: e696e97de78272f9d19091c9238bc9555f949361
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66707308"
---
# <a name="name-property-ado"></a>Name-Eigenschaft (ADO)
Gibt den Namen eines Objekts.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt einen **Zeichenfolge** Wert, der den Namen eines Objekts angibt.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **Namen** Eigenschaft, um einen Namen zuweisen, oder rufen Sie den Namen des eine **Befehl**, **Eigenschaft**, **Feld**, oder **Parameter**  Objekt.  
  
 Der Wert ist Lese-/Schreibzugriff auf eine **Befehl** Objekt und Read-only auf eine **Eigenschaft** Objekt.  
  
 Für eine **Feld** Objekt **Namen** normalerweise schreibgeschützt ist. Jedoch für den neuen **Feld** Objekte, die angefügt wurden die [Felder](../../../ado/reference/ado-api/fields-collection-ado.md) Auflistung von einem [Datensatz](../../../ado/reference/ado-api/record-object-ado.md), **Namen** Lese-/Schreibzugriff wird erst nach die [Wert](../../../ado/reference/ado-api/value-property-ado.md) -Eigenschaft für die **Feld** angegeben wurde und der neue der Datenanbieter wurde erfolgreich hinzugefügt **Feld** durch Aufrufen der [ Update](../../../ado/reference/ado-api/update-method.md) Methode der **Felder** Auflistung.  
  
 Für **Parameter** Objekte noch nicht angefügt werden, um die [Parameter](../../../ado/reference/ado-api/parameters-collection-ado.md) -Auflistung, die **Namen** Eigenschaft schreibgeschützt ist. Für angefügt **Parameter** Objekte und alle anderen Objekte, die **Namen** Eigenschaft ist schreibgeschützt. Namen müssen nicht in einer Auflistung eindeutig sein.  
  
 Sie können abrufen, die **Namen** Eigenschaft eines Objekts durch einen Ordnungszahlverweis, nach dem sehen Sie sich das Objekt direkt anhand Ihres Namens. Z. B. wenn `rstMain.Properties(20).Name` ergibt `Updatability`, anschließend sehen Sie sich diese Eigenschaft als `rstMain.Properties("Updatability")`.  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[Command-Objekt (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Field-Objekt](../../../ado/reference/ado-api/field-object.md)|  
|[Parameter-Objekt](../../../ado/reference/ado-api/parameter-object.md)|[Property-Objekt (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [Attribute und Name Eigenschaften – Beispiel (VB)](../../../ado/reference/ado-api/attributes-and-name-properties-example-vb.md)   
 [Attribute und Name Eigenschaften – Beispiel (VC++)](../../../ado/reference/ado-api/attributes-and-name-properties-example-vc.md)   
