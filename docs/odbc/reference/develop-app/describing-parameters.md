---
title: Beschreibt Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLBindParameter function [ODBC], describing parameters
ms.assetid: 118d0f47-2afd-4955-bb47-38b1e2c2f38f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1bc752afc0cb5214e629a343c35464e612b57c36
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47808968"
---
# <a name="describing-parameters"></a>Beschreiben von Parametern
**SQLBindParameter** enthält Argumente, die den Parameter zu beschreiben: die SQL-Datentyp, Genauigkeit und Skalierung. Der Treiber verwendet diese Informationen, oder *Metadaten* umzuwandelnde Wert des Parameters in den Typ, der von der Datenquelle erforderlich sind. Auf den ersten Blick scheint es sich, dass der Treiber in einer besseren Position, die Metadaten von Parametern als die Anwendung wissen ist; Schließlich kann der Treiber mühelos ermitteln, die Metadaten für eine Resultsetspalte. Wie sich herausstellt, ist dies nicht der Fall. Zunächst die meisten Datenquellen bieten keine Möglichkeit für den Treiber, um Metadaten von Parametern zu ermitteln. Zweitens wird die meisten Anwendungen bereits kennen, die Metadaten.  
  
 Wenn eine SQL-Anweisung in der Anwendung hartcodiert ist, weiß der Autor der Anwendung bereits den Typ jedes Parameters an. Wenn eine SQL-Anweisung, die von der Anwendung zur Laufzeit erstellt wird, kann die Metadaten die Anwendung bestimmen, wie sie die Anweisung erstellt. Konstruiert z. B. wenn die Anwendung die-Klausel  
  
```  
WHERE OrderID = ?  
```  
  
 Er kann Aufrufen **SQLColumns** für die Spalte "OrderID".  
  
 Die einzige Situation, in der die Anwendung ganz einfach die Parametermetadaten bestimmen kann nicht, ist, wenn der Benutzer eine parametrisierte Anweisung eingibt. In diesem Fall die Anwendung ruft **SQLPrepare** zum Vorbereiten der Anweisung **SQLNumParams** um zu bestimmen, die Anzahl der Parameter, und **SQLDescribeParam** beschreiben Jeder Parameter. Wie bereits erwähnt wurde, die meisten Datenquellen keine bieten jedoch eine Möglichkeit für den Treiber, um Metadaten von Parametern, also ermitteln **SQLDescribeParam** wird allgemein nicht unterstützt.
