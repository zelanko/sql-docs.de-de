---
title: LoadFromFile-Methode (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_LoadFromFile
helpviewer_keywords:
- LoadFromFile method [ADO]
ms.assetid: b18d8d38-7354-4a94-b637-6ac035faa433
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ce90b13a677246fb64462fbe691eb9e3efaa3c7f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67918269"
---
# <a name="loadfromfile-method-ado"></a>LoadFromFile-Methode (ADO)
Lädt den Inhalt einer vorhandenen Datei in eine [Stream](../../../ado/reference/ado-api/stream-object-ado.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Stream.LoadFromFileFileName  
```  
  
#### <a name="parameters"></a>Parameter  
 *FileName*  
 Ein **Zeichenfolge** -Wert, der den Namen einer Datei geladen werden enthält die **Stream**. *FileName* können alle gültigen Pfad und Namen im UNC-Format enthalten. Wenn die angegebene Datei nicht vorhanden ist, tritt ein Laufzeitfehler auf.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode kann verwendet werden, beim Laden des Inhalts einer lokalen Datei in eine **Stream** Objekt. Dies kann verwendet werden, um den Inhalt einer lokalen Datei auf einen Server hochzuladen.  
  
 Die **Stream** Objekt muss bereits vor dem Aufruf geöffnet **LoadFromFile**. Diese Methode ändert sich nicht auf die Bindung des der **Stream** -Objekt wird immer noch auf das Objekt, das von der URL angegebenen gebunden werden oder **Datensatz** mit dem die **Stream** war ursprünglich geöffnet.  
  
 **LoadFromFile** überschreibt den aktuellen Inhalt des der **Stream** Objekt mit Daten aus der Datei gelesen. Alle vorhandenen Bytes in den **Stream** werden durch den Inhalt der Datei überschrieben. Alle folgenden zuvor vorhandenen und verbleibenden Bytes der [EOS](../../../ado/reference/ado-api/eos-property.md) erstellt **LoadFromFile**, werden abgeschnitten.  
  
 Nach einem Aufruf von **LoadFromFile**, die aktuelle Position festgelegt ist, an den Anfang der **Stream** ([Position](../../../ado/reference/ado-api/position-property-ado.md) ist 0).  
  
 Da 2 Bytes auf den Anfang des Datenstroms für die Codierung hinzugefügt werden kann, kann die Größe des Streams nicht genau der Größe der Datei übereinstimmen, aus der sie geladen wurde.  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
