---
title: STAT-Methode | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Stat
helpviewer_keywords:
- Stat method [ADO]
ms.assetid: 99a2b2d4-e6b1-4205-b011-72d024ea7240
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 127aab5e00247ce5550f25e2a281e190472b0186
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47828228"
---
# <a name="stat-method"></a>Stat-Methode
Ruft Informationen ab, zu einem [Stream](../../../ado/reference/ado-api/stream-object-ado.md) Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Long stream.Stat(StatStg, StatFlag)  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein **lange** Wert, der den Status des Vorgangs.  
  
#### <a name="parameters"></a>Parameter  
 *StatStg*  
 Eine STATSTG-Struktur, die mit Informationen über den Stream gefüllt werden. Die Implementierung der **Stat** durch das ADO-Stream-Objekt verwendete Methode ist nicht in alle Felder der Struktur aufgefüllt.  
  
 *StatFlag*  
 Gibt an, dass es sich bei dieser Methode einige der Member nicht in der STATSTG-Struktur, und speichern daher ein speicherbelegungsvorgang zurückgegeben werden. Werte werden aus der STATFLAG-Enumeration entnommen. Die STATFLAG-Enumeration hat zwei Werte  
  
|Konstante|value|  
|--------------|-----------|  
|STATFLAG_DEFAULT|0|  
|STATFLAG_NONAME|1|  
  
## <a name="remarks"></a>Hinweise  
 Die Version der Stat-Methode implementiert, die für das ADO-Stream-Objekt füllt die folgenden Felder der Struktur STATSTG ab:  
  
 *pwcsName*  
 Eine Zeichenfolge, die mit dem Namen des Streams, sofern verfügbar und StatFlag Wert STATFLAG_NONAME wurde nicht angegeben.  
  
 *cbSize*  
 Gibt die Größe des Streams oder Bytearrays in Bytes an.  
  
 *mtime*  
 Gibt den Zeitpunkt der letzten Änderung für dieses Speicherkonto, Stream- oder Byte-Array an.  
  
 *ctime*  
 Gibt den Zeitpunkt der Erstellung für dieses Speicherkonto, Stream- oder Byte-Array an.  
  
 *"atime"*  
 Gibt den Zeitpunkt des letzten Zugriffs für dieses Speicherkonto, Stream- oder Byte-Array an.  
  
 Wenn STATFLAG_NONAME im StatFlag-Parameter angegeben wird, wird der Name des Datenstroms nicht zurückgegeben.  
  
 Wenn kein Name vorhanden, für den aktuellen Stream ist STATFLAG_NONAME im StatFlag-Parameter nicht angegeben wurde, wird dieser Wert E_NOTIMPL sein.  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
