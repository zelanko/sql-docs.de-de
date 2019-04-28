---
title: Den Benutzer aufgefordert, Verbindungsinformationen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connecting to data source [ODBC], SqlConnect
- connecting to driver [ODBC], prompting user for information
- connecting to driver [ODBC], SQLConnect
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], SqlDriverConnect
- SQLConnect function [ODBC], prompting user for connection information
- connecting to data source [ODBC], prompting user for information
- prompting user for connection information [ODBC]
- SQLDriverConnect function [ODBC], prompting user for connection information
ms.assetid: da98e9b9-a4ac-4a9d-bae6-e9252b1fe1e5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 58df84bf96306a2cfbc0567a3d5f6cb13514a06e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62861897"
---
# <a name="prompting-the-user-for-connection-information"></a>Aufforderung an Benutzer zur Eingabe von Verbindungsinformationen
Wenn die Anwendung verwendet **SQLConnect** und fordert den Benutzer für alle Verbindungsinformationen, z. B. einen Benutzernamen und ein Kennwort, sie müssen dazu selbst. Die Anwendung das "Erscheinungsbild" steuern können, kann die Anwendung, Treiber-spezifischen Code enthalten erzwingen. Dies tritt auf, wenn die Anwendung benötigt, um den Benutzer für treiberspezifische Verbindungsinformationen aufzufordern. Dies stellt eine unmögliche Situation für allgemeine Anwendungen, die konzipiert werden alle Treiber, wie Treiber, die nicht vorhanden sind, wenn die Anwendung geschrieben wird.  
  
 **SQLDriverConnect** kann den Benutzer zur Verbindung auffordern. Das benutzerdefinierte Programm zuvor erwähnten könnten z. B. die folgende Verbindungszeichenfolge zu übergeben **SQLDriverConnect**:  
  
```  
DSN=XYZ Corp;  
```  
  
 Der Treiber kann dann ein Dialogfeld angezeigt, die Benutzer-IDs und Kennwörtern, ähnlich der folgenden Abbildung abfragt.  
  
 ![Dialogfeld, das für die Benutzer-IDs und Kennwörter fordert](../../../odbc/reference/develop-app/media/pr18.gif "pr18")  
  
 Der Treiber für Verbindungsinformationen auffordern kann ist besonders nützlich, um generisch und vertikale Anwendungen. Diese Anwendungen sollten keine treiberspezifische Informationen und müssen die Treiber-Eingabeaufforderung für die benötigten Informationen hält diese Informationen aus der Anwendung. Dies wird von den beiden vorherigen Beispielen gezeigt. Wenn die Anwendung nur der Name der Datenquelle an den Treiber übergeben, wird die Anwendung keine treiberspezifische Informationen enthalten und wurde daher nicht an einen bestimmten Treiber gebunden. Wenn die Anwendung eine vollständige Verbindungszeichenfolge für den Treiber übergeben, war es an den Treiber gebunden, die die Zeichenfolge interpretieren kann.  
  
 Eine generische Anwendung möglicherweise einen Schritt weitergehen und nicht einmal eine Datenquelle angeben. Wenn **SQLDriverConnect** empfängt einer leere Verbindungszeichenfolge, die Treiber-Manager zeigt das folgende Dialogfeld.  
  
 ![Wählen Sie im Dialogfeld der Datenquelle](../../../odbc/reference/develop-app/media/ch06a.gif "CH06A")  
  
 Nachdem der Benutzer eine Datenquelle ausgewählt hat, wird der Treiber-Manager eine Verbindungszeichenfolge angeben, die Datenquelle erstellt und übergibt es an den Treiber. Der Treiber kann dann den Benutzer für zusätzliche Informationen auffordern, benötigten.  
  
 Die Bedingungen, unter dem der Treiber den Benutzer fordert, gesteuert werden, indem die *DriverCompletion* kennzeichnen; es gibt Möglichkeiten, auffordern, fordert bei Bedarf oder nie Fragen. Eine vollständige Beschreibung dieses Kennzeichens, finden Sie unter den [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) funktionsbeschreibung.
