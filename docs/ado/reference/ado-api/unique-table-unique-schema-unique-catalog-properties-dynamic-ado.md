---
title: Steuern von Änderungen an der Recordset-Basistabelle (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Unique Table property [ADO]
- Unique Schema property [ADO]
- Unique Catalog property [ADO]
ms.assetid: d0e775d8-e353-46a1-ad10-ed4cc240dfaa
author: rothja
ms.author: jroth
ms.openlocfilehash: ac7fa0cf50a92b2738d3e83d5e7b9d5fac46fd9b
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82759516"
---
# <a name="unique-table-unique-schema-unique-catalog-properties-dynamic-ado"></a>Unique Table, Unique Schema, Unique Catalog Properties-Dynamic (ADO)
Ermöglicht es Ihnen, Änderungen an einer bestimmten Basistabelle in einem [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) , das durch eine Joinoperation in mehreren Basistabellen gebildet wurde, genau zu steuern.  
  
-   **Unique Table** gibt den Namen der Basistabelle an, auf der Updates, Einfügungen und Löschungen zulässig sind.  
  
-   Eindeutiges **Schema** gibt das *Schema*oder den Namen des Besitzers der Tabelle an.  
  
-   Der **eindeutige Katalog** gibt den *Katalog*oder den Namen der Datenbank an, in der die Tabelle enthalten ist.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen **Zeichen** folgen Wert fest, der den Namen einer Tabelle, eines Schemas oder eines Katalogs angibt, oder gibt ihn zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 Die gewünschte Basistabelle wird durch die Katalog-, Schema-und Tabellennamen eindeutig identifiziert. Wenn die **Unique Table** -Eigenschaft festgelegt ist, werden die Werte der Eigenschaften des **eindeutigen Schemas** oder des **eindeutigen Katalogs** verwendet, um nach der Basistabelle zu suchen. Es ist beabsichtigt, aber nicht erforderlich, dass entweder oder sowohl die **eindeutigen Schema** -als auch die **eindeutigen Katalog** Eigenschaften festgelegt werden, bevor die **Unique Table** -Eigenschaft festgelegt wird.  
  
 Der Primärschlüssel der **eindeutigen Tabelle** wird als Primärschlüssel des gesamten **Recordsets**behandelt. Dies ist der Schlüssel, der für jede Methode verwendet wird, die einen Primärschlüssel erfordert.  
  
 Obwohl **Unique Table** festgelegt ist, wirkt sich die [Delete](../../../ado/reference/ado-api/delete-method-ado-recordset.md) -Methode nur auf die benannte Tabelle aus. Die [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)-, [Resync](../../../ado/reference/ado-api/resync-method.md)-, [Update](../../../ado/reference/ado-api/update-method.md)-und [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) -Methoden wirken sich auf alle entsprechenden zugrunde liegenden Basistabellen des **Recordsets**aus.  
  
 Vor der Durchführung benutzerdefinierter Neusynchronisierung muss eine **eindeutige Tabelle** angegeben werden. Wenn keine **eindeutige Tabelle** angegeben wurde, hat die [Resync-Befehls](../../../ado/reference/ado-api/resync-command-property-dynamic-ado.md) Eigenschaft keine Auswirkung.  
  
 Ein Laufzeitfehler tritt auf, wenn eine eindeutige Basistabelle nicht gefunden werden kann.  
  
 Diese dynamischen Eigenschaften werden alle an die Auflistung der **Recordset** -Objekt [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md) angehängt, wenn die [Cursor Location](../../../ado/reference/ado-api/cursorlocation-property-ado.md) -Eigenschaft auf **adUseClient**festgelegt ist.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
