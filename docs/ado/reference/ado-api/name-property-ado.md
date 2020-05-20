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
author: rothja
ms.author: jroth
ms.openlocfilehash: 38846bcb832df7cc535d35d8f07fb636f2db37f7
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82762421"
---
# <a name="name-property-ado"></a>Name-Eigenschaft (ADO)
Gibt den Namen eines Objekts an.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen **Zeichen** folgen Wert fest, der den Namen eines Objekts angibt, oder gibt ihn zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **Name** -Eigenschaft, um einen Namen zu zuweisen oder den Namen eines **Befehls**, einer **Eigenschaft**, eines **Felds**oder eines **Parameter** Objekts abzurufen.  
  
 Der Wert ist Lese-/Schreibzugriff auf ein **Befehls** Objekt und schreibgeschützt für ein **Eigenschafts** Objekt.  
  
 Für ein **Feld** Objekt ist **Name** normalerweise schreibgeschützt. Bei neuen **Feld** Objekten, die an die [Fields](../../../ado/reference/ado-api/fields-collection-ado.md) -Auflistung eines [Datensatzes](../../../ado/reference/ado-api/record-object-ado.md)angefügt wurden, ist der **Name** jedoch nur dann Lese-/Schreibzugriff, nachdem die [value](../../../ado/reference/ado-api/value-property-ado.md) -Eigenschaft für das **Feld** angegeben wurde und der Datenanbieter das neue **Feld** durch Aufrufen der [Update](../../../ado/reference/ado-api/update-method.md) -Methode der **Fields** -Auflistung erfolgreich hinzugefügt hat.  
  
 Für **Parameter** Objekte, die noch nicht an die [Parameter](../../../ado/reference/ado-api/parameters-collection-ado.md) Auflistung angefügt wurden, ist die **Name** -Eigenschaft Lese-/Schreibzugriff. Für angefügte **Parameter** Objekte und alle anderen Objekte ist die **Name** -Eigenschaft schreibgeschützt. Namen müssen innerhalb einer Sammlung nicht eindeutig sein.  
  
 Sie können die **Name** -Eigenschaft eines Objekts durch einen Ordinalverweis abrufen, nach dem Sie direkt auf das Objekt über den Namen verweisen können. Wenn z. b `rstMain.Properties(20).Name` `Updatability` . ergibt, können Sie anschließend auf diese Eigenschaft als verweisen `rstMain.Properties("Updatability")` .  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[Command-Objekt (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Field-Objekt](../../../ado/reference/ado-api/field-object.md)|  
|[Parameter-Objekt](../../../ado/reference/ado-api/parameter-object.md)|[Property-Objekt (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Attribute und namens Eigenschaften (VB)](../../../ado/reference/ado-api/attributes-and-name-properties-example-vb.md)   
 [Beispiel für Attribute und namens Eigenschaften (VC + +)](../../../ado/reference/ado-api/attributes-and-name-properties-example-vc.md)   
