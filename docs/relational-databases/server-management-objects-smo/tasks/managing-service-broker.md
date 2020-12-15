---
description: Verwalten von Service Broker
title: Verwalten von Service Broker
ms.custom: seo-dt-2019
ms.date: 05/24/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- Service Broker [SMO]
ms.assetid: b29d7432-d1e5-4bb6-b544-57b3a9430f95
author: markingmyname
ms.author: maghan
monikerRange: =azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 03dd1f5c0eb1e8e1808d346521732b64cc035171
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97475471"
---
# <a name="managing-service-broker"></a>Verwalten von Service Broker

[!INCLUDE[sql-asdbmi](../../../includes/applies-to-version/sql-asdbmi.md)]

  In SMO werden die [!INCLUDE[ssSB](../../../includes/sssb-md.md)] -Objekte im **Microsoft.SqlServer.Management.Smo.Broker** -Namespace gefunden, was einen Verweis auf Microsoft.SqlServer.Smo.dll erforderlich macht. Ein Verweis auf Microsoft.SqlServer.ServiceBrokerEnum.dll ist auch für das Unterstützen von Klasseninformationen erforderlich.  
  
 SMO stellt einen Satz an [!INCLUDE[ssSB](../../../includes/sssb-md.md)] -Objekten bereit, die programmgesteuerte Verwaltung (DDL) der [!INCLUDE[ssSB](../../../includes/sssb-md.md)] -Implementierung zulassen. Hierzu gehört das Definieren der Nachrichtentypen, Verträge, Warteschlangen und Dienste. Da SMO ein Verwaltungstool ist, das nicht für die Bearbeitung von Daten konzipiert ist, wird das Senden und Empfangen von [!INCLUDE[ssSB](../../../includes/sssb-md.md)] -Nachrichten von SMO nicht unterstützt.  
  
 In SMO ist das <xref:Microsoft.SqlServer.Management.Smo.Database.ServiceBroker%2A>-Objekt die Klasse oberster Ebene, unter der sich die gesamte [!INCLUDE[ssSB](../../../includes/sssb-md.md)]-Funktionalität befindet. Eine [!INCLUDE[ssSB](../../../includes/sssb-md.md)] -Implementierung ist für jede Datenbank erforderlich, die an der verteilten Messaginganwendung teilnimmt. Daher ist das <xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceBroker>-Objekt ein untergeordnetes Objekt des <xref:Microsoft.SqlServer.Management.Smo.Database>-Objekts.  
  
 Das <xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceBroker>-Objekt enthält Auflistungen der folgenden Objekte, die verwendet werden, um die [!INCLUDE[ssSB](../../../includes/sssb-md.md)]-Implementierung zu definieren:  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Broker.MessageType>-Objekte stellen Nachrichtentypen dar, die den Inhalt von Nachrichten definieren.  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Broker.MessageTypeMapping>-Objekte stellen Verträge dar, die die Richtung und den Typ von Nachrichten in einer angegebenen Konversation angeben.  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceQueue>-Objekte speichern Nachrichten vor dem Senden und nachdem sie empfangen wurden. Sie bieten asynchrone Kommunikation zwischen Diensten sowie andere Vorteile, wie etwa das automatische Sperren von Nachrichten in derselben Konversationsgruppe.  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Broker.BrokerService>-Objekte stellen [!INCLUDE[ssSB](../../../includes/sssb-md.md)]-Dienste dar, die die adressierbaren Endpunkte für Konversationen bilden. [!INCLUDE[ssSB](../../../includes/sssb-md.md)]-Meldungen werden von einem Dienst an einen anderen Dienst gesendet. Ein Dienst gibt eine Warteschlange zum Aufbewahren von Nachrichten sowie Verträge an, für die der Dienst das Ziel sein kann.  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Broker.RemoteServiceBinding>-Objekte stellen die Einstellungen dar, die von [!INCLUDE[ssSB](../../../includes/sssb-md.md)] für die Sicherheit und Authentifizierung bei der Kommunikation mit einem Remotedienst verwendet werden.  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceRoute>-Objekte stellen eine [!INCLUDE[ssSB](../../../includes/sssb-md.md)]-Route dar, die die Speicherortinformationen für den Dienst und die Datenbank, in der sie definiert ist, enthält. Eine Route ist für die Nachrichtenübermittlung erforderlich. Standardmäßig enthält jede Datenbank eine Route, die den Speicherort als aktuelle Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]angibt.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.SqlServer.Management.Smo.Broker>   
 [SQL Server Service Broker](../../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  
