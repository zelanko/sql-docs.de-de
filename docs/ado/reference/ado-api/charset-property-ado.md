---
title: Charset-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Charset
helpviewer_keywords:
- Charset property [ADO]
ms.assetid: e42507cb-9b46-4ce4-8191-2948eaf14ca2
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: da9e41d594890b399be975a9f1465a6bff50010a
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66698806"
---
# <a name="charset-property-ado"></a>Charset-Eigenschaft (ADO)
Gibt den Zeichensatz in den der Inhalt einer [Stream](../../../ado/reference/ado-api/stream-object-ado.md) übersetzt werden soll, für die Speicherung im internen Puffer von der **Stream** Objekt.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt eine **Zeichenfolge** Wert, der angibt, das Zeichen festgelegt werden, in dem der Inhalt des der **Stream** übersetzt werden. Der Standardwert ist **Unicode**. Zulässige Werte sind typische Zeichenfolgen, die über die Schnittstelle übergeben werden, als Zeichen Satz Internetnamen (z. B. "Iso-8859-1", "Windows-1252" und So weiter). Eine Liste der Namen das Zeichen, die von einem System bekannt sind, finden Sie unter dem Unterschlüssel des HKEY_CLASSES_ROOT\MIME\Database\Charset in der Windows-Registrierung.  
  
## <a name="remarks"></a>Hinweise  
 In einem Text **Stream** Textdaten befindet sich in den Zeichensatz, der vom angegebenen Objekt der **Charset** Eigenschaft. Der Standardwert ist Unicode. Die **Charset** Eigenschaft wird verwendet, für die Konvertierung von Daten in die **Stream** oder kommenden aus der **Stream**. Z. B. wenn die **Stream** enthält ISO-8859-1-Daten als auch, dass Daten, auf ein BSTR kopiert werden, das **Stream** Objekt die Daten in Unicode konvertiert. Das Gegenteil trifft ebenfalls zu.  
  
 Für eine offene **Stream**, die aktuelle [Position](../../../ado/reference/ado-api/position-property-ado.md) muss am Anfang der **Stream** (0) festlegen können **Charset**.  
  
 **CharSet** wird verwendet, nur mit Text **Stream** Objekte ([Typ](../../../ado/reference/ado-api/type-property-ado-stream.md) ist **AdTypeText**). Diese Eigenschaft wird ignoriert, wenn **Typ** ist **AdTypeBinary**.  
  
 Ein Codebeispiel finden Sie unter [Schritt 4: Auffüllen des Texfelds "Details"](../../../ado/guide/data/step-4-populate-the-details-text-box.md).  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
