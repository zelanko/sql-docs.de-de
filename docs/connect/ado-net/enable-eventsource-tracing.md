---
title: Aktivieren der Ereignisablaufverfolgung in SqlClient
description: In diesem Artikel wird erläutert, wie Sie die Ereignisablaufverfolgung in SqlClient aktivieren, indem Sie einen Ereignislistener implementieren. Außerdem erfahren Sie, wie Sie auf Ereignisdaten zugreifen.
ms.date: 06/15/2020
dev_langs:
- csharp
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: johnnypham
ms.author: v-jopha
ms.reviewer: ''
ms.openlocfilehash: 17e947c108d14accb880dbd6673231e82b0b133c
ms.sourcegitcommit: 6b3569977b034554883a94d73d1c4df6e2f74fe2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2020
ms.locfileid: "85110130"
---
# <a name="enabling-event-tracing-in-sqlclient"></a>Aktivieren der Ereignisablaufverfolgung in SqlClient

[!INCLUDE [appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE [Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

[Ereignisablaufverfolgung für Windows-Ereignisse (ETW)](https://docs.microsoft.com/windows/win32/etw/event-tracing-portal) ist eine effiziente Funktion für Ablaufverfolgung auf Kernelebene, mit der Sie vom Treiber definierte Ereignisse zu Debug- und Testzwecken protokollieren können. SqlClient unterstützt das Erfassen von ETW-Ereignissen auf verschiedenen Informationsebenen. Clientanwendungen sollten auf Ereignisse aus der EventSource-Implementierung von SqlClient lauschen, um die Erfassung von Ereignisablaufverfolgungen zu starten.

```
Microsoft.Data.SqlClient.EventSource
```

Die aktuelle Implementierung unterstützt die folgenden Schlüsselwörter für Ereignisse:

| Name des Schlüsselworts | Wert | BESCHREIBUNG |
| ------------ | ----- | ----------- |
| ExecutionTrace | 1 | Dieses Schlüsselwort aktiviert die Erfassung von Start/Stop-Ereignissen vor und nach der Befehlsausführung. |
| Trace | 2 | Dieses Schlüsselwort aktiviert die Erfassung einfacher Ereignisse der Anwendungsflowablaufverfolgung. |
| `Scope` | 4 | Dieses Schlüsselwort aktiviert die Erfassung von Enter- und Exit-Ereignissen. |
| NotificationTrace | 8 | Dieses Schlüsselwort aktiviert die Erfassung von `SqlNotification`-Ablaufverfolgungsereignissen. |
| NotificationScope | 16 | Dieses Schlüsselwort aktiviert Enter- und Exit-Ereignisse im `SqlNotification`-Bereich. |
| PoolerTrace | 32 | Dieses Schlüsselwort aktiviert Ablaufverfolgungsereignisse des Verbindungspoolingflows. |
| PoolerScope | 64 | Dieses Schlüsselwort aktiviert Ablaufverfolgungsereignisse des Verbindungspoolingbereichs. |
| AdvancedTrace | 128 | Dieses Schlüsselwort aktiviert die Erfassung erweiterter Flowablaufverfolgungsereignisse. |
| AdvancedTraceBin  | 256 | Dieses Schlüsselwort aktiviert die Erfassung erweiterter Flowablaufverfolgungsereignisse mit zusätzlichen Informationen. |
| CorrelationTrace | 512 | Dieses Schlüsselwort aktiviert die Erfassung von Ablaufverfolgungsereignissen für Korrelationsflows. |
| StateDump | 1024 | Dieses Schlüsselwort aktiviert die Erfassung einer vollständigen Statussicherung von `SqlConnection`. |
| SNITrace | 2048 | Dieses Schlüsselwort aktiviert die Erfassung von Flowablaufverfolgungsereignissen in der Implementierung von verwalteten Netzwerken (gilt nur für .NET Core). |
| SNIScope | 4096 | Dieses Schlüsselwort aktiviert die Erfassung von Bereichsablaufverfolgungsereignissen in der Implementierung von verwalteten Netzwerken (gilt nur für .NET Core). |
|||

## <a name="example"></a>Beispiel
Im folgenden Beispiel wird die Ereignisablaufverfolgung für einen Datenvorgang für die **AdventureWorks**-Beispieldatenbank aktiviert, und die Ereignisse werden im Konsolenfenster angezeigt.

[!code-csharp [SqlClientEventSource#1](~/../sqlclient/doc/samples/SqlClientEventSource.cs#1)]

## <a name="external-resources"></a>Externe Ressourcen  
Weitere Informationen finden Sie in den folgenden Ressourcen.  
  
|Resource|BESCHREIBUNG|  
|--------------|-----------------|  
|[EventSource-Klasse](https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing.eventsource)|Diese Klasse ermöglicht das Erstellen von ETW-Ereignissen.| 
|[EventListener-Klasse](https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing.eventlistener)|Diese Klasse stellt Methoden zum Aktivieren und Deaktivieren von Ereignissen aus Ereignisquellen bereit.| 
