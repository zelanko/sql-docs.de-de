---
title: Entwickeln von Verbindungspool Unterstützung in einem ODBC-Treiber | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: c63d5cae-24fc-4fee-89a9-ad0367cddc3e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b82e56dd7998ca19ce9e401369cd8d2f52b58573
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52417371"
---
# <a name="developing-connection-pool-awareness-in-an-odbc-driver"></a>Entwickeln von Verbindungspool-Unterstützung in einem ODBC-Treiber
Dieses Thema behandelt die Details der Entwicklung von einem ODBC-Treiber, der Informationen darüber, wie der Treiber Connection pooling-Dienste bieten sollte enthält.  
  
## <a name="enabling-driver-aware-connection-pooling"></a>Aktivieren der Treiberfähiges Verbindungspooling  
 Treiber muss die folgenden ODBC-Service Provider Interface (SPI)-Funktionen implementieren:  
  
-   SQLSetConnectAttrForDbcInfo  
  
-   SQLSetConnectInfo  
  
-   SQLSetDriverConnectInfo  
  
-   SQLGetPoolID  
  
-   SQLRateConnection  
  
-   SQLPoolConnect  
  
-   SQLCleanupConnectionPoolID  
  
 Finden Sie unter [ODBC Service Provider Interface (SPI) Verweis](../../../odbc/reference/syntax/odbc-service-provider-interface-spi-reference.md) für Weitere Informationen.  
  
 Treiber muss auch die folgenden vorhandenen Funktionen implementieren, damit die treiberfähiges Verbindungspooling aktiviert werden kann:  
  
|Funktion|Zusätzliche Funktionalität|  
|--------------|-------------------------|  
|[SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)<br /><br /> [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)<br /><br /> [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)<br /><br /> [SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)|Unterstützung für den neuen Handletyp: SQL_HANDLE_DBC_INFO_TOKEN (siehe Beschreibung unten).|  
|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|Das neue Verbindungsattribut der nur eine zu unterstützen: SQL_ATTR_DBC_INFO_TOKEN für das Zurücksetzen der Verbindung (siehe Beschreibung unten).|  
  
> [!NOTE]  
>  Veraltete Funktionen wie z. B. **SQLError** und **SQLSetConnectOption** werden für treiberfähiges Verbindungspooling nicht unterstützt.  
  
## <a name="the-pool-id"></a>Die Pool-ID  
 Die Pool-ID ist ein Zeiger mit der Länge treiberspezifische-ID eine bestimmte Gruppe von Verbindungen dar, die austauschbar verwendet werden können. Wenn eine Reihe von Verbindungsinformationen, sollte ein Treiber schnell die entsprechenden Pool-ID hergeleitet werden können  
  
 Beispielsweise sollten die Pool-ID, die Serverinformationen für den Namen und Anmeldeinformationen codieren. Der Name der Datenbank ist jedoch nicht erforderlich, da ein Treiber möglicherweise wiederverwenden einer Verbindung, und ändern Sie die Datenbank in kürzerer Zeit als Sie eine neue Verbindung herstellen können.  
  
 Ein Treiber sollte einen Satz von Schlüsselattributen, festlegen, die die Pool-ID umfassen Der Wert für diese wichtige Attribute kann aus Verbindungsattribute, Verbindungszeichenfolge und DSN stammen. Für den Fall, dass alle Konflikte in diesen Quellen vorhanden sind, sollte die vorhandenen, Treiber-spezifische Richtlinie zur konfliktlösung für Abwärtskompatibilität verwendet werden.  
  
 Der Treiber-Manager verwendet einen anderen Pool für verschiedene-Pool-IDs. Alle Verbindungen im gleichen Pool können wiederverwendet werden. Der Treiber-Manager wird eine Verbindung mit einem anderen Pool-ID nie wiederverwendet werden.  
  
 Aus diesem Grund sollte eine eindeutiger Pool-ID für jede Gruppe von Verbindungen mit dem gleichen Wert in die definierte Schlüsselattribute Treiber zugewiesen werden. Wenn ein Treiber die gleichen Pool-ID für zwei Verbindungen mit unterschiedlichen Werten in den wichtigsten Attributen verwendet, wird der Treiber-Manager immer noch im selben Pool Einsatzort (der Treiber-Manager nicht bekannt ist, Informationen zu den wichtigsten Attributen des Treiber-spezifische). Dies bedeutet, dass der Treiber muss an den Treiber-Manager zu melden, die eine Verbindung mit einem anderen Satz von Schlüsselattributen nicht innerhalb von wiederverwendbaren [SQLRateConnection-Funktion](../../../odbc/reference/syntax/sqlrateconnection-function.md). Dies kann die Leistung reduzieren, und dies wird nicht empfohlen.  
  
 Der Treiber-Manager wird nicht wiederverwendet, eine Verbindung von einer anderen Umgebung der Treiber zugeordnet sind, auch wenn alle Verbindungsinformationen übereinstimmt. Der Treiber-Manager verwendet einen anderen Pool für andere Umgebung, selbst wenn Verbindungen die gleichen Pool-ID Aus diesem Grund ist die Pool-ID für ihre Umgebung Treiber lokal.  
  
 Die Funktion zum Abrufen der Pool-ID aus dem Treiber [SQLGetPoolID-Funktion](../../../odbc/reference/syntax/sqlgetpoolid-function.md).  
  
## <a name="the-connection-rating"></a>Die Verbindung-Bewertung  
 Im Vergleich zu eine neue Verbindung herstellen, erhalten eine bessere Leistung Sie durch einige Verbindungsinformationen (z. B. Datenbank) in einer gepoolten Verbindung zurücksetzen. Daher sollten Sie nicht den Datenbanknamen in den Satz von Schlüsselattributen sein. Andernfalls können Sie für jede Datenbank, die möglicherweise nicht gut in Mid-Tier-Anwendungen, einen separaten Pool verwenden, in denen Kunden verschiedene unterschiedliche Verbindungszeichenfolgen verwenden.  
  
 Wenn Sie eine Verbindung, die einige attributkonflikts verfügt wiederverwenden, sollten Sie die nicht übereinstimmende Attribute basierend auf der neuen anwendungsanforderung, zurücksetzen, so, dass die zurückgegebene Verbindung mit der anwendungsanforderung identisch ist (siehe die Erläuterung des Attributs SQL_ATTR _DBC_INFO_TOKEN in [SQLSetConnectAttr-Funktion](https://go.microsoft.com/fwlink/?LinkId=59368)). Zurücksetzen dieser Attribute kann jedoch die Leistung verringern. So erfordert beispielsweise das Zurücksetzen einer Datenbank einen Netzwerkaufruf Server. Aus diesem Grund wiederverwenden Sie eine Verbindung, die perfekt abgeglichen wird, wenn eine verfügbar ist.  
  
 Eine Bewertung-Funktion in der Treiber kann es sich um eine vorhandene Verbindung mit einer neuen verbindungsanforderung auswerten. Beispielsweise kann die Bewertung Funktion des Treibers ermitteln:  
  
-   Wenn die vorhandene Verbindung durchaus mit der Anforderung zugeordnet ist.  
  
-   Wenn abweichungen vorhanden nur einige unbedeutend, z. B. Verbindungstimeout, die keine Kommunikation mit dem Server zum Zurücksetzen erforderlich sind sind.  
  
-   Wenn eine nicht übereinstimmende Attribute, die eine Kommunikation mit dem Server zurücksetzen erfordern, aber würde immer noch eine bessere Leistung als das Herstellen einer neuen Verbindung vorhanden sind.  
  
-   Wenn die nicht übereinstimmende für ein Attribut aufgetreten, die zum Zurücksetzen sehr zeitaufwändig ist (der Entwickler des Treibers ggf. durch Hinzufügen dieses Attributs in den Satz von Schlüssel-Attribute, die verwendet wird, um die Pool-ID zu generieren).  
  
 Eine Bewertung zwischen 0 und 100 ist möglich, wobei 0 bedeutet, dass nicht wieder verwendet werden können und 100 bedeutet, dass absolut übereinstimmt. [SQLRateConnection](../../../odbc/reference/syntax/sqlrateconnection-function.md) ist die Funktion für die Bewertung einer Verbindungs.  
  
## <a name="new-odbc-handle---sqlhandledbcinfotoken"></a>Neue ODBC-Anweisungshandle - SQL_HANDLE_DBC_INFO_TOKEN  
 Um treiberfähiges Verbindungspooling zu unterstützen, benötigt der Treiber Verbindungsinformationen, um die Pool-ID zu berechnen. Der Treiber benötigt auch Verbindungsinformationen, um neue verbindungsanforderungen mit Verbindungen im Pool zu vergleichen.  Wenn keine Verbindung im Pool wiederverwendet werden kann, hat der Treiber zum Herstellen einer neuen Verbindungs, die Verbindungsinformationen-masterdatenbankzugriff erforderlich ist.  
  
 Da die Verbindungsinformationen aus mehreren Quellen (Verbindungszeichenfolge-Verbindungsattributen und DSN) stammen kann, müssen ggf. der Treiber zum Analysieren der Verbindungszeichenfolge, und lösen Sie den Konflikt zwischen diesen Quellen in jedem der obigen Funktionsaufruf.  
  
 Aus diesem Grund wird eine neue ODBC-Anweisungshandle eingeführt: SQL_HANDLE_DBC_INFO_TOKEN. Mit SQL_HANDLE_DBC_INFO_TOKEN muss ein Treiber nicht zum Analysieren der Verbindungszeichenfolge und mehr als einmal Auflösen von Konflikten in Verbindungsinformationen. Da es sich um eine treiberspezifische Datenstruktur handelt, der Treiber Daten wie Verbindungsinformationen speichern und pool-ID  
  
 Dieses Handle wird nur als Schnittstelle zwischen der Treiber-Manager und Treiber verwendet. Dieses Handle eine Anwendung nicht direkt zugewiesen werden.  
  
 Das übergeordnete Handle dieses Handle ist vom Typ SQL_HANDLE_ENV auf, was bedeutet, dass der Treiber die Umgebungsinformationen aus dem HENV Handle während der Auflösung von Verbindung Informationen abrufen kann.  
  
 Wenn sie eine neue verbindungsanforderung empfängt, wird der Treiber-Manager ein Handle Typs SQL_HANDLE_DBC_INFO_TOKEN zugeordnet, für das Speichern von Verbindungsinformationen, nachdem er bestätigt, dass der Treiber den Verbindungspool Unterstützung unterstützt. Nachdem das Handle verwendet (aber vor der Rückgabe wird einige Rückgabecodes als SQL_STILL_EXECUTING aus [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) oder [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)), des Treiber-Managers gibt das Handle frei. Aus diesem Grund wird das Handle nach dem Aufruf SQLAllocHandle erstellt, und nach dem Aufruf SQLFreeHandle zerstört. Der Treiber-Manager wird sichergestellt, das Handle vor dem Freigeben von der zugeordneten HENV freigegeben wird (Wenn [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) oder [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) gibt einen Fehler zurück).  
  
 Der Treiber sollten die folgenden Funktionen zum Übernehmen des neuen Handletyp SQL_HANDLE_DBC_INFO_TOKEN ändern:  
  
1.  [SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)  
  
2.  [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)  
  
3.  [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)  
  
4.  [SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)  
  
 Der Treiber-Manager wird sichergestellt, dass mehrere Threads gleichzeitig nicht das gleiche SQL_HANDLE_DBC_INFO_TOKEN Handle verwendet werden. Aus diesem Grund kann das Synchronisierungsmodell dieses Handle innerhalb des Treibers sehr einfach sein. Der Treiber-Manager werden eine Sperre für die Umgebung vor dem zuweisen und Freigeben von SQL_HANDLE_DBC_INFO_TOKEN.  
  
 Der Treiber-Manager **SQLAllocHandle** und **SQLFreeHandle** akzeptiert keine dieses neue Handle-Typs.  
  
 SQL_HANDLE_DBC_INFO_TOKEN kann vertrauliche Daten z. B. Anmeldeinformationen enthalten. Aus diesem Grund sollten ein Treiber sicher der Arbeitsspeicherpuffer löschen (mithilfe von [SecureZeroMemory](https://msdn.microsoft.com/library/windows/desktop/aa366877\(v=vs.85\).aspx)), enthält die vertrauliche Informationen vor dem Freigeben von diesem Handle mit **SQLFreeHandle**. Wenn Sie einer Anwendung Umgebungshandle geschlossen wird, werden alle zugeordneten Verbindungspools geschlossen.  
  
## <a name="driver-manager-connection-pool-rating-algorithm"></a>Bewertung der Algorithmus-Treiber-Manager-Verbindungspool  
 Dieser Abschnitt beschreibt die Bewertung Algorithmus für das Treibermanager-Verbindungspooling. Treiberentwickler können denselben Algorithmus für die Abwärtskompatibilität implementieren. Dieser Algorithmus möglicherweise nicht die beste Option. Sie sollten dies verfeinern Algorithmus basiert, Ihre Implementierung (andernfalls besteht kein Grund für die Implementierung dieser Funktion).  
  
 Der Treiber-Manager wird eine ganzzahlige Bewertung zwischen 0 und 100 für jede Verbindung aus dem Pool zurückgegeben. 0 bedeutet, dass die Verbindung kann nicht wiederverwendet werden, und 100 gibt an, eine perfekte Übereinstimmung. Angenommen Sie, die verbindungsanforderung hRequest ist und die vorhandene Verbindung aus dem Pool als hCandidate benannt ist. Wenn einer der folgenden Bedingungen auf "false" festgelegt ist, kann nicht die Verbindung in einem Pool hCandidate für hRequest wiederverwendet werden (der Treiber-Manager wird eine Bewertung von 0 zuweisen).  
  
-   hCandidate und hRequest stammen aus UNICODE-API (z. B. sqldriverconnectw durchzuführen) oder ANSI-API (z. B. sqldriverconnecta durchzuführen). (UNICODE-Treiber können ein anderes Verhalten angegeben wird, ANSI-API und UNICODE-API (Siehe das Verbindungsattribut SQL_ATTR_ANSI_APP).)  
  
-   hCandidate und hRequest werden von der gleichen Funktion erstellt. SQLDriverConnect oder SQLConnect.  
  
-   Die Verbindungszeichenfolge verwendet, um hCandidate öffnen sollte hRequest, identisch sein, wenn SQLDriverConnect verwendet wird.  
  
-   Der ServerName (oder DSN), Benutzername und das Kennwort zum Öffnen von hCandidate muss mit dem hRequest geöffnet, wenn SQLConnect verwendet wird.  
  
-   Die Sicherheits-ID (SID) des aktuellen Threads sollte identisch sein, wie der SID verwendet, um hCandidate zu öffnen.  
  
-   Für den Treiber, die teuer eintragen und austragen (finden Sie unter der Erläuterung SQL_DTC_TRANSITION_COST in [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)), die Wiederverwendung von *hRequest* eine zusätzliche Eintragung oder Unenlistment nicht erforderlich.  
  
 Die folgende Tabelle zeigt die Zuweisung der Bewertung für verschiedene Szenarien.  
  
|Vergleich auf Verbindungsattribute zwischen die zusammengeführte Verbindung und der Anforderung|Keine Eintragung / Unenlistment|Erfordert zusätzliche Eintragung / Unenlistment|  
|---------------------------------------------------------------------------------------|-----------------------------------|----------------------------------------------|  
|Katalog (SQL_ATTR_CURRENT_CATALOG) unterscheidet.|60|50|  
|Unterscheiden sich einige Verbindungsattribute, aber der Katalog ist gleich|90|70|  
|Alle Verbindungsattribute, die perfekt abgeglichen.|100|80|  
  
## <a name="sequence-diagram"></a>Sequenzdiagramm  
 Dieses Diagramm zeigt den grundlegenden pooling-Mechanismus, die in diesem Thema beschrieben. Zeigt nur die Verwendung von [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) jedoch [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) Fall ähnelt.  
  
 ![Sequenzieren Diagramm](../../../odbc/reference/develop-driver/media/odbc_seq_dia.gif "Odbc_seq_dia")  
  
## <a name="state-diagram"></a>Zustandsdiagramm  
 Diese Zustandsdiagramm zeigt die Informationen token Verbindungsobjekt können in diesem Thema beschriebenen. Zeigt das Diagramm nur [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) jedoch [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) Fall ähnelt. Da der Treiber-Manager unter Umständen um Fehler zu einem beliebigen Zeitpunkt zu behandeln, kann der Treiber-Manager aufrufen [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md) für sämtliche Staaten.  
  
 ![Statusdiagramm](../../../odbc/reference/develop-driver/media/odbc_state_diagram.gif "Odbc_state_diagram")  
  
## <a name="see-also"></a>Siehe auch  
 [Treiberfähiges Verbindungspooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [ODBC-Dienstanbieterschnittstelle (Service Provider Interface, SPI) – Referenz](../../../odbc/reference/syntax/odbc-service-provider-interface-spi-reference.md)
