---
title: Sortieren Sie die Eigenschaft | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::get_Sort
- Recordset15::put_Sort
- Recordset15::PutSort
- Recordset15::GetSort
- Recordset15::Sort
helpviewer_keywords:
- DESC [ADO]
- ASC [ADO]
- Sort property [ADO]
ms.assetid: 3683ffa0-6f93-4906-9533-ef6942f24f39
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 092eb49216874a59e4bcba09431fcc01dc3679a4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66711157"
---
# <a name="sort-property"></a>Sort-Eigenschaft
Gibt einen oder mehrere Feldnamen auf dem die [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) sortiert ist, und gibt an, ob jedes Feld in aufsteigender oder absteigender Reihenfolge sortiert wird.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt einen **Zeichenfolge** Wert, der das Feld gibt Namen, der **Recordset** für die Sortierung. Jeder Name wird durch ein Komma getrennt, und optional durch ein Leerzeichen und dem Schlüsselwort folgt **ASC**, das Feld in aufsteigender Reihenfolge sortiert oder **DESC**, das Feld in absteigender Reihenfolge sortiert. In der Standardeinstellung Wenn kein Schlüsselwort angegeben ist, wird das Feld in aufsteigender Reihenfolge sortiert.  
  
## <a name="remarks"></a>Hinweise  
 Diese Eigenschaft erfordert die [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) Eigenschaft festgelegt werden, um **AdUseClient**. Ein temporärer Index erstellt werden für jedes Feld im angegebenen die **Sortierreihenfolge** Eigenschaft, wenn ein Index noch nicht vorhanden ist.  
  
 Der Sortiervorgang ist effizient, da die Daten physisch nicht neu angeordnet, sondern einfach in der Reihenfolge, die vom Index angegebenen zugegriffen wird.  
  
 Bei den Wert des der **sortieren** -Eigenschaft ist etwas anderes als eine leere Zeichenfolge, die **sortieren** Reihenfolge der Eigenschaft hat Vorrang vor der Reihenfolge im eine **ORDER BY** Klausel enthalten in der SQL-Anweisung, die zum Öffnen der **Recordset**.  
  
 Die **Recordset** muss nicht geöffnet werden, bevor Sie den Zugriff auf die **sortieren** Eigenschaft kann zu einem beliebigen Zeitpunkt nach festgelegt werden die **Recordset** -Objekt instanziiert wird.  
  
 Festlegen der **Sortierreihenfolge** Eigenschaft auf eine leere Zeichenfolge wird die Zeilen in der ursprünglichen Reihenfolge zurücksetzen und Löschen temporärer Indizes. Vorhandene Indizes werden nicht gelöscht werden.  
  
 Nehmen Sie an einer **Recordset** enthält drei Felder, die mit dem Namen *FirstName*, *MiddleInitial*, und *"LastName"* . Legen Sie die **sortieren** Eigenschaft, um die Zeichenfolge "`lastName DESC, firstName ASC`", welcher Reihenfolge werden die **Recordset** nach dem Nachnamen in absteigender Reihenfolge aus, und klicken Sie dann nach Vornamen in aufsteigender Reihenfolge. Der Wert von MiddleInitial wird ignoriert.  
  
 Kein Feld kann den Namen "ASC" oder "DESC", da diese Namen in mit den Schlüsselwörtern Konflikt **ASC** und **DESC**. Sie können einen Alias für ein Feld mit einem in Konflikt stehende Namen erstellen, mit der **AS** Schlüsselwort in der Abfrage, die gibt die **Recordset**.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Sort-Eigenschaft – Beispiel (VB)](../../../ado/reference/ado-api/sort-property-example-vb.md)   
 [Sort-Eigenschaft – Beispiel (VC++)](../../../ado/reference/ado-api/sort-property-example-vc.md)   
 [Optimieren Sie die dynamische Eigenschaft (ADO)](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)   
 [SortColumn-Eigenschaft (RDS)](../../../ado/reference/rds-api/sortcolumn-property-rds.md)   
 [SortDirection-Eigenschaft (RDS)](../../../ado/reference/rds-api/sortdirection-property-rds.md)
