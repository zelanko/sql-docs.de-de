---
title: Verwalten von Service Broker | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- Service Broker [SMO]
ms.assetid: b29d7432-d1e5-4bb6-b544-57b3a9430f95
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: fb5f300776f7dfdaa09eaae6bda301d707816155
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47814688"
---
# <a name="managing-service-broker"></a>Verwalten von Service Broker
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  In SMO werden die [!INCLUDE[ssSB](../../../includes/sssb-md.md)] Objekte befinden sich die **Microsoft.SqlServer.Management.Smo.Broker** -Namespace, der einen Verweis auf Microsoft.SqlServer.Smo.dll erforderlich. Ein Verweis auf Microsoft.SqlServer.ServiceBrokerEnum.dll ist auch für das Unterstützen von Klasseninformationen erforderlich.  
  
 SMO stellt einen Satz von [!INCLUDE[ssSB](../../../includes/sssb-md.md)] Objekte, die programmgesteuerte Verwaltung (DDL) der zulassen der [!INCLUDE[ssSB](../../../includes/sssb-md.md)] Implementierung. Hierzu gehört das Definieren der Nachrichtentypen, Verträge, Warteschlangen und Dienste. Da SMO ein Verwaltungstool ist, das nicht für die Bearbeitung von Daten konzipiert ist, wird das Senden und Empfangen von [!INCLUDE[ssSB](../../../includes/sssb-md.md)]-Nachrichten von SMO nicht unterstützt.  
  
 In SMO werden die <xref:Microsoft.SqlServer.Management.Smo.Database.ServiceBroker%2A> Objekt ist die Klasse der obersten Ebene mit dem alle der [!INCLUDE[ssSB](../../../includes/sssb-md.md)] Funktionalität befindet sich. Ein [!INCLUDE[ssSB](../../../includes/sssb-md.md)] Implementierung ist erforderlich für jede Datenbank, die in der verteilten Messaginganwendung teilnimmt. Daher ist das <xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceBroker>-Objekt ein untergeordnetes Objekt des <xref:Microsoft.SqlServer.Management.Smo.Database>-Objekts.  
  
 Das <xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceBroker>-Objekt enthält Auflistungen der folgenden Objekte, die verwendet werden, um die [!INCLUDE[ssSB](../../../includes/sssb-md.md)]-Implementierung zu definieren:  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Broker.MessageType>-Objekte stellen Nachrichtentypen dar, die den Inhalt von Nachrichten definieren.  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Broker.MessageTypeMapping>-Objekte stellen Verträge dar, die die Richtung und den Typ von Nachrichten in einer angegebenen Konversation angeben.  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceQueue>-Objekte speichern Nachrichten vor dem Senden und nachdem sie empfangen wurden. Sie bieten asynchrone Kommunikation zwischen Diensten sowie andere Vorteile, wie etwa das automatische Sperren von Nachrichten in derselben Konversationsgruppe.  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Broker.BrokerService>-Objekte stellen [!INCLUDE[ssSB](../../../includes/sssb-md.md)]-Dienste dar, die die adressierbaren Endpunkte für Konversationen bilden. [!INCLUDE[ssSB](../../../includes/sssb-md.md)] Nachrichten werden von einem Dienst an einen anderen Dienst gesendet. Ein Dienst gibt eine Warteschlange zum Aufbewahren von Nachrichten sowie Verträge an, für die der Dienst das Ziel sein kann.  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Broker.RemoteServiceBinding> Objekte stellen die Einstellungen dar, die [!INCLUDE[ssSB](../../../includes/sssb-md.md)] für Sicherheit und Authentifizierung verwendet wird, bei der Kommunikation mit einem Remotedienst.  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceRoute> Stellt Objekte eine [!INCLUDE[ssSB](../../../includes/sssb-md.md)] Route enthält, die die Speicherortinformationen für den Dienst und die Datenbank auf dem es definiert ist. Eine Route ist für die Nachrichtenübermittlung erforderlich. Standardmäßig enthält jede Datenbank eine Route, die den Speicherort, wie die aktuelle Instanz von angibt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.SqlServer.Management.Smo.Broker>   
 [SQL Server Service Broker](../../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  
