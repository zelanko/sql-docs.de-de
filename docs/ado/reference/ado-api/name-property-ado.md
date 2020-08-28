---
description: Name-Eigenschaft (ADO)
title: Name-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 0636b77959a003248ee798684fc74c6309145737
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88990481"
---
# <a name="name-property-ado"></a>Name-Eigenschaft (ADO)
Gibt den Namen eines Objekts an.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen **Zeichen** folgen Wert fest, der den Namen eines Objekts angibt, oder gibt ihn zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **Name** -Eigenschaft, um einen Namen zu zuweisen oder den Namen eines **Befehls**, einer **Eigenschaft**, eines **Felds**oder eines **Parameter** Objekts abzurufen.  
  
 Der Wert ist Lese-/Schreibzugriff auf ein **Befehls** Objekt und schreibgeschützt für ein **Eigenschafts** Objekt.  
  
 Für ein **Feld** Objekt ist **Name** normalerweise schreibgeschützt. Bei neuen **Feld** Objekten, die an die [Fields](./fields-collection-ado.md) -Auflistung eines [Datensatzes](./record-object-ado.md)angefügt wurden, ist der **Name** jedoch nur dann Lese-/Schreibzugriff, nachdem die [value](./value-property-ado.md) -Eigenschaft für das **Feld** angegeben wurde und der Datenanbieter das neue **Feld** durch Aufrufen der [Update](./update-method.md) -Methode der **Fields** -Auflistung erfolgreich hinzugefügt hat.  
  
 Für **Parameter** Objekte, die noch nicht an die [Parameter](./parameters-collection-ado.md) Auflistung angefügt wurden, ist die **Name** -Eigenschaft Lese-/Schreibzugriff. Für angefügte **Parameter** Objekte und alle anderen Objekte ist die **Name** -Eigenschaft schreibgeschützt. Namen müssen innerhalb einer Sammlung nicht eindeutig sein.  
  
 Sie können die **Name** -Eigenschaft eines Objekts durch einen Ordinalverweis abrufen, nach dem Sie direkt auf das Objekt über den Namen verweisen können. Wenn z. b `rstMain.Properties(20).Name` `Updatability` . ergibt, können Sie anschließend auf diese Eigenschaft als verweisen `rstMain.Properties("Updatability")` .  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [Command-Objekt (ADO)](./command-object-ado.md)  
        [Field-Objekt](./field-object.md)  
    :::column-end:::
    :::column:::
        [Parameter-Objekt](./parameter-object.md)  
        [Property-Objekt (ADO)](./property-object-ado.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Attribute und namens Eigenschaften (VB)](./attributes-and-name-properties-example-vb.md)   
 [Beispiel für Attribute und namens Eigenschaften (VC + +)](./attributes-and-name-properties-example-vc.md)