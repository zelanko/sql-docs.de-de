---
title: Befehl SET BLOCKSIZE | Microsoft-Dokumentation
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67997762"
---
# <a name="set-blocksize-command"></a>SET BLOCKSIZE-Befehl
Gibt an, wie der Speicherplatz für die Speicherung der Memo-Felder verwendet wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SET BLOCKSIZE TO nBytes  
```  
  
## <a name="arguments"></a>Argumente  
 *nBytes*  
 Gibt die Blockgröße, die in der Speicherplatz für Memo-Felder verwendet wird. Wenn *nBytes* gleich 0 ist, wird Speicherplatz auf dem Datenträger als einzelbytes (Blöcke von 1 Byte) zugeordnet. Wenn *nBytes* ist, wird eine ganze Zahl zwischen 1 und 32, Speicherplatz auf dem Datenträger zugeordnet, in Blöcken von *nBytes* Bytes multipliziert mit 512. Wenn *nBytes* ist größer als 32, Speicherplatz wird verwendet, in Blöcken von *nBytes* Bytes. Wenn Sie einen Block-Größenwert, der größer als 32 angeben, können Sie erhebliche Speicherplatz sparen.  
  
## <a name="remarks"></a>Hinweise  
 Der Standardwert für BLOCKSIZE festgelegt ist 64. Um die Blockgröße auf einen anderen Wert zurückzusetzen, nachdem die Datei erstellt wurde, legen Sie ihn auf einen neuen Wert aus, und klicken Sie dann verwenden Sie kopieren, um eine neue Tabelle zu erstellen. Die neue Tabelle weist die angegebene Blockgröße.
