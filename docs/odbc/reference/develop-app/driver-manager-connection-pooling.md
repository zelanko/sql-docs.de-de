---
title: Treiber-Manager-Verbindungspooling | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 84ccc0db8f9a54eecc8337ca5efbc7b4c4baa239
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305821"
---
# <a name="driver-manager-connection-pooling"></a>Verbindungspooling des Treiber-Managers
Das Verbindungspooling ermöglicht es einer Anwendung, eine Verbindung aus einem Pool von Verbindungen zu verwenden, die nicht für jede Verwendung wiederhergestellt werden müssen. Nachdem eine Verbindung erstellt und in einem Pool platziert wurde, kann eine Anwendung diese Verbindung wiederverwenden, ohne den vollständigen Verbindungsvorgang auszuführen.  
  
 Die Verwendung einer gepoolten Verbindung kann zu erheblichen Leistungssteigerungen führen, da Anwendungen den Aufwand für das Herstellen einer Verbindung sparen können. Dies kann besonders für Anwendungen der mittleren Ebene, die eine Verbindung über ein Netzwerk herstellen, oder für Anwendungen, die wiederholt eine Verbindung herstellen und die Verbindung trennen, wie z. B. Internetanwendungen, von Bedeutung sein.  
  
 Zusätzlich zu den Leistungssteigerungen ermöglicht die Verbindungspoolingarchitektur die Verwendung einer Umgebung und der zugehörigen Verbindungen durch mehrere Komponenten in einem einzigen Prozess. Dies bedeutet, dass eigenständige Komponenten im gleichen Prozess miteinander interagieren können, ohne sich gegenseitig zu kennen. Eine Verbindung in einem Verbindungspool kann wiederholt von mehreren Komponenten verwendet werden.  
  
> [!NOTE]
>  Das Verbindungspooling kann von einer ODBC-Anwendung mit ODBC 2 verwendet werden. *x-Verhalten,* solange die Anwendung *SQLSetEnvAttr*aufrufen kann. Bei der Verwendung des Verbindungspoolings darf die Anwendung keine SQL-Anweisungen ausführen, \<die die Datenbank oder den Kontext der Datenbank ändern, z. B. das Ändern des *Datenbanknamens*>, wodurch der von einer Datenquelle verwendete Katalog geändert wird.  


 Ein ODBC-Treiber muss vollständig threadsicher sein, und Verbindungen dürfen keine Threadaffinität haben, um das Verbindungspooling zu unterstützen. Dies bedeutet, dass der Treiber in der Lage ist, einen Aufruf eines beliebigen Threads jederzeit zu verarbeiten und eine Verbindung mit einem Thread herzustellen, die Verbindung auf einem anderen Thread zu verwenden und die Verbindung zu einem dritten Thread zu trennen.  
  
 Der Verbindungspool wird vom Treiber-Manager verwaltet. Verbindungen werden aus dem Pool gezogen, wenn die Anwendung **SQLConnect** oder **SQLDriverConnect** aufruft, und werden an den Pool zurückgegeben, wenn die Anwendung **SQLDisconnect**aufruft. Die Größe des Pools wird dynamisch, basierend auf den angeforderten Ressourcenzuordnungen. Sie wird basierend auf dem Inaktivitätstimeout verkleinert: Wenn eine Verbindung für einen bestimmten Zeitraum inaktiv ist (sie wurde in einer Verbindung nicht verwendet), wird sie aus dem Pool entfernt. Die Größe des Pools ist nur durch Speichereinschränkungen und Einschränkungen auf dem Server begrenzt.  
  
 Der Treiber-Manager bestimmt, ob eine bestimmte Verbindung in einem Pool gemäß den in **SQLConnect** oder **SQLDriverConnect**übergebenen Argumenten und entsprechend den Verbindungsattributen verwendet werden soll, die nach der Zuweisung der Verbindung festgelegt wurden.  
  
 Wenn der Treiber-Manager Verbindungen bündelt, muss er feststellen können, ob eine Verbindung noch funktioniert, bevor die Verbindung verteilt wird. Andernfalls gibt der Treiber-Manager die tote Verbindung an die Anwendung weiter, wenn ein vorübergehender Netzwerkfehler auftritt. Ein neues Verbindungsattribut wurde in ODBC 3 *.x*definiert : SQL_ATTR_CONNECTION_DEAD. Dies ist ein schreibgeschütztes Verbindungsattribut, das entweder SQL_CD_TRUE oder SQL_CD_FALSE zurückgibt. Der Wert SQL_CD_TRUE bedeutet, dass die Verbindung verloren gegangen ist, während der Wert SQL_CD_FALSE bedeutet, dass die Verbindung noch aktiv ist. (Treiber, die früheren ODBC-Versionen entsprechen, können dieses Attribut ebenfalls unterstützen.)  
  
 Ein Treiber muss diese Option effizient implementieren, da dies die Leistung des Verbindungspoolings beeinträchtigt. Insbesondere sollte ein Aufruf zum Abrufen dieses Verbindungsattributs keinen Roundtrip zum Server verursachen. Stattdessen sollte ein Treiber einfach den letzten bekannten Zustand der Verbindung zurückgeben. Die Verbindung ist tot, wenn die letzte Verbindung zum Server fehlgeschlagen ist, und nicht tot, wenn die letzte Verbindung erfolgreich war.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn eine Verbindung verloren gegangen ist (über SQL_ATTR_CONNECTION_DEAD gemeldet), zerstört der ODBC-Treiber-Manager diese Verbindung, indem er SQLDisconnect im Treiber aufruft. Neue Verbindungsanforderungen finden möglicherweise keine verwendbare Verbindung im Pool. Schließlich kann der Treiber-Manager eine neue Verbindung herstellen, vorausgesetzt, der Pool ist leer.  
  
 Um einen Verbindungspool zu verwenden, führt eine Anwendung die folgenden Schritte aus:  
  
1.  Aktiviert das Verbindungspooling, indem **SQLSetEnvAttr** aufgerufen wird, um das SQL_ATTR_CONNECTION_POOLING Umgebungsattribut auf SQL_CP_ONE_PER_DRIVER oder SQL_CP_ONE_PER_HENV festzulegen. Dieser Aufruf muss erfolgen, bevor die Anwendung die freigegebene Umgebung zuweist, für die das Verbindungspooling aktiviert werden soll. Das Umgebungshandle im Aufruf von **SQLSetEnvAttr** sollte auf null festgelegt werden, was SQL_ATTR_CONNECTION_POOLING ein Attribut auf Prozessebene macht. Wenn das Attribut auf SQL_CP_ONE_PER_DRIVER festgelegt ist, wird für jeden Treiber ein einzelner Verbindungspool unterstützt. Wenn eine Anwendung mit vielen Treibern und wenigen Umgebungen funktioniert, ist dies möglicherweise effizienter, da möglicherweise weniger Vergleiche erforderlich sind. Wenn auf SQL_CP_ONE_PER_HENV festgelegt ist, wird für jede Umgebung ein einzelner Verbindungspool unterstützt. Wenn eine Anwendung mit vielen Umgebungen und wenigen Treibern funktioniert, ist dies möglicherweise effizienter, da möglicherweise weniger Vergleiche erforderlich sind. Das Verbindungspooling ist deaktiviert, indem SQL_ATTR_CONNECTION_POOLING auf SQL_CP_OFF gesetzt wird.  
  
2.  Ordnet eine Umgebung zu, indem **SQLAllocHandle** mit dem *HandleType-Argument* aufgerufen wird, das auf SQL_HANDLE_ENV festgelegt ist. Die von diesem Aufruf zugewiesene Umgebung ist eine implizite freigegebene Umgebung, da das Verbindungspooling aktiviert wurde. Die zu verwendende Umgebung wird jedoch erst bestimmt, **wenn SQLAllocHandle** mit einem *HandleType* von SQL_HANDLE_DBC in dieser Umgebung aufgerufen wird.  
  
3.  Ordnet eine Verbindung zu, indem **SQLAllocHandle** aufgerufen wird, wobei *InputHandle* auf SQL_HANDLE_DBC festgelegt ist und das *InputHandle* auf das Umgebungshandle festgelegt ist, das für das Verbindungspooling zugewiesen ist. Der Treiber-Manager versucht, eine vorhandene Umgebung zu finden, die den von der Anwendung festgelegten Umgebungsattributen entspricht. Wenn keine solche Umgebung vorhanden ist, wird eine mit einer Referenzanzahl (vom Treiber-Manager verwaltet) von 1 erstellt. Wenn eine übereinstimmende freigegebene Umgebung gefunden wird, wird die Umgebung an die Anwendung zurückgegeben, und die Referenzanzahl wird erhöht. (Die tatsächlich zu verwendende Verbindung wird vom Treiber-Manager erst festgelegt, wenn **SQLConnect** oder **SQLDriverConnect** aufgerufen wird.)  
  
4.  Ruft **SQLConnect** oder **SQLDriverConnect** auf, um die Verbindung herzustellen. Der Treiber-Manager verwendet die Verbindungsoptionen beim Aufruf von **SQLConnect** (oder die Verbindungsschlüsselwörter im Aufruf von **SQLDriverConnect**) und die Verbindungsattribute, die nach der Verbindungszuordnung festgelegt wurden, um zu bestimmen, welche Verbindung im Pool verwendet werden soll.  
  
    > [!NOTE]  
    >  Wie eine angeforderte Verbindung mit einer gepoolten Verbindung abgeglichen wird, wird durch das SQL_ATTR_CP_MATCH Umgebungsattribut bestimmt. Weitere Informationen finden Sie unter [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md).  
  
     ODBC-Anwendungen, die Verbindungspooling verwenden, sollten [CoInitializeEx](https://go.microsoft.com/fwlink/?LinkID=116307) während der Anwendungsinitialisierung aufrufen und [CoUninitialize](https://go.microsoft.com/fwlink/?LinkId=116310) aufrufen, wenn die Anwendung geschlossen wird.  
  
5.  Ruft **SQLDisconnect** auf, wenn die Verbindung hergestellt wird. Die Verbindung wird an den Verbindungspool zurückgegeben und steht zur Wiederverwendung zur Verfügung.  
  
 Ausführliche Informationen finden Sie unter [Pooling in den Microsoft Data Access Components](https://go.microsoft.com/fwlink/?LinkId=120776).  
  
## <a name="connection-pooling-considerations"></a>Überlegungen zum Verbindungspooling  
 Das Ausführen einer der folgenden Aktionen mithilfe eines SQL-Befehls (und nicht über die ODBC-API) kann sich auf den Zustand der Verbindung auswirken und unerwartete Probleme verursachen, wenn das Verbindungspooling aktiv ist:  
  
-   Öffnen einer Verbindung und Ändern der Standarddatenbank.  
  
-   Verwenden der SET-Anweisung zum Ändern aller konfigurierbaren Optionen (einschließlich SET ROWCOUNT, ANSI_NULL, IMPLICIT_TRANSACTIONS, SHOWPLAN, STATISTICS, TEXTSIZE und DATEFORMAT).  
  
-   Erstellen temporärer Tabellen und gespeicherter Prozeduren.  
  
 Wenn eine dieser Aktionen außerhalb der ODBC-API ausgeführt wird, erbt die nächste Person, die die Verbindung verwendet, automatisch die vorherigen Einstellungen, Tabellen oder Prozeduren.  
  
> [!NOTE]  
>  Sie erwarten nicht, dass bestimmte Einstellungen im Verbindungsstatus vorhanden sind. Sie sollten immer den Verbindungsstatus in Ihrer Anwendung festlegen und sicherstellen, dass die Anwendung alle nicht verwendeten Verbindungspoolingeinstellungen entfernt.  
  
## <a name="driver-aware-connection-pooling"></a>Treiberfähiges Verbindungspooling  
 Ab Windows 8 kann ein ODBC-Treiber Verbindungen im Pool effizienter nutzen. Weitere Informationen finden Sie unter [Treiber-Aware Connection Pooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Herstellen einer Verbindung mit einer Datenquelle oder einem Treiber](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md)   
 [Entwickeln eines ODBC-Treibers](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Pooling in den Microsoft Data Access-Komponenten](https://go.microsoft.com/fwlink/?LinkId=120776)
