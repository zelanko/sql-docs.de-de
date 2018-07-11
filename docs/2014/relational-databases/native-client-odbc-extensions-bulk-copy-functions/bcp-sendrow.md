---
title: Bcp_sendrow | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
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
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2810dd25a14f35ed275a7d1117fc21d7946cc90e
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37423539"
---
# <a name="bcpsendrow"></a>'bcp_sendrow'
  Sendet eine Datenzeile aus Programmvariablen nach [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RETCODE bcp_sendrow (  
    HDBC   
hdbc  
);  
  
```  
  
## <a name="arguments"></a>Argumente  
 *HDBC*  
 Das für den Massenkopiervorgang aktivierte ODBC-Verbindungshandle.  
  
## <a name="returns"></a>Rückgabewert  
 SUCCEED oder FAIL.  
  
## <a name="remarks"></a>Hinweise  
 Die **Bcp_sendrow** Funktion erstellt eine Zeile aus Programmvariablen und sendet sie an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Vor dem Aufruf **Bcp_sendrow**, es müssen Aufrufe [Bcp_bind](bcp-bind.md) um die Programmvariablen mit den Zeilendaten anzugeben.  
  
 Wird **bcp_bind** unter Angabe eines langen Datentyps variabler Länge wie einem *eDataType* -Parameter von SQLTEXT und einem *pData* -Parameter ungleich NULL aufgerufen, sendet **bcp_sendrow** wie bei jedem anderen Datentyp den gesamten Datenwert. IF, allerdings **Bcp_bind** enthält eine NULL *pData* Parameter **Bcp_sendrow** übergibt die Steuerung an die Anwendung sofort, nachdem alle Spalten mit den angegebenen Daten an gesendet werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Die Anwendung kann dann aufrufen [Bcp_moretext](bcp-moretext.md) wiederholt, um die langen variabler Länge, die Daten zu senden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ein Segment zu einem Zeitpunkt. Weitere Informationen finden Sie unter [Bcp_moretext](bcp-moretext.md).  
  
 Wenn **Bcp_sendrow** wird verwendet, um Zeilen aus Programmvariablen in massenkopiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabellen wird ein Commit Zeilen nur, wenn der Benutzer ruft [Bcp_batch](bcp-batch.md) oder [Bcp_done](bcp-done.md) . Der Benutzer kann **bcp_batch** wahlweise einmal für alle *n* Zeilen aufrufen oder dann, wenn bei den eingehenden Daten eine Pause auftritt. Wird **bcp_batch** nie aufgerufen, wird ein Commit für die Zeilen ausgeführt, wenn **bcp_done** aufgerufen wird.  
  
 Informationen über eine wichtige Änderung Massenkopieren ab [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], finden Sie unter [Durchführen von Massenkopiervorgängen &#40;ODBC&#41;](../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Massenkopierfunktionen](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
