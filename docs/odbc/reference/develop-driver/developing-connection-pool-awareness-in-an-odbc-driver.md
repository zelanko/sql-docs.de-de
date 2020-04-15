---
title: Entwickeln der Verbindungspool-Bewusstseinin in einem ODBC-Treiber | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: c63d5cae-24fc-4fee-89a9-ad0367cddc3e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f77fea1d8439ac9ce7374b7dd47db5665686cfbc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283430"
---
# <a name="developing-connection-pool-awareness-in-an-odbc-driver"></a>Entwickeln von Verbindungspool-Unterstützung in einem ODBC-Treiber
In diesem Thema werden die Details zum Entwickeln eines ODBC-Treibers erläutert, der Informationen darüber enthält, wie der Treiber Verbindungspoolingdienste bereitstellen soll.  
  
## <a name="enabling-driver-aware-connection-pooling"></a>Aktivieren des Treiber-Aware-Verbindungspoolings  
 Ein Treiber muss die folgenden SPI-Funktionen (ODBC Service Provider Interface) implementieren:  
  
-   SQLSetConnectAttrForDbcInfo  
  
-   SQLSetConnectInfo  
  
-   SQLSetDriverConnectInfo  
  
-   SQLGetPoolID  
  
-   SQLRateConnection  
  
-   SQLPoolConnect  
  
-   SQLCleanupConnectionPoolID  
  
 Weitere Informationen finden Sie unter [ODBC Service Provider Interface (SPI)-Referenz.](../../../odbc/reference/syntax/odbc-service-provider-interface-spi-reference.md)  
  
 Ein Treiber muss außerdem die folgenden vorhandenen Funktionen implementieren, damit das treiberfähige Pooling aktiviert werden kann:  
  
|Funktion|Zusätzliche Funktionalität|  
|--------------|-------------------------|  
|[SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)<br /><br /> [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)<br /><br /> [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)<br /><br /> [SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)|Unterstützen Sie den neuen Handletyp: SQL_HANDLE_DBC_INFO_TOKEN (siehe Beschreibung unten).|  
|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|Unterstützen Sie das neue Nur-Set-Connection-Attribut: SQL_ATTR_DBC_INFO_TOKEN zum Zurücksetzen der Verbindung (siehe Beschreibung unten).|  
  
> [!NOTE]  
>  Veraltete Funktionen wie **SQLError** und **SQLSetConnectOption** werden für das treiberorientierte Verbindungspooling nicht unterstützt.  
  
## <a name="the-pool-id"></a>Die Pool-ID  
 Die Pool-ID ist eine treiberspezifische ID für Zeigerlängen, die eine bestimmte Gruppe von Verbindungen darstellt, die austauschbar verwendet werden können. Bei einer Reihe von Verbindungsinformationen sollte ein Treiber in der Lage sein, schnell die entsprechende Pool-ID abzuleiten.  
  
 Die Pool-ID sollte z. B. den Servernamen und die Anmeldeinformationen codieren. Der Datenbankname ist jedoch nicht erforderlich, da ein Treiber möglicherweise eine Verbindung wiederverwenden und die Datenbank dann in weniger Zeit ändern kann als eine neue Verbindung.  
  
 Ein Treiber sollte einen Satz von Schlüsselattributen definieren, die die Pool-ID umfassen. Der Wert dieser Schlüsselattribute kann von Verbindungsattributen, Verbindungszeichenfolgen und DSN stammen. Falls konflikte in diesen Quellen auftreten, sollte die vorhandene, treiberspezifische Lösungsrichtlinie für die Abwärtskompatibilität verwendet werden.  
  
 Der Treiber-Manager verwendet einen anderen Pool für verschiedene Pool-IDs. Alle Verbindungen im selben Pool sind wiederverwendbar. Der Treiber-Manager verwendet niemals eine Verbindung mit einer anderen Pool-ID.  
  
 Daher sollten Treiber für jede Gruppe von Verbindungen mit demselben Wert in ihren definierten Schlüsselattributen eine eindeutige Pool-ID zuweisen. Wenn ein Treiber dieselbe Pool-ID für zwei Verbindungen mit unterschiedlichen Werten in seinen Schlüsselattributen verwendet, legt der Treiber-Manager sie weiterhin in denselben Pool ein (der Treiber-Manager weiß nichts über die treiberspezifischen Schlüsselattribute). Dies bedeutet, dass der Treiber dem Treiber-Manager melden muss, dass eine Verbindung mit einem anderen Satz von Schlüsselattributen in der [SQLRateConnection-Funktion](../../../odbc/reference/syntax/sqlrateconnection-function.md)nicht wiederverwendet werden kann. Dies kann die Leistung beeinträchtigen, und dies wird nicht empfohlen.  
  
 Der Treiber-Manager verwendet keine Verbindung, die aus einer anderen Treiberumgebung zugewiesen wurde, auch wenn alle Verbindungsinformationen übereinstimmen. Der Treiber-Manager verwendet einen anderen Pool für eine andere Umgebung, auch wenn Verbindungen dieselbe Pool-ID haben. Daher ist die Pool-ID lokal für ihre Treiberumgebung.  
  
 Die Funktion zum Abrufen der Pool-ID vom Treiber ist [SQLGetPoolID Function](../../../odbc/reference/syntax/sqlgetpoolid-function.md).  
  
## <a name="the-connection-rating"></a>Die Verbindungsbewertung  
 Im Vergleich zum Herstellen einer neuen Verbindung können Sie eine bessere Leistung erzielen, indem Sie einige Verbindungsinformationen (z. B. DATABASE) in einer gepoolten Verbindung zurücksetzen. Daher möchten Sie möglicherweise nicht, dass sich der Datenbankname in Ihrem Satz von Schlüsselattributen befindet. Andernfalls können Sie einen separaten Pool für jede Datenbank haben, was in Mid-Tier-Anwendungen möglicherweise nicht gut ist, in denen Kunden verschiedene Verbindungszeichenfolgen verwenden.  
  
 Wenn Sie eine Verbindung wiederverwenden, die eine Attributübereinstimmung weist, sollten Sie die nicht übereinstimmenden Attribute basierend auf der neuen Anwendungsanforderung zurücksetzen, damit die zurückgegebene Verbindung mit der Anwendungsanforderung identisch ist (siehe Die Erläuterung des Attributs SQL_ATTR_DBC_INFO_TOKEN in [SQLSetConnectAttr Function](https://go.microsoft.com/fwlink/?LinkId=59368)). Das Zurücksetzen dieser Attribute kann jedoch die Leistung beeinträchtigen. Zum Zurücksetzen einer Datenbank ist beispielsweise ein Netzwerkaufruf an den Server erforderlich. Verwenden Sie daher eine Verbindung wieder, die perfekt aufeinander abgestimmt ist, sofern eine verbindung verfügbar ist.  
  
 Eine Bewertungsfunktion im Treiber kann eine bestehende Verbindung mit einer neuen Verbindungsanforderung auswerten. Die Bewertungsfunktion des Fahrers kann z. B. bestimmen:  
  
-   Wenn die bestehende Verbindung perfekt mit der Anforderung übereinstimmt.  
  
-   Wenn es nur einige unerhebliche Diskrepanzen gibt, z. B. Verbindungstimeout, das keine Kommunikation mit dem Server zum Zurücksetzen erfordert.  
  
-   Wenn es einige nicht übereinstimmende Attribute gibt, die eine Kommunikation mit dem Server zum Zurücksetzen erfordern, aber dennoch zu einer besseren Leistung als dem Herstellen einer neuen Verbindung führen würden.  
  
-   Wenn das nicht übereinstimmende Attribut für ein Attribut aufgetreten ist, das sehr zeitaufwändig zurückgesetzt werden muss (der Entwickler des Treibers kann erwägen, dieses Attribut in den Satz von Schlüsselattributen hinzuzufügen, der zum Generieren der Pool-ID verwendet wird).  
  
 Eine Punktzahl zwischen 0 und 100 ist möglich, wobei 0 Mittel nicht wiederverwendet werden und 100 bedeutet perfekt aufeinander abgestimmt. [SQLRateConnection](../../../odbc/reference/syntax/sqlrateconnection-function.md) ist die Funktion zum Bewerten einer Verbindung.  
  
## <a name="new-odbc-handle---sql_handle_dbc_info_token"></a>Neuer ODBC-Griff - SQL_HANDLE_DBC_INFO_TOKEN  
 Um das treiberbewusste Verbindungspooling zu unterstützen, benötigt der Treiber Verbindungsinformationen, um die Pool-ID zu berechnen. Der Treiber benötigt auch Verbindungsinformationen, um neue Verbindungsanforderungen mit Verbindungen im Pool zu vergleichen.  Wenn keine Verbindung im Pool wiederverwendet werden kann, muss der Treiber eine neue Verbindung herstellen, sodass Verbindungsinformationen erforderlich sind.  
  
 Da Verbindungsinformationen aus mehreren Quellen stammen können (Verbindungszeichenfolge, Verbindungsattribute und DSN), muss der Treiber möglicherweise die Verbindungszeichenfolge analysieren und den Konflikt zwischen diesen Quellen in jeder der oben genannten Funktionsaufrufen lösen.  
  
 Daher wird ein neues ODBC-Handle eingeführt: SQL_HANDLE_DBC_INFO_TOKEN. Bei SQL_HANDLE_DBC_INFO_TOKEN muss ein Treiber die Verbindungszeichenfolge nicht mehr als einmal analysieren und Konflikte in Verbindungsinformationen lösen. Da es sich um eine treiberspezifische Datenstruktur handelt, kann der Treiber Daten wie Verbindungsinformationen oder Pool-ID speichern.  
  
 Dieses Handle wird nur als Schnittstelle zwischen Treiber-Manager und Treiber verwendet. Eine Anwendung kann dieses Handle nicht direkt zuweisen.  
  
 Das übergeordnete Handle dieses Handles ist vom Typ SQL_HANDLE_ENV, was bedeutet, dass der Treiber die Umgebungsinformationen während der Verbindungsinformationsauflösung aus dem HENV-Handle abrufen kann.  
  
 Wenn eine neue Verbindungsanforderung empfangen wird, weist der Treiber-Manager ein Handle vom Typ SQL_HANDLE_DBC_INFO_TOKEN zum Speichern von Verbindungsinformationen zu, nachdem er bestätigt hat, dass der Treiber die Verbindungspool-Integrität unterstützt. Wenn Sie das Handle verwendet haben (aber bevor Sie einige andere Rückgabecodes als SQL_STILL_EXECUTING von [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) oder [SQLConnect zurückgeben),](../../../odbc/reference/syntax/sqlconnect-function.md)gibt der Treiber-Manager das Handle frei. Daher wird das Handle nach dem SQLAllocHandle-Aufruf erstellt und nach dem SQLFreeHandle-Aufruf zerstört. Der Treiber-Manager garantiert, dass das Handle freigegeben wird, bevor der zugehörige HENV freigegeben wird (wenn [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) oder [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) einen Fehler zurückgibt).  
  
 Der Treiber sollte die folgenden Funktionen ändern, um den neuen Handletyp SQL_HANDLE_DBC_INFO_TOKEN zu akzeptieren:  
  
1.  [SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)  
  
2.  [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)  
  
3.  [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)  
  
4.  [SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)  
  
 Der Treiber-Manager garantiert, dass mehrere Threads nicht denselben SQL_HANDLE_DBC_INFO_TOKEN gleichzeitig verwenden. Daher kann das Synchronisationsmodell dieses Handles innerhalb des Treibers sehr einfach sein. Der Treiber-Manager nimmt keine Umgebungssperre, bevor SQL_HANDLE_DBC_INFO_TOKEN zugewiesen und freiwird.  
  
 **SQLAllocHandle** und **SQLFreeHandle** des Treiber-Managers akzeptieren diesen neuen Handletyp nicht.  
  
 SQL_HANDLE_DBC_INFO_TOKEN können vertrauliche Informationen wie Anmeldeinformationen enthalten. Daher sollte ein Treiber den Speicherpuffer (mit [SecureZeroMemory](https://msdn.microsoft.com/library/windows/desktop/aa366877\(v=vs.85\).aspx)), der die vertraulichen Informationen enthält, sicher löschen, bevor dieses Handle mit **SQLFreeHandle**freigegeben wird. Wenn das Umgebungshandle einer Anwendung geschlossen wird, werden alle zugeordneten Verbindungspools geschlossen.  
  
## <a name="driver-manager-connection-pool-rating-algorithm"></a>Treiber-Manager-Verbindungspool-Bewertungsalgorithmus  
 In diesem Abschnitt wird der Bewertungsalgorithmus für das Driver Manager-Verbindungspooling erläutert. Treiberentwickler können denselben Algorithmus für die Abwärtskompatibilität implementieren. Dieser Algorithmus ist möglicherweise nicht der beste. Sie sollten diesen Algorithmus basierend auf Ihrer Implementierung verfeinern (sonst gibt es keinen Grund, diese Funktion zu implementieren).  
  
 Der Treiber-Manager gibt für jede Verbindung aus dem Pool eine integrale Bewertung von 0 bis 100 zurück. 0 bedeutet, dass die Verbindung nicht wiederverwendet werden kann und 100 eine perfekte Übereinstimmende anzeiget. Angenommen, die Verbindungsanforderung heißt hRequest, und die vorhandene Verbindung aus dem Pool wird als hCandidate benannt. Wenn eine der folgenden Bedingungen false ist, kann die gepoolte Verbindung hCandidate nicht für hRequest wiederverwendet werden (der Treiber-Manager weist eine Bewertung von 0 zu).  
  
-   hCandidate und hRequest stammen entweder von der UNICODE-API (z. B. SQLDriverConnectW) oder der ANSI-API (z. B. SQLDriverConnectA). (UNICODE-Treiber können unterschiedlich verhalten, wenn DIE ANSI-API und die UNICODE-API (siehe Verbindungsattribut SQL_ATTR_ANSI_APP).)  
  
-   hCandidate und hRequest werden von derselben Funktion erstellt. SQLDriverConnect oder SQLConnect.  
  
-   Die Verbindungszeichenfolge, die zum Öffnen von hCandidate verwendet wird, sollte mit hRequest identisch sein, wenn SQLDriverConnect verwendet wird.  
  
-   Der Servername (oder DSN), der Benutzername und das Kennwort, die zum Öffnen von hCandidate verwendet werden, sollten identisch sein, um hRequest zu öffnen, wenn SQLConnect verwendet wird.  
  
-   Die Sicherheitskennung (Security Identifier, SID) des aktuellen Threads sollte mit der SID identisch sein, die zum Öffnen von hCandidate verwendet wird.  
  
-   Für Treiber, die teuer zu erführen und aufzulisten sind (siehe die Diskussion über SQL_DTC_TRANSITION_COST in [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)), darf die Wiederverwendung von *hRequest* keine zusätzliche Einschreibung oder Nichteinschreibung erfordern.  
  
 Die folgende Tabelle zeigt die Punktezuweisung für verschiedene Szenarien.  
  
|Vergleich der Verbindungsattribute zwischen der gepoolten Verbindung und der Anforderung|Keine Einschreibung / Nichteinschreibung|Erfordern Sie zusätzliche Einschreibung / Unenlistment|  
|---------------------------------------------------------------------------------------|-----------------------------------|----------------------------------------------|  
|Katalog (SQL_ATTR_CURRENT_CATALOG) ist anders|60|50|  
|Einige Verbindungsattribute sind unterschiedlich, aber der Katalog ist derselbe.|90|70|  
|Alle Verbindungsattribute perfekt aufeinander abgestimmt|100|80|  
  
## <a name="sequence-diagram"></a>Sequenzdiagramm  
 Dieses Sequenzdiagramm zeigt den grundlegenden Pooling-Mechanismus, der in diesem Thema beschrieben wird. Es zeigt nur die Verwendung von [SQLDriverConnect,](../../../odbc/reference/syntax/sqldriverconnect-function.md) aber die [SQLConnect-Anfrage](../../../odbc/reference/syntax/sqlconnect-function.md) ist ähnlich.  
  
 ![Sequenzdiagramm](../../../odbc/reference/develop-driver/media/odbc_seq_dia.gif "odbc_seq_dia")  
  
## <a name="state-diagram"></a>Zustandsdiagramm  
 Dieses Zustandsdiagramm zeigt das in diesem Thema beschriebene Verbindungsinfotokenobjekt. Das Diagramm zeigt nur [SQLDriverConnect,](../../../odbc/reference/syntax/sqldriverconnect-function.md) aber die [SQLConnect-Anfrage](../../../odbc/reference/syntax/sqlconnect-function.md) ist ähnlich. Da der Treiber-Manager möglicherweise jederzeit Fehler behandeln muss, kann der Treiber-Manager [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md) für jeden Status aufrufen.  
  
 ![Zustandsdiagramm](../../../odbc/reference/develop-driver/media/odbc_state_diagram.gif "odbc_state_diagram")  
  
## <a name="see-also"></a>Weitere Informationen  
 [Treiber-Aware-Verbindungspooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [ODBC-Dienstanbieterschnittstelle (Service Provider Interface, SPI) – Referenz](../../../odbc/reference/syntax/odbc-service-provider-interface-spi-reference.md)
