---
title: Bcp_sendrow | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- bcp_sendrow
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_sendrow function
ms.assetid: ddbdb4bd-ad4e-4bf1-9a75-656aa26ce10a
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 84a8e4c35d752e8ee8bf34ac3ee754e57173f8ff
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68099449"
---
# <a name="bcpsendrow"></a>'bcp_sendrow'
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Sendet eine Datenzeile aus Programmvariablen an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RETCODE bcp_sendrow (  
    HDBC hdbc);  
```  
  
## <a name="arguments"></a>Argumente  
 *hdbc*  
 Das für den Massenkopiervorgang aktivierte ODBC-Verbindungshandle.  
  
## <a name="returns"></a>Rückgabewert  
 SUCCEED oder FAIL.  
  
## <a name="remarks"></a>Hinweise  
 Die **bcp_sendrow** -Funktion erstellt eine Zeile aus Programmvariablen und sendet sie an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Vor dem Aufruf von **bcp_sendrow**müssen Sie Aufrufe an [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) vornehmen, um die Programmvariablen mit den Zeilendaten anzugeben.  
  
 Wenn **Bcp_bind** heißt die Angabe eines langen Daten variabler Länge-Typs, z. B. eine *eDataType* -Parameter von SQLTEXT und ein Wert ungleich NULL *pData* -Parameter, **Bcp_sendrow** sendet den gesamten Datenwert, genau wie bei jedem anderen Datentyp. Hat dagegen **bcp_bind** einen *pData* -Parameter mit NULL-Wert, gibt **bcp_sendrow** die Steuerung an die Anwendung zurück, sobald alle angegebenen Datenspalten an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]gesendet wurden. Die Anwendung kann dann wiederholt [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md) aufrufen, um die langen Daten variabler Länge Segment für Segment an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu senden. Weitere Informationen finden Sie unter [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md).  
  
 Wenn mit **bcp_sendrow** Zeilen aus Programmvariablen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabellen massenkopiert werden, wird für die Zeilen erst dann ein Commit durchgeführt, wenn der Benutzer [bcp_batch](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md) oder [bcp_done](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-done.md)aufruft. Der Benutzer kann **bcp_batch** wahlweise einmal für alle *n* Zeilen aufrufen oder dann, wenn bei den eingehenden Daten eine Pause auftritt. Wird **bcp_batch** nie aufgerufen, wird ein Commit für die Zeilen ausgeführt, wenn **bcp_done** aufgerufen wird.  
  
 Informationen über eine wichtige Änderung Massenkopieren ab [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], finden Sie unter [Durchführen von Massenkopiervorgängen &#40;ODBC&#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Massenkopierfunktionen](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
