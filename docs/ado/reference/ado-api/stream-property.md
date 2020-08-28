---
description: Stream-Eigenschaft
title: Stream-Eigenschaft | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 1903644370172e716de78bc49a68af03a742c125
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88988511"
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