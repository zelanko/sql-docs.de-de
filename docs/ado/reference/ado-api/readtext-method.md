---
title: ReadText-Methode | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 9d57b193cd66c4c6428e3c60d6b1ef5d6331ffc9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47613258"
---
# <a name="readtext-method"></a>ReadText-Methode
Liest eine angegebene Anzahl von Zeichen aus einem Textobjekt [Stream](../../../ado/reference/ado-api/stream-object-ado.md) Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
String = Stream.ReadText ( NumChars)  
```  
  
#### <a name="parameters"></a>Parameter  
 *"NUMCHARS"*  
 Optional. Ein **lange** Wert, der die Anzahl der zu lesenden Zeichen aus der Datei angibt oder ein [StreamReadEnum](../../../ado/reference/ado-api/streamreadenum.md) Wert. Der Standardwert ist **AdReadAll**.  
  
## <a name="return-value"></a>Rückgabewert  
 Die **ReadText** Methode liest eine angegebene Anzahl von Zeichen, eine ganze Zeile oder der gesamte Stream, aus einem **Stream** Objekt und gibt die resultierende Zeichenfolge zurück.  
  
## <a name="remarks"></a>Hinweise  
 Wenn *NUMCHARS angegebene* bleibt mehr als die Anzahl der Zeichen im Datenstrom, der nur die verbleibenden Zeichen zurückgegeben werden. Die Zeichenfolge zu lesen ist nicht entsprechend die vom angegebenen Länge aufgefüllt *NUMCHARS angegebene*. Wenn es keine sind um zu lesenden Zeichen, wird ein Variant-Wert, dessen Wert null wird, zurückgegeben. **ReadText** kann nicht verwendet werden, um rückwärts zu lesen.  
  
> [!NOTE]
>  Die **ReadText** Methode wird verwendet, mit dem Text-Streams ([Typ](../../../ado/reference/ado-api/type-property-ado-stream.md) ist **AdTypeText**). Für binäre Datenströme (**Typ** ist **AdTypeBinary**), verwenden Sie [lesen](../../../ado/reference/ado-api/read-method.md).  
  
 Abfragen, die sich eine große Menge von XML-Daten, die zurückgegeben wird ergeben, über die **ReadText** -Methode des Objekts ActiveX Data Object (ADO)-Stream kann viel Zeit für die Ausführung dauern, geschieht dies in einer COM+-Komponente, die aufgerufen wird, aus einer ASP-Seite kann ein Timeout der Sitzung des Benutzers. ADO werden Objektdaten Stream aus UTF-8-Codierung in Unicode konvertiert; die neuzuordnung häufig Speicher bei der Konvertierung von solch eine große Menge von Daten werden gleichzeitig beteiligt ist oft sehr zeitaufwendig. Um zu beheben, stellen Sie wiederholte Aufrufe von der **ReadText** Methode von der ADO command-Objekt, und geben Sie eine kleinere Anzahl von Zeichen. Tests haben gezeigt, dass der Wert auf 128 KB (131.072) optimal geeignet ist. Antwortzeiten verkürzt, da dieser Wert verringert wird. Weitere Informationen finden Sie im Knowledge Base-Artikel 280067, "PRB: Abrufen von sehr großen XML-Dokumenten aus SQLServer 2000 mit ReadText-Methode der ADO-Stream-Objekt kann langsam sein", in der Microsoft Knowledge Base unter http://support.microsoft.com.  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Read-Methode](../../../ado/reference/ado-api/read-method.md)
