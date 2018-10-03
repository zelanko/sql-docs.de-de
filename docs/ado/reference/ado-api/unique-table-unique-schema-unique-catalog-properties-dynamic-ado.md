---
title: Steuerelement geändert wird, auf die Basistabelle von Recordsets (ADO) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bcca3701807ebb591a0c083c4f4762b7597b9856
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47777388"
---
# <a name="unique-table-unique-schema-unique-catalog-properties-dynamic-ado"></a>Eindeutige Tabelle, eindeutiges Schema, eindeutige Katalog Sie dynamische Eigenschaften (ADO)
Ermöglicht es Ihnen zu eng Steuerelement Änderungen an einer bestimmten Basistabelle in eine [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) , die durch eine JOIN-Operation auf mehrere Basistabellen gebildet wurde.  
  
-   **Eindeutige Tabelle** gibt den Namen der Basistabelle, auf denen Updates, einfügungen und löschungen zulässig sind.  
  
-   **Eindeutiges Schema** gibt an, die *Schema*, oder der Name des Besitzers der Tabelle.  
  
-   **Eindeutige Katalogressource** gibt an, die *Katalog*, oder der Name der Datenbank mit der Tabelle.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt einen **Zeichenfolge** Wert, der den Namen der Tabellen, Schema oder Katalog ist.  
  
## <a name="remarks"></a>Hinweise  
 Die gewünschte Basistabelle wird durch seine Katalog, Schema und Tabellennamen eindeutig identifiziert. Wenn die **eindeutige Tabelle** Eigenschaft festgelegt ist, werden die Werte der der **eindeutiges Schema** oder **Unique Catalog** Eigenschaften werden verwendet, um die Basistabelle zu suchen. Es ist vorgesehen, aber nicht erforderlich, eine oder beide der **eindeutiges Schema** und **Unique Catalog** Eigenschaften festgelegt werden, bevor die **eindeutige Tabelle** festgelegt wird.  
  
 Den primären Schlüssel für die **eindeutige Tabelle** behandelt, als den primären Schlüssel für die gesamte **Recordset**. Dies ist der Schlüssel, der für jede Methode erfordert einen Primärschlüssel verwendet wird.  
  
 Während **eindeutige Tabelle** festgelegt ist, wird die [löschen](../../../ado/reference/ado-api/delete-method-ado-recordset.md) Methode wirkt sich nur auf die benannte Tabelle. Die [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md), [Resync](../../../ado/reference/ado-api/resync-method.md), [Update](../../../ado/reference/ado-api/update-method.md), und [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) Methoden wirken sich auf alle entsprechenden zugrunde liegenden Basistabellen der **Recordset**.  
  
 **Eindeutige Tabelle** muss angegeben werden, bevor alle benutzerdefinierten neusynchronisierungen durchführen. Wenn **eindeutige Tabelle** wurde nicht angegeben, die [Resync Command](../../../ado/reference/ado-api/resync-command-property-dynamic-ado.md) Eigenschaft hat keine Auswirkungen.  
  
 Ein Laufzeitfehler ausgegeben, wenn es sich bei eine eindeutige Basistabelle nicht gefunden werden kann.  
  
 Diese dynamischen Eigenschaften werden alle angehängt der **Recordset** Objekt [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md) Auflistung bei der [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) -Eigenschaftensatz auf  **AdUseClient**.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
