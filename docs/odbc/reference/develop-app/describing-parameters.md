---
title: Beschreiben von Parametern | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f4d9284294707da0a469bf75ff9812ad5f7855bb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305941"
---
# <a name="describing-parameters"></a>Beschreiben von Parametern
**SQLBindParameter** verfügt über Argumente, die den Parameter beschreiben: SQL-Typ, Genauigkeit und Skalierung. Der Treiber verwendet diese Informationen oder Metadaten, um den Parameterwert in den Typ zu *konvertieren,* der von der Datenquelle benötigt wird. Auf den ersten Blick scheint es, dass der Treiber in einer besseren Position ist, um die Parametermetadaten als die Anwendung zu kennen; Schließlich kann der Treiber die Metadaten für eine Ergebnissatzspalte leicht ermitteln. Wie sich herausstellt, ist dies nicht der Fall. Erstens bieten die meisten Datenquellen keine Möglichkeit für den Treiber, Parametermetadaten zu ermitteln. Zweitens kennen die meisten Anwendungen die Metadaten bereits.  
  
 Wenn eine SQL-Anweisung in der Anwendung hartcodiert ist, kennt der Anwendungsschreiber bereits den Typ der einzelnen Parameter. Wenn eine SQL-Anweisung von der Anwendung zur Laufzeit erstellt wird, kann die Anwendung die Metadaten beim Erstellen der Anweisung bestimmen. Wenn die Anwendung z. B. die Klausel erstellt  
  
```  
WHERE OrderID = ?  
```  
  
 Es kann **SQLColumns** für die OrderID-Spalte aufrufen.  
  
 Die einzige Situation, in der die Anwendung die Parametermetadaten nicht einfach bestimmen kann, ist, wenn der Benutzer eine parametriertisierte Anweisung eingibt. In diesem Fall ruft die Anwendung **SQLPrepare** auf, um die Anweisung vorzubereiten, **SQLNumParams,** um die Anzahl der Parameter zu bestimmen, und **SQLDescribeParam,** um die einzelnen Parameter zu beschreiben. Wie bereits erwähnt, bieten die meisten Datenquellen jedoch keine Möglichkeit für den Treiber, Parametermetadaten zu ermitteln, sodass **SQLDescribeParam** nicht umfassend unterstützt wird.
