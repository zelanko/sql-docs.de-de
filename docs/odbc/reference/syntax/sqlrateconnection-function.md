---
description: SQLRateConnection-Funktion
title: Sqlrateconnetction-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLRateConnection function [ODBC]
ms.assetid: e8da2ffb-d6ef-4ca7-824f-57afd29585d8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cc6b217e8d9e06c4ab011d15cfe016dfefc91d76
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487121"
---
# <a name="sqlrateconnection-function"></a>SQLRateConnection-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 3,81 Standards Compliance: ODBC  
  
 **Zusammenfassung**  
 **Sqlrateconnetction** bestimmt, ob ein Treiber eine vorhandene Verbindung im Verbindungspool wieder verwenden kann.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
  
SQLRETURN  SQLRateConnection(  
                SQLHDBC_INFO_TOKEN   hRequest,  
                SQLHDBC              hCandidateConnection,  
                BOOL                 fRequiredTransactionEnlistment,  
                TRANSID              transId,  
                DWORD *              pRating );  
```  
  
## <a name="arguments"></a>Argumente  
 *hrequest*  
 Der Ein Tokenhandle, das die neue Anwendungs Verbindungsanforderung darstellt.  
  
 *hcandidateconnetzction*  
 Der Die vorhandene Verbindung im Verbindungspool. Die Verbindung muss sich im geöffneten Zustand befinden.  
  
 *frequiredtransaktioneintragung*  
 Der Wenn true, erfordert die Wiederverwendung der *hcandidateconnetction* der vorhandenen Verbindung für die neue Verbindungsanforderung (*hrequest*) eine zusätzliche Eintragung.  
  
 *Transid*  
 Der Wenn *frequiredtransaktionenlistment* auf true festgelegt ist, stellt *Transid* die DTC-Transaktion dar, die von der Anforderung eingetragen wird. Wenn *frequiredtransaktionumlistment* false ist, wird *Transid* ignoriert.  
  
 *wird entfernt*  
 Ausgeben die Wiederverwendungs Bewertung von *hcandidateconnetction*für den *hrequest*. Diese Bewertung liegt zwischen 0 und 100 (einschließlich).  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Der Treiber-Manager verarbeitet keine Diagnoseinformationen, die von dieser Funktion zurückgegeben werden.  
  
## <a name="remarks"></a>Bemerkungen  
 **Sqlrateconnetction** erzeugt ein Ergebnis zwischen 0 und 100 (einschließlich), das angibt, wie gut eine vorhandene Verbindung mit der Anforderung übereinstimmt.  
  
|Ergebnis|Bedeutung (Wenn SQL_SUCCESS zurückgegeben wird)|  
|-----------|-----------------------------------------------|  
|0|*hcandidateconnetction* darf für den *hrequest*nicht wieder verwendet werden.|  
|Alle Werte zwischen 1 und 98 (einschließlich)|Je höher das Ergebnis, desto näher die *hcandidateconnetzction* mit *hrequest*.|  
|99|Es gibt nur falsche Übereinstimmungen in unbedeutenden Attributen.  Der Treiber-Manager sollte die Bewertungs Schleife abbrechen.|  
|100|Perfekte Entsprechung.  Der Treiber-Manager sollte die Bewertungs Schleife abbrechen.|  
|Jeder andere Wert größer als 100|*hcandidateconnetction* ist als unzustellbar gekennzeichnet und wird auch in einer zukünftigen Verbindungsanforderung nicht wieder verwendet.|  
  
 Der Treiber-Manager markiert eine Verbindung als unzustellbar, wenn der Rückgabecode etwas anderes als SQL_SUCCESS (einschließlich SQL_SUCCESS_WITH_INFO) oder die Bewertung größer als 100 ist. Diese unzustellbare Verbindung wird nicht wieder verwendet (auch bei zukünftigen Verbindungsanforderungen) und wird schließlich nach dem Durchlaufen von CPTimeout überschritten. Der Treiber-Manager findet weiterhin eine weitere Verbindung aus dem Pool, um die Rate zu bewerten.  
  
 Wenn der Treiber-Manager eine Verbindung wieder verwendet, deren Ergebnis streng kleiner als 100 (einschließlich 99) ist, ruft der Treiber-Manager SQLSetConnectAttr (SQL_ATTR_DBC_INFO_TOKEN) auf, um die Verbindung wieder in den von der Anwendung angeforderten Zustand zurückzusetzen. Der Treiber sollte die Verbindung in diesem Funktions aufrufsbefehl nicht zurücksetzen.  
  
 Wenn *frequiredtransaktionslistment* auf true festgelegt ist, benötigt die Wiederverwendung von *hcandidateconnetction* eine zusätzliche Eintragung (*Transid* ! = null) oder austragungs Zeichen (*Transid* = = null). Dies gibt die Kosten für die Wiederverwendung einer Verbindung an und gibt an, ob der Treiber die Verbindung eintragen und austragen soll, wenn die Verbindung wieder verwendet werden soll. Wenn *frequiretransaktionslistment* den Wert false hat, sollte der Treiber den Wert *Transid*ignorieren.  
  
 Der Treiber-Manager garantiert, dass das übergeordnete HENV-Handle von *hrequest* und *hcandidateconnetction* identisch ist. Der Treiber-Manager garantiert, dass die der *hrequest* -und *hcandidateconnetction* zugeordneten Pool-IDs identisch sind.  
  
 Anwendungen sollten diese Funktion nicht direkt aufzurufen. Ein ODBC-Treiber, der Treiber fähiges Verbindungspooling unterstützt, muss diese Funktion implementieren.  
  
 Fügen Sie sqlspi. h für die ODBC-Treiberentwicklung ein.  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln eines ODBC-Treibers](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Treiber fähiges Verbindungs Pooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Developing Connection-Pool Awareness in an ODBC Driver (Entwickeln von Verbindungspool-Unterstützung in einem ODBC-Treiber)](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
