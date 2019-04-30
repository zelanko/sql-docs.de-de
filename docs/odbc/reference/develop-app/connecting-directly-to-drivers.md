---
title: Herstellen einer Verbindung direkt mit dem Treiber | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], SqlDriverConnect
- SQLDriverConnect function [ODBC], connecting directly to drivers
- connecting to driver [ODBC], drivers
ms.assetid: f86e198f-a088-4401-9106-aa62a0eb8f6e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3f5818d67659769ae104b3e98248c26f5b9fe8a7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63151241"
---
# <a name="connecting-directly-to-drivers"></a>Herstellen einer Verbindung direkt mit Treibern
Wie in beschrieben wurde [Auswählen einer Datenquelle oder Treiber](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md)weiter oben in diesem Abschnitt einige Anwendungen möchten nicht an eine Datenquelle verwenden. Stattdessen möchten sie direkt auf einen Treiber zu verbinden. **SQLDriverConnect** bietet eine Möglichkeit für die Anwendung direkt zu einem Treiber herstellen, ohne eine Datenquelle angeben. Vom Konzept her ist eine temporäre Datenquelle zur Laufzeit erstellt.  
  
 Um direkt auf einen Treiber zu verbinden, die Anwendung gibt an, die **Treiber** Schlüsselwort in der Verbindungszeichenfolge anstelle von der **DSN** Schlüsselwort. Der Wert des der **Treiber** Schlüsselwort ist die Beschreibung des Treibers von zurückgegeben **SQLDrivers**. Nehmen wir beispielsweise an ein Treiber wurde die Beschreibung Paradox-Treiber und erfordert den Namen eines Verzeichnisses, die die Datendateien enthält. Zur Verbindung mit dieser Treiber kann die Anwendung eines der folgenden Verbindungszeichenfolgen verwenden:  
  
```  
DRIVER={Paradox Driver};Directory=C:\PARADOX;  
DRIVER={Paradox Driver};  
```  
  
 Die erste Zeichenfolge benötigt der Treiber nicht zusätzliche Informationen. Der Treiber müssen mit der zweiten Zeichenfolge für den Namen des Verzeichnisses mit den Datendateien aufgefordert.
