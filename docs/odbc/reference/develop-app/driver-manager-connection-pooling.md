---
title: Treibermanager-Verbindungspooling | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connection pooling [ODBC]
- pooled connections [ODBC]
- connecting to driver [ODBC], connection pooling
- connecting to data source [ODBC], connection pooling
ms.assetid: ee95ffdb-5aa1-49a3-beb2-7695b27c3df9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 96a48d60cc0c127f41e6e1b79b9faf29ea4392cf
ms.sourcegitcommit: eacc2d979f1f13cfa07e0aa4887eb9d48824b633
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2019
ms.locfileid: "67533824"
---
# <a name="driver-manager-connection-pooling"></a>Verbindungspooling des Treiber-Managers
Verbindungspooling ermöglicht einer Anwendung eine Verbindung aus einem Pool von Verbindungen verwendet werden, die nicht für jede Verwendung neu eingerichtet werden müssen. Sobald eine Verbindung erstellt und in einen Pool aufgenommen wurde, kann eine Anwendung diese Verbindung wiederverwenden, ohne den Prozess für die Verbindung abgeschlossen.  
  
 Mithilfe einer in einem Pool zusammengefasste Verbindung kann erheblichen Leistungsgewinn führen, da es sich bei den Aufwand beim Herstellen einer Verbindung mit Anwendungen gespeichert werden können. Dies kann besonders schwerwiegend, für Anwendungen der mittleren Ebene, die über ein Netzwerk verbunden oder für Anwendungen, die wiederholt eine Verbindung herstellen und trennen, z. B. Internetanwendungen sein.  
  
 Neben der Leistung verbessert wurde können der Verbindungspooling-Architektur, eine Umgebung und die zugeordneten Verbindungen von mehreren Komponenten in einem einzigen Prozess verwendet werden. Dies bedeutet, dass eigenständige Komponenten im selben Prozess miteinander interagieren können, ohne die Sensibilisierung für einander. Eine Verbindung in einem Verbindungspool kann wiederholt von mehreren Komponenten verwendet werden.  
  
> [!NOTE]
>  Verbindungspooling kann von einer ODBC-Anwendung, die mit ODBC 2. verwendet werden. *x* Verhalten, solange die Anwendung aufrufen kann *SQLSetEnvAttr*. Beim Verwenden von Verbindungspools, die Anwendung muss nicht ausführen, SQL-Anweisungen, die die Datenbank oder im Kontext der Datenbank, z. B. das ändern, Ändern der \< *Datenbanknamen*>, welche Änderungen es sich um den Katalog verwendet, die von einem Quelle.  


 Ein ODBC-Treiber muss vollständig threadsicher sein, und Verbindungen darf keinen Thread-Affinität, um Verbindungspooling zu unterstützen. Dies bedeutet, dass der Treiber ist einen Aufruf für einen Thread zu einem beliebigen Zeitpunkt zu verarbeiten und in einem Thread, um die Verbindung in einem anderen Thread verwendet werden, und klicken Sie auf ein dritter Thread getrennt eine Verbindung herstellen kann.  
  
 Der Verbindungspool wird vom Treiber-Manager verwaltet werden. Verbindungen aus dem Pool entnommen werden, wenn die Anwendung aufruft **SQLConnect** oder **SQLDriverConnect** und an den Pool zurückgegeben werden, wenn die Anwendung aufruft **SQLDisconnect**. Die Größe des Pools wird dynamisch, basierend auf die angeforderte Ressource-Zuordnungen. Diese verkleinert basierend auf das Timeout bei Inaktivität: Wenn eine Verbindung für eine bestimmte Zeitdauer inaktiv ist (es wurde nicht in einer Verbindung verwendet), wird er aus dem Pool entfernt. Die Größe des Pools wird nur durch Arbeitsspeicher und Einschränkungen auf dem Server beschränkt.  
  
 Der Treiber-Manager bestimmt, ob eine bestimmte Verbindung in einem Pool soll, gemäß den übergebenen Argumenten verwendet werden **SQLConnect** oder **SQLDriverConnect**, und gemäß der Verbindungsattribute festgelegt, nachdem die Verbindung zugewiesen wurde.  
  
 Beim pooling von Verbindungen wird der Treiber-Manager muss es in der Lage, um festzustellen, ob eine Verbindung, die Verbindung fungiert, bevor Sie weiterhin ausgeführt wird. Andernfalls speichert der Treiber-Manager auf Behandlung, die inaktiven Verbindung mit der Anwendung nach einem vorübergehenden Netzwerkausfall. Ein neues Verbindungsattribut in ODBC 3. definiert wurde *.x*: SQL_ATTR_CONNECTION_DEAD. Hierbei handelt es sich um eine schreibgeschützte Verbindung-Attribut, das entweder SQL_CD_TRUE und SQL_CD_FALSE zurückgibt. Der Wert SQL_CD_TRUE bedeutet, dass die Verbindung unterbrochen, wurde der Wert SQL_CD_FALSE bedeutet, dass die Verbindung noch aktiv ist. (Mit früheren Versionen der ODBC-Treiber können auch dieses Attribut unterstützt.)  
  
 Ein Treiber muss diese Option effizient implementieren oder es ist das Verbindungspooling, die Leistung beeinträchtigt. Insbesondere sollte ein Aufruf zum Abrufen dieses Verbindungsattribut nicht auf einen Roundtrip zum Server verursachen. Stattdessen sollte ein Treiber nur den letzten bekannten Status der Verbindung zurück. Die Verbindung ist inaktiv, wenn die letzte Fahrt auf dem Server fehlgeschlagen ist und nicht inaktiv, wenn die letzte Fahrt erfolgreich ausgeführt wurde.  
  
## <a name="remarks"></a>Hinweise  
 Wenn eine Verbindung unterbrochen wurde (über SQL_ATTR_CONNECTION_DEAD gemeldet), werden der ODBC-Treiber-Manager durch Aufrufen von SQLDisconnect im Treiber auf die Verbindung zerstört. Neue verbindungsanforderungen können eine verwendbare Verbindung im Pool nicht gefunden werden. Schließlich kann der Treiber-Manager, eine neue Verbindung, vorausgesetzt, dass der Pool leer ist.  
  
 Um einem Verbindungspool zu verwenden, führt eine Anwendung die folgenden Schritte aus:  
  
1.  Ermöglicht es, Verbindungspooling durch Aufrufen von **SQLSetEnvAttr** umgebungsattributs SQL_ATTR_CONNECTION_POOLING SQL_CP_ONE_PER_DRIVER oder SQL_CP_ONE_PER_HENV festlegen. Dieser Aufruf muss vorgenommen werden, bevor die Anwendung die freigegebene Umgebung weist pooling ist für die Verbindung aktiviert werden. Das Umgebungshandle im Aufruf von **SQLSetEnvAttr** sollte auf Null, deshalb SQL_ATTR_CONNECTION_POOLING einer auf Prozessebene-Attribut festgelegt werden. Wenn das Attribut auf SQL_CP_ONE_PER_DRIVER festgelegt ist, wird ein einzelne Verbindungspool für jeden Treiber unterstützt. Wenn eine Anwendung mit vielen Treibern und einige Umgebungen funktioniert, kann dies effizienter sein, da weniger Vergleiche erforderlich sein können. Wenn auf SQL_CP_ONE_PER_HENV, eines einzelnen Verbindungspools für jede Umgebung unterstützt wird. Wenn eine Anwendung mit vielen Umgebungen und einige Treiber funktioniert, kann dies effizienter sein, da weniger Vergleiche erforderlich sein können. Verbindungspooling ist deaktiviert, indem SQL_ATTR_CONNECTION_POOLING auf SQL_CP_OFF festlegen.  
  
2.  Ordnet eine Umgebung durch den Aufruf **SQLAllocHandle** mit der *HandleType* -Argument auf SQL_HANDLE_ENV auf festgelegt. Eine implizite freigegebenen Umgebung kann von die Umgebung, die durch diesen Aufruf zugeordnet ist, werden, weil Verbindungs-pooling aktiviert wurde. Die Umgebung verwendet werden, nicht festgelegt wurde, jedoch erst **SQLAllocHandle** mit einem *HandleType* SQL_HANDLE_DBC auf, die für diese Umgebung aufgerufen wird.  
  
3.  Ordnet eine Verbindung durch den Aufruf **SQLAllocHandle** mit *InputHandle* auf SQL_HANDLE_DBC auf, festgelegt und die *InputHandle* legen Sie auf das Umgebungshandle zugewiesen Verbindungspooling. Der Treiber-Manager versucht, eine vorhandene Umgebung zu finden, die festlegen, indem die Anwendung Umgebungsattribute entspricht. Wenn keine Umgebung dieser Art vorhanden ist, wird eine mit einer Verweisanzahl von 1 (verwaltet durch den Treiber-Manager) erstellt. Wenn eine entsprechende freigegebene Umgebung gefunden wird, die Umgebung an die Anwendung zurückgegeben wird und dessen Verweiszähler erhöht wird. (Die eigentliche Verbindung verwendet werden, wird nicht vom Treiber-Manager bis bestimmt **SQLConnect** oder **SQLDriverConnect** aufgerufen wird.)  
  
4.  Aufrufe **SQLConnect** oder **SQLDriverConnect** zum Herstellen die Verbindung. Der Treiber-Manager verwendet die Verbindungsoptionen im Aufruf von **SQLConnect** (oder die Verbindungsschlüsselwörter im Aufruf von **SQLDriverConnect**) und die Verbindungsattribute festlegen, nach der Zuordnung der Verbindung um Bestimmen Sie, welche Verbindung im Pool verwendet werden soll.  
  
    > [!NOTE]  
    >  Wie eine angeforderte Verbindung eine gepoolte Verbindung zugeordnet ist, wird dies durch umgebungsattributs SQL_ATTR_CP_MATCH bestimmt. Weitere Informationen finden Sie unter [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md).  
  
     ODBC-Anwendungen mithilfe von Verbindungspooling sollten Aufrufen [CoInitializeEx](https://go.microsoft.com/fwlink/?LinkID=116307) während der anwendungsinitialisierung und [CoUninitialize](https://go.microsoft.com/fwlink/?LinkId=116310) beim Schließen der Anwendung.  
  
5.  Aufrufe **SQLDisconnect** Wenn die Verbindung nicht mehr benötigen. Die Verbindung an den Verbindungspool zurückgegeben, und für die Wiederverwendung verfügbar wird.  
  
 Eine ausführliche Erläuterung finden Sie unter [Verbindungspooling in der Microsoft Data Access Components](https://go.microsoft.com/fwlink/?LinkId=120776).  
  
## <a name="connection-pooling-considerations"></a>Überlegungen für die Verbindungspooling  
 Ausführen einer der folgenden Aktionen mit einem SQL‑Befehl (anstatt über die ODBC-API) und beeinflussen kann, der Status der Verbindung zu unerwarteten Problemen kommen, wenn Verbindungspooling aktiviert ist:  
  
-   Öffnen einer Verbindung, und ändern die Standarddatenbank.  
  
-   Verwenden die SET-Anweisung, um konfigurierbaren Optionen (einschließlich SET ROWCOUNT, ANSI_NULL, IMPLICIT_TRANSACTIONS, SHOWPLAN, Statistiken, TEXTSIZE und DateFormat-Einstellung) zu ändern.  
  
-   Erstellen von temporären Tabellen und gespeicherten Prozeduren.  
  
 Wenn eine dieser Aktionen außerhalb der ODBC-API ausgeführt werden, erben die nächste Person, die die Verbindung verwendet automatisch die vorherigen Einstellungen, Tabellen oder Prozeduren.  
  
> [!NOTE]  
>  Erwarten Sie nicht bestimmte Einstellungen in den Verbindungsstatus vorhanden sein. Sollten Sie immer den Verbindungsstatus in Ihrer Anwendung festgelegt und stellen Sie sicher, dass die Anwendung alle nicht verwendeten Verbindungs-pooling Einstellungen entfernt.  
  
## <a name="driver-aware-connection-pooling"></a>Treiberfähiges Verbindungspooling  
 Ab Windows 8 kann ein ODBC-Treiber Verbindungen im Pool effizienter verwenden. Weitere Informationen finden Sie unter [Treiberfähiges Verbindungspooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Herstellen einer Verbindung mit einer Datenquelle oder einem Treiber](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md)   
 [Entwickeln einen ODBC-Treiber](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Verbindungspooling in der Microsoft Data Access Components](https://go.microsoft.com/fwlink/?LinkId=120776)
