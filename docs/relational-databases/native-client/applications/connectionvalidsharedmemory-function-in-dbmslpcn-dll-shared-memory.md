---
title: Connectionvalidsharedmemory dbmslpcn. dll
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 6ae35826-7d75-4542-b686-5f79316b6157
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1f3bb097965563afb458b4529676d1e9967e4899
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303885"
---
# <a name="connectionvalidsharedmemory-function-in-dbmslpcndll-shared-memory"></a>Funktion „ConnectionValidSharedMemory“ in dbmslpcn.dll von Shared Memory
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Die Funktion bestimmt, ob SQL Server Shared Memory installiert und aktiv ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
BOOL ConnectionValidSharedMemory(char * szServerName);  
```  
  
## <a name="parameters"></a>Parameter  
 *szservername*  
  
-   Typ: **Char\* **  
  
-   Der Name des SQL-Servers.  
  
## <a name="return-value"></a>Rückgabewert  
 Typ: **bool**  
  
 Gibt 0 zurück, wenn es nicht gültig ist. Andernfalls wird ungleich NULL zurückgegeben.  
  
  
