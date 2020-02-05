---
title: FrameWindowVisible | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 9091d714-98bc-43ec-b8d1-9c892cb57f19
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 228238f4a326790f22f0298beb2e1b51fbfcf7d5
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "68126581"
---
# <a name="sqltoolsvsnativehelpers---framewindowvisible"></a>SqlToolsVSNativeHelpers – FrameWindowVisible
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Eigenschaft, die angibt, ob ein angegebener Fensterrahmen sichtbar ist. Die Hilfsmethode wird in verwaltetem Code verwendet.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
BOOL WINAPI IsFrameWindowVisible(IVsWindowFrame* frame)  
{  
    if (NULL == frame)  
    {  
        return FALSE;  
    }  
  
    return S_OK == frame->IsVisible();  
}  
```  
  
#### <a name="parameters"></a>Parameter  
 *frame*  
  
 IVsWindowFrame*-Zeiger auf Visual Studio WindowFrame.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Boolescher Wert, der angibt, ob der Fensterrahmen, der durch *frame* angegeben wird, sichtbar ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SqlToolsVSNativeHelpers](../relational-databases/sqltoolsvsnativehelpers.md)  
  
  
