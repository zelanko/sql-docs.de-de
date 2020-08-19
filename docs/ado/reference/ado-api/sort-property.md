---
description: Sort-Eigenschaft
title: Sort-Eigenschaft | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: a8ec5c6812e2800825677cd844756d1dd9325729
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88442062"
---
# <a name="sort-property"></a>Sort-Eigenschaft
Gibt einen oder mehrere Feldnamen an, für die das [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) sortiert ist, und gibt an, ob die einzelnen Felder in aufsteigender oder absteigender Reihenfolge sortiert sind.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen **Zeichen** folgen Wert fest, der die Feldnamen in dem **Recordset** angibt, nach dem sortiert werden soll, oder gibt ihn zurück. Jeder Name wird durch ein Komma getrennt, und es folgt optional ein leeres und das Schlüsselwort **ASC**, das das Feld in aufsteigender Reihenfolge sortiert, oder **DESC**, das das Feld in absteigender Reihenfolge sortiert. Wenn kein Schlüsselwort angegeben wird, wird das Feld standardmäßig in aufsteigender Reihenfolge sortiert.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Eigenschaft erfordert, dass die [Cursor Location](../../../ado/reference/ado-api/cursorlocation-property-ado.md) -Eigenschaft auf **adUseClient**festgelegt ist. Ein temporärer Index wird für jedes Feld erstellt, das in der **Sort** -Eigenschaft angegeben ist, wenn noch kein Index vorhanden ist.  
  
 Der Sortiervorgang ist effizient, da die Daten nicht physisch neu angeordnet werden, sondern nur in der vom Index angegebenen Reihenfolge aufgerufen wird.  
  
 Wenn der Wert der **Sort** -Eigenschaft etwas anderes als eine leere Zeichenfolge ist, hat die **Sortier** Eigenschaften Reihenfolge Vorrang vor der Reihenfolge, die in einer **Order by** -Klausel in der SQL-Anweisung, die zum Öffnen des **Recordsets**verwendet wird, angegeben ist.  
  
 Das **Recordset** muss vor dem Zugriff auf die **Sort** -Eigenschaft nicht geöffnet werden. Sie kann jederzeit festgelegt werden, nachdem das **Recordset** -Objekt instanziiert wurde.  
  
 Wenn Sie die **Sort** -Eigenschaft auf eine leere Zeichenfolge festlegen, werden die Zeilen auf Ihre ursprüngliche Reihenfolge zurückgesetzt und temporäre Indizes gelöscht. Vorhandene Indizes werden nicht gelöscht.  
  
 Angenommen, ein **Recordset** enthält drei Felder namens *FirstName*, *Mittel dleinitial*und *LastName*. Legen Sie die **Sort** -Eigenschaft auf die Zeichenfolge " `lastName DESC, firstName ASC` " fest, die das **Recordset** nach dem Nachnamen in absteigender Reihenfolge sortiert, und dann nach dem Vornamen in aufsteigender Reihenfolge. Der erste Mittelwert wird ignoriert.  
  
 Es kann kein Feld mit den Namen "ASC" oder "DESC" benannt werden, da diese Namen mit den Schlüsselwörtern **ASC** und **DESC**in Konflikt stehen. Sie können einen Alias für ein Feld mit einem in Konflikt stehenden Namen erstellen, indem Sie das **As** -Schlüsselwort in der Abfrage verwenden, die das **Recordset**zurückgibt.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für eine Sortier Eigenschaft (VB)](../../../ado/reference/ado-api/sort-property-example-vb.md)   
 [Beispiel für eine Sortier Eigenschaft (VC + +)](../../../ado/reference/ado-api/sort-property-example-vc.md)   
 [Optimieren von Eigenschaften-Dynamic (ADO)](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)   
 [SortColumn-Eigenschaft (RDS)](../../../ado/reference/rds-api/sortcolumn-property-rds.md)   
 [SortDirection-Eigenschaft (RDS)](../../../ado/reference/rds-api/sortdirection-property-rds.md)
