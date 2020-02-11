---
title: Fields-Auflistung (ADO) | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67918714"
---
# <a name="fields-collection-ado"></a>Fields-Collection (ADO)
Enthält alle [Feld](../../../ado/reference/ado-api/field-object.md) Objekte eines [Recordsets](../../../ado/reference/ado-api/recordset-object-ado.md) oder eines [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) -Objekts.  
  
## <a name="remarks"></a>Bemerkungen  
 Ein **Recordset** -Objekt verfügt über eine **Fields** -Auflistung, die aus **Feld** Objekten besteht. Jedes **Feld** Objekt entspricht einer Spalte im **Recordset**. Sie können die **Fields** -Auflistung vor dem Öffnen des **Recordsets** auffüllen, indem Sie die [Refresh](../../../ado/reference/ado-api/refresh-method-ado.md) -Methode für die Auflistung aufrufen.  
  
> [!NOTE]
>  Eine ausführlichere Erläuterung der Verwendung von **Feld** Objekten finden Sie im Thema **Feld** Objekt.  
  
 Die **Fields** -Auflistung verfügt über eine [Append](../../../ado/reference/ado-api/append-method-ado.md) -Methode, die vorläufig ein **Feld** Objekt erstellt und der Auflistung hinzufügt, sowie eine **Update** -Methode, die alle Ergänzungen oder Löschungen schließt.  
  
 Ein **Datensatz** -Objekt verfügt über zwei spezielle Felder, die mit [fieldenum](../../../ado/reference/ado-api/fieldenum.md) -Konstanten indiziert werden können. Eine Konstante greift auf ein Feld zu, das den Standardstream für den **Datensatz**enthält, und die andere auf ein Feld, das die absolute URL Zeichenfolge für den **Datensatz**enthält.  
  
 Bestimmte Anbieter (z. b. der [Microsoft OLE DB-Anbieter für die Internet Veröffentlichung](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)) können die **Fields** -Auflistung mit einer Teilmenge der verfügbaren Felder für den **Datensatz** oder das **Recordset**auffüllen. Der Auflistung werden keine anderen Felder hinzugefügt, bis Sie zunächst anhand ihres Namens referenziert oder durch den Code indiziert werden.  
  
 Wenn Sie versuchen, mit dem Namen auf ein nicht vorhandenes Feld zu verweisen, wird ein neues **Feld** Objekt an die **Fields** -Auflistung mit dem [Status](../../../ado/reference/ado-api/status-property-ado-field.md) **adfieldpdinginsert**angehängt. Wenn Sie [Update](../../../ado/reference/ado-api/update-method.md)aufruft, erstellt ADO ein neues Feld in der Datenquelle, wenn es von Ihrem Anbieter zugelassen wird.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Eigenschaften, Methoden und Ereignisse der Fields-Auflistung](../../../ado/reference/ado-api/fields-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Field-Objekt](../../../ado/reference/ado-api/field-object.md)
