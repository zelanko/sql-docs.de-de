---
title: Kontext Verbindung | Microsoft-Dokumentation
description: In Microsoft SQL Server können Sie mit der Kontext Verbindung Transact-SQL-Anweisungen in demselben Kontext ausführen, in dem der Code aufgerufen wurde.
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
ms.openlocfilehash: cd0b57e73757348959a0b8b5f144fbc5c4ef0f8c
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85892469"
---
# <a name="context-connection"></a>Kontextverbindung
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Der interne Datenzugriff ist ein verbreitetes Problem. Es tritt auf, wenn Sie auf denselben Server zugreifen möchten, auf dem auch die CLR-gespeicherte Prozedur (Common Language Runtime, CLR) oder -Funktion ausgeführt wird. Eine Möglichkeit besteht darin, mithilfe von **System. Data. SqlClient. SqlConnection**eine Verbindung herzustellen, eine Verbindungs Zeichenfolge anzugeben, die auf den lokalen Server zeigt, und die Verbindung zu öffnen. Dies erfordert die Angabe von Anmeldeinformationen für die Anmeldung. Die Verbindung befindet sich in einer anderen Daten banksitzung als die gespeicherte Prozedur oder Funktion, Sie kann über unterschiedliche **Set** -Optionen verfügen, Sie befindet sich in einer separaten Transaktion, ihre temporären Tabellen werden nicht angezeigt usw. Wenn der Code Ihrer verwalteten gespeicherten Prozedur oder Funktion im SQL Serverprozess ausgeführt wird, liegt das daran, dass jemand eine Verbindung mit diesem Server hergestellt und eine SQL-Anweisung ausgeführt hat, um den Code aufzurufen. Wahrscheinlich möchten Sie, dass die gespeicherte Prozedur oder Funktion im Kontext dieser Verbindung zusammen mit der zugehörigen Transaktion, den **Set** -Optionen usw. ausgeführt wird. Dies wird als Kontextverbindung bezeichnet.  
  
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
  
  
