---
title: Index-Eigenschaft | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset21::Index
helpviewer_keywords:
- Index property
ms.assetid: 1c79e271-21ec-41a8-8163-c5e89f0001a7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4194cf7bea9d2a7cb52ea255ee7a858cdf4de6e5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47716308"
---
# <a name="index-property"></a>Index-Eigenschaft
Gibt den Namen des Indexes derzeit für eine [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt einen **Zeichenfolge** Wert, der den Namen des Indexes angibt.  
  
## <a name="remarks"></a>Hinweise  
 Der Index, der mit dem Namen, indem die **Index** Eigenschaft muss zuvor deklariert worden sein, für den zugrunde liegenden Basistabelle die **Recordset** Objekt. D. h. der Index muss deklariert programmgesteuert entweder als eine ADOX [Index](../../../ado/reference/adox-api/index-object-adox.md) -Objekt, oder wenn die Basistabelle erstellt wurde.  
  
 Ein Laufzeitfehler treten auf, wenn der Index kann nicht festgelegt werden. Die **Index** Eigenschaft kann nicht unter den folgenden Bedingungen festgelegt werden:  
  
-   Innerhalb einer [WillChangeRecordset](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md) oder **RecordsetChangeComplete** -Ereignishandler.  
  
-   Wenn die **Recordset** noch ausgeführt wird, einen Vorgang (das kann bestimmt werden, indem die [Zustand](../../../ado/reference/ado-api/state-property-ado.md) Eigenschaft).  
  
-   Wenn ein Filter festgelegt wurde auf die **Recordset** mit der [Filter](../../../ado/reference/ado-api/filter-property.md) Eigenschaft.  
  
 Die **Index** Eigenschaft kann immer erfolgreich festgelegt werden, wenn die **Recordset** geschlossen ist, aber die **Recordset** nicht erfolgreich geöffnet, oder der Index wird nicht verwendet werden kann, wenn der zugrunde liegende Anbieter unterstützt keine Indizes.  
  
 Wenn der Index festgelegt werden kann, kann die aktuelle Zeilenposition ändern. Dies bewirkt, dass ein Update für die [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md) -Eigenschaft, und löst die **WillChangeRecordset**, **RecordsetChangeComplete**, [WillMove ](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md), und [MoveComplete](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md) Ereignisse.  
  
 Wenn der Index festgelegt werden kann und die [LockType](../../../ado/reference/ado-api/locktype-property-ado.md) Eigenschaft **AdLockPessimistic** oder **AdLockOptimistic**, klicken Sie dann eine implizite [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) Vorgang wird ausgeführt. Damit werden die aktuellen und dem betroffenen Gruppen. Alle vorhandener Filter wird freigegeben, und die aktuelle Zeilenposition wird geändert, auf die erste Zeile der neu angeordneten **Recordset**.  
  
 Die **Index** Eigenschaft wird verwendet, in Verbindung mit der [Seek](../../../ado/reference/ado-api/seek-method.md) Methode. Wenn der zugrunde liegenden Anbieter nicht unterstützt die **Index** -Eigenschaft, und somit die **Seek** -Methode in Betracht der [finden](../../../ado/reference/ado-api/find-method-ado.md) Methode stattdessen. Bestimmt, ob die **Recordset** Objekt unterstützt die Indizes mit der [unterstützt](../../../ado/reference/ado-api/supports-method.md)**(AdIndex)** Methode.  
  
 Die integrierte **Index** Eigenschaft bezieht sich nicht an den dynamischen [optimieren](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md) -Eigenschaft, obwohl beide Indizes verarbeiten.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Seek-Methode und Index-Eigenschaft – Beispiel (VB)](../../../ado/reference/ado-api/seek-method-and-index-property-example-vb.md)   
 [Index-Objekt (ADOX)](../../../ado/reference/adox-api/index-object-adox.md)   
 [Seek-Methode](../../../ado/reference/ado-api/seek-method.md)
