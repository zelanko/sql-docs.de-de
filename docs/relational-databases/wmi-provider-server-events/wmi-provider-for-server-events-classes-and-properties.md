---
description: Klassen und Eigenschaften für den WMI-Anbieter für Serverereignisse
title: Klassen und Eigenschaften für den WMI-Anbieter für Serverereignisse
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- event classes [WMI]
- WMI Provider for Server Events, events listed
- classes [WMI]
ms.assetid: e2916cd7-a3ed-41e6-97b4-2ee060754cbe
author: markingmyname
ms.author: maghan
ms.openlocfilehash: be17f5425d66956028fce13144b6bb908230fca9
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89542730"
---
# <a name="wmi-provider-for-server-events-classes-and-properties"></a>Klassen und Eigenschaften für den WMI-Anbieter für Serverereignisse
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Die folgenden Serverereignisse bilden das Programmiermodell für den WMI-Anbieter für Serverereignisse. Es gibt zwei Hauptkategorien von Ereignissen, die durch Absetzen von WQL-Abfragen an den Anbieter abgefragt werden können: DDL-Ereignisse (Data Definition Language) und Ablaufverfolgungsereignisse. Auch die Service Broker-Ereignisse QUEUE_ACTIVATION und BROKER_QUEUE_DISABLED können abgefragt werden. Beachten Sie den inklusiven Charakter der folgenden Strukturdiagramme. Das DDL_ASSEMBLY_EVENTS-Ereignis schließt z. B. beliebige Ereignisse vom Typ ALTER_ASSEMBLY, CREATE_ASSEMBLY und DROP_ASSEMBLY ein. Analog dazu schließt das TRC_FULL_TEXT-Ereignis beliebige Ereignisse vom Typ FT_CRAWL_ABORTED, FT_CRAWL_STARTED und FT_CRAWL_STOPPED ein. ALL_EVENTS deckt alle DDL-Ereignisse, Ablaufverfolgungsereignisse, QUEUE_ACTIVATION und BROKER_QUEUE_DISABLED ab.  
  
 Um zu ermitteln, welche Eigenschaften aus einem Ereignis oder einer Ereignisgruppe abgefragt werden können, konsultieren Sie das Ereignisschema. Standardmäßig wird das Ereignisschema im folgenden Verzeichnis installiert: [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)] Tools\Binn\schemas\sqlserver\2006\11\events\events .xsd.  
  
 Alternativ dazu können Sie auch auf das Ereignis Schema verweisen, das unter veröffentlicht wurde [https://schemas.microsoft.com/sqlserver](https://go.microsoft.com/fwlink/?linkid=43100) .  
  
 Wenn Sie z. b. auf das ALTER_DATABASE-Ereignis verweisen **, werden Sie feststellen,** dass das übergeordnete Ereignis DDL_SERVER_LEVEL_EVENTS und seine Eigenschaften den Namen "" und " **DatabaseName**" aufweisen. Das Ereignis erbt auch die Eigenschaften **SQLInstance**, **PostTime**, **Computername**, **SPID**und **LoginName**. Das Ereignis verfügt über keinen untergeordneten Ereignisse.  
  
> [!NOTE]  
>  Gespeicherte Systemprozeduren, die DDL-ähnliche Vorgänge ausführen, können auch Ereignisbenachrichtigungen auslösen. Testen Sie die Ereignisbenachrichtigungen, um ihre Reaktion auf gespeicherte Systemprozeduren, die ausgeführt werden, zu bestimmen. Beispielsweise lösen die CREATE TYPE-Anweisung und die gespeicherte Prozedur **sp_addtype** eine Ereignis Benachrichtigung aus, die für ein CREATE_TYPE-Ereignis erstellt wird. Weitere Informationen finden Sie unter [DDL-Ereignisse](../../relational-databases/triggers/ddl-events.md).  
  
 **Ereignisse und Ereignisgruppen der Datendefinitionssprache (DDL)**  
  
 ![WMI-Anbieter für Serverereignisse-Ereignisstruktur](../../relational-databases/wmi-provider-server-events/media/sql-wmi-ddl-events-ktm.gif "WMI-Anbieter für Serverereignisse-Ereignisstruktur")  
  
 **Ablaufverfolgungsereignisse und Ereignisgruppen**  
  
 ![Ablauf Verfolgungs Ereignisse und Ereignis Gruppen](../../relational-databases/wmi-provider-server-events/media/sql-wmi-trc-all-events.gif "Ablaufverfolgungsereignisse und -Ereignisgruppen")  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konzepte des WMI-Anbieters für Server Ereignisse](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md)   
 [Verwenden von WQL mit dem WMI-Anbieter für Serverereignisse](../../relational-databases/wmi-provider-server-events/using-wql-with-the-wmi-provider-for-server-events.md)  
  
  
