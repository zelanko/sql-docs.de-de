---
title: Read-Text-Methode | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_ReadText
- _Stream::ReadText
helpviewer_keywords:
- ReadText method [ADO]
ms.assetid: be5a409e-cf87-4859-9ea5-713401755a77
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d6c174d2e6a659a3b9da8f89816b5bdf90342416
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67917374"
---
# <a name="readtext-method"></a>ReadText-Methode
Liest die angegebene Anzahl von Zeichen aus einem [Textstreamobjekt](../../../ado/reference/ado-api/stream-object-ado.md) .  
  
## <a name="syntax"></a>Syntax  
  
```  
  
String = Stream.ReadText ( NumChars)  
```  
  
#### <a name="parameters"></a>Parameter  
 *NumChars*  
 Optional. Ein **Long** -Wert, der die Anzahl der Zeichen angibt, die aus der Datei gelesen werden sollen, oder ein [streamleseenumerationswert](../../../ado/reference/ado-api/streamreadenum.md) . Der Standardwert ist " **ADRead all**".  
  
## <a name="return-value"></a>Rückgabewert  
 Die Read **Text** -Methode liest eine angegebene Anzahl von Zeichen, eine ganze Zeile oder den gesamten Stream aus einem **Streamobjekt** und gibt die resultierende Zeichenfolge zurück.  
  
## <a name="remarks"></a>Hinweise  
 Wenn *NumChar* größer als die Anzahl der im Stream verbliebenen Zeichen ist, werden nur die verbleibenden Zeichen zurückgegeben. Die gelesene Zeichenfolge wird nicht so aufgefüllt, dass Sie der von *NumChar*angegebenen Länge entspricht. Wenn keine zu lesenden Zeichen vorhanden sind, wird eine Variante zurückgegeben, deren Wert NULL ist. "Read **Text** " kann nicht zum Rück Lesen verwendet werden.  
  
> [!NOTE]
>  Die Read **Text** -Methode wird mit Textstreams verwendet ([Type](../../../ado/reference/ado-api/type-property-ado-stream.md) ist **adtypetext**). Verwenden Sie für binäre Datenströme (**Typ** : **adTypeBinary**) den Wert [Lesen](../../../ado/reference/ado-api/read-method.md).  
  
 Abfragen, die zu einer großen Menge von XML-Daten führen, die durch die Read **Text** -Methode des ADO-Datenstrom Objekts (ActiveX Data Object) zurückgegeben werden, können viel Zeit in Anspruch nehmen. Wenn dies in einer COM+-Komponente erfolgt, die von einer ASP-Seite aufgerufen wird, kann ein Timeout für die Sitzung des Benutzers auftreten. ADO konvertiert streamobjektdaten von UTF-8-Codierung in Unicode. die häufige Umwandlung von Speicher Belegungen bei einer solchen großen Datenmenge auf einmal ist recht zeitaufwändig. Um das Problem zu beheben, führen Sie wiederholte Aufrufe der Read- **Text** -Methode des ADO-Befehls Objekts aus, und geben Sie eine geringere Anzahl von Zeichen an. Tests haben ergeben, dass ein Wert, der 128 KB (131.072) entspricht, optimal ist. Die Antwortzeit sinkt, wenn dieser Wert verringert wird. Weitere Informationen finden Sie im Knowledge Base-Artikel 280067, "PRB: Abrufen sehr großer XML-Dokumente aus SQL Server 2000 mithilfe der Read Text-Methode des ADO-Streamobjekts ist möglicherweise langsam" in der Microsoft https://support.microsoft.comKnowledge Base unter.  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Read-Methode](../../../ado/reference/ado-api/read-method.md)
