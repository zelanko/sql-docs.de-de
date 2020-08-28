---
description: Unique Table, Unique Schema, Unique Catalog Properties-Dynamic (ADO)
title: Steuern von Änderungen an der Recordset-Basistabelle (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 50a17938a2e1cffd3cc0bf76d3cc3758358318d2
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88988161"
---
# <a name="unique-table-unique-schema-unique-catalog-properties-dynamic-ado"></a>Unique Table, Unique Schema, Unique Catalog Properties-Dynamic (ADO)
Ermöglicht es Ihnen, Änderungen an einer bestimmten Basistabelle in einem [Recordset](./recordset-object-ado.md) , das durch eine Joinoperation in mehreren Basistabellen gebildet wurde, genau zu steuern.  
  
-   **Unique Table** gibt den Namen der Basistabelle an, auf der Updates, Einfügungen und Löschungen zulässig sind.  
  
-   Eindeutiges **Schema** gibt das *Schema*oder den Namen des Besitzers der Tabelle an.  
  
-   Der **eindeutige Katalog** gibt den *Katalog*oder den Namen der Datenbank an, in der die Tabelle enthalten ist.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen **Zeichen** folgen Wert fest, der den Namen einer Tabelle, eines Schemas oder eines Katalogs angibt, oder gibt ihn zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 Die gewünschte Basistabelle wird durch die Katalog-, Schema-und Tabellennamen eindeutig identifiziert. Wenn die **Unique Table** -Eigenschaft festgelegt ist, werden die Werte der Eigenschaften des **eindeutigen Schemas** oder des **eindeutigen Katalogs** verwendet, um nach der Basistabelle zu suchen. Es ist beabsichtigt, aber nicht erforderlich, dass entweder oder sowohl die **eindeutigen Schema** -als auch die **eindeutigen Katalog** Eigenschaften festgelegt werden, bevor die **Unique Table** -Eigenschaft festgelegt wird.  
  
 Der Primärschlüssel der **eindeutigen Tabelle** wird als Primärschlüssel des gesamten **Recordsets**behandelt. Dies ist der Schlüssel, der für jede Methode verwendet wird, die einen Primärschlüssel erfordert.  
  
 Obwohl **Unique Table** festgelegt ist, wirkt sich die [Delete](./delete-method-ado-recordset.md) -Methode nur auf die benannte Tabelle aus. Die [AddNew](./addnew-method-ado.md)-, [Resync](./resync-method.md)-, [Update](./update-method.md)-und [UpdateBatch](./updatebatch-method.md) -Methoden wirken sich auf alle entsprechenden zugrunde liegenden Basistabellen des **Recordsets**aus.  
  
 Vor der Durchführung benutzerdefinierter Neusynchronisierung muss eine **eindeutige Tabelle** angegeben werden. Wenn keine **eindeutige Tabelle** angegeben wurde, hat die [Resync-Befehls](./resync-command-property-dynamic-ado.md) Eigenschaft keine Auswirkung.  
  
 Ein Laufzeitfehler tritt auf, wenn eine eindeutige Basistabelle nicht gefunden werden kann.  
  
 Diese dynamischen Eigenschaften werden alle an die Auflistung der **Recordset** -Objekt [Eigenschaften](./properties-collection-ado.md) angehängt, wenn die [Cursor Location](./cursorlocation-property-ado.md) -Eigenschaft auf **adUseClient**festgelegt ist.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Recordset-Objekt (ADO)](./recordset-object-ado.md)