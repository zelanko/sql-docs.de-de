---
title: Debuggen von Datenbankobjekten der Common Language Runtime (CLR)
description: SQL Server bietet Unterstützung für das Debuggen von Transact-SQL-und CLR-Objekten in der Datenbank, die SQL Server Debugger mit Microsoft Visual Studio Debugger integriert.
ms.date: 10/06/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: how-to
helpviewer_keywords:
- database objects [CLR integration], debugging
- permissions [CLR integration]
- debugging [CLR integration]
- building database objects [CLR integration], debugging
- common language runtime [SQL Server], debugging
ms.assetid: 1332035c-d6ed-424d-8234-46ad21168319
author: rothja
ms.author: jroth
ms.openlocfilehash: 2a6e723c8ad5ff8c97a3b57edb554092211da4d7
ms.sourcegitcommit: 610e3ebe21ac6575850a29641a32f275e71557e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2020
ms.locfileid: "91785163"
---
# <a name="how-to-debug-clr-database-objects"></a>Debuggen von CLR-Datenbankobjekten

[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
 
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt das Debuggen von [!INCLUDE[tsql](../../includes/tsql-md.md)] und CLR (Common Language Runtime)-Objekten in der Datenbank. Die Hauptaspekte des Debuggens in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sind die leichte Einrichtung und Handhabung und die Integration des SQL Server-Debuggers in den Microsoft Visual Studio-Debugger. Darüber hinaus ist das Debuggen sprachübergreifend. Benutzer können Einzelschritte in CLR-Objekte aus [!INCLUDE[tsql](../../includes/tsql-md.md)] und umgekehrt ausführen. Der Transact-SQL-Debugger in SQL Server Management Studio kann nicht verwendet werden, um Datenbankobjekte zu debuggen, aber Sie können die Objekte debuggen, indem Sie die Debugger in Visual Studio verwenden. Das Debuggen verwalteter Datenbankobjekte in Visual Studio unterstützt alle gängigen Debugfunktionen, wie z. B. „Einzelschritt“- und „Prozedurschritt“-Anweisungen innerhalb von Routinen, die auf dem Server ausgeführt werden. Debugger können während des Debuggens Breakpoints festlegen, Aufruflisten prüfen, Variablen prüfen und Variablenwerte ändern. 

> [!NOTE]
> Visual Studio .NET 2003 kann nicht für die CLR-Integrations Programmierung oder das Debuggen verwendet werden. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] beinhaltet ein vorinstalliertes .NET Framework, und Visual Studio .NET 2003 kann nicht die .NET Framework 2.0-Assemblys verwenden.  
  
## <a name="debugging-permissions-and-restrictions"></a>Debugberechtigungen und-Einschränkungen

Das Debuggen ist ein stark privilegierter Vorgang, daher dürfen nur Mitglieder der festen Server Rolle **sysadmin** dies in tun [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
Während des Debuggens gelten die folgenden Einschränkungen:  
  
- Das Debuggen von CLR-Routinen kann nur von einer Debugger-Instanz gleichzeitig vorgenommen werden. Diese Einschränkung ist vorhanden, da jegliche CLR-Codeausführung eingefroren wird, wenn der Breakpoint erreicht wird, und die Ausführung wird erst fortgesetzt, wenn sich der Debugger vom Breakpoint fortbewegt. Allerdings können Sie das Debuggen von [!INCLUDE[tsql](../../includes/tsql-md.md)] auf anderen Verbindungen fortführen. Obwohl das [!INCLUDE[tsql](../../includes/tsql-md.md)]-Debuggen keine anderen Ausführungen auf dem Server einfriert, könnte es dazu führen, dass durch Aufrechterhaltung einer Sperre andere Verbindungen warten.  
  
- Für vorhandene Verbindungen kann kein Debuggen vorgenommen werden. Nur neue Verbindungen, wie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], erfordern Informationen über die Client- und Debugger-Umgebung, bevor die Verbindung hergestellt werden kann.  
  
Aufgrund der oben genannten Einschränkungen empfehlen wir, dass [!INCLUDE[tsql](../../includes/tsql-md.md)]- und CLR-Code auf einem Testserver und nicht auf einem Produktionsserver gedebuggt werden.  
  
## <a name="overview"></a>Übersicht

Das Debuggen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erfolgt nach einem Pro-Verbindungsmodell. Ein Debugger kann nur Aktivitäten zu einer Clientverbindung erkennen und debuggen, mit der er verknüpft ist. Da die Funktionalität eines Debuggers nicht durch den Verbindungstyp eingeschränkt wird, können sowohl TDS- (Tabular Data Stream) als auch HTTP-Verbindungen gedebuggt werden. Allerdings ermöglicht [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht das Debuggen vorhandener Verbindungen. Das Debuggen unterstützt alle üblichen Debugfunktionen innerhalb von Routinen, die auf dem Server ausgeführt werden. Die Interaktion zwischen einem Debugger und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] geschieht durch DCOM (Distributed Component Object Model).  
  
Weitere Informationen und Szenarien zum Debuggen von verwalteten gespeicherten Prozeduren, Funktionen, Triggern, benutzerdefinierten Typen und Aggregaten finden Sie unter [SQL Server CLR-Integration Datenbank-Debuggen](https://go.microsoft.com/fwlink/?LinkId=120378) in der Visual Studio-Dokumentation.  
  
Das TCP/IP-Netzwerkprotokoll muss in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz aktiviert werden, damit Visual Studio von einem Remotecomputer aus zum Entwickeln, Debuggen und Bereitstellen verwendet werden kann. Weitere Informationen zum Aktivieren des TCP/IP-Protokolls auf dem Server finden Sie unter [Konfigurieren von Client Protokollen](../../database-engine/configure-windows/configure-client-protocols.md).  
  
## <a name="debugging-steps"></a>Debugschritte

Verwenden Sie die folgenden Schritte zum Debuggen eines CLR-Datenbankobjekts in Microsoft Visual Studio:

1. Öffnen Sie Microsoft Visual Studio, und erstellen Sie ein neues SQL Server Projekt. Sie können die SQL localdb-Instanz verwenden, die in Visual Studio verfügbar ist.

2. Erstellen Sie einen neuen SQL CLR-Typ (c#):

   1. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, und wählen Sie **Hinzufügen**, **Neues Element...** aus. 
   1. Wählen Sie im Fenster **Neues Element hinzufügen** die Option **gespeicherte SQL CLR c#-Prozedur**, **benutzerdefinierte SQL CLR c#-Funktion**, benutzerdefinierter SQL CLR **c#-Typ**, **SQL CLR c#-Triggertyp**, **SQL CLR c#-Aggregat**oder **Klasse**aus.
   1. Geben Sie einen Namen für die Quelldatei des neuen Typs an, und klicken Sie dann auf **Hinzufügen**.

3. Fügen Sie Code für den neuen Typ zum Texteditor hinzu. Beispielcode für eine gespeicherte Beispiel Prozedur finden Sie im folgenden Beispiel Abschnitt in diesem Artikel.

4. Fügen Sie ein Skript hinzu, das den Typ testet: 

   1. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie **Hinzufügen**, **Skript...** aus. 
   1. Wählen Sie im Fenster **Neues Element hinzufügen** die Option **Skript (nicht im Build)** aus, und geben Sie einen Namen an, z `Test.sql` . b.. Wählen Sie die Schaltfläche **Hinzufügen** aus.
   1. Doppelklicken Sie in **Projektmappen-Explorer**auf den `Test.sql` Knoten, um die standardmäßige Testskript-Quelldatei zu öffnen.
   1. Fügen Sie das Testskript (eines, das den zu debuggenden Code aufruft) dem Text-Editor hinzu. Ein Beispielskript finden Sie im Beispiel im nächsten Abschnitt.

5. Platzieren Sie einen oder mehrere Breakpoints im Quellcode. Klicken Sie mit der rechten Maustaste auf eine Codezeile im Text-Editor für die Funktion oder Routine, die Sie debuggen möchten. Wählen Sie halte **Punkt**und halte **Punkt einfügen**aus. Der Breakpoint wird hinzugefügt und hebt die Codezeile in Rot hervor.

6. Wählen Sie im Menü **Debuggen** die Option **Debugging starten** aus, um das Projekt zu kompilieren, bereitzustellen und zu testen. Das Testskript in `Test.sql` wird ausgeführt, und das verwaltete Datenbankobjekt wird aufgerufen.

7. Wenn der gelbe Pfeil (durch Festlegen des Anweisungs Zeigers) am Breakpoint angezeigt wird, wird die Codeausführung angehalten. Sie können dann das verwaltete Datenbankobjekt Debuggen:

   1. Verwenden Sie "Prozedur **Schritt** " im Menü " **Debuggen** ", um den Anweisungs Zeiger auf die nächste Codezeile zu verschieben.
   1. Verwenden Sie **das Fenster Lokal, um den Zustand** der Objekte zu überwachen, die aktuell vom Anweisungs Zeiger hervorgehoben werden.
   1. Fügen Sie dem Fenster über **Wachen** Variablen hinzu. Sie können den Status der überwachten Variablen während der Debugsitzung beobachten, auch wenn sich die Variable nicht in der Codezeile befindet, die aktuell vom Anweisungs Zeiger hervorgehoben ist. 
   1. Wählen Sie im Menü **Debuggen** die Option **weiter** aus, um den Anweisungs Zeiger auf den nächsten Breakpoint zu verschieben oder die Ausführung der Routine abzuschließen, wenn keine Haltepunkte mehr vorhanden sind.
  
## <a name="example-code"></a>Beispielcode

Das folgende Beispiel gibt die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Version an den Aufrufer zurück.  
  
```csharp
using System.Data.SqlClient;
using Microsoft.SqlServer.Server;

public class StoredProcedures
{
    [Microsoft.SqlServer.Server.SqlProcedure]
    public static void GetVersion()
    {
        using (var connection = new SqlConnection("context connection=true"))
        {
            connection.Open();
            var command = new SqlCommand("select @@version", connection);
            SqlContext.Pipe.ExecuteAndSend(command);
        }
    }
}
```

## <a name="example-test-script"></a>Beispiel für ein Testskript

Das folgende Testskript zeigt, wie Sie die `GetVersion` gespeicherte Prozedur aufrufen, die im vorherigen Beispiel definiert wurde.  
  
```sql
EXEC GetVersion  
```  

## <a name="next-steps"></a>Nächste Schritte
  
Weitere Informationen zum Debuggen von verwaltetem Code mithilfe von Visual Studio finden Sie unter [Debugging von verwaltetem Code](https://go.microsoft.com/fwlink/?LinkId=120377) in der Visual Studio-Dokumentation.  

Weitere Informationen finden Sie unter [Programmier Konzepte für die Common Language Runtime-Integration](../../relational-databases/clr-integration/common-language-runtime-clr-integration-programming-concepts.md) .  
