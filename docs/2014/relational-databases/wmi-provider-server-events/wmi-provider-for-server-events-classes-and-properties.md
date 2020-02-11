---
title: Klassen und Eigenschaften für den WMI-Anbieter für Server Ereignisse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- event classes [WMI]
- WMI Provider for Server Events, events listed
- classes [WMI]
ms.assetid: e2916cd7-a3ed-41e6-97b4-2ee060754cbe
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 24624a5071bad5403afc15259d97754a7feffdcf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63288476"
---
# <a name="wmi-provider-for-server-events-classes-and-properties"></a>Klassen und Eigenschaften für den WMI-Anbieter für Serverereignisse
  Die folgenden Serverereignisse bilden das Programmiermodell für den WMI-Anbieter für Serverereignisse. Es gibt zwei Hauptkategorien von Ereignissen, die durch Absetzen von WQL-Abfragen an den Anbieter abgefragt werden können: DDL-Ereignisse (Data Definition Language) und Ablaufverfolgungsereignisse. Auch die Service Broker-Ereignisse QUEUE_ACTIVATION und BROKER_QUEUE_DISABLED können abgefragt werden. Beachten Sie den inklusiven Charakter der folgenden Strukturdiagramme. Das DDL_ASSEMBLY_EVENTS-Ereignis schließt z. B. beliebige Ereignisse vom Typ ALTER_ASSEMBLY, CREATE_ASSEMBLY und DROP_ASSEMBLY ein. Analog dazu schließt das TRC_FULL_TEXT-Ereignis beliebige Ereignisse vom Typ FT_CRAWL_ABORTED, FT_CRAWL_STARTED und FT_CRAWL_STOPPED ein. ALL_EVENTS deckt alle DDL-Ereignisse, Ablaufverfolgungsereignisse, QUEUE_ACTIVATION und BROKER_QUEUE_DISABLED ab.  
  
 Um zu ermitteln, welche Eigenschaften aus einem Ereignis oder einer Ereignisgruppe abgefragt werden können, konsultieren Sie das Ereignisschema. Standardmäßig wird das Ereignisschema im folgenden Verzeichnis installiert: [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)] Tools\Binn\schemas\sqlserver\2006\11\events\events .xsd.  
  
 Alternativ dazu können Sie auch auf das Ereignis Schema verweisen, [https://schemas.microsoft.com/sqlserver](https://go.microsoft.com/fwlink/?linkid=43100)das unter veröffentlicht wurde.  
  
 Zum ALTER_DATABASE-Ereignis erfahren Sie beispielsweise, dass DDL_SERVER_LEVEL_EVENTS das übergeordnete Ereignis ist und seine Eigenschaften `TSQLCommand` und `DatabaseName` sind. Das Ereignis erbt auch die Eigenschaften `SQLInstance`, `PostTime`, `ComputerName`, `SPID` und `LoginName`. Das Ereignis verfügt über keinen untergeordneten Ereignisse.  
  
> [!NOTE]  
>  Gespeicherte Systemprozeduren, die DDL-ähnliche Vorgänge ausführen, können auch Ereignisbenachrichtigungen auslösen. Testen Sie die Ereignisbenachrichtigungen, um ihre Reaktion auf gespeicherte Systemprozeduren, die ausgeführt werden, zu bestimmen. Beispielsweise lösen die CREATE TYPE-Anweisung und die gespeicherte Prozedur **sp_addtype** eine Ereignis Benachrichtigung aus, die für ein CREATE_TYPE-Ereignis erstellt wird. Weitere Informationen finden Sie unter[DDL-Ereignisse](../../relational-databases/triggers/ddl-events.md).  
  
 **Ereignisse und Ereignisgruppen der Datendefinitionssprache (DDL)**  
  
 ![WMI-Anbieter für Serverereignisse-Ereignisstruktur](../../../2014/database-engine/dev-guide/media/sql-wmi-ddl-events-ktm.gif "WMI-Anbieter für Serverereignisse-Ereignisstruktur")  
  
 **Ablaufverfolgungsereignisse und Ereignisgruppen**  
  
 ![Ablauf Verfolgungs Ereignisse und Ereignis Gruppen](../../../2014/database-engine/dev-guide/media/sql-wmi-trc-all-events.gif "Ablaufverfolgungsereignisse und -Ereignisgruppen")  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konzepte des WMI-Anbieters für Server Ereignisse](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md)   
 [Verwenden von WQL mit dem WMI-Anbieter für Serverereignisse](../../relational-databases/wmi-provider-server-events/using-wql-with-the-wmi-provider-for-server-events.md)  
  
  
