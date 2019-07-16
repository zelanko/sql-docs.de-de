---
title: Fields-Collection (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Fields
- Recordset15::Fields
- _Record::Fields
helpviewer_keywords:
- Fields collection [ADO]
ms.assetid: 7c371474-b88f-4730-afa5-44163a0488d5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9c9216ee655e371633837c5653ebac56fac1a782
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67918714"
---
# <a name="fields-collection-ado"></a>Fields-Collection (ADO)
Enthält alle der [Feld](../../../ado/reference/ado-api/field-object.md) Objekte von einem [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oder [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) Objekt.  
  
## <a name="remarks"></a>Hinweise  
 Ein **Recordset** Objekt verfügt über eine **Felder** -Auflistung, die von **Feld** Objekte. Jede **Feld** -Objekt entspricht, auf eine Spalte in der **Recordset**. Sie füllen können die **Felder** Auflistung vor dem Öffnen der **Recordset** durch Aufrufen der [aktualisieren](../../../ado/reference/ado-api/refresh-method-ado.md) Methode in der Auflistung.  
  
> [!NOTE]
>  Finden Sie unter den **Feld** Thema-Objekt für eine ausführlichere Erläuterung zur Verwendung **Feld** Objekte.  
  
 Die **Felder** Auflistung verfügt über eine [Append](../../../ado/reference/ado-api/append-method-ado.md) -Methode, die vorläufig erstellt und fügt eine **Feld** Objekt, das der Auflistung und ein **Aktualisieren**-Methode, die hinzugefügten oder gelöschten schließt ab.  
  
 Ein **Datensatz** Objekt verfügt über zwei spezielle Felder, die mit indizierbaren [FieldEnum](../../../ado/reference/ado-api/fieldenum.md) Konstanten. Eine Konstante greift auf ein Feld für den Standarddatenstrom der **Datensatz**, und die andere greift auf die ein Feld mit der absoluten URL-Zeichenfolge für die **Datensatz**.  
  
 Bestimmte Anbieter (z. B. die [Microsoft OLE DB-Anbieter für Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)) auffüllen kann die **Felder** Auflistung mit einer Teilmenge der verfügbaren Felder für die **Datensatz** oder **Recordset**. Andere Felder werden der Auflistung nicht hinzugefügt werden, bis sie zuerst anhand des Namens verwiesen oder von Ihrem Code indiziert werden.  
  
 Wenn Sie versuchen, ein nicht vorhandenes Feld Namen verweisen, ein neues **Feld** Objekt angefügt die **Felder** Sammlung mit einer [Status](../../../ado/reference/ado-api/status-property-ado-field.md) von  **AdFieldPendingInsert**. Beim Aufruf [Update](../../../ado/reference/ado-api/update-method.md), ADO wird ein neues Feld in der Datenquelle erstellt, wenn die von Ihrem Anbieter zugelassen.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Felder Auflistung – Eigenschaften, Methoden und Ereignisse](../../../ado/reference/ado-api/fields-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Field-Objekt](../../../ado/reference/ado-api/field-object.md)
