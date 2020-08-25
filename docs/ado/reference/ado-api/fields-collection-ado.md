---
description: Fields-Collection (ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: d94803ecbe53addb2efb7ef738863bc6541a5801
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88775379"
---
# <a name="fields-collection-ado"></a>Fields-Collection (ADO)
Enthält alle [Feld](./field-object.md) Objekte eines [Recordsets](./recordset-object-ado.md) oder eines [Datensatz](./record-object-ado.md) -Objekts.  
  
## <a name="remarks"></a>Bemerkungen  
 Ein **Recordset** -Objekt verfügt über eine **Fields** -Auflistung, die aus **Feld** Objekten besteht. Jedes **Feld** Objekt entspricht einer Spalte im **Recordset**. Sie können die **Fields** -Auflistung vor dem Öffnen des **Recordsets** auffüllen, indem Sie die [Refresh](./refresh-method-ado.md) -Methode für die Auflistung aufrufen.  
  
> [!NOTE]
>  Eine ausführlichere Erläuterung der Verwendung von **Feld** Objekten finden Sie im Thema **Feld** Objekt.  
  
 Die **Fields** -Auflistung verfügt über eine [Append](./append-method-ado.md) -Methode, die vorläufig ein **Feld** Objekt erstellt und der Auflistung hinzufügt, sowie eine **Update** -Methode, die alle Ergänzungen oder Löschungen schließt.  
  
 Ein **Datensatz** -Objekt verfügt über zwei spezielle Felder, die mit [fieldenum](./fieldenum.md) -Konstanten indiziert werden können. Eine Konstante greift auf ein Feld zu, das den Standardstream für den **Datensatz**enthält, und die andere auf ein Feld, das die absolute URL Zeichenfolge für den **Datensatz**enthält.  
  
 Bestimmte Anbieter (z. b. der [Microsoft OLE DB-Anbieter für die Internet Veröffentlichung](../../guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)) können die **Fields** -Auflistung mit einer Teilmenge der verfügbaren Felder für den **Datensatz** oder das **Recordset**auffüllen. Der Auflistung werden keine anderen Felder hinzugefügt, bis Sie zunächst anhand ihres Namens referenziert oder durch den Code indiziert werden.  
  
 Wenn Sie versuchen, mit dem Namen auf ein nicht vorhandenes Feld zu verweisen, wird ein neues **Feld** Objekt an die **Fields** -Auflistung mit dem [Status](./status-property-ado-field.md) **adfieldpdinginsert**angehängt. Wenn Sie [Update](./update-method.md)aufruft, erstellt ADO ein neues Feld in der Datenquelle, wenn es von Ihrem Anbieter zugelassen wird.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Eigenschaften, Methoden und Ereignisse der Fields-Auflistung](./fields-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Field-Objekt](./field-object.md)