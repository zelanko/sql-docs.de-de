---
title: Kontextverbindung | Microsoft Docs
description: In Microsoft SQL Server können Sie mit der Kontextverbindung Transact-SQL-Anweisungen in demselben Kontext ausführen, in dem der Code aufgerufen wurde.
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
ms.openlocfilehash: 3f29914557e3a1c1e7a929bec22a2b55d0db2a50
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81485509"
---
# <a name="context-connection"></a>Kontextverbindung
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Der interne Datenzugriff ist ein verbreitetes Problem. Es tritt auf, wenn Sie auf denselben Server zugreifen möchten, auf dem auch die CLR-gespeicherte Prozedur (Common Language Runtime, CLR) oder -Funktion ausgeführt wird. Eine Möglichkeit besteht darin, eine Verbindung mit **System.Data.SqlClient.SqlConnection**zu erstellen, eine Verbindungszeichenfolge anzugeben, die auf den lokalen Server verweist, und die Verbindung zu öffnen. Dies erfordert die Angabe von Anmeldeinformationen für die Anmeldung. Die Verbindung befindet sich in einer anderen Datenbanksitzung als die gespeicherte Prozedur oder Funktion, sie kann unterschiedliche **SET-Optionen** haben, sie befindet sich in einer separaten Transaktion, sie sieht Ihre temporären Tabellen nicht an usw. Wenn der Code Ihrer verwalteten gespeicherten Prozedur oder Funktion im SQL Serverprozess ausgeführt wird, liegt das daran, dass jemand eine Verbindung mit diesem Server hergestellt und eine SQL-Anweisung ausgeführt hat, um den Code aufzurufen. Sie möchten wahrscheinlich, dass die gespeicherte Prozedur oder Funktion im Kontext dieser Verbindung zusammen mit ihrer Transaktion, **SET-Optionen** usw. ausgeführt wird. Dies wird als Kontextverbindung bezeichnet.  
  
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
  
  
