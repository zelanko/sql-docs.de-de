---
description: CursorOptionEnum
title: Cursor optionumum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CursorOptionEnum
helpviewer_keywords:
- CursorOptionEnum enumeration [ADO]
ms.assetid: 4e10cda7-ce81-4466-94c2-844d38191cf1
author: rothja
ms.author: jroth
ms.openlocfilehash: 83ba6960e6e7f81db55f3a8292fd054c1377b106
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88775519"
---
# <a name="cursoroptionenum"></a>CursorOptionEnum
Gibt an, auf welche Funktionalität die [unterstützte](./supports-method.md) Methode testen soll.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adAddNew**|0x1000400|Unterstützt die [AddNew](./addnew-method-ado.md) -Methode, um neue Datensätze hinzuzufügen.|  
|**adapproxposition**|0x4000|Unterstützt die Eigenschaften [AbsolutePosition](./absoluteposition-property-ado.md) und [AbsolutePage](./absolutepage-property-ado.md) .|  
|**adbookmark**|0x2000|Unterstützt die [Bookmark](./bookmark-property-ado.md) -Eigenschaft, um Zugriff auf bestimmte Datensätze zu erhalten.|  
|**addelete**|0x1000800|Unterstützt die [Delete](./delete-method-ado-recordset.md) -Methode zum Löschen von Datensätzen.|  
|**adFind**|0x80000|Unterstützt die [Find](./find-method-ado.md) -Methode, um eine Zeile in einem [Recordset](./recordset-object-ado.md)zu suchen.|  
|**adholdrecords**|0x100|Ruft weitere Datensätze ab oder ändert die nächste Position, ohne alle ausstehenden Änderungen zu übernehmen.|  
|**adIndex**|0x100000|Unterstützt die [Index](./index-property.md) -Eigenschaft, um einen Index zu benennen.|  
|**admuveprevious**|0x200|Unterstützt die [MoveFirst](./movefirst-movelast-movenext-and-moveprevious-methods-ado.md) -Methode und die [MovePrevious](./movefirst-movelast-movenext-and-moveprevious-methods-ado.md) -Methode, und [Move](./move-method-ado.md) -oder [GetRows](./getrows-method-ado.md) -Methoden, um die aktuelle Daten Satz Position rückwärts zu verschieben, ohne Lesezeichen|  
|**adnotify**|0x40000|Gibt an, dass der zugrunde liegende Datenanbieter Benachrichtigungen unterstützt (die bestimmen, ob **recordsetereignisse** unterstützt werden).|  
|**adresync**|0x20000|Unterstützt die [Resync](./resync-method.md) -Methode, um den Cursor mit den Daten zu aktualisieren, die in der zugrunde liegenden Datenbank sichtbar sind.|  
|**adSeek**|0x200000|Unterstützt die [Seek](./seek-method.md) -Methode, um eine Zeile in einem **Recordset**zu suchen.|  
|**adupdate**|0x1008000|Unterstützt die [Update](./update-method.md) -Methode, um vorhandene Daten zu ändern.|  
|**adUpdateBatch**|0x10000|Unterstützt die Batch Aktualisierung ([UpdateBatch](./updatebatch-method.md) -und [CancelBatch](./cancelbatch-method-ado.md) -Methoden) zum Übertragen von Gruppen von Änderungen an den Anbieter.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Konstante|  
|--------------|  
|Adoerums. Cursor Option. AddNew|  
|Adoerums. Cursor Option. approxposition|  
|AdoEnums. Cursor Option. Bookmark|  
|Adoerums. Cursor Option. Delete|  
|Adoerums. Cursor Option. Find|  
|Adoerums. Cursor Option. holdrecords|  
|AdoEnums. Cursor Option. Index|  
|Adoerums. Cursor Option. muveprevious|  
|Adoerums. Cursor Option. Notify|  
|Adoerums. Cursor Option. Resync|  
|Adoerums. Cursor Option. Seek|  
|Adoerums. Cursor Option. Update|  
|AdoEnums. Cursor Option. UpdateBatch|  
  
## <a name="applies-to"></a>Gilt für  
 [Supports-Methode](./supports-method.md)