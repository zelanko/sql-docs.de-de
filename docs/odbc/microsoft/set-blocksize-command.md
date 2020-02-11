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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4fe84a470f5e877c73701168394cd85d75253fb7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67997762"
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
