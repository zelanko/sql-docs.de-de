---
title: bcp_getcolfmt | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 793543cce582bd4e17cbf8d06f096056a2ecb89b
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82701973"
---
# <a name="bcp_getcolfmt"></a>bcp_getcolfmt
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
  
 *Flächen*  
 Die Spaltenzahl, für die die Eigenschaft abgerufen wird.  
  
 *property*  
 Eine der Eigenschaftskonstanten.  
  
 *pValue*  
 Der Verweis auf den Puffer, von dem der Eigenschaftswert abgerufen werden soll.  
  
 *cbValue*  
 Die Länge des Puffers der Eigenschaft in Bytes.  
  
 *pcbLen*  
 Verweis auf Länge der Daten, die im Eigenschaftspuffer zurückgegeben werden.  
  
## <a name="returns"></a>Gibt zurück  
 SUCCEED oder FAIL.  
  
## <a name="remarks"></a>Bemerkungen  
 Spalten Format-Eigenschaftswerte sind im Thema [bcp_setcolfmt](bcp-setcolfmt.md) aufgeführt. Die Spalten Format-Eigenschaftswerte werden durch Aufrufen der **bcp_setcolfmt** -Funktion festgelegt, und die **bcp_getcolfmt** -Funktion wird verwendet, um den Eigenschafts Wert des Spalten Formats zu suchen.  
  
 Verhaltensänderungen werden möglicherweise beim Herstellen einer Verbindung mit einem [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Server Computer (oder höher) im Vergleich zu früheren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Versionen beobachtet. Weitere Informationen finden Sie unter [Metadatenermittlung](../native-client/features/metadata-discovery.md).  
  
## <a name="bcp_getcolfmt-support-for-enhanced-date-and-time-features"></a>bcp_getcolfmt-Unterstützung für erweiterte Funktionen für Datum und Uhrzeit  
 Die Typen, die mit der- `BCP_FMT_TYPE` Eigenschaft für Datums-/Uhrzeittypen verwendet werden, sind wie in [Massen Kopier Änderungen für verbesserte Datums-und Uhrzeit Typen &#40;OLE DB und ODBC-&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)angegeben.  
  
 Weitere Informationen finden Sie unter [Verbesserungen bei Datum und Uhrzeit &#40;ODBC-&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bulk Copy Functions](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
