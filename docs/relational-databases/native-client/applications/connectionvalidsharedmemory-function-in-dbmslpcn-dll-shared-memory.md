---
description: Funktion „ConnectionValidSharedMemory“ in dbmslpcn.dll von Shared Memory
title: Connectionvalidsharedmemory-dbmslpcn.dll
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 6ae35826-7d75-4542-b686-5f79316b6157
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a487eb380ea4e7b0fe246efdb9281cbab63a1303
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97475991"
---
# <a name="connectionvalidsharedmemory-function-in-dbmslpcndll-shared-memory"></a>Funktion „ConnectionValidSharedMemory“ in dbmslpcn.dll von Shared Memory
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Die Funktion bestimmt, ob SQL Server Shared Memory installiert und aktiv ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
BOOL ConnectionValidSharedMemory(char * szServerName);  
```  
  
## <a name="parameters"></a>Parameter  
 *szservername*  
  
-   Typ: **Char \** _  
  
-   Der Name des SQL-Servers.  
  
## <a name="return-value"></a>Rückgabewert  
 Typ: _ *bool**  
  
 Gibt 0 zurück, wenn es nicht gültig ist. Andernfalls wird ungleich NULL zurückgegeben.  
  
  
