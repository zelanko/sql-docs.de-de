---
title: NativeError-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error::GetNativeError
- Error::get_NativeError
- Error::NativeError
helpviewer_keywords:
- NativeError property [ADO]
ms.assetid: b9b47e57-18a4-4186-aef5-5bd18d7b1d74
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 42888190dcd7b5e41987e6e8ec7194242549aa9c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67918018"
---
# <a name="nativeerror-property-ado"></a>NativeError-Eigenschaft (ADO)
Gibt den anbieterspezifischen Fehlercode für ein bestimmtes [Fehler](../../../ado/reference/ado-api/error-object.md) Objekt an.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen **Long** -Wert zurück, der den Fehlercode angibt.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden Sie die **NativeError** -Eigenschaft, um die datenbankspezifischen Fehlerinformationen für ein bestimmtes **Fehler** Objekt abzurufen. Wenn Sie z. b. den Microsoft ODBC-Anbieter für die OLE DB mit einer Microsoft SQL Server-Datenbank verwenden, werden systemeigene Fehlercodes, die aus SQL Server stammen, über ODBC und den ODBC-Anbieter an die ADO **NativeError** -Eigenschaft übergeben.  
  
## <a name="applies-to"></a>Gilt für  
 [Error-Objekt](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Beschreibung, HelpContext, HelpFile, NativeError, Number, Source und SQLSTATE Properties (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Beschreibung, HelpContext, HelpFile, NativeError, Number, Source und SQLSTATE Properties Example (VC + +)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
