---
title: Funktion "ConnectionValidSharedMemory" in dbmslpcn.dll von Shared Memory-Protokoll | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 6ae35826-7d75-4542-b686-5f79316b6157
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 49885ca7d11ef7dbbe716375c399fe5fc4d4c93e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68069314"
---
# <a name="connectionvalidsharedmemory-function-in-dbmslpcndll-shared-memory"></a>Funktion „ConnectionValidSharedMemory“ in dbmslpcn.dll von Shared Memory
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Die Funktion bestimmt, ob SQL Server Shared Memory installiert und aktiv ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
BOOL ConnectionValidSharedMemory(char * szServerName);  
```  
  
## <a name="parameters"></a>Parameter  
 *szServerName*  
  
-   Typ: **Char\***  
  
-   Der Name der SqlServer.  
  
## <a name="return-value"></a>Rückgabewert  
 Typ: **"BOOL"**  
  
 Gibt 0, wenn nicht gültig Gibt andernfalls ungleich NULL zurück.  
  
  
