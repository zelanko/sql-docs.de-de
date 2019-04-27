---
title: Bcp_getcolfmt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_getcolfmt
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_getcolfmt function
ms.assetid: f8bdada5-7b2d-4475-8c98-f93e9d77b130
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: db8b433652829b16890552a70bd1e0d08d1c1bc4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62689091"
---
# <a name="bcpgetcolfmt"></a>bcp_getcolfmt
  Zum Suchen des Spaltenformat-Eigenschaftswerts.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RETCODE bcp_getcolfmt (  
HDBC   
hdbc  
,  
INT   
field  
,  
INT   
property  
,  
void*   
pValue  
,  
INT   
cbvalue,  
INT*   
pcbLen  
);  
  
```  
  
## <a name="arguments"></a>Argumente  
 *hdbc*  
 Das für den Massenkopiervorgang aktivierte ODBC-Verbindungshandle.  
  
 *field*  
 Die Spaltenzahl, für die die Eigenschaft abgerufen wird.  
  
 *property*  
 Eine der Eigenschaftskonstanten.  
  
 *pValue*  
 Der Verweis auf den Puffer, von dem der Eigenschaftswert abgerufen werden soll.  
  
 *cbValue*  
 Die Länge des Puffers der Eigenschaft in Bytes.  
  
 *pcbLen*  
 Verweis auf Länge der Daten, die im Eigenschaftspuffer zurückgegeben werden.  
  
## <a name="returns"></a>Rückgabewert  
 SUCCEED oder FAIL.  
  
## <a name="remarks"></a>Hinweise  
 Spaltenformat-Eigenschaftswerte finden Sie in der [Bcp_setcolfmt](bcp-setcolfmt.md) Thema. Die Spaltenformat-Eigenschaftswerte werden festgelegt, durch den Aufruf der **Bcp_setcolfmt** -Funktion, und die **Bcp_getcolfmt** Funktion wird verwendet, um das Spaltenformat-Eigenschaftswert suchen.  
  
 Verändertes Programmverhalten können beobachtet werden, beim Herstellen einer Verbindung mit einem [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] (oder höher) Server-Computer im Vergleich zu früher [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Versionen. Weitere Informationen finden Sie unter [Metadatenermittlung](../native-client/features/metadata-discovery.md).  
  
## <a name="bcpgetcolfmt-support-for-enhanced-date-and-time-features"></a>bcp_getcolfmt-Unterstützung für erweiterte Funktionen für Datum und Uhrzeit  
 Die Typen der Verwendung der `BCP_FMT_TYPE` -Eigenschaft für Datums-/Uhrzeittypen werden gemäß den Angaben in [Massenkopieränderungen für verbesserte Datums- und Uhrzeittypen &#40;OLEDB- und ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).  
  
 Weitere Informationen finden Sie unter [Datums- / Uhrzeitverbesserungen &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Massenkopierfunktionen](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
