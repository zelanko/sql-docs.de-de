---
title: Arrays für Parameterwerte | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 03479a0187c7720a595b550290a8f5ac8197fa9c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63288413"
---
# <a name="arrays-of-parameter-values"></a>Arrays für Parameterwerte
Es ist häufig nützlich für Anwendungen, die zum Übergeben von Arrays von Parametern. Verwenden Sie z. B. Arrays von Parametern und einer parametrisierten **einfügen** -Anweisung, eine Anwendung kann eine Anzahl von Zeilen auf einmal einfügen. Es gibt mehrere Vorteile gegenüber der Verwendung von Arrays. Zunächst wird der Netzwerkverkehr reduziert, da die Daten für mehrere Anweisungen in einem einzelnen Paket gesendet werden (wenn die Datenquelle Parameterarrays nativ unterstützt). Zweitens können einige Datenquellen Arrays schneller als das Ausführen der gleichen Anzahl von unterschiedlichen SQL-Anweisungen mit SQL-Anweisungen ausführen. Abschließend, wenn die Daten in einem Array gespeichert werden, wie häufig der Fall für die Bildschirmdaten ist, die Anwendung kann gebunden werden alle Zeilen in einer bestimmten Spalte mit einem einzigen Aufruf **SQLBindParameter** und aktualisieren, indem Sie Ausführung einer einzelnen Anweisung.  
  
 Leider unterstützt nicht viele Datenquellen Parameterarrays. Allerdings kann ein Treiber Parameterarrays emulieren Ausführen einer SQL­Anweisung einmal für jeden Satz von Parameterwerten. Dies kann zu Anstieg von Geschwindigkeit führen, da der Treiber klicken Sie dann die Anweisung werden, die es Pläne vorbereitet kann, die einmal für jeden Parametersatz ausgeführt. Es kann auch zu einfacheren Anwendungscode führen.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Binden von Parameterarrays](../../../odbc/reference/develop-app/binding-arrays-of-parameters.md)  
  
-   [Verwenden von Parameterarrays](../../../odbc/reference/develop-app/using-arrays-of-parameters.md)
