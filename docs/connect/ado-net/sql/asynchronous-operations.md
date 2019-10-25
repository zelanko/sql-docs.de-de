---
title: Asynchrone Vorgänge
description: Beschreibt das Ausführen asynchroner Datenbankoperationen mithilfe einer API, die auf der Grundlage des von .NET Framework verwendeten asynchronen Modells entwickelt wurde.
ms.date: 09/30/2019
ms.assetid: e7d32c3c-bf78-4bfc-a357-c9e82e4a4b3c
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 79cde936328476408fabb3df7a6bff8d983ace1c
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452323"
---
# <a name="asynchronous-operations"></a>Asynchrone Vorgänge

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Einige Daten Bank Vorgänge, z. b. Befehls Ausführungen, können eine beträchtliche Zeit in Anspruch nehmen. In diesem Fall müssen Single Thread-Anwendungen andere Vorgänge blockieren und warten, bis der Befehl abgeschlossen ist, bevor Sie Ihre eigenen Vorgänge fortsetzen können. Im Gegensatz dazu kann der Vordergrundthread während des gesamten Vorgangs aktiv bleiben, wenn der Vorgang mit langer Ausführungszeit einem Hintergrundthread zugewiesen werden kann. In einer Windows-Anwendung kann der Benutzeroberflächen Thread z. b. während der Ausführung des Vorgangs reaktionsfähig bleiben, wenn der Vorgang mit langer Laufzeit an einen Hintergrund Thread delegiert wird.  
  
.Net bietet mehrere standardmäßige asynchrone Entwurfsmuster, die Entwickler verwenden können, um Hintergrundthreads zu nutzen und die Benutzeroberfläche oder Threads mit hoher Priorität zum Ausführen anderer Vorgänge in der <xref:Microsoft.Data.SqlClient.SqlCommand>-Klasse freizugeben. Insbesondere die Methoden <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>, <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteReader%2A> und <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A>, die mit den Methoden <xref:Microsoft.Data.SqlClient.SqlCommand.EndExecuteNonQuery%2A>, <xref:Microsoft.Data.SqlClient.SqlCommand.EndExecuteReader%2A> und <xref:Microsoft.Data.SqlClient.SqlCommand.EndExecuteXmlReader%2A> gekoppelt sind, stellen die asynchrone Unterstützung bereit.  
  
> [!NOTE]
>  Die asynchrone Programmierung ist ein Kern Feature von .net. Weitere Informationen zu den verschiedenen asynchronen Techniken, die Entwicklern zur Verfügung stehen, finden Sie unter [Asynchrones Aufrufen synchroner Methoden](https://docs.microsoft.com/dotnet/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously).  
  
Obwohl die Verwendung von asynchronen Techniken mit ADO.NET-Features keine besonderen Überlegungen bietet, ist es wichtig, dass Sie die Vorteile und Fehler beim Erstellen von Multithreadanwendungen kennen. In den Beispielen in diesem Abschnitt werden einige wichtige Probleme erläutert, die Entwickler beim Erstellen von Anwendungen berücksichtigen müssen, die Multithreadfunktionen integrieren.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
[Verwenden von Rückrufen in Windows-Anwendungen](windows-applications-callbacks.md)  
Bietet ein Beispiel, das zeigt, wie ein asynchroner Befehl sicher ausgeführt werden kann, wobei die Interaktion mit einem Formular und dessen Inhalt von einem separaten Thread ordnungsgemäß verarbeitet wird.  
  
[Verwenden von Wait-Handles in ASP.NET-Anwendungen](aspnet-apps-use-wait-handles.md)  
Enthält ein Beispiel, das veranschaulicht, wie mehrere gleichzeitige Befehle von einer ASP.NET-Seite aus ausgeführt werden können. dabei wird mithilfe von Wait-Handles der Vorgang bei Abschluss aller Befehle verwaltet.  
  
[Abrufen in Konsolenanwendungen](poll-console-applications.md)  
Enthält ein Beispiel für die Verwendung von Abruf, um auf den Abschluss einer asynchronen Befehlsausführung aus einer Konsolenanwendung zu warten. Diese Technik ist auch in einer Klassenbibliothek oder einer anderen Anwendung ohne Benutzeroberfläche gültig.  
  
## <a name="next-steps"></a>Nächste Schritte
- [SQL Server und ADO.NET](index.md)
- [Asynchrones Aufrufen von synchronen Methoden](https://docs.microsoft.com/dotnet/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously)
