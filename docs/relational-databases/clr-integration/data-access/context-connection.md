---
title: Kontextverbindung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- context connections [CLR integration]
- database objects [CLR integration], connections
- connections [CLR integration]
- context [CLR integration]
ms.assetid: 67dd1925-d672-4986-a85f-bce4fe832ef7
author: rothja
ms.author: jroth
ms.openlocfilehash: 3b091f515af926fb17cea424b4f8875baf0fa83a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68068421"
---
# <a name="context-connection"></a>Kontextverbindung
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Der interne Datenzugriff ist ein verbreitetes Problem. Es tritt auf, wenn Sie auf denselben Server zugreifen möchten, auf dem auch die CLR-gespeicherte Prozedur (Common Language Runtime, CLR) oder -Funktion ausgeführt wird. Eine Möglichkeit besteht darin, erstellen Sie eine Verbindung mit **System.Data.SqlClient.SqlConnection**, geben Sie eine Verbindungszeichenfolge, die auf dem lokalen Server verweist, und öffnen Sie die Verbindung. Dies erfordert die Angabe von Anmeldeinformationen für die Anmeldung. Die Verbindung befindet sich in einer anderen datenbanksitzung als die gespeicherte Prozedur oder Funktion, die möglicherweise andere **festgelegt** Optionen, die es in einer separaten Transaktion ist, nicht in die temporären Tabellen und so weiter. Wenn der Code Ihrer verwalteten gespeicherten Prozedur oder Funktion im SQL Serverprozess ausgeführt wird, liegt das daran, dass jemand eine Verbindung mit diesem Server hergestellt und eine SQL-Anweisung ausgeführt hat, um den Code aufzurufen. Empfiehlt sich die gespeicherte Prozedur oder Funktion, die im Rahmen dieser Verbindung sowie entsprechende Transaktion ausgeführt **festgelegt** Optionen und So weiter. Dies wird als Kontextverbindung bezeichnet.  
  
 Die Kontextverbindung ermöglicht, Transact-SQL-Anweisungen im selben Kontext auszuführen wie den Code, der anfänglich aufgerufen wurde. Um die Kontextverbindung herzustellen, müssen Sie "context connection", das Schlüsselwort für die Verbindungszeichenfolge der Kontextverbindung, verwenden, wie im nachstehenden Beispiel gezeigt:  
  
 [C#]  
  
```  
using(SqlConnection connection = new SqlConnection("context connection=true"))   
{  
    connection.Open();  
    // Use the connection  
}  
```  
  
 [Visual Basic]  
  
```  
Using connection as new SqlConnection("context connection=true")  
    connection.Open()  
    ' Use the connection  
End Using  
  
```  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Reguläre vs. Kontextverbindungen](../../../relational-databases/clr-integration/data-access/context-connections-vs-regular-connections.md)  
 Beschreibt die Unterschiede zwischen regulären Verbindungen und Kontextverbindungen.  
  
 [Einschränkungen hinsichtlich regulärer Verbindungen und Kontextverbindungen](../../../relational-databases/clr-integration/data-access/context-connections-and-regular-connections-restrictions.md)  
 Beschreibt die Einschränkungen hinsichtlich regulärer Verbindungen und Kontextverbindungen.  
  
  
