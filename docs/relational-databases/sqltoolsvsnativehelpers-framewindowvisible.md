---
title: FrameWindowVisible | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: reference
ms.assetid: 9091d714-98bc-43ec-b8d1-9c892cb57f19
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: bacf2e0b9e109f36a29edb79d3e15aefe7aa1ce1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47623108"
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
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SqlToolsVSNativeHelpers](../relational-databases/sqltoolsvsnativehelpers.md)  
  
  
