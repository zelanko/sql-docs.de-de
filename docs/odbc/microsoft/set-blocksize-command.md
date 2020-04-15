---
title: SET BLOCKSIZE Befehl | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- set blocksize command [ODBC]
ms.assetid: 0c11580f-37f5-4a8e-99be-9fb9c44bb433
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3eb9fbe9df90f7ddafebc6baa029164a578a6da3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300900"
---
# <a name="set-blocksize-command"></a>SET BLOCKSIZE-Befehl
Gibt an, wie Speicherplatz für die Speicherung von Memofeldern reserviert wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SET BLOCKSIZE TO nBytes  
```  
  
## <a name="arguments"></a>Argumente  
 *nBytes*  
 Gibt die Blockgröße an, in der Speicherplatz für Memofelder zugeordnet ist. Wenn *nBytes* 0 ist, wird Speicherplatz in einzelnen Bytes (Blöcke von 1 Byte) zugewiesen. Wenn *nBytes* eine ganze Zahl zwischen 1 und 32 ist, wird Speicherplatz in Blöcken von *nBytes* Bytes multipliziert mit 512 zugewiesen. Wenn *nBytes* größer als 32 ist, wird Speicherplatz in Blöcken von *nBytes* Bytes zugewiesen. Wenn Sie einen Blockgrößenwert größer als 32 angeben, können Sie erheblichen Speicherplatz sparen.  
  
## <a name="remarks"></a>Bemerkungen  
 Der Standardwert für SET BLOCKSIZE ist 64. Um die Blockgröße auf einen anderen Wert zurückzusetzen, nachdem die Datei erstellt wurde, legen Sie sie auf einen neuen Wert fest, und verwenden Sie dann COPY, um eine neue Tabelle zu erstellen. Die neue Tabelle hat die angegebene Blockgröße.
