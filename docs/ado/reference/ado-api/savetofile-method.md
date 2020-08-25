---
description: SaveToFile-Methode
title: Savedefile-Methode | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_SaveToFile
- _Stream::SaveToFile
helpviewer_keywords:
- SaveToFile method [ADO]
ms.assetid: 8a8594f2-422b-4d2e-94f8-7fe337445900
author: rothja
ms.author: jroth
ms.openlocfilehash: a1f6890d25922789a4b3656429582e4e8a60efc1
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777549"
---
# <a name="savetofile-method"></a>SaveToFile-Methode
Speichert den binären Inhalt eines [Streams](./stream-object-ado.md) in einer Datei.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Stream.SaveToFile FileName, SaveOptions  
```  
  
#### <a name="parameters"></a>Parameter  
 *FileName*  
 Ein **Zeichen** folgen Wert, der den voll qualifizierten Namen der Datei enthält, in der der Inhalt des **Streams** gespeichert wird. Sie können an einem beliebigen gültigen lokalen Speicherort oder an einem beliebigen Speicherort speichern, auf den Sie über einen UNC-Wert zugreifen können.  
  
 *SaveOptions*  
 Ein [saveoptionsenum](./saveoptionsenum.md) -Wert, der angibt, ob eine neue Datei von **savedefile**erstellt werden soll, wenn Sie nicht bereits vorhanden ist. Der Standardwert ist **adsavecreatenotexists**. Mit diesen Optionen können Sie angeben, dass ein Fehler auftritt, wenn die angegebene Datei nicht vorhanden ist. Sie können auch angeben, dass **savedefile** den aktuellen Inhalt einer vorhandenen Datei überschreibt.  
  
> [!NOTE]
>  Wenn Sie eine vorhandene Datei überschreiben (wenn **adsavecreateüberschreit** festgelegt ist), werden alle Bytes aus der ursprünglichen vorhandenen Datei, die auf die neue [EOS](./eos-property.md)folgt, von **savedefile** abgeschnitten.  
  
## <a name="remarks"></a>Bemerkungen  
 **Savedefile** kann verwendet werden, um den Inhalt eines Daten **Strom** Objekts in eine lokale Datei zu kopieren. Der Inhalt oder die Eigenschaften des Daten **Strom** Objekts sind nicht geändert. Das **Stream** -Objekt muss vor dem Aufrufen von **SaveToFile**geöffnet sein.  
  
 Mit dieser Methode wird die Zuordnung des Daten **Strom** Objekts zu seiner zugrunde liegenden Quelle nicht geändert. Das **Stream** -Objekt wird nach wie vor mit der ursprünglichen URL oder dem **Daten Satz** verknüpft, der beim Öffnen der Quelle war.  
  
 Nach einem **savedefile** -Vorgang wird die aktuelle Position ([Position](./position-property-ado.md)) im Stream auf den Anfang des Streams (0) festgelegt.  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](./stream-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Open-Methode (ADO-Stream)](./open-method-ado-stream.md)   
 [Save-Methode](./save-method.md)