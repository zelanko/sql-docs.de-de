---
title: Direkte Verbindung mit Treibern | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299080"
---
# <a name="connecting-directly-to-drivers"></a>Herstellen einer Verbindung direkt mit Treibern
Wie unter [Auswählen einer Datenquelle oder eines Treibers](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md)weiter oben in diesem Abschnitt erläutert, möchten einige Anwendungen überhaupt keine Datenquelle verwenden. Stattdessen möchten sie eine direkte Verbindung zu einem Treiber herstellen. **SQLDriverConnect** bietet der Anwendung die Möglichkeit, eine direkte Verbindung mit einem Treiber herzustellen, ohne eine Datenquelle anzugeben. Konzeptionell wird zur Laufzeit eine temporäre Datenquelle erstellt.  
  
 Um eine direkte Verbindung mit einem Treiber herzustellen, gibt die Anwendung das **SCHLÜSSELwort DRIVER** in der Verbindungszeichenfolge anstelle des **DSN-Schlüsselworts** an. Der Wert des **SCHLÜSSELworts DRIVER** ist die Beschreibung des Treibers, der von **SQLDrivers**zurückgegeben wird. Angenommen, ein Treiber hat die Beschreibung Paradox Driver und erfordert den Namen eines Verzeichnisses, das die Datendateien enthält. Um eine Verbindung mit diesem Treiber herzustellen, verwendet die Anwendung möglicherweise eine der folgenden Verbindungszeichenfolgen:  
  
```  
DRIVER={Paradox Driver};Directory=C:\PARADOX;  
DRIVER={Paradox Driver};  
```  
  
 Bei der ersten Zeichenfolge benötigt der Treiber keine zusätzlichen Informationen. Bei der zweiten Zeichenfolge muss der Treiber den Namen des Verzeichnisses, das die Datendateien enthält, anfordern.
