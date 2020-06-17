---
title: Description-Eigenschaft | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Description-Eigenschaft des Error-Objekts in ADO, das einen Zeichen folgen Wert zurückgibt, der eine Beschreibung des Fehlers enthält.
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error::Description
- Error::GetDescription
- Error::get_Description
helpviewer_keywords:
- Description property
ms.assetid: 4b5d6790-6c29-42aa-bf78-d9cfb8ad7965
author: rothja
ms.author: jroth
ms.openlocfilehash: 5bbaa998c419ba1a0af49ffa28e32fe91ffc96b9
ms.sourcegitcommit: 5c7634b007f6808c87094174b80376cb20545d5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84880545"
---
# <a name="description-property"></a>Description-Eigenschaft
Beschreibt ein [Fehler](../../../ado/reference/ado-api/error-object.md) Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen **Zeichen** folgen Wert zurück, der eine Beschreibung des Fehlers enthält.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **Description** -Eigenschaft, um eine kurze Beschreibung des Fehlers zu erhalten. Zeigen Sie diese Eigenschaft an, um den Benutzer auf einen Fehler aufmerksam zu machen, den Sie nicht oder nicht verarbeiten möchten. Die Zeichenfolge stammt entweder aus ADO oder einem Anbieter.  
  
 Anbieter sind dafür verantwortlich, bestimmten Fehlertext an ADO zu übergeben. ADO fügt der **Fehler** Auflistung für jeden empfangende Anbieter Fehler oder jede empfangene Warnung ein [Fehler](../../../ado/reference/ado-api/error-object.md) Objekt hinzu. Auflisten der **Fehler** Auflistung, um die Fehler zu verfolgen, die der Anbieter übergibt.  
  
## <a name="applies-to"></a>Gilt für  
 [Error-Objekt](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Beschreibung, HelpContext, HelpFile, NativeError, Number, Source und SQLSTATE Properties (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Beschreibung, HelpContext, HelpFile, NativeError, Number, Source und SQLSTATE Properties Example (VC + +)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [HelpContext, HelpFile-Eigenschaften](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [Number-Eigenschaft (ADO)](../../../ado/reference/ado-api/number-property-ado.md)   
 [Source-Eigenschaft (ADO Error)](../../../ado/reference/ado-api/source-property-ado-error.md)
