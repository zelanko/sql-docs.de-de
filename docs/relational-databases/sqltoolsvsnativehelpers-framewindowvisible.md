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
ms.openlocfilehash: d0a370d81be0c5220e23a04a45c3db5c9be0fca4
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85750845"
---
# <a name="sqltoolsvsnativehelpers---framewindowvisible"></a>SqlToolsVSNativeHelpers – FrameWindowVisible
[!INCLUDE [SQL Server Azure SQL Database](../includes/applies-to-version/sql-asdb.md)]
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
  
  
