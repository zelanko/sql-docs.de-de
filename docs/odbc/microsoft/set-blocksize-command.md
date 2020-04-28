---
title: Block Size-Befehl festlegen | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300900"
---
# <a name="set-blocksize-command"></a>SET BLOCKSIZE-Befehl
Gibt an, wie Speicherplatz für die Speicherung von Memo Feldern zugeordnet wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SET BLOCKSIZE TO nBytes  
```  
  
## <a name="arguments"></a>Argumente  
 *nBytes*  
 Gibt die Blockgröße an, in der Speicherplatz für Memo Felder zugeordnet wird. Wenn *nbytes* den Wert 0 hat, wird der Speicherplatz in einzelnen Bytes (Blöcke von 1 Byte) zugeordnet. Wenn *nbytes* eine ganze Zahl zwischen 1 und 32 ist, wird der Speicherplatz in Blöcken von *nbyte* -Bytes multipliziert mit 512 zugeordnet. Wenn *nbytes* größer als 32 ist, wird Speicherplatz in Blöcken von *nbyte* -Bytes zugeordnet. Wenn Sie einen Wert für die Blockgröße angeben, der größer als 32 ist, können Sie erheblichen Speicherplatz sparen.  
  
## <a name="remarks"></a>Bemerkungen  
 Der Standardwert für Set BLOCKSIZE ist 64. Wenn Sie die Blockgröße nach dem Erstellen der Datei auf einen anderen Wert zurücksetzen möchten, legen Sie Sie auf einen neuen Wert fest, und verwenden Sie dann Copy, um eine neue Tabelle zu erstellen. Die neue Tabelle hat die angegebene Blockgröße.
