---
title: OLE DB-Verbindungs-Manager | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- OLE DB connection manager
- data sources [Integration Services], connections
- connection managers [Integration Services], OLE DB
- connections [Integration Services], OLE DB
ms.assetid: 91e3622e-4b1a-439a-80c7-a00b90d66979
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 00d28ef5dbe2c0a19e5a464981934f2a84df7a7c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62833727"
---
# <a name="ole-db-connection-manager"></a>OLE DB-Verbindungs-Manager
  Durch einen OLE DB-Verbindungs-Manager kann ein Paket mithilfe eines OLE DB-Anbieters eine Verbindung mit einer Datenquelle herstellen. Beispielsweise kann ein OLE DB-Verbindungs-Manager, der eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellt, den [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB-Anbieter für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwenden.  
  
> [!NOTE]
>  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 11.0 OLEDB-Anbieter unterstützt die neuen Schlüsselwörter für Verbindungszeichenfolgen (MultiSubnetFailover=True) für Multisubnetz-Failoverclustering nicht. Weitere Informationen finden Sie in den [Anmerkungen](https://go.microsoft.com/fwlink/?LinkId=247824) zu dieser Version von SQL Server und im Blogbeitrag [AlwaysOn-multisubnetz-Failover und SSIS](https://www.mattmasson.com/2012/03/alwayson-multi-subnet-failover-and-ssis/)auf www.mattmasson.com.  
  
 Mehrere Tasks und Datenflusskomponenten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] verwenden einen OLE DB-Verbindungs-Manager. Beispielsweise extrahieren und laden die OLE DB-Quelle und das OLE DB-Ziel mit diesem Verbindungs-Manager Daten. Und der Task SQL ausführen kann damit eine Verbindung mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank herstellen, um Abfragen auszuführen.  
  
 Der OLE DB-Verbindungs-Manager wird auch für den Zugriff auf OLE DB-Datenquellen in benutzerdefinierten Tasks verwendet, die in nicht verwaltetem Code und einer Programmiersprache wie z. B. C++ geschrieben sind.  
  
 Wenn Sie einem Paket einen OLE DB-Verbindungs-Manager hinzufügen, erstellt [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] einen Verbindungs-Manager, der zur Laufzeit in eine OLE DB-Verbindung aufgelöst wird, die Eigenschaften des Verbindungs-Managers festlegt und der `Connections`-Auflistung im Paket den Verbindungs-Manager hinzufügt.  
  
 Die `ConnectionManagerType`-Eigenschaft des Verbindungs-Managers ist auf `OLEDB` festgelegt.  
  
 Der OLE DB-Verbindungs-Manager kann wie folgt konfiguriert werden:  
  
-   Stellen Sie eine Verbindungszeichenfolge bereit, die die Anforderungen des ausgewählten Anbieters erfüllt.  
  
-   Schließen Sie in Abhängigkeit vom Anbieter den Namen der Datenquelle ein, mit der eine Verbindung hergestellt werden soll.  
  
-   Stellen Sie entsprechende Sicherheitsanmeldeinformationen für den ausgewählten Anbieter bereit.  
  
-   Geben Sie an, ob die im Verbindungs-Manager erstellte Verbindung zur Laufzeit beibehalten wird.  
  
## <a name="logging"></a>Protokollierung  
 Sie können die vom OLE DB-Verbindungs-Manager an externe Datenanbieter gerichteten Aufrufe protokollieren. Mithilfe dieser Protokollierungsfunktionen können Sie Probleme bei Verbindungen behandeln, die vom OLE DB-Verbindungs-Manager mit externen Datenquellen hergestellt werden. Aktivieren Sie zum Protokollieren der vom OLE DB Verbindungs-Manager an externe Datenanbieter gerichteten Aufrufe die Paket Protokollierung, und wählen Sie das **Diagnose** Ereignis auf Paketebene aus. Weitere Informationen finden Sie unter [Behandeln von Problemen mit Paketausführungstools](../troubleshooting/troubleshooting-tools-for-package-execution.md).  
  
## <a name="configuration-of-the-oledb-connection-manager"></a>Konfiguration des OLEDB-Verbindungs-Managers  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen. Weitere Informationen zu den Eigenschaften, die Sie im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer festlegen können, finden Sie unter [Konfigurieren des OLE DB-Verbindungs-Managers](../configure-ole-db-connection-manager.md). Informationen zum programmgesteuerten Konfigurieren eines Verbindungs-Managers finden Sie in der Dokumentation zur **T:Microsoft.SqlServer.Dts.Runtime.ConnectionManager** -Klasse im Entwicklerhandbuch.  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   Wiki-Artikel [SSIS mit Oracle-Connectors](https://go.microsoft.com/fwlink/?LinkId=220670) auf Social.technet.Microsoft.com.  
  
-   Technischer Artikel, [Connection Strings for OLE DB Providers](https://go.microsoft.com/fwlink/?LinkId=220744)(Verbindungszeichenfolgen für OLE DB-Anbieter), auf carlprothman.net.  
  
## <a name="see-also"></a>Weitere Informationen  
 [OLE DB-Quelle](../data-flow/ole-db-source.md)   
 [OLE DB-Ziel](../data-flow/ole-db-destination.md)   
 [SQL ausführen (Task)](../control-flow/execute-sql-task.md)   
 [Integration Services-Verbindungen &#40;SSIS&#41;](integration-services-ssis-connections.md)  
  
  
