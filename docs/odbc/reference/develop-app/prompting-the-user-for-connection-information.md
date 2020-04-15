---
title: Aufforderung an den Benutzer, Verbindungsinformationen zu erhalten | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9b0f120a1076f14f5e67d506e52a446e0a3d4713
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282083"
---
# <a name="prompting-the-user-for-connection-information"></a>Aufforderung an Benutzer zur Eingabe von Verbindungsinformationen
Wenn die Anwendung **SQLConnect** verwendet und den Benutzer zu Verbindungsinformationen wie Benutzername und Kennwort auffordern muss, muss sie dies selbst tun. Dies ermöglicht es der Anwendung, ihr "Look and Feel" zu steuern, aber es könnte die Anwendung zwingen, treiberspezifischen Code zu enthalten. Dies tritt auf, wenn die Anwendung den Benutzer zur Eingabe treiberspezifischer Verbindungsinformationen auffordern muss. Dies stellt eine unmögliche Situation für generische Anwendungen dar, die für die Arbeit mit allen Treibern ausgelegt sind, einschließlich Treibern, die nicht vorhanden sind, wenn die Anwendung geschrieben wird.  
  
 **SQLDriverConnect** kann den Benutzer zur Eingabe von Verbindungsinformationen auffordern. Das oben erwähnte benutzerdefinierte Programm kann z. B. die folgende Verbindungszeichenfolge an **SQLDriverConnect**übergeben:  
  
```  
DSN=XYZ Corp;  
```  
  
 Der Treiber zeigt dann möglicherweise ein Dialogfeld an, in dem Benutzer-IDs und Kennwörter aufgefordert werden, ähnlich wie in der folgenden Abbildung.  
  
 ![Dialogfeld, das die Eingabe von Benutzer-IDs und Kennwörtern erfordert](../../../odbc/reference/develop-app/media/pr18.gif "pr18")  
  
 Dass der Treiber zur Eingabe von Verbindungsinformationen auffordern kann, ist besonders nützlich für generische und vertikale Anwendungen. Diese Anwendungen sollten keine treiberspezifischen Informationen enthalten, und die Treiberaufforderung für die Informationen, die sie benötigt, hält diese Informationen aus der Anwendung heraus. Dies wird durch die beiden vorherigen Beispiele veranschaulicht. Wenn die Anwendung nur den Datenquellennamen an den Treiber übergeben hat, enthielt die Anwendung keine treiberspezifischen Informationen und war daher nicht an einen bestimmten Treiber gebunden. Wenn die Anwendung eine vollständige Verbindungszeichenfolge an den Treiber übergeben hat, wurde sie an den Treiber gebunden, der diese Zeichenfolge interpretieren konnte.  
  
 Eine generische Anwendung kann dies einen Schritt weiter gehen und nicht einmal eine Datenquelle angeben. Wenn **SQLDriverConnect** eine leere Verbindungszeichenfolge empfängt, zeigt der Treiber-Manager das folgende Dialogfeld an.  
  
 ![Dialogfeld "Datenquelle auswählen"](../../../odbc/reference/develop-app/media/ch06a.gif "CH06A")  
  
 Nachdem der Benutzer eine Datenquelle ausgewählt hat, erstellt der Treiber-Manager eine Verbindungszeichenfolge, die diese Datenquelle angibt, und übergibt sie an den Treiber. Der Treiber kann den Benutzer dann zur Eingabe zusätzlicher Informationen auffordern.  
  
 Die Bedingungen, unter denen der Treiber den Benutzer auffordert, werden durch das *DriverCompletion-Flag* gesteuert. Es gibt Optionen, um immer eine Eingabeaufforderung, bei Bedarf eine Eingabeaufforderung oder nie eine Eingabeaufforderung zu erstellen. Eine vollständige Beschreibung dieses Flags finden Sie in der [SQLDriverConnect-Funktionsbeschreibung.](../../../odbc/reference/syntax/sqldriverconnect-function.md)
