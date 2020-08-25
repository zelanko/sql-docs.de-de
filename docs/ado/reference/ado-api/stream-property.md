---
description: Stream-Eigenschaft
title: Stream-Eigenschaft | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADOStreamConstruction::GetStream
- ADOStreamConstruction::PutStream
- ADOStreamConstruction::put_Stream
- ADOStreamConstruction::Stream
- ADOStreamConstruction::get_Stream
helpviewer_keywords:
- Stream property
ms.assetid: 4a44f9f6-0265-4c00-8def-d85b6af923b1
author: rothja
ms.author: jroth
ms.openlocfilehash: 97f378e1be87be95682bf2eeb05e112abfb96f9d
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777209"
---
# <a name="stream-property"></a>Stream-Eigenschaft
Ruft ein OLE DB **Stream** -Objekt von/für ein **adostreamconstruction** -Objekt ab oder legt es fest.  
  
 Lese-/Schreibzugriff.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT get_Stream([out, retval] IUnknown** ppStream);  
HRESULT put_Stream([in] IUnknown* pStream);  
```  
  
## <a name="parameters"></a>Parameter  
 *ppStream*  
 Zeiger auf ein OLE DB **Stream** -Objekt.  
  
 *pStream*  
 Ein OLE DB **Stream** -Objekt.  
  
## <a name="return-values"></a>Rückgabewerte  
 Diese Eigenschaften Methode gibt die HRESULT-Standardwerte zurück. Dies schließt S_OK und E_FAIL ein.  
  
## <a name="applies-to"></a>Gilt für  
 [ADOStreamConstruction-Schnittstelle](./adostreamconstruction-interface.md)