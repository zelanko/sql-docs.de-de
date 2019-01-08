---
title: Unterstützung von Dienstprinzipalnamen (SPN) in Clientverbindungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/08/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client, SPNs
- ODBC, SPNs
- OLE DB, SPNs
- SPNs [SQL Server]
ms.assetid: 96598c69-ce9a-4090-aacb-d546591e8af7
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 415e1a46734eeed97457a6235a0d9912b17e232b
ms.sourcegitcommit: 467b2c708651a3a2be2c45e36d0006a5bbe87b79
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53979966"
---
# <a name="service-principal-name-spn-support-in-client-connections"></a>Unterstützung von Dienstprinzipalnamen (SPN) in Clientverbindungen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Ab [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] wurde die Unterstützung für Dienstprinzipalnamen (Service Principal Names, SPNs) erweitert und die gegenseitige Authentifizierung über alle Protokolle hinweg aktiviert. In vorherigen Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] wurden SPNs nur für Kerberos statt TCP unterstützt, wenn der Standard-SPN der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz in Active Directory registriert wurde.  
  
 SPNs werden vom Authentifizierungsprotokoll verwendet, um das Konto zu bestimmen, in dem eine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Instanz ausgeführt wird. Ist das Konto der Instanz bekannt, kann mithilfe der Kerberos-Authentifizierung die gegenseitige Authentifizierung von Client und Server durchgeführt werden. Ist das Konto der Instanz nicht bekannt, wird die NTML-Authentifizierung verwendet, die nur die Authentifizierung des Clients durch den Server durchführt. Die Authentifizierungssuche wird derzeit vom [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ausgeführt. Der SPN wird vom Instanznamen und den Netzwerkverbindungseigenschaften abgeleitet. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanzen versuchen, SPNs beim Start zu registrieren, oder sie können manuell registriert werden. Die Registrierung schlägt jedoch fehl, wenn das Konto, dass die Registrierung der SPNs vornimmt, nicht über ausreichende Zugriffsrechte verfügt.  
  
 Domänen- und Computerkonten werden automatisch in Active Directory registriert. Diese können als SPNs verwendet werden, oder Administratoren können ihre eigenen SPNs definieren. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ist einfacher zu verwalten und auch zuverlässiger, da Clients direkt den zu verwendenden SPN festlegen können.  
  
> [!NOTE]  
>  Ein von einer Clientanwendung festgelegter SPN wird nur verwendet, wenn eine Verbindung mit integrierten Sicherheitsfunktionen von Windows hergestellt wird.  
  
> [!TIP]  
>  **[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Kerberos-Konfigurations-Manager für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]** ist ein Diagnosetool zur Behebung Kerberos-bezogener Verbindungsprobleme bei [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Weitere Informationen finden Sie unter [Microsoft Kerberos-Konfigurations-Manager für SQL Server](https://www.microsoft.com/download/details.aspx?id=39046).  
  
 Weitere Informationen zu Kerberos finden Sie in den folgenden Artikeln:  
  
-   [Kerberos – Technische Ergänzung für Windows](https://go.microsoft.com/fwlink/?LinkId=101449)  
  
-   [Microsoft Kerberos](https://go.microsoft.com/fwlink/?LinkID=100758)  
  
## <a name="usage"></a>Verwendung  
 In der folgenden Tabelle werden die häufigsten Szenarien beschrieben, in denen Clientanwendungen die sichere Authentifizierung aktivieren können.  
  
|Szenario|Description|  
|--------------|-----------------|  
|Eine ältere Anwendung gibt keinen SPN an.|Dieses Kompatibilitätsszenario stellt sicher, dass sich das Verhalten von Anwendungen, die für frühere Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]entwickelt wurden, nicht verändert. Wenn kein SPN angegeben wurde, verwendet die Anwendung generierte SPNs und erkennt nicht, welche Methode zur Authentifizierung verwendet wurde.|  
|Eine Clientanwendung, die die aktuelle Version von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client verwendet, gibt in der Verbindungszeichenfolge einen SPN als Domänenbenutzerkonto oder Computerkonto, als instanzabhängigen SPN oder als benutzerdefinierte Zeichenfolge an.|Das **ServerSPN** -Schlüsselwort kann von einem Anbieter, einer Initialisierung oder einer Verbindungszeichenfolge zu folgenden Zwecken verwendet werden:<br /><br /> - Angeben des von der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz verwendeten Kontos. Dies vereinfacht den Zugriff auf die Kerberos-Authentifizierung. Wenn ein Kerberos-Schlüsselverteilungscenter (Key Distribution Center, KDC) vorhanden ist und das richtige Konto angegeben wurde, wird wahrscheinlich die Kerberos- anstatt der NTLM-Authentifizierung durchgeführt. Das KDC befindet sich normalerweise auf dem gleichen Computer wie der Domänencontroller.<br /><br /> - Angeben eines SPNs, um nach dem Dienstkonto der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz zu suchen. Für jede [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz werden zwei Standard-SPNs generiert, die für diesen Zweck verwendet werden können. Diese Schlüssel sind jedoch nicht unbedingt in Active Directory vorhanden. Daher ist in dieser Situation die Kerberos-Authentifizierung nicht gewährleistet.<br /><br /> - Angeben eines SPN, der für die Suche nach dem Dienstkonto der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz verwendet werden soll. Dies kann eine beliebige benutzerdefinierte Zeichenfolge sein, die dem Dienstkonto zugeordnet wird. In diesem Fall muss der Schlüssel im KDC manuell registriert werden und den Richtlinien für einen benutzerdefinierten SPN entsprechen.<br /><br /> Das **FailoverPartnerSPN** -Schlüsselwort kann verwendet werden, um den SPN für den Failoverpartnerserver anzugeben. Der Wertebereich des Kontos und des Active Directory-Schlüssels entspricht den Werten, die Sie für den Prinzipalserver angeben können.|  
|Eine ODBC-Anwendung legt einen SPN als Verbindungsattribut für den Prinzipalserver oder Failoverpartnerserver fest.|Das Verbindungsattribut **SQL_COPT_SS_SERVER_SPN** kann zur Festlegung des SPN für eine Verbindung zum Prinzipalserver verwendet werden.<br /><br /> Das Verbindungsattribut **SQL_COPT_SS_FAILOVER_PARTNER_SPN** kann zur Festlegung des SPN für eine Verbindung zum Failoverpartnerserver verwendet werden.|  
|Eine OLE DB-Anwendung legt einen SPN als Initialisierungseigenschaft der Datenquelle für den Prinzipalserver oder einen Failoverpartnerserver fest.|Die Verbindungseigenschaft **SSPROP_INIT_SERVER_SPN** im **DBPROPSET_SQLSERVERDBINIT** -Eigenschaftensatz kann zur Festlegung des SPN für eine Verbindung verwendet werden.<br /><br /> Die Verbindungseigenschaft **SSPROP_INIT_FAILOVER_PARTNER_SPN** in **DBPROPSET_SQLSERVERDBINIT** kann zur Festlegung des SPN für eine Verbindung zum Failoverpartnerserver verwendet werden.|  
|Ein Benutzer legt einen SPN für einen Server oder Failoverpartnerserver in einem ODBC-Datenquellenamen (Data Source Name, DSN) fest.|Der SPN kann in einem ODBC DSN durch die DSN-Setupdialogfelder angegeben werden.|  
|Der Benutzer legt einen SPN für einen Server oder Failoverpartnerserver in den OLE DB-Dialogfeldern **Datenlink** oder **Anmeldung** fest.|Der SPN kann im Dialogfeld **Datenlinks** oder **Anmeldung** angegeben werden. Das Dialogfeld **Anmeldung** kann mit entweder ODBC oder OLE DB verwendet werden.|  
|Eine ODBC-Anwendung bestimmt die Authentifizierungsmethode, die zum Herstellen einer Verbindung verwendet wird.|Wenn eine Verbindung erfolgreich hergestellt wurde, kann eine Anwendung das Verbindungsattribut **SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD** abfragen, um festzustellen, welche Authentifizierungsmethode verwendet wurde. Die Werte enthalten unter anderem **NTLM** und **Kerberos**.|  
|Eine OLE DB-Anwendung bestimmt die Authentifizierungsmethode, die zum Herstellen einer Verbindung verwendet wird.|Wenn eine Verbindung erfolgreich hergestellt wurde, kann eine Anwendung die Verbindungseigenschaft **SSPROP_AUTHENTICATION_METHOD** im **DBPROPSET_SQLSERVERDATASOURCEINFO** -Eigenschaftensatz abfragen, um festzustellen, welche Authentifizierungsmethode verwendet wurde. Die Werte enthalten unter anderem **NTLM** und **Kerberos**.|  
  
## <a name="failover"></a>Failover  
 SPNs werden nicht im Failovercache gespeichert und daher nicht zwischen Verbindungen übergeben. SPNs werden bei allen Verbindungsversuchen mit dem Prinzipal und dem Partner verwendet, wenn Sie in der Verbindungszeichenfolge oder in den Verbindungsattributen angegeben sind.  
  
## <a name="connection-pooling"></a>Verbindungspooling  
 Wenn SPNs nur in einigen, aber nicht in allen Verbindungszeichenfolgen angegeben werden, kann dies zur Poolfragmentierung führen.  
  
 Anwendungen können SPNs programmgesteuert als Verbindungsattribute festlegen, anstatt Schlüsselwörter für Verbindungszeichenfolgen anzugeben. Dadurch kann die Fragmentierung beim Verbindungspooling besser gesteuert werden.  
  
 SPNs in Verbindungszeichenfolgen können durch Festlegen der entsprechenden Verbindungsattribute überschrieben werden, aber Verbindungszeichenfolgen, die vom Verbindungspooling verwendet werden, verwenden die Verbindungszeichenfolgenwerte für Poolingzwecke.  
  
## <a name="down-level-server-behavior"></a>Downlevelserver-Verhalten  
 Das neue Verbindungsverhalten ist clientseitig implementiert und daher kein spezifisches Verhalten von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="linked-servers-and-delegation"></a>Verbindungsserver und Delegierung  
 Beim Einrichten von Verbindungsservern wird der Parameter **@provstr** von [sp_addlinkedserver](../../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md) verwendet, um den SPN für den Server und Failoverpartner festzulegen. Die Vorteile dieser Vorgehensweise sind identisch mit der Angabe von SPNs in clientverbindungszeichenfolgen: Es ist einfacher und zuverlässiger, Verbindungen herzustellen, die die Kerberos-Authentifizierung verwenden.  
  
 Delegierung über Verbindungsserver erfordert die Kerberos-Authentifizierung.  
  
## <a name="management-aspects-of-spns-specified-by-applications"></a>Verwaltungsaspekte von SPNs, die von Anwendungen angegeben werden  
 Berücksichtigen Sie die folgenden Faktoren bei der Entscheidung, ob SPNs in einer Anwendung (über Verbindungszeichenfolgen) oder programmgesteuert über Verbindungseigenschaften (anstatt sich auf den standardmäßig vom Anbieter erstellten SPN zu verlassen) angegeben werden.  
  
-   Sicherheit: Legt die angegebene SPN geschützte Informationen offen?  
  
-   Zuverlässigkeit: Zur Aktivierung von Standard-SPNs muss das Dienstkonto der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] über ausreichende Privilegien zum Update von Active Directory im KDC verfügen.  
  
-   Benutzerfreundlichkeit und Speicherorttransparenz: Wie wirkt es sich auf die SPNs einer Anwendung aus, wenn die Datenbank in eine andere Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verschoben wird? Dies gilt für sowohl den Prinzipalserver als auch seinen Failoverpartner, wenn Sie die Datenbankspiegelung verwenden. Wie wirkt es sich auf Anwendungen aus, wenn eine Serveränderung bedeutet, dass SPNs geändert werden müssen? Werden die Änderungen verwaltet?  
  
## <a name="specifying-the-spn"></a>Angeben des SPN  
 Sie können einen SPN in Dialogfeldern und Code angeben. In diesem Abschnitt wird erläutert, wie Sie einen SPN angeben können.  
  
 Die maximale Länge für einen SPN beträgt 260 Zeichen.  
  
 Die Syntax, die SPNs in Attributen für Verbindungszeichenfolgen und Verbindungen verwenden, lautet wie folgt:  
  
|Syntax|Description|  
|------------|-----------------|  
|MSSQLSvc/*fqdn*|Der vom Anbieter erstellte Standard-SPN für eine Standardinstanz, wenn ein anderes Protokoll als TCP verwendet wird.<br /><br /> *fqdn* ist ein vollqualifizierter Domänenname.|  
|MSSQLSvc/*fqdn*:*port*|Der vom Anbieter erstellte Standard-SPN, wenn TCP verwendet wird.<br /><br /> *port* ist eine TCP-Portnummer.|  
|MSSQLSvc/*fqdn*:*InstanceName*|Der vom Anbieter erstellte Standard-SPN für eine benannte Instanz, wenn ein anderes Protokoll als TCP verwendet wird.<br /><br /> *InstanceName* ist ein Instanzname von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|  
|HOST/*fqdn*<br /><br /> HOST/*MachineName*|Der SPN, der integrierten Computerkonten zugeordnet wird, die automatisch von Windows registriert werden.|  
|*Username*@*Domain*|Direkte Spezifikation eines Domänenkontos.<br /><br /> *Username* ist der Name des Windows-Benutzerkontos.<br /><br /> *Domain* ist ein Windows-Domänenname oder ein vollqualifizierter Domänenname.|  
|*MachineName*$@*Domain*|Ein Computerkonto wird direkt angegeben.<br /><br /> (Wenn der Server, zu dem Sie eine Verbindung herstellen, unter den Konten LOCAL SYSTEM oder NETWORK SERVICE ausgeführt wird, kann **ServerSPN** zum Einrichten der Kerberos-Authentifizierung im Format *MachineName*$@*Domain* angegeben werden.)|  
|*KDCKey*/*MachineName*|Ein vom Benutzer angegebener SPN.<br /><br /> *KDCKey* ist eine alphanumerische Zeichenfolge, die den Regeln für einen KDC-Schlüssel entspricht.|  
  
## <a name="odbc-and-ole-db-syntax-supporting-spns"></a>SPNs, die ODBC und OLE DB-Syntax unterstützen  
 Informationen zur Syntax finden Sie in den folgenden Themen:  
  
-   [Dienstprinzipalnamen &#40;SPNs&#41; in Clientverbindungen &#40;ODBC&#41;](../../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md)  
  
-   [Dienstprinzipalnamen (SPN) &#40;SPNs&#41; in Clientverbindungen &#40;(OLE DB&#41;)](../../../relational-databases/native-client/ole-db/service-principal-names-spns-in-client-connections-ole-db.md)  
  
 Informationen zu Beispielanwendungen, die diese Funktion veranschaulichen, finden Sie unter [Beispiele zur Programmierbarkeit von SQL Server-Daten](https://msftdpprodsamples.codeplex.com/).  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Native Client-Features](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
[Registrieren eines Dienstprinzipalnamens für Kerberos-Verbindungen](../../../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md)  
  
