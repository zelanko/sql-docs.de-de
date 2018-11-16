---
title: 'Der ODBC-Treiber unter Linux und macOS: Hochverfügbarkeit und Notfallwiederherstellung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 04/04/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: fa656c5b-a935-40bf-bc20-e517ca5cd0ba
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 952194b55ef14527e2f04d18edb5873e6098d2da
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "51600100"
---
# <a name="odbc-driver-on-linux-and-macos-support-for-high-availability-and-disaster-recovery"></a>Der ODBC-Treiber unter Linux und macOS für Hochverfügbarkeit und Notfallwiederherstellung
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Die ODBC-Treiber für Linux und MacOS-Unterstützung [!INCLUDE[ssHADR](../../../includes/sshadr_md.md)]. Weitere Informationen zu [!INCLUDE[ssHADR](../../../includes/sshadr_md.md)] finden Sie hier:  
  
-   [Verfügbarkeitsgruppenlistener, Clientkonnektivität und Anwendungsfailover (SQL Server)](https://msdn.microsoft.com/library/hh213417.aspx)  
  
-   [Erstellung und Konfiguration von Verfügbarkeitsgruppen (SQL Server)](https://msdn.microsoft.com/library/ff878265.aspx)  
  
-   [Failoverclustering und Always On-Verfügbarkeitsgruppen (SQL Server)](https://msdn.microsoft.com/library/ff929171.aspx)  
  
-   [Aktive sekundäre Replikate: Lesbare sekundäre Replikate (Always On-Verfügbarkeitsgruppen)](https://msdn.microsoft.com/library/ff878253.aspx)  
  
Sie können den Verfügbarkeitsgruppenlistener einer bestimmten Verfügbarkeitsgruppe in der Verbindungszeichenfolge angeben. Wenn eine ODBC-Anwendung unter Linux oder macOS mit einer Datenbank in einer Verfügbarkeitsgruppe verbunden ist, die ein Failover ausführt, wird die ursprüngliche Verbindung unterbrochen, und die Anwendung muss eine neue Verbindung herstellen, um die Arbeit nach dem Failover fortzusetzen.

Die ODBC-Treiber unter Linux und MacOS durchlaufen nacheinander alle IP-Adressen, die einen DNS-Hostnamen zugeordnet, wenn Sie nicht eine mit einem Verfügbarkeitsgruppen-Listener Verbindung und mehrere IP-Adressen Hostnamen zugeordnet sind.

Wenn der DNS-Server die erste zurückgegebene IP-Adresse nicht verbunden ist, können diese Iterationen zeitaufwendig sein. Beim Verbinden mit einem Verfügbarkeitsgruppenlistener versucht der Treiber mit allen IP-Adressen parallel Verbindungen herzustellen. Falls ein Verbindungsversuch erfolgreich war, bricht der Treiber alle weiteren laufenden Verbindungsversuche ab.

> [!NOTE]  
> Da eine Verbindung aufgrund eines Verfügbarkeitsgruppenfailovers fehlschlagen kann, empfiehlt sich die Implementierung einer Verbindungswiederholungslogik, wodurch im Fall einer fehlgeschlagenen Verbindung bis zur erneuten Verbindung Wiederholungsversuche erfolgen. Das Erhöhen des Verbindungstimeouts sowie die Implementierung einer Verbindungswiederholungslogik erhöhen die Chance auf eine Verbindung mit der Verfügbarkeitsgruppe.

## <a name="connecting-with-multisubnetfailover"></a>Verbinden mit MultiSubnetFailover

Geben Sie immer **MultiSubnetFailover=Yes** an, wenn Sie eine Verbindung mit einem [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]-Verfügbarkeitsgruppenlistener oder einer [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]-Failoverclusterinstanz herstellen. **MultiSubnetFailover** ermöglicht für alle Verfügbarkeitsgruppen und Failoverclusterinstanzen in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] ein schnelleres Failover. **MultiSubnetFailover** reduziert auch die Failoverzeit für Einzel- und Multisubnetz Always On-Topologien. Während eines Multisubnetzfailovers versucht der Client, Verbindungen parallel herzustellen. Während eines subnetzfailovers versucht der Treiber die TCP-Verbindung aggressiv auszuführen.

Die **MultiSubnetFailover** -Verbindungseigenschaft zeigt an, dass die Anwendung in einer Verfügbarkeitsgruppe oder einer Failoverclusterinstanz bereitgestellt wird. Der Treiber versucht, sich mit der Datenbank auf der primären [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz zu verbinden, indem er versucht, sich mit allen IP-Adressen zu verbinden. Bei der Verbindung mit **MultiSubnetFailover=Yes** wiederholt der Client die Verbindungsversuche mit der TCP-Verbindung mit TCP-Neuübertragungsintervallen, die kürzer sind, als vom Betriebssystem vorgegebenen. **MultiSubnetFailover=Yes** ermöglicht eine schnellere Verbindungswiederherstellung nach dem Failover entweder einer AlwaysOn-Verfügbarkeitsgruppe oder einer AlwaysOn-Failoverclusterinstanz. **MultiSubnetFailover=Yes** gilt sowohl für Einzel- als auch Multisubnetzverfügbarkeitsgruppen und Failoverclusterinstanzen.  

Verwenden Sie **MultiSubnetFailover=Yes** wenn Sie eine Verbindung mit einem Verfügbarkeitsgruppenlistener oder einer Failoverclusterinstanz herstellen. Andernfalls kann die Leistung Ihrer Anwendung negativ beeinträchtigt werden.

Beachten Sie beim Herstellen einer Verbindung mit einem Server in einer Verfügbarkeitsgruppe oder einer Failoverclusterinstanz Folgendes:
  
-   Geben Sie **MultiSubnetFailover = Yes** zur Verbesserung der Leistung bei der Verbindung mit einem Einzelsubnetz oder multisubnetz-Verfügbarkeitsgruppe.

-   Geben Sie den verfügbarkeitsgruppenlistener der verfügbarkeitsgruppe, wie der Server in der Verbindungszeichenfolge.
  
-   Sie können keine Verbindung mit einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz herstellen, die mit mehr als 64 IP-Adressen konfiguriert ist.

-   Beide [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentifizierung oder Kerberos-Authentifizierung mit verwendet werden kann **MultiSubnetFailover = Yes** ohne Auswirkungen auf das Verhalten der Anwendung.

-   Sie können den Wert von **loginTimeout** erhöhen, um die Failoverzeit zu berücksichtigen und die Anzahl der von der Anwendung durchgeführten Verbindungsversuche zu reduzieren.

-   Verteilte Transaktionen werden nicht unterstützt.  
  
Wenn das schreibgeschützte Routing nicht aktiviert ist, scheitert die Verbindungsherstellung mit einem sekundären Replikatspeicherort in einer Verfügbarkeitsgruppe in den folgenden Situationen:  
  
1.  Wenn der sekundäre Replikatspeicherort nicht zum Akzeptieren von Verbindungen konfiguriert ist.  
  
2.  Wenn eine Anwendung **ApplicationIntent=ReadWrite** verwendet wird und der sekundäre Replikatspeicherort für den schreibgeschützten Zugriff konfiguriert ist.  
  
Es kann keine Verbindung hergestellt werden, wenn ein primäres Replikat so konfiguriert ist, dass schreibgeschützte Arbeitsauslastungen abgelehnt werden und die Verbindungszeichenfolge **ApplicationIntent=ReadOnly**enthält.  


[!INCLUDE[specify-application-intent_read-only-routing](~/includes/paragraph-content/specify-application-intent-read-only-routing.md)]


## <a name="odbc-syntax"></a>ODBC-Syntax

Zwei ODBC-Verbindungszeichenfolgen-Schlüsselwörter unterstützen [!INCLUDE[ssHADR](../../../includes/sshadr_md.md)]:  
  
-   **ApplicationIntent**  
  
-   **MultiSubnetFailover**  
  
Weitere Informationen zu ODBC-Verbindungszeichenfolgen-Schlüsselwörtern finden Sie unter [Using Connection String Keywords with SQL Server Native Client (Verwenden von Schlüsselwörtern für Verbindungszeichenfolgen mit SQL Native Client)](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
Die entsprechende Verbindungsattribute sind:
  
-   **SQL_COPT_SS_APPLICATION_INTENT**  
  
-   **SQL_COPT_SS_MULTISUBNET_FAILOVER**  
  
Weitere Informationen zu den ODBC-Verbindungsattributen finden Sie unter [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md).  
  
Eine ODBC-Anwendung, die [!INCLUDE[ssHADR](../../../includes/sshadr_md.md)] verwendet, kann eine von zwei Funktionen verwenden, um die Verbindung herzustellen:  
  
|Funktion|und Beschreibung|  
|------------|---------------|  
|[SQLConnect-Funktion](../../../odbc/reference/syntax/sqlconnect-function.md)|**SQLConnect** unterstützt sowohl **ApplicationIntent** als auch **MultiSubnetFailover** über einen Datenquellennamen (DSN) oder Verbindungsattribute.|  
|[SQLDriverConnect-Funktion](../../../odbc/reference/syntax/sqldriverconnect-function.md)|**SQLDriverConnect** unterstützt **ApplicationIntent** und **MultiSubnetFailover** über DSN, Schlüsselwörter für Verbindungszeichenfolgen oder Verbindungsattribute.|
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  

[Schlüsselwörter für Verbindungszeichenfolgen und Datenquellennamen (DSNs)](../../../connect/odbc/linux-mac/connection-string-keywords-and-data-source-names-dsns.md)

[Programmierrichtlinien](../../../connect/odbc/linux-mac/programming-guidelines.md)

[Versionsanmerkungen](../../../connect/odbc/linux-mac/release-notes.md)  
