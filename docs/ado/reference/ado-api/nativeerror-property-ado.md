---
description: NativeError-Eigenschaft (ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 0c22667a9cd5855e4715b8aa37774a9137ab3cc4
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88774059"
---
# <a name="nativeerror-property-ado"></a>NativeError-Eigenschaft (ADO)
Gibt den anbieterspezifischen Fehlercode für ein bestimmtes [Fehler](./error-object.md) Objekt an.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen **Long** -Wert zurück, der den Fehlercode angibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **NativeError** -Eigenschaft, um die datenbankspezifischen Fehlerinformationen für ein bestimmtes **Fehler** Objekt abzurufen. Wenn Sie z. b. den Microsoft ODBC-Anbieter für die OLE DB mit einer Microsoft SQL Server-Datenbank verwenden, werden systemeigene Fehlercodes, die aus SQL Server stammen, über ODBC und den ODBC-Anbieter an die ADO **NativeError** -Eigenschaft übergeben.  
  
## <a name="applies-to"></a>Gilt für  
 [Error-Objekt](./error-object.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Beschreibung, HelpContext, HelpFile, NativeError, Number, Source und SQLSTATE Properties (VB)](./description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Beschreibung, HelpContext, HelpFile, NativeError, Number, Source und SQLSTATE Properties Example (VC + +)](./description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)