---
title: SqlToolsVSNativeHelpers | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: reference
ms.assetid: d33cb556-0380-490a-9220-b74062dbd6d9
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: a917e4a6fa60b311d3c369556fdf2558f4e6d06c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47614931"
---
# <a name="sqltoolsvsnativehelpers"></a>SqlToolsVSNativeHelpers
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Bibliothek, die SQL Server-Funktionalität in Visual Studio unterstützt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
BOOL WINAPI DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID /*lpReserved*/)  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Boolescher Wert, **True** , wenn der DLL-Einstiegspunkt ordnungsgemäß initialisiert wurde; andernfalls **False**.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [FrameWindowVisible](../relational-databases/sqltoolsvsnativehelpers-framewindowvisible.md)  
  
  
