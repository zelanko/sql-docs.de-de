---
description: Entwickeln von Verbindungspool-Unterstützung in einem ODBC-Treiber
title: Entwickeln von Connection-Pool Awareness in einem ODBC-Treiber | Microsoft-Dokumentation
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
ms.openlocfilehash: f22be001a7434c13158deae8677b8c7bcb2f0630
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "92192310"
---
# <a name="developing-connection-pool-awareness-in-an-odbc-driver"></a>Entwickeln von Verbindungspool-Unterstützung in einem ODBC-Treiber
In diesem Thema werden die Details der Entwicklung eines ODBC-Treibers erläutert, der Informationen darüber enthält, wie der Treiber Verbindungspooling-Dienste bereitstellen soll.  
  
## <a name="enabling-driver-aware-connection-pooling"></a>Aktivieren von Driver-Aware Verbindungs Pooling  
 Ein Treiber muss die folgenden SPI-Funktionen (ODBC Service Provider Interface) implementieren:  
  
-   Sqlsetconnectattrfordbcinfo  
  
-   Sqlsetconnectinfo  
  
-   Sqlsetdriverconnectinfo  
  
-   Sqlgetpoolid  
  
-   Sqlrateconnetction  
  
-   Sqlpoolconnect  
  
-   Sqlcleanupconnectionpoolid  
  
 Weitere Informationen finden Sie in der [Referenz zur ODBC-Dienstanbieter Schnittstelle (SPI)](../../../odbc/reference/syntax/odbc-service-provider-interface-spi-reference.md) .  
  
 Ein Treiber muss außerdem die folgenden vorhandenen Funktionen implementieren, damit das Treiber fähige Pooling aktiviert werden kann:  
  
|Funktion|Hinzugefügte Funktionalität|  
|--------------|-------------------------|  
|[SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)<br /><br /> [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)<br /><br /> [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)<br /><br /> [SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)|Unterstützung für den neuen Handles-Typ: SQL_HANDLE_DBC_INFO_TOKEN (siehe Beschreibung unten).|  
|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|Unterstützung des neuen Set-Only Connection-Attributs: SQL_ATTR_DBC_INFO_TOKEN für das Zurücksetzen der Verbindung (siehe Beschreibung unten).|  
  
> [!NOTE]  
>  Veraltete Funktionen wie **SQLError** und **SQLSetConnectOption** werden für Treiber fähiges Verbindungspooling nicht unterstützt.  
  
## <a name="the-pool-id"></a>Die Pool-ID  
 Die Pool-ID ist eine Treiber spezifische ID für die Zeiger Länge, die eine bestimmte Gruppe von Verbindungen darstellt, die austauschbar verwendet werden können. Bei einem bestimmten Satz von Verbindungsinformationen sollte ein Treiber die entsprechende Pool-ID schnell ableiten können.  
  
 Die Pool-ID muss z. b. den Servernamen und die Anmelde Informationen codieren. Der Datenbankname ist jedoch nicht erforderlich, da ein Treiber möglicherweise eine Verbindung wieder verwenden und dann die Datenbank in kürzerer Zeit ändern kann, als eine neue Verbindung herzustellen.  
  
 Ein Treiber sollte eine Reihe von Schlüssel Attributen definieren, die die Pool-ID bilden. Der Wert dieser Schlüssel Attribute kann aus Verbindungs Attributen, Verbindungs Zeichenfolgen und DSN stammen. Falls in diesen Quellen Konflikte auftreten, sollte die vorhandene Treiber spezifische Auflösungs Richtlinie aus Gründen der Abwärtskompatibilität verwendet werden.  
  
 Der Treiber-Manager verwendet einen anderen Pool für verschiedene Pool-IDs. Alle Verbindungen im gleichen Pool sind wiederverwendbar. Der Treiber-Manager verwendet niemals eine Verbindung mit einer anderen Pool-ID.  
  
 Daher sollten die Treiber eine eindeutige Pool-ID für jede Gruppe von Verbindungen mit dem gleichen Wert in ihren definierten Schlüssel Attributen zuweisen. Wenn ein Treiber dieselbe Pool-ID für zwei Verbindungen mit unterschiedlichen Werten in seinen Schlüssel Attributen verwendet, werden diese vom Treiber-Manager immer noch im selben Pool abgelegt (der Treiber-Manager weiß nichts über Treiber spezifische Schlüssel Attribute). Dies bedeutet, dass der Treiber dem Treiber-Manager Berichten muss, dass eine Verbindung mit einem anderen Satz von Schlüssel Attributen in der [sqlrateconnetction-Funktion](../../../odbc/reference/syntax/sqlrateconnection-function.md)nicht wieder verwendet werden kann. Dies kann die Leistung beeinträchtigen und wird nicht empfohlen.  
  
 Der Treiber-Manager verwendet keine von einer anderen Treiber Umgebung zugewiesene Verbindung, auch wenn alle Verbindungsinformationen übereinstimmen. Der Treiber-Manager verwendet einen anderen Pool für die unterschiedliche Umgebung, auch wenn Verbindungen dieselbe Pool-ID aufweisen. Daher ist die Pool-ID lokal in der jeweiligen Treiber Umgebung.  
  
 Die Funktion zum erhalten der Pool-ID aus dem Treiber ist die [sqlgetpoolid-Funktion](../../../odbc/reference/syntax/sqlgetpoolid-function.md).  
  
## <a name="the-connection-rating"></a>Die Verbindungs Bewertung  
 Im Vergleich zum Einrichten einer neuen Verbindung können Sie eine bessere Leistung erzielen, indem Sie einige Verbindungsinformationen (z. b. Datenbank) in einer gepoolten Verbindung zurücksetzen. Daher ist es möglich, dass der Datenbankname nicht in Ihrem Satz von Schlüssel Attributen angezeigt wird. Andernfalls können Sie für jede Datenbank einen separaten Pool verwenden, der in Mid-Tier-Anwendungen möglicherweise nicht gut geeignet ist, wenn Kunden verschiedene Verbindungs Zeichenfolgen verwenden.  
  
 Wenn Sie eine Verbindung mit einem Attribut Konflikt wieder verwenden, sollten Sie die nicht übereinstimmenden Attribute auf der Grundlage der neuen Anwendungsanforderung zurücksetzen, sodass die zurückgegebene Verbindung mit der Anwendungsanforderung identisch ist (Weitere Informationen finden Sie in der Beschreibung des Attributs SQL_ATTR_DBC_INFO_TOKEN in der [SQLSetConnectAttr-Funktion](../syntax/sqlsetconnectattr-function.md)). Durch das Zurücksetzen dieser Attribute kann jedoch die Leistung beeinträchtigt werden. Zum Zurücksetzen einer Datenbank ist beispielsweise ein Netzwerkserver Server erforderlich. Verwenden Sie daher eine Verbindung, die vollständig abgeglichen wird, wenn eine Verbindung verfügbar ist.  
  
 Eine Bewertungsfunktion im Treiber kann eine vorhandene Verbindung mit einer neuen Verbindungsanforderung auswerten. Beispielsweise kann die Bewertungsfunktion des Treibers Folgendes bestimmen:  
  
-   , Wenn die vorhandene Verbindung vollständig mit der Anforderung übereinstimmt.  
  
-   Wenn nur einige unbedeutende Konflikte vorliegen, z. b. Verbindungs Timeout, bei denen keine Kommunikation mit dem Server erforderlich ist, um zurückgesetzt zu werden.  
  
-   Wenn einige nicht übereinstimmende Attribute vorhanden sind, die eine Kommunikation mit dem Server erfordern, um zurückgesetzt zu werden, würde jedoch eine bessere Leistung als das Herstellen einer neuen Verbindung zur Folge haben.  
  
-   Wenn bei einem Attribut, das zum Zurücksetzen sehr zeitaufwändig ist, nicht übereinstimmende Fehler aufgetreten sind (der Entwickler des Treibers kann dieses Attribut ggf. dem Satz von Schlüssel Attributen hinzufügen, der zum Generieren der Pool-ID verwendet wird).  
  
 Ein Ergebnis zwischen 0 und 100 ist möglich, wobei 0 bedeutet, dass keine Wiederverwendung erfolgt und 100 eine perfekte Übereinstimmung aufweist. [Sqlrateconnetction](../../../odbc/reference/syntax/sqlrateconnection-function.md) ist die Funktion zum Bewerten einer Verbindung.  
  
## <a name="new-odbc-handle---sql_handle_dbc_info_token"></a>Neues ODBC-Handle-SQL_HANDLE_DBC_INFO_TOKEN  
 Zur Unterstützung des Treiber fähigen Verbindungspooling benötigt der Treiber Verbindungsinformationen, um die Pool-ID zu berechnen. Der Treiber benötigt außerdem Verbindungsinformationen, um neue Verbindungsanforderungen mit Verbindungen im Pool zu vergleichen.  Wenn keine Verbindung im Pool wieder verwendet werden kann, muss der Treiber eine neue Verbindung herstellen und somit Verbindungsinformationen benötigen.  
  
 Da Verbindungsinformationen aus mehreren Quellen stammen können (Verbindungs Zeichenfolge, Verbindungs Attribute und DSN), muss der Treiber möglicherweise die Verbindungs Zeichenfolge analysieren und den Konflikt zwischen diesen Quellen in jedem der obigen Funktionsaufrufe auflösen.  
  
 Daher wird ein neues ODBC-Handle eingeführt: SQL_HANDLE_DBC_INFO_TOKEN. Bei SQL_HANDLE_DBC_INFO_TOKEN muss ein Treiber die Verbindungs Zeichenfolge nicht analysieren und Konflikte in Verbindungsinformationen mehrmals lösen. Da es sich um eine Treiber spezifische Datenstruktur handelt, kann der Treiber Daten wie z. b. Verbindungsinformationen oder die Pool-ID speichern.  
  
 Dieses Handle wird nur als Schnittstelle zwischen dem Treiber-Manager und dem Treiber verwendet. Eine Anwendung kann dieses Handle nicht direkt zuordnen.  
  
 Das übergeordnete handle dieses Handles ist vom Typ SQL_HANDLE_ENV. Dies bedeutet, dass der Treiber während der Auflösung der Verbindungsinformationen die Umgebungs Informationen aus dem HENV-handle abrufen kann.  
  
 Wenn eine neue Verbindungsanforderung empfangen wird, weist der Treiber-Manager ein Handle vom Typ SQL_HANDLE_DBC_INFO_TOKEN zum Speichern von Verbindungsinformationen zu, nachdem bestätigt wurde, dass der Treiber die Verbindungspool Informationen unterstützt. Wenn die Verwendung des Handles abgeschlossen ist (aber vor der Rückgabe anderer Rückgabecodes als SQL_STILL_EXECUTING von [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) oder [SQLCONNECT](../../../odbc/reference/syntax/sqlconnect-function.md)), gibt der Treiber-Manager das Handle frei. Daher wird das Handle nach dem sqlfreichandle-Rückruf erstellt und nach dem SQLFreeHandle-Befehl zerstört. Der Treiber-Manager garantiert, dass das Handle freigegeben wird, bevor der zugehörige "HENV" freigegeben wird (wenn [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) oder [SQLCONNECT](../../../odbc/reference/syntax/sqlconnect-function.md) einen Fehler zurückgibt).  
  
 Der Treiber sollte die folgenden Funktionen ändern, um den neuen behandetyp SQL_HANDLE_DBC_INFO_TOKEN zu akzeptieren:  
  
1.  [SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)  
  
2.  [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)  
  
3.  [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)  
  
4.  [SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)  
  
 Der Treiber-Manager stellt sicher, dass mehrere Threads nicht dasselbe SQL_HANDLE_DBC_INFO_TOKEN handle gleichzeitig verwenden. Daher kann das Synchronisierungs Modell dieses Handles innerhalb des Treibers sehr einfach sein. Der Treiber-Manager nimmt vor dem zuordnen und Freigeben von SQL_HANDLE_DBC_INFO_TOKEN keine Umgebungs Sperre vor.  
  
 **Sqlfreichandle** und **SQLFreeHandle** des Treiber-Managers akzeptieren diesen neuen Handlertyp nicht.  
  
 SQL_HANDLE_DBC_INFO_TOKEN können vertrauliche Informationen wie Anmelde Informationen enthalten. Daher sollte ein Treiber den Speicherpuffer (unter Verwendung von [securezeromemory](https://msdn.microsoft.com/library/windows/desktop/aa366877\(v=vs.85\).aspx)), der die vertraulichen Informationen enthält, sicher löschen, bevor er dieses Handle mit **SQLFreeHandle**freigibt. Wenn das Umgebungs Handle einer Anwendung geschlossen wird, werden alle zugeordneten Verbindungspools geschlossen.  
  
## <a name="driver-manager-connection-pool-rating-algorithm"></a>Filter für Treiber-Manager-Verbindungs Pool Bewertung  
 In diesem Abschnitt wird der Bewertungs Algorithmus für das Treiber-Manager-Verbindungspooling erläutert. Treiber Entwickler können für die Abwärtskompatibilität denselben Algorithmus implementieren. Dieser Algorithmus ist möglicherweise nicht der beste. Sie sollten diesen Algorithmus auf Grundlage ihrer Implementierung verfeinern (andernfalls gibt es keinen Grund, diese Funktion zu implementieren).  
  
 Der Treiber-Manager gibt für jede Verbindung aus dem Pool eine ganzzahlige Bewertung von 0 bis 100 zurück. 0 bedeutet, dass die Verbindung nicht wieder verwendet werden kann und 100 einen perfekten übereinstimmenden angibt. Angenommen, die Verbindungsanforderung hat den Namen hrequest, und die vorhandene Verbindung aus dem Pool wird als hcandidate benannt. Wenn eine der folgenden Bedingungen false ist, kann der in einem Pool zusammengefasste Verbindungs-hcandidate nicht für hrequest wieder verwendet werden (der Treiber-Manager weist eine Bewertung von 0 zu).  
  
-   hcandidate und hrequest stammen sowohl aus der Unicode-API (z. b. sqldriverconnectw) als auch aus der ANSI-API (z. b. sqldriverconnecta). (Bei Unicode-Treibern kann es sich um verschiedene ANSI-APIs und Unicode-APIs Verhalten (siehe das Connection-Attribut SQL_ATTR_ANSI_APP).)  
  
-   hcandidate und hrequest werden von derselben Funktion erstellt. entweder SQLDriverConnect oder SQLCONNECT.  
  
-   Die Verbindungs Zeichenfolge, die zum Öffnen von hcandidate verwendet wird, sollte mit hrequest identisch sein, wenn SQLDriverConnect verwendet wird.  
  
-   Der Servername (oder DSN), der Benutzername und das Kennwort, die zum Öffnen von hcandidate verwendet werden, müssen identisch sein, um hrequest zu öffnen, wenn SQLConnect verwendet wird.  
  
-   Die Sicherheits-ID (SID) des aktuellen Threads sollte mit der SID identisch sein, die zum Öffnen von hcandidate verwendet wurde.  
  
-   Bei einem Treiber, der sich für die Eintragung und Austragen von Ressourcen eignet (Weitere Informationen finden Sie in der Erörterung von SQL_DTC_TRANSITION_COST in [SQLCONNECT](../../../odbc/reference/syntax/sqlconnect-function.md)), muss für die Wiederverwendung von *hrequest* keine zusätzliche Eintragung oder Aufhebung der Registrierung erforderlich sein.  
  
 Die folgende Tabelle zeigt die Bewertungs Zuweisung für verschiedene Szenarien.  
  
|Vergleich mit Verbindungs Attributen zwischen der gepoolten Verbindung und der Anforderung|Keine Eintragung/Einschreibung|Zusätzliche Eintragung/Einschreibung erforderlich|  
|---------------------------------------------------------------------------------------|-----------------------------------|----------------------------------------------|  
|Der Katalog (SQL_ATTR_CURRENT_CATALOG) ist unterschiedlich.|60|50|  
|Einige Verbindungs Attribute sind unterschiedlich, der Katalog ist aber identisch.|90|70|  
|Alle Verbindungs Attribute Stimmen perfekt überein.|100|80|  
  
## <a name="sequence-diagram"></a>Sequenzdiagramm  
 Dieses Sequenzdiagramm zeigt den grundlegenden Pooling-Mechanismus, der in diesem Thema beschrieben wird. Es wird nur die Verwendung von [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) angezeigt, aber der [SQLCONNECT](../../../odbc/reference/syntax/sqlconnect-function.md) -Fall ist ähnlich.  
  
 ![Sequenzdiagramm](../../../odbc/reference/develop-driver/media/odbc_seq_dia.gif "odbc_seq_dia")  
  
## <a name="state-diagram"></a>Zustandsdiagramm  
 Dieses Status Diagramm zeigt das Verbindungs Info-Tokenobjekt, das in diesem Thema beschrieben wird. Das Diagramm zeigt nur [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) an, aber der [SQLCONNECT](../../../odbc/reference/syntax/sqlconnect-function.md) -Fall ist ähnlich. Da der Treiber-Manager möglicherweise jederzeit Fehler verarbeiten muss, kann der Treiber-Manager [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md) für jeden beliebigen Status abrufen.  
  
 ![Zustandsdiagramm](../../../odbc/reference/develop-driver/media/odbc_state_diagram.gif "odbc_state_diagram")  
  
## <a name="see-also"></a>Weitere Informationen  
 [Treiber fähiges Verbindungs Pooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [ODBC-Dienstanbieterschnittstelle – Referenz](../../../odbc/reference/syntax/odbc-service-provider-interface-spi-reference.md)