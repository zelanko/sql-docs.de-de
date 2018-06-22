---
title: SqlToolsVSNativeHelpers | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: d33cb556-0380-490a-9220-b74062dbd6d9
caps.latest.revision: 5
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 98384288159ca4dea6dbd1f70deeb0be834c15a0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050076"
---
# <a name="sqltoolsvsnativehelpers"></a>SqlToolsVSNativeHelpers
  Bibliothek, die SQL Server-Funktionalität in Visual Studio unterstützt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
BOOL WINAPI DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID /*lpReserved*/)  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein boolescher Wert `True` Wenn DLL-Einstiegspunkt ordnungsgemäß andernfalls initialisiert `False`.  
  
## <a name="see-also"></a>Siehe auch  
 [FrameWindowVisible](sqltoolsvsnativehelpers-framewindowvisible.md)  
  
  