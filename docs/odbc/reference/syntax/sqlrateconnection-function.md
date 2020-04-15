---
title: SQLRateConnection-Funktion | Microsoft Docs
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
ms.openlocfilehash: d29033460a7f89fc4a8b1c371a4d32bdf94a2a05
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288880"
---
# <a name="sqlrateconnection-function"></a>SQLRateConnection-Funktion
**Konformität**  
 Eingeführte Version: ODBC 3.81 Standard-Konformität: ODBC  
  
 **Zusammenfassung**  
 **SQLRateConnection** bestimmt, ob ein Treiber eine vorhandene Verbindung im Verbindungspool wiederverwenden kann.  
  
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
 *hRequest*  
 [Eingabe] Ein Tokenhandle, das die neue Anwendungsverbindungsanforderung darstellt.  
  
 *hCandidateConnection*  
 [Eingabe] Die vorhandene Verbindung im Verbindungspool. Die Verbindung muss sich in einem geöffneten Zustand befinden.  
  
 *fRequiredTransactionEnlistment*  
 [Eingabe] Wenn TRUE, erfordert die Wiederverwendung der *hCandidateConnection* der vorhandenen Verbindung für die neue Verbindungsanforderung (*hRequest*) eine zusätzliche Einschreibung.  
  
 *transId*  
 [Eingabe] Wenn *fRequiredTransactionEnlistment* TRUE ist, stellt *transId* die DTC-Transaktion dar, die von der Anforderung eingeschrieben wird. Wenn *fRequiredTransactionEnlistment* FALSE ist, wird *transId* ignoriert.  
  
 *pRating*  
 [Ausgabe] *hCandidateConnection*'s Wiederverwendungsbewertung für *hRequest*. Diese Bewertung liegt zwischen 0 und 100 (inklusive).  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Der Treiber-Manager verarbeitet keine Diagnoseinformationen, die von dieser Funktion zurückgegeben werden.  
  
## <a name="remarks"></a>Bemerkungen  
 **SQLRateConnection** erzeugt eine Punktzahl zwischen 0 und 100 (inklusive), die angibt, wie gut eine vorhandene Verbindung mit der Anforderung übereinstimmt.  
  
|Ergebnis|Bedeutung (wenn SQL_SUCCESS zurückgegeben wird)|  
|-----------|-----------------------------------------------|  
|0|*hCandidateConnection* darf für *hRequest*nicht wiederverwendet werden.|  
|Alle Werte zwischen 1 und 98 (inklusive)|Je höher die Punktzahl, desto näher ist die Übereinstimmung von *hCandidateConnection* mit *hRequest*.|  
|99|Es gibt nur Inkongruenzen in unbedeutenden Attributen.  Der Treiber-Manager sollte die Bewertungsschleife beenden.|  
|100|PerfekteS Match.  Der Treiber-Manager sollte die Bewertungsschleife beenden.|  
|Jeder andere Wert größer als 100|*hCandidateConnection* ist als tot markiert und wird auch in einer zukünftigen Verbindungsanforderung nicht wiederverwendet.|  
  
 Der Treiber-Manager markiert eine Verbindung als tot, wenn der Rückgabecode etwas anderes als SQL_SUCCESS (einschließlich SQL_SUCCESS_WITH_INFO) ist oder die Bewertung größer als 100 ist. Diese tote Verbindung wird nicht wiederverwendet (auch in zukünftigen Verbindungsanforderungen) und wird schließlich nach dem Verstreich von CPTimeout zeitumzichert. Der Treiber-Manager sucht weiterhin eine weitere Verbindung aus dem Pool, um zu bewerten.  
  
 Wenn der Treiber-Manager eine Verbindung wiederverwendet hat, deren Punktzahl deutlich kleiner als 100 ist (einschließlich 99), ruft der Treiber-Manager SQLSetConnectAttr(SQL_ATTR_DBC_INFO_TOKEN) auf, um die Verbindung wieder in den von der Anwendung angeforderten Zustand zurückzusetzen. Der Treiber sollte die Verbindung in diesem Funktionsaufruf nicht zurücksetzen.  
  
 Wenn *fRequiredTransactionEnlistment* TRUE ist, benötigt die Wiederverwendung von *hCandidateConnection* eine zusätzliche Registrierung (*transId* != NULL) oder unenlistment (*transId* == NULL). Dies gibt die Kosten für die Wiederverwendung einer Verbindung an und ob der Treiber die Verbindung ein- und ausschreiben soll, wenn er die Verbindung wiederverwenden möchte. Wenn *fRequireTransactionEnlistment* FALSE ist, sollte der Treiber den Wert von *transId*ignorieren.  
  
 Der Treiber-Manager garantiert, dass das übergeordnete HENV-Handle von *hRequest* und *hCandidateConnection* identisch ist. Der Treiber-Manager garantiert, dass die Pool-ID, die *hRequest* und *hCandidateConnection* zugeordnet ist, identisch ist.  
  
 Anwendungen sollten diese Funktion nicht direkt aufrufen. Ein ODBC-Treiber, der treiberbewusstes Verbindungspooling unterstützt, muss diese Funktion implementieren.  
  
 Fügen Sie sqlspi.h für die ODBC-Treiberentwicklung ein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Entwickeln eines ODBC-Treibers](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Treiber-Aware-Verbindungspooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Developing Connection-Pool Awareness in an ODBC Driver (Entwickeln von Verbindungspool-Unterstützung in einem ODBC-Treiber)](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
