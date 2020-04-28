---
title: Direkte Verbindung mit Treibern | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d6aacb5d3df985949e04cdd47a9fe460cddbde6a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299080"
---
# <a name="connecting-directly-to-drivers"></a>Herstellen einer Verbindung direkt mit Treibern
Wie bei der [Auswahl einer Datenquelle oder eines Treibers](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md)erläutert, möchten einige Anwendungen zuvor in diesem Abschnitt keine Datenquelle verwenden. Stattdessen möchten Sie eine direkte Verbindung mit einem Treiber herstellen. **SQLDriverConnect** bietet der Anwendung die Möglichkeit, eine direkte Verbindung mit einem Treiber herzustellen, ohne eine Datenquelle anzugeben. Konzeptionell wird zur Laufzeit eine temporäre Datenquelle erstellt.  
  
 Um eine direkte Verbindung mit einem Treiber herzustellen, gibt die Anwendung das **Driver** -Schlüsselwort in der Verbindungs Zeichenfolge anstelle des **DSN** -Schlüssel Worts an. Der Wert des **Treiber** Schlüsselworts ist die Beschreibung des Treibers, wie von **SQLDrivers**zurückgegeben. Nehmen wir z. b. an, ein Treiber hat den Beschreibungs-Paradox-Treiber und erfordert den Namen eines Verzeichnisses, das die Datendateien enthält. Zum Herstellen einer Verbindung mit diesem Treiber verwendet die Anwendung möglicherweise eine der folgenden Verbindungs Zeichenfolgen:  
  
```  
DRIVER={Paradox Driver};Directory=C:\PARADOX;  
DRIVER={Paradox Driver};  
```  
  
 Bei der ersten Zeichenfolge benötigt der Treiber keine zusätzlichen Informationen. Bei der zweiten Zeichenfolge muss der Treiber den Namen des Verzeichnisses eingeben, das die Datendateien enthält.
