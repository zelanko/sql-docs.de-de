---
title: Bcp_sendrow | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_sendrow
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_sendrow function
ms.assetid: ddbdb4bd-ad4e-4bf1-9a75-656aa26ce10a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3e8ef7aa7a4354f5a3fbc334504512b2ee8d131b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62688830"
---
# <a name="bcpsendrow"></a>'bcp_sendrow'
  Sendet eine Datenzeile aus Programmvariablen an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RETCODE bcp_sendrow (  
    HDBC   
hdbc  
);  
  
```  
  
## <a name="arguments"></a>Argumente  
 *hdbc*  
 Das für den Massenkopiervorgang aktivierte ODBC-Verbindungshandle.  
  
## <a name="returns"></a>Rückgabewert  
 SUCCEED oder FAIL.  
  
## <a name="remarks"></a>Hinweise  
 Die **bcp_sendrow** -Funktion erstellt eine Zeile aus Programmvariablen und sendet sie an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Vor dem Aufruf von **bcp_sendrow**müssen Sie Aufrufe an [bcp_bind](bcp-bind.md) vornehmen, um die Programmvariablen mit den Zeilendaten anzugeben.  
  
 Wird **bcp_bind** unter Angabe eines langen Datentyps variabler Länge wie einem *eDataType* -Parameter von SQLTEXT und einem *pData* -Parameter ungleich NULL aufgerufen, sendet **bcp_sendrow** wie bei jedem anderen Datentyp den gesamten Datenwert. Hat dagegen **bcp_bind** einen *pData* -Parameter mit NULL-Wert, gibt **bcp_sendrow** die Steuerung an die Anwendung zurück, sobald alle angegebenen Datenspalten an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]gesendet wurden. Die Anwendung kann dann wiederholt [bcp_moretext](bcp-moretext.md) aufrufen, um die langen Daten variabler Länge Segment für Segment an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu senden. Weitere Informationen finden Sie unter [bcp_moretext](bcp-moretext.md).  
  
 Wenn mit **bcp_sendrow** Zeilen aus Programmvariablen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabellen massenkopiert werden, wird für die Zeilen erst dann ein Commit durchgeführt, wenn der Benutzer [bcp_batch](bcp-batch.md) oder [bcp_done](bcp-done.md)aufruft. Der Benutzer kann **bcp_batch** wahlweise einmal für alle *n* Zeilen aufrufen oder dann, wenn bei den eingehenden Daten eine Pause auftritt. Wird **bcp_batch** nie aufgerufen, wird ein Commit für die Zeilen ausgeführt, wenn **bcp_done** aufgerufen wird.  
  
 Informationen über eine wichtige Änderung Massenkopieren ab [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], finden Sie unter [Durchführen von Massenkopiervorgängen &#40;ODBC&#41;](../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Massenkopierfunktionen](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
