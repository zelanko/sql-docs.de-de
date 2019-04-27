---
title: Bcp_done | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_done
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_done function
ms.assetid: e59b3f16-5b59-40da-880f-f3edf657d1ee
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b0326330e3d2052e8e997a293f666a8fc725391b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62689076"
---
# <a name="bcpdone"></a>'bcp_done'
  Beendet einen Massenkopiervorgang aus Programmvariablen nach [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , der mit [bcp_sendrow](bcp-sendrow.md)ausgeführt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DBINT bcp_done (  
    HDBC   
hdbc  
);  
  
```  
  
## <a name="arguments"></a>Argumente  
 *hdbc*  
 Das für den Massenkopiervorgang aktivierte ODBC-Verbindungshandle.  
  
## <a name="returns"></a>Rückgabewert  
 Die Anzahl von Zeilen, die nach dem letzten Aufruf von [bcp_batch](bcp-batch.md) permanent gespeichert wurden, oder -1 im Fall eines Fehlers.  
  
## <a name="remarks"></a>Hinweise  
 Rufen Sie **bcp_done** nach dem letzten Aufruf von [bcp_sendrow](bcp-sendrow.md) oder [bcp_moretext](bcp-moretext.md)auf. Wenn Sie **bcp_done** nach dem Kopieren aller Daten nicht aufrufen, treten Fehler auf.  
  
## <a name="see-also"></a>Siehe auch  
 [Massenkopierfunktionen](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
