---
title: Beschreiben von Parametern | Microsoft-Dokumentation
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
ms.openlocfilehash: 2d32e5212ba1ba28262d871498f2974485d38233
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68040020"
---
# <a name="describing-parameters"></a>Beschreiben von Parametern
**SQLBindParameter** verfügt über Argumente, die den Parameter beschreiben: den SQL-Typ, die Genauigkeit und die Skalierung. Der Treiber verwendet diese Informationen oder *Metadaten,* um den Parameterwert in den von der Datenquelle benötigten Typ zu konvertieren. Auf den ersten Blick scheint es so, als ob sich der Treiber an einer besseren Position befindet, um die Parameter Metadaten zu kennen als die Anwendung. Schließlich kann der Treiber die Metadaten für eine Resultsetspalte problemlos ermitteln. Wie sich herausstellt, ist dies nicht der Fall. Erstens bieten die meisten Datenquellen keine Möglichkeit für den Treiber, Parameter Metadaten zu ermitteln. Zweitens kennen die meisten Anwendungen bereits die Metadaten.  
  
 Wenn eine SQL-Anweisung in der Anwendung hart codiert ist, kennt der anwendungswriter bereits den Typ der einzelnen Parameter. Wenn eine SQL-Anweisung zur Laufzeit von der Anwendung erstellt wird, kann die Anwendung die Metadaten beim Erstellen der Anweisung ermitteln. Wenn die Anwendung beispielsweise die-Klausel erstellt  
  
```  
WHERE OrderID = ?  
```  
  
 **SQLColumns** kann für die OrderID-Spalte aufgerufen werden.  
  
 Die einzige Situation, in der die Anwendung die Parameter Metadaten nicht einfach ermitteln kann, ist der Benutzer, der eine parametrisierte Anweisung eingibt. In diesem Fall ruft die Anwendung **SQLPrepare** auf, um die Anweisung vorzubereiten, **SQLNumParams** , um die Anzahl der Parameter zu bestimmen, und **SQLDescribeParam** , um die einzelnen Parameter zu beschreiben. Wie bereits erwähnt, bieten die meisten Datenquellen jedoch keine Möglichkeit für den Treiber, Parameter Metadaten zu ermitteln, sodass **SQLDescribeParam** nicht häufig unterstützt wird.
