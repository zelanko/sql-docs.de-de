---
title: Debuggen von CLR-Datenbankobjekten | Microsoft Docs
description: SQL Server bietet Unterstützung für das Debuggen von Transact-SQL- und CLR-Objekten in der Datenbank, die SQL Server-Debugger in Den Microsoft Visual Studio-Debugger integrieren.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- database objects [CLR integration], debugging
- permissions [CLR integration]
- debugging [CLR integration]
- building database objects [CLR integration], debugging
- common language runtime [SQL Server], debugging
ms.assetid: 1332035c-d6ed-424d-8234-46ad21168319
author: rothja
ms.author: jroth
ms.openlocfilehash: 71a766dc473c1bef47a8104ae76c0e70bd8b31b8
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488395"
---
# <a name="debugging-clr-database-objects"></a>Debuggen von CLR-Datenbankobjekten
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt das Debuggen von [!INCLUDE[tsql](../../includes/tsql-md.md)] und CLR (Common Language Runtime)-Objekten in der Datenbank. Die Hauptaspekte des Debuggens in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sind die leichte Einrichtung und Handhabung und die Integration des SQL Server-Debuggers in den Microsoft Visual Studio-Debugger. Darüber hinaus ist das Debuggen sprachübergreifend. Benutzer können Einzelschritte in CLR-Objekte aus [!INCLUDE[tsql](../../includes/tsql-md.md)] und umgekehrt ausführen. Der Transact-SQL-Debugger in SQL Server Management Studio kann nicht verwendet werden, um Datenbankobjekte zu debuggen, aber Sie können die Objekte debuggen, indem Sie die Debugger in Visual Studio verwenden. Das Debuggen verwalteter Datenbankobjekte in Visual Studio unterstützt alle gängigen Debugfunktionen, wie z. B. „Einzelschritt“- und „Prozedurschritt“-Anweisungen innerhalb von Routinen, die auf dem Server ausgeführt werden. Debugger können während des Debuggens Breakpoints festlegen, Aufruflisten prüfen, Variablen prüfen und Variablenwerte ändern. Beachten Sie, dass Visual Studio .NET 2003 nicht für CLR-Integrationsprogrammierung oder das Debuggen verwendet werden kann. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] beinhaltet ein vorinstalliertes .NET Framework, und Visual Studio .NET 2003 kann nicht die .NET Framework 2.0-Assemblys verwenden.  
  
 Weitere Informationen zum Debuggen von verwaltetem Code mithilfe von Visual Studio finden Sie im Thema "[Debuggen von verwaltetem Code](https://go.microsoft.com/fwlink/?LinkId=120377)" in der Visual Studio-Dokumentation.  
  
## <a name="debugging-permissions-and-restrictions"></a>Debuggen von Berechtigungen und Einschränkungen  
 Das Debuggen ist ein Vorgang mit hohen Berechtigungen, und daher dürfen nur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Mitglieder der **sysadmin** Fixed Server-Rolle in die s.  
  
 Während des Debuggens gelten die folgenden Einschränkungen:  
  
-   Das Debuggen von CLR-Routinen kann nur von einer Debugger-Instanz gleichzeitig vorgenommen werden. Diese Einschränkung ist vorhanden, da jegliche CLR-Codeausführung eingefroren wird, wenn der Breakpoint erreicht wird, und die Ausführung wird erst fortgesetzt, wenn sich der Debugger vom Breakpoint fortbewegt. Allerdings können Sie das Debuggen von [!INCLUDE[tsql](../../includes/tsql-md.md)] auf anderen Verbindungen fortführen. Obwohl das [!INCLUDE[tsql](../../includes/tsql-md.md)]-Debuggen keine anderen Ausführungen auf dem Server einfriert, könnte es dazu führen, dass durch Aufrechterhaltung einer Sperre andere Verbindungen warten.  
  
-   Für vorhandene Verbindungen kann kein Debuggen vorgenommen werden. Nur neue Verbindungen, wie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], erfordern Informationen über die Client- und Debugger-Umgebung, bevor die Verbindung hergestellt werden kann.  
  
 Aufgrund der oben genannten Einschränkungen empfehlen wir, dass [!INCLUDE[tsql](../../includes/tsql-md.md)]- und CLR-Code auf einem Testserver und nicht auf einem Produktionsserver gedebuggt werden.  
  
## <a name="overview-of-debugging-managed-database-objects"></a>Übersicht über das Debuggen von verwalteten Datenbankobjekten  
 Das Debuggen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erfolgt nach einem Pro-Verbindungsmodell. Ein Debugger kann nur Aktivitäten zu einer Clientverbindung erkennen und debuggen, mit der er verknüpft ist. Da die Funktionalität eines Debuggers nicht durch den Verbindungstyp eingeschränkt wird, können sowohl TDS- (Tabular Data Stream) als auch HTTP-Verbindungen gedebuggt werden. Allerdings ermöglicht [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht das Debuggen vorhandener Verbindungen. Das Debuggen unterstützt alle üblichen Debugfunktionen innerhalb von Routinen, die auf dem Server ausgeführt werden. Die Interaktion zwischen einem Debugger und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] geschieht durch DCOM (Distributed Component Object Model).  
  
 Weitere Informationen und Szenarien zum Debuggen verwalteter gespeicherter Prozeduren, Funktionen, Trigger, benutzerdefinierter Typen und Aggregate finden Sie im Thema "[SQL Server CLR Integration Database Debugging](https://go.microsoft.com/fwlink/?LinkId=120378)" in der Visual Studio-Dokumentation.  
  
 Das TCP/IP-Netzwerkprotokoll muss in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz aktiviert werden, damit Visual Studio von einem Remotecomputer aus zum Entwickeln, Debuggen und Bereitstellen verwendet werden kann. Weitere Informationen zum Aktivieren des TCP/IP-Protokolls auf dem Server finden Sie unter Konfigurieren von [Clientprotokollen](../../database-engine/configure-windows/configure-client-protocols.md).  
  
#### <a name="to-debug-a-managed-database-object"></a>So debuggen Sie ein verwaltetes Datenbankobjekt  
  
1.  Öffnen Sie Microsoft Visual Studio, und erstellen Sie ein neues [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Projekt. Stellen Sie eine Verbindung zu einer Datenbank auf einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] her.  
  
2.  Erstellen Sie einen neuen Typ. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, und wählen Sie **Hinzufügen** und **Neues Element aus...** Wählen Sie im Fenster **Neues Element hinzufügen** die Option **Gespeicherte Prozedur**, **Benutzerdefinierte Funktion**, **Benutzerdefinierter Typ**, **Trigger**, **Aggregat**oder **Klasse**" aus. Geben Sie einen Namen für die Quelldatei des neuen Typs an, und klicken Sie auf **Hinzufügen**.  
  
3.  Fügen Sie Code für den neuen Typ zum Texteditor hinzu. Beispielcode für eine gespeicherte Prozedur finden Sie in einem späteren Abschnitt in diesem Thema.  
  
4.  Fügen Sie ein Skript hinzu, das den Typ testet. Erweitern Sie im **Projektmappen-Explorer**das **Verzeichnis TestScripts,** **um** die Standardquelldatei für Testskripte zu öffnen. Fügen Sie das Testskript, das den Code dazu aufruft, zu debuggen, zum Texteditor hinzu. Ein Beispielskript sehen Sie unten.  
  
5.  Platzieren Sie einen oder mehrere Breakpoints im Quellcode. Klicken Sie mit der rechten Maustaste auf eine Codezeile im Texteditor innerhalb der Funktion oder Routine, die Sie debuggen möchten, und wählen Sie **Breakpoint** und **Insert Breakpoint**aus. Der Breakpoint wird hinzugefügt und hebt die Codezeile in Rot hervor.  
  
6.  Wählen Sie im **Menü Debuggen** die Option **Debuggen starten** aus, um das Projekt zu kompilieren, bereitzustellen und zu testen. Das Testskript in Test.sql wird ausgeführt, und das verwaltete Datenbankobjekt wird aufgerufen.  
  
7.  Wenn der gelbe Pfeil, der den Anweisungszeiger kennzeichnet, am Breakpoint angezeigt wird, pausiert die Codeausführung, und Sie können mit dem Debuggen Ihres verwalteten Datenbankobjekts beginnen. Sie können über das **Debugmenü** **springen,** um den Anweisungszeiger zur nächsten Codezeile zu bringen. Das Fenster **Locals** wird verwendet, um den Status der Objekte zu beobachten, die derzeit durch den Anweisungszeiger hervorgehoben werden. Variablen können dem **Überwachungsfenster** hinzugefügt werden. Der Zustand der überwachten Variablen kann während der gesamten Debuggingsitzung beobachtet werden und nicht nur, wenn die Variable sich in der Codezeile befindet, die aktuell vom Anweisungszeiger hervorgehoben wird. Wählen Sie im Menü Debuggen Weiter aus, um mit dem Anweisungszeiger zum nächsten Breakpoint zu springen oder um die Ausführung der Routine abzuschließen, wenn keine weiteren Breakpoints vorhanden sein sollten.  
  
### <a name="example"></a>Beispiel  
 Das folgende Beispiel gibt die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Version an den Aufrufer zurück.  
  
 C#  
  
```  
using System;  
using System.Data;  
using System.Data.SqlTypes;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
  
public class StoredProcedures   
{  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void GetVersion()  
   {  
   using(SqlConnection connection = new SqlConnection("context connection=true"))   
   {  
      connection.Open();  
      SqlCommand command = new SqlCommand("select @@version",  
                                           connection);  
      SqlContext.Pipe.ExecuteAndSend(command);  
      }  
   }  
}  
```  
  
 Visual Basic  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
Partial Public Class StoredProcedures   
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub GetVersion()  
        Using connection As New SqlConnection("context connection=true")  
            connection.Open()  
            Dim command As New SqlCommand("SELECT @@VERSION", connection)  
            SqlContext.Pipe.ExecuteAndSend(command)  
        End Using  
    End Sub  
End Class  
```  
  
 Im Folgenden handelt es sich um ein Testskript, das die oben definierte gespeicherte Prozedur GetVersion aufruft.  
  
```  
EXEC GetVersion  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Programmierkonzepte für die Integration der Common Language Runtime &#40;CLR&#41;](../../relational-databases/clr-integration/common-language-runtime-clr-integration-programming-concepts.md)  
  
  
