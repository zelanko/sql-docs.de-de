---
title: Arrays von Parameterwerten | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- arrays of parameter values [ODBC]
- parameter arrays [ODBC]
ms.assetid: 9b572c5b-1dfe-40af-bebd-051548ab6d90
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: eb9389c769e3a7bb0c39959a559531e8051a7bec
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298798"
---
# <a name="arrays-of-parameter-values"></a>Arrays für Parameterwerte
Es ist oft nützlich für Anwendungen, Arrays von Parametern zu übergeben. Beispielsweise kann eine Anwendung mithilfe von Arrays von Parametern und einer parametrisierten **INSERT-Anweisung** eine Reihe von Zeilen gleichzeitig einfügen. Die Verwendung von Arrays bietet mehrere Vorteile. Erstens wird der Netzwerkverkehr reduziert, da die Daten für viele Anweisungen in einem einzelnen Paket gesendet werden (wenn die Datenquelle Parameterarrays nativ unterstützt). Zweitens können einige Datenquellen SQL-Anweisungen schneller mithilfe von Arrays ausführen als die gleiche Anzahl separater SQL-Anweisungen. Wenn die Daten in einem Array gespeichert werden, wie dies bei Bildschirmdaten häufig der Fall ist, kann die Anwendung alle Zeilen in einer bestimmten Spalte mit einem einzelnen Aufruf von **SQLBindParameter** binden und aktualisieren, indem sie eine einzelne Anweisung ausführt.  
  
 Leider unterstützen nicht viele Datenquellen Parameterarrays. Ein Treiber kann jedoch Parameterarrays emulieren, indem er einmal eine SQL-Anweisung für jeden Satz von Parameterwerten ausführt. Dies kann zu einer Erhöhung der Geschwindigkeit führen, da der Treiber dann die Anweisung vorbereiten kann, die er einmal für jeden Parametersatz ausführen möchte. Es kann auch zu einfacherem Anwendungscode führen.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Binden von Parameterarrays](../../../odbc/reference/develop-app/binding-arrays-of-parameters.md)  
  
-   [Verwenden von Parameterarrays](../../../odbc/reference/develop-app/using-arrays-of-parameters.md)
