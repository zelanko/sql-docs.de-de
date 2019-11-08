---
title: SQLGetConnectAttr | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLGetConnectAttr function
ms.assetid: 26e4e69a-44fd-45e3-b47a-ae39184f041b
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8e302fe1c5a1f4bcf5f51728a866a72b993076f3
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73786721"
---
# <a name="sqlgetconnectattr"></a>SQLGetConnectAttr
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber definiert treiberspezifische Verbindungsattribute. Einige der Attribute sind für **SQLGetConnectAttr**verfügbar, und die-Funktion wird verwendet, um Ihre aktuellen Einstellungen zu melden. Die für diese Attribute gemeldeten Werte werden erst nach dem Herstellen einer Verbindung oder dem Festlegen des Attributs mithilfe von [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)sichergestellt.  
  
 In diesem Thema sind die schreibgeschützten Attribute aufgeführt. Weitere Informationen zu den anderen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC-treiberspezifischen Verbindungs Attributen für Native Client finden Sie unter [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md).  
  
## <a name="sql_copt_ss_connection_dead"></a>SQL_COPT_SS_CONNECTION_DEAD  
 Das SQL_COPT_SS_CONNECTION_DEAD-Attribut meldet den Status einer Verbindung zu einem Server. Der Treiber sendet eine Abfrage an das Netzwerk bezüglich des aktuellen Status der Verbindung.  
  
> [!NOTE]  
>  Das Standard-ODBC-Verbindungsattribut SQL_ATTR_CONNECTION_DEAD gibt den letzten Status der Verbindung zurück. Dabei handelt es sich nicht zwingend um den aktuellen Verbindungsstatus.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SQL_CD_TRUE|Die Verbindung zum Server wurde unterbrochen.|  
|SQL_CD_FALSE|Die Verbindung besteht und ist für die Anweisungsverarbeitung verfügbar.|  
  
## <a name="sql_copt_ss_client_connection_id"></a>SQL_COPT_SS_CLIENT_CONNECTION_ID  
 Das SQL_COPT_SS_CLIENT_CONNECTION_ID-Attribut ruft die Clientverbindungs-ID ab, die dann für die Suche verwendet werden kann:  
  
-   Diagnoseinformationen im XEvents-Protokoll, wenn aktiviert.  
  
-   Verbindungsfehlerinformationen im Verbindungsringpuffer.  
  
-   Diagnoseinformationen in den Datenzugriff-Ablaufverfolgungsprotokollen, wenn aktiviert.  
  
 Weitere Informationen finden Sie unter [zugreifen auf Diagnoseinformationen im Protokoll für erweiterte Ereignisse](../../relational-databases/native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md).  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SQL_ERROR|Die Verbindung konnte nicht hergestellt werden.|  
|SQL_SUCCESS|Die Verbindung wurde erfolgreich hergestellt. Die Clientverbindungs-ID befindet sich im Ausgabepuffer.|  
  
## <a name="sql_copt_ss_perf_data"></a>SQL_COPT_SS_PERF_DATA  
 Das SQL_COPT_SS_PERF_DATA-Attribut gibt einen Zeiger auf eine SQLPERF-Struktur zurück, die die aktuellen statistischen Daten zur Treiberleistung enthält. **SQLGetConnectAttr** gibt NULL zurück, wenn die Leistungs Protokollierung nicht aktiviert ist. Die Statistik in der SQLPERF-Struktur wird nicht dynamisch vom Treiber aktualisiert. Aufrufen von **SQLGetConnectAttr** jedes Mal, wenn die Leistungsstatistik aktualisiert werden muss.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|NULL|Die Leistungsprotokollierung wird nicht aktiviert.|  
|Ein beliebiger anderer Wert.|Ein Zeiger auf eine SQLPERF-Struktur.|  
  
## <a name="sql_copt_ss_perf_query"></a>SQL_COPT_SS_PERF_QUERY  
 Das SQL_COPT_SS_PERF_QUERY-Attribut gibt TRUE zurück, wenn die Protokollierung von Abfragen mit langer Ausführungszeit aktiviert ist. Die Anforderung gibt FALSE zurück, wenn die Abfrageprotokollierung nicht aktiv ist.  
  
## <a name="sql_copt_ss_user_data"></a>SQL_COPT_SS_USER_DATA  
 Das SQL_COPT_SS_USER_DATA-Attribut ruft den Benutzerdatenzeiger ab. Benutzerdaten werden im Besitz des Client Speichers gespeichert und pro Verbindung aufgezeichnet. Wenn der Benutzerdatenzeiger nicht festgelegt wurde, wird SQL_UD_NOTSET, ein NULL-Zeiger, zurückgegeben.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SQL_UD_NOTSET|Es ist kein Benutzerdatenzeiger festgelegt.|  
|Ein beliebiger anderer Wert.|Ein Zeiger auf die Benutzerdaten.|  
  
## <a name="sqlgetconnectattr-support-for-service-principal-names-spns"></a>SQLGetConnectAttr-Unterstützung für Dienstprinzipalnamen (SPNs)  
 SQLGetConnectAttr kann verwendet werden, um den Wert der neuen Verbindungs Attribute SQL_COPT_SS_SERVER_SPN, SQL_COPT_SS_FAILOVER_PARTNER_SPN, SQL_COPT_SS_MUTUALLY_AUTHENTICATED und SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD abzufragen. (SQLGetConnectOption kann auch verwendet werden, um diese Werte abzufragen.)  
  
 SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD ist nur für geöffnete Verbindungen verfügbar, die die Windows-Authentifizierung verwenden.  
  
 Wenn SQL_COPT_SS_SERVER_SPN oder SQL_COPT_SS_FAILOVER_PARTNER nicht festgelegt wurde, wird der Standardwert (eine leere Zeichenfolge) zurückgegeben.  
  
 Weitere Informationen zu SPNs finden Sie unter [Dienst Prinzipal &#40;Namen-&#41; Dienst Prinzipal &#40;Namen (&#41;SPNs) in Client Verbindungen ODBC](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQLGetConnectAttr-Funktion](https://go.microsoft.com/fwlink/?LinkId=59347)   
 [Implementierungs Details für die ODBC-API](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)   
 [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/set-quoted-identifier-transact-sql.md)   
 [SET ANSI_NULLS &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-nulls-transact-sql.md)   
 [SET ANSI_PADDING &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-padding-transact-sql.md)   
 [Festlegen ANSI_WARNINGS &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-warnings-transact-sql.md)  
  
  
