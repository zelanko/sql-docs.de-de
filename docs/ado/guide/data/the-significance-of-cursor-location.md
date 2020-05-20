---
title: Die Bedeutung der Cursor Position | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- server-side cursors [ADO]
- cursors [ADO], client-side
- client-side cursors [ADO]
- cursors [ADO], server-side
ms.assetid: 70ef5b1c-0459-41a1-b796-031f61a29a8a
author: rothja
ms.author: jroth
ms.openlocfilehash: 7f5e960aa4ccc71079b8c06690665af74cffd0ab
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82759066"
---
# <a name="the-significance-of-cursor-location"></a>Die Bedeutung der Cursorposition
Jeder Cursor verwendet temporäre Ressourcen, um die Daten zu speichern. Bei diesen Ressourcen kann es sich um Speicher, eine Auslagerungs Datei auf dem Datenträger, temporäre Datenträger Dateien oder sogar einen temporären Speicher in der Datenbank handeln. Der Cursor wird als *Client seitiger* Cursor bezeichnet, wenn sich diese Ressourcen auf dem Client Computer befinden. Der Cursor wird als *serverseitiger* Cursor bezeichnet, wenn sich diese Ressourcen auf dem Server befinden.  
  
## <a name="client-side-cursors"></a>Client seitige Cursor  
 Verwenden Sie in ADO für einen Client seitigen Cursor, indem Sie den **adUseClient cursorlocationsum verwenden.** Bei einem Client seitigen Cursor, der keine Keysets ist, sendet der Server das gesamte Resultset über das Netzwerk an den Client Computer. Der Client Computer stellt die für den Cursor und das Resultset benötigten temporären Ressourcen bereit und verwaltet diese. Die Client seitige Anwendung kann das gesamte Resultset durchsuchen, um zu bestimmen, welche Zeilen erforderlich sind.  
  
 Statische und keysetgesteuerte Client seitige Cursor können auf Ihrer Arbeitsstation erheblich ausgelastet sein, wenn Sie zu viele Zeilen enthalten. Obwohl alle Cursor Bibliotheken in der Lage sind, Cursor mit Tausenden von Zeilen zu entwickeln, können Anwendungen, die so große Rowsets abrufen, eine schlechte Leistung erzielen. Natürlich gibt es Ausnahmen. Bei einigen Anwendungen kann ein großer Client seitiger Cursor perfekt geeignet sein, und die Leistung ist möglicherweise kein Problem.  
  
 Ein offensichtlicher Vorteil des Client seitigen Cursors ist die schnelle Reaktion. Nachdem das Resultset auf den Client Computer heruntergeladen wurde, ist das Durchsuchen der Zeilen sehr schnell. Die Anwendung ist in der Regel mit Client seitigen Cursorn skalierbar, da die Ressourcenanforderungen des Cursors auf jedem separaten Client und nicht auf dem Server platziert werden.  
  
## <a name="server-side-cursors"></a>Server seitige Cursor  
 Verwenden Sie in ADO für einen serverseitigen Cursor, indem Sie den **addeserver-cursorlocationsum verwenden.** Bei einem serverseitigen Cursor verwaltet der Server das Resultset mithilfe von Ressourcen, die vom Server Computer bereitgestellt werden. Der serverseitige Cursor gibt nur die angeforderten Daten über das Netzwerk zurück. Diese Art von Cursor kann manchmal eine bessere Leistung als der Client seitige Cursor bieten, insbesondere in Situationen, in denen ein übermäßiger Netzwerkverkehr ein Problem darstellt.  
  
 Es ist jedoch wichtig, darauf hinzuweisen, dass es sich bei einem serverseitigen Cursor um mindestens temporär nutzende Server Ressourcen für jeden aktiven Client handelt. Sie müssen entsprechend planen, um sicherzustellen, dass Ihre Server Hardware alle serverseitigen Cursor verwalten kann, die von aktiven Clients angefordert werden. Außerdem kann ein serverseitiger Cursor langsam sein, da er nur einen Einzel Zeilen Zugriff bietet, da kein Batch Cursor verfügbar ist.  
  
 Server seitige Cursor sind beim Einfügen, aktualisieren oder Löschen von Datensätzen nützlich. Bei serverseitigen Cursorn können Sie über mehrere aktive Anweisungen für dieselbe Verbindung verfügen.
