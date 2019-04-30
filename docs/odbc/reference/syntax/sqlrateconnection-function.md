---
title: SQLRateConnection-Funktion | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3d36224329fa29a54f7163cb4e1ce6228f460875
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63262499"
---
# <a name="sqlrateconnection-function"></a>SQLRateConnection-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 3.81 Standards Compliance: ODBC  
  
 **Zusammenfassung**  
 **SQLRateConnection** bestimmt, ob ein Treiber eine vorhandene Verbindung im Verbindungspool wiederverwendet werden kann.  
  
## <a name="syntax"></a>Syntax  
  
```  
SQLRETURN  SQLRateConnection(  
                SQLHDBC_INFO_TOKEN   hRequest,  
                SQLHDBC              hCandidateConnection,  
                BOOL                 fRequiredTransactionEnlistment,  
                TRANSID              transId,  
                DWORD *              pRating );  
```  
  
## <a name="arguments"></a>Argumente  
 *hRequest*  
 [Eingabe] Ein token-Handle, das die neue verbindungsanforderung für die Anwendung darstellt.  
  
 *hCandidateConnection*  
 [Eingabe] Die vorhandene Verbindung im Verbindungspool. Die Verbindung muss geöffnet sein.  
  
 *fRequiredTransactionEnlistment*  
 [Eingabe] True gibt an, Wiederverwendung der vorhandenen Verbindungs *hCandidateConnection* für die neue verbindungsanforderung (*hRequest*) erfordert eine zusätzliche Eintragung.  
  
 *transId*  
 [Eingabe] Wenn *fRequiredTransactionEnlistment* ist "true", *Transaktions* stellt dar, die DTC-Transaktion, die die Anforderung eingetragen wird. Wenn *fRequiredTransactionEnlistment* ist "false", *Transaktions* ignoriert werden.  
  
 *pRating*  
 [Ausgabe] *hCandidateConnection*die Wiederverwendung, die für die Bewertung der *hRequest*. Diese Bewertung wird zwischen 0 und 100 (einschließlich) sein.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Der Treiber-Manager verarbeitet keine Diagnoseinformationen, die von dieser Funktion zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 **SQLRateConnection** erzeugt eine Bewertung zwischen 0 und 100 (einschließlich), der angibt, wie gut die Anforderung von eine vorhandene Verbindung übereinstimmt.  
  
|Ergebnis|Bedeutung (wenn SQL_SUCCESS zurückgegeben wird)|  
|-----------|-----------------------------------------------|  
|0|*hCandidateConnection* dürfen nicht wiederverwendet werden, für die *hRequest*.|  
|Alle Werte zwischen 1 und 98 (inklusiv)|Je höher die Bewertung, desto näher, *hCandidateConnection* stimmt mit *hRequest*.|  
|99|Es gibt nur Konflikte in nicht signifikanter Attribute ein.  Der Treiber-Manager sollte die Schleife für die Bewertung beendet.|  
|100|Perfekte Übereinstimmung.  Der Treiber-Manager sollte die Schleife für die Bewertung beendet.|  
|Alle anderen Werte, die größer als 100|*hCandidateConnection* als Warteschlange für unzustellbare Nachrichten und auch in eine zukünftige verbindungsanforderung nicht wiederverwendet werden markiert.|  
  
 Der Treiber-Manager wird eine Verbindung als unzustellbar markiert, wenn der Rückgabewert etwas anderes als SQL_SUCCESS ist (einschließlich SQL_SUCCESS_WITH_INFO) oder die Bewertung größer als 100 ist. Stillgelegten Verbindung wird nicht wiederverwendet werden (auch in zukünftigen verbindungsanforderungen) und schließlich Timeout nach CPTimeout übergibt. Der Treiber-Manager weiterhin eine andere Verbindung aus dem Pool zu Rate zu suchen.  
  
 Wenn der Treiber-Manager eine Verbindung wiederverwendet werden, deren Ergebnis streng kleiner als 100 (einschließlich 99) ist, ruft der Treiber-Manager SQLSetConnectAttr(SQL_ATTR_DBC_INFO_TOKEN), um die Verbindung wieder in den von der Anwendung angeforderten Zustand zurückzusetzen. Der Treiber sollte die Verbindung in Aufrufen der Funktion nicht zurückgesetzt werden.  
  
 Wenn *fRequiredTransactionEnlistment* ist "true" werden die Wiederverwendung von *hCandidateConnection* benötigt eine Eintragung zusätzliche (*Transaktions* ! = NULL) oder Unenlistment ( *Transaktions* == NULL). Dies gibt an, die Kosten für das Wiederverwenden einer Verbindung und gibt an, ob der Treiber sollte eintragen / die Verbindung, austragen Wenn es vor sich geht, die Verbindung erneut zu verwenden. Wenn *fRequireTransactionEnlistment* ist "false", Treiber, den Wert der ignorieren soll *Transaktions*.  
  
 Der Treiber-Manager wird sichergestellt, dass das übergeordnete Element HENV Handles aus *hRequest* und *hCandidateConnection* sind identisch. Der Treiber-Manager wird sichergestellt, dass die Pool-ID zugeordnet *hRequest* und *hCandidateConnection* sind identisch.  
  
 Anwendungen sollten diese Funktion nicht direkt aufrufen. Ein ODBC-Treiber, der treiberfähiges Verbindungspooling unterstützt, muss diese Funktion implementieren.  
  
 Umfassen Sie sqlspi.h für die Entwicklung von ODBC-Treiber.  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln einen ODBC-Treiber](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Treiberfähiges Verbindungspooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Developing Connection-Pool Awareness in an ODBC Driver (Entwickeln von Verbindungspool-Unterstützung in einem ODBC-Treiber)](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
