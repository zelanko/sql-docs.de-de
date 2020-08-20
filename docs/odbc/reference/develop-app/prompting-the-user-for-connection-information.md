---
description: Aufforderung an Benutzer zur Eingabe von Verbindungsinformationen
title: Benutzer werden zur Eingabe von Verbindungsinformationen aufgefordert | Microsoft-Dokumentation
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
ms.openlocfilehash: f52e0d120fb150fe58b850107847d7ef5df20e7c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88465712"
---
# <a name="prompting-the-user-for-connection-information"></a>Aufforderung an Benutzer zur Eingabe von Verbindungsinformationen
Wenn die Anwendung **SQLCONNECT** verwendet und den Benutzer zur Eingabe von Verbindungsinformationen auffordern muss, wie z. b. Benutzername und Kennwort, muss dies selbst durchführen. Dies ermöglicht es der Anwendung, das "Aussehen und fühlen" zu steuern, es kann jedoch dazu gezwungen werden, dass die Anwendung treiberspezifischen Code enthält. Dieser Fehler tritt auf, wenn die Anwendung den Benutzer zur Eingabe von treiberspezifischen Verbindungsinformationen auffordern muss. Dies stellt eine unmögliche Situation für generische Anwendungen dar, die für die Arbeit mit allen Treibern entwickelt wurden, einschließlich Treiber, die beim Schreiben der Anwendung nicht vorhanden sind.  
  
 **SQLDriverConnect** kann den Benutzer zur Eingabe von Verbindungsinformationen auffordern. Beispielsweise könnte das zuvor erwähnte benutzerdefinierte Programm die folgende Verbindungs Zeichenfolge an **SQLDriverConnect**übergeben:  
  
```  
DSN=XYZ Corp;  
```  
  
 Der Treiber zeigt möglicherweise ein Dialogfeld an, in dem Benutzer-IDs und Kenn Wörter wie in der folgenden Abbildung angezeigt werden.  
  
 ![Dialogfeld, das die Eingabe von Benutzer-IDs und Kennwörtern erfordert](../../../odbc/reference/develop-app/media/pr18.gif "pr18")  
  
 Der Treiber kann zur Eingabe von Verbindungsinformationen für generische und vertikale Anwendungen besonders nützlich sein. Diese Anwendungen sollten keine treiberspezifischen Informationen enthalten, und bei der Eingabeaufforderung des Treibers für die benötigten Informationen werden diese Informationen von der Anwendung beibehalten. Dies wird in den beiden vorherigen Beispielen gezeigt. Wenn die Anwendung nur den Datenquellen Namen an den Treiber übermittelt hat, enthielt die Anwendung keine treiberspezifischen Informationen und wurde daher nicht an einen bestimmten Treiber gebunden. Wenn die Anwendung eine komplette Verbindungs Zeichenfolge an den Treiber übermittelt hat, wurde sie an den Treiber gebunden, der diese Zeichenfolge interpretieren konnte.  
  
 Eine generische Anwendung kann dies einen Schritt weiter gehen und nicht einmal eine Datenquelle angeben. Wenn **SQLDriverConnect** eine leere Verbindungs Zeichenfolge empfängt, zeigt der Treiber-Manager das folgende Dialogfeld an.  
  
 ![Dialogfeld "Datenquelle auswählen"](../../../odbc/reference/develop-app/media/ch06a.gif "CH06A")  
  
 Nachdem der Benutzer eine Datenquelle ausgewählt hat, erstellt der Treiber-Manager eine Verbindungs Zeichenfolge, die diese Datenquelle angibt und übergibt sie an den Treiber. Der Treiber kann dann den Benutzer zur Eingabe zusätzlicher Informationen auffordern, die er benötigt.  
  
 Die Bedingungen, unter denen der Treiber den Benutzer anfordert, werden durch das *DriverCompletion* -Flag gesteuert. Es gibt Optionen, die immer zur Eingabeaufforderung, bei Bedarf auffordern oder nie aufgefordert werden. Eine umfassende Beschreibung dieses Flags finden Sie in der Beschreibung der [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) -Funktion.
