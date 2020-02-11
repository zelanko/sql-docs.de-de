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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67918269"
---
# <a name="loadfromfile-method-ado"></a>LoadFromFile-Methode (ADO)
Lädt den Inhalt einer vorhandenen Datei in einen [Stream](../../../ado/reference/ado-api/stream-object-ado.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Stream.LoadFromFileFileName  
```  
  
#### <a name="parameters"></a>Parameter  
 *Einfügen*  
 Ein **Zeichen** folgen Wert, der den Namen einer Datei enthält, die in den **Stream**geladen werden soll. *Filename* kann einen beliebigen gültigen Pfad und Namen im UNC-Format enthalten. Wenn die angegebene Datei nicht vorhanden ist, tritt ein Laufzeitfehler auf.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode kann verwendet werden, um den Inhalt einer lokalen Datei in ein Daten **Strom** Objekt zu laden. Dies kann verwendet werden, um den Inhalt einer lokalen Datei auf einen Server hochzuladen.  
  
 Das **Stream** -Objekt muss vor dem Aufruf von **LoadFromFile**bereits geöffnet sein. Mit dieser Methode wird die Bindung des Daten **Strom** Objekts nicht geändert. Sie wird weiterhin an das Objekt gebunden, das von der URL oder dem **Datensatz** angegeben wird, mit dem der **Stream** ursprünglich geöffnet wurde.  
  
 **LoadFromFile** überschreibt den aktuellen Inhalt des **Streamobjekts** mit aus der Datei gelesenen Daten. Alle vorhandenen Bytes im **Stream** werden durch den Inhalt der Datei überschrieben. Alle bereits vorhandenen und verbleibenden Bytes, die nach der von **LoadFromFile**erstellten [EOS](../../../ado/reference/ado-api/eos-property.md) liegen, werden abgeschnitten.  
  
 Nach dem Aufrufen von **LoadFromFile**wird die aktuelle Position auf den Anfang des **Streams** festgelegt ([Position](../../../ado/reference/ado-api/position-property-ado.md) ist 0).  
  
 Da dem Anfang des Streams für die Codierung 2 Bytes hinzugefügt werden können, entspricht die Größe des Streams möglicherweise nicht exakt der Größe der Datei, aus der Sie geladen wurde.  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
