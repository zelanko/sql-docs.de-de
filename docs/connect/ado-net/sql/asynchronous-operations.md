---
title: Asynchrone Vorgänge
description: Beschreibt das Ausführen asynchroner Datenbankoperationen mithilfe einer API, die auf der Grundlage des von .NET Framework verwendeten asynchronen Modells entwickelt wurde.
ms.date: 09/30/2019
ms.assetid: e7d32c3c-bf78-4bfc-a357-c9e82e4a4b3c
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 7a070d71b653b0afc9e94c898653432e7e388d07
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "75250932"
---
# <a name="asynchronous-operations"></a>Asynchrone Vorgänge

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Einige Datenbankvorgänge, z. B. Befehlsausführungen, können beträchtliche Zeit in Anspruch nehmen. In derartigen Fällen müssen Singlethread-Anwendungen andere Vorgänge blockieren und warten, bis der Befehl abgeschlossen ist, ehe ihre eigenen Vorgänge fortgesetzt werden können. Im Gegensatz dazu kann der Vordergrundthread während des gesamten Vorgangs aktiv bleiben, wenn der Vorgang mit langer Ausführungszeit einem Hintergrundthread zugewiesen werden kann. In einer Windows-Anwendung beispielsweise ermöglicht das Delegieren des Vorgangs mit langer Ausführungszeit an einen Hintergrundthread, dass der Benutzeroberflächenthread während der Ausführung des Vorgangs reaktionsfähig bleibt.  
  
.NET bietet mehrere asynchrone Standardentwurfsmuster, die Entwickler verwenden können, um die Vorteile von Hintergrundthreads zu nutzen und die Benutzeroberfläche oder Threads mit hoher Priorität freizugeben, um andere Vorgänge in seiner <xref:Microsoft.Data.SqlClient.SqlCommand>-Klasse abzuschließen. Insbesondere die Methoden <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>, <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteReader%2A> und <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A> gepaart mit den Methoden <xref:Microsoft.Data.SqlClient.SqlCommand.EndExecuteNonQuery%2A>, <xref:Microsoft.Data.SqlClient.SqlCommand.EndExecuteReader%2A> und <xref:Microsoft.Data.SqlClient.SqlCommand.EndExecuteXmlReader%2A> bieten die asynchrone Unterstützung.  
  
> [!NOTE]
>  Die asynchrone Programmierung ist ein Kernmerkmal von .NET. Weitere Informationen zu den verschiedenen asynchronen Techniken, die Entwicklern zur Verfügung stehen, finden Sie unter [Asynchrones Aufrufen von synchronen Methoden](https://docs.microsoft.com/dotnet/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously).  
  
Obwohl die Verwendung asynchroner Techniken mit ADO.NET-Features keine besonderen Überlegungen erfordert, ist es wichtig, sich der Vorteile und Tücken der Erstellung von Anwendungen mit mehreren Threads bewusst zu sein. Die folgenden Beispiele in diesem Abschnitt weisen auf mehrere wichtige Punkte hin, die Entwickler bei der Erstellung von Anwendungen mit Multithread-Funktionalität berücksichtigen müssen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
[Verwenden von Rückrufen in Windows-Anwendungen](windows-applications-callbacks.md)  
Bietet ein Beispiel, das zeigt, wie ein asynchroner Befehl sicher ausgeführt werden kann, wobei die Interaktion mit einem Formular und dessen Inhalt in einem separaten Thread ordnungsgemäß gehandhabt wird.  
  
[Verwenden von Wait-Handles in ASP.NET-Anwendungen](aspnet-apps-use-wait-handles.md)  
Enthält ein Beispiel, das veranschaulicht, wie mehrere gleichzeitige Befehle auf einer ASP.NET-Seite ausgeführt werden können, wobei Wait-Handles verwendet werden, um den Vorgang nach Ausführung aller Befehle zu verwalten.  
  
[Abrufen in Konsolenanwendungen](poll-console-applications.md)  
Enthält ein Beispiel, das die Verwendung von Abrufen demonstriert, um in einer Konsolenanwendung auf den Abschluss der Ausführung eines asynchronen Befehls zu warten. Diese Technik eignet sich auch in einer Klassenbibliothek oder einer anderen Anwendung ohne Benutzerschnittstelle.  
  
## <a name="next-steps"></a>Nächste Schritte
- [SQL Server und ADO.NET](index.md)
- [Asynchrones Aufrufen von synchronen Methoden](https://docs.microsoft.com/dotnet/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously)
