---
title: Bcp_sendrow | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- bcp_sendrow
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_sendrow function
ms.assetid: ddbdb4bd-ad4e-4bf1-9a75-656aa26ce10a
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 937ea3a4086e65712f77b569976902fbd2038007
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2018
ms.locfileid: "39561910"
---
# <a name="bcpsendrow"></a>'bcp_sendrow'
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Sendet eine Datenzeile aus Programmvariablen nach [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RETCODE bcp_sendrow (  
    HDBC hdbc);  
```  
  
## <a name="arguments"></a>Argumente  
 *HDBC*  
 Das für den Massenkopiervorgang aktivierte ODBC-Verbindungshandle.  
  
## <a name="returns"></a>Rückgabewert  
 SUCCEED oder FAIL.  
  
## <a name="remarks"></a>Hinweise  
 Die **Bcp_sendrow** Funktion erstellt eine Zeile aus Programmvariablen und sendet sie an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Vor dem Aufruf **Bcp_sendrow**, es müssen Aufrufe [Bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) um die Programmvariablen mit den Zeilendaten anzugeben.  
  
 Wenn **Bcp_bind** heißt die Angabe eines langen Daten variabler Länge-Typs, z. B. eine *eDataType* -Parameter von SQLTEXT und ein Wert ungleich NULL *pData* -Parameter, **Bcp_sendrow** sendet den gesamten Datenwert, genau wie bei jedem anderen Datentyp. IF, allerdings **Bcp_bind** enthält eine NULL *pData* Parameter **Bcp_sendrow** übergibt die Steuerung an die Anwendung sofort, nachdem alle Spalten mit den angegebenen Daten an gesendet werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Die Anwendung kann dann aufrufen [Bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md) wiederholt, um die langen variabler Länge, die Daten zu senden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ein Segment zu einem Zeitpunkt. Weitere Informationen finden Sie unter [Bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md).  
  
 Wenn **Bcp_sendrow** wird verwendet, um Zeilen aus Programmvariablen in massenkopiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabellen wird ein Commit Zeilen nur, wenn der Benutzer ruft [Bcp_batch](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md) oder [Bcp_done](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-done.md) . Der Benutzer kann **bcp_batch** wahlweise einmal für alle *n* Zeilen aufrufen oder dann, wenn bei den eingehenden Daten eine Pause auftritt. Wird **bcp_batch** nie aufgerufen, wird ein Commit für die Zeilen ausgeführt, wenn **bcp_done** aufgerufen wird.  
  
 Informationen über eine wichtige Änderung Massenkopieren ab [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], finden Sie unter [Durchführen von Massenkopiervorgängen &#40;ODBC&#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Massenkopierfunktionen](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
