---
title: Arrays von Parameter Werten | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298798"
---
# <a name="arrays-of-parameter-values"></a>Arrays für Parameterwerte
Es ist häufig hilfreich, wenn Anwendungen Arrays von Parametern übergeben. Wenn Sie beispielsweise Arrays von Parametern und eine parametrisierte **Insert** -Anweisung verwenden, kann eine Anwendung eine Reihe von Zeilen gleichzeitig einfügen. Es gibt mehrere Vorteile bei der Verwendung von Arrays. Erstens wird der Netzwerk Datenverkehr reduziert, da die Daten für viele Anweisungen in einem einzelnen Paket gesendet werden (wenn die Datenquelle Parameter Arrays nativ unterstützt). Zweitens können einige Datenquellen SQL-Anweisungen mit Arrays schneller ausführen, als die gleiche Anzahl von separaten SQL-Anweisungen auszuführen. Wenn die Daten in einem Array gespeichert werden, wie es häufig bei Bildschirm Daten der Fall ist, kann die Anwendung alle Zeilen in einer bestimmten Spalte mit einem einzelnen **SQLBindParameter** -Befehl binden und Sie durch Ausführen einer einzigen Anweisung aktualisieren.  
  
 Leider unterstützen nicht viele Datenquellen Parameter Arrays. Allerdings kann ein Treiber Parameter Arrays emulieren, indem eine SQL-Anweisung für jeden Satz von Parameterwerten einmal ausgeführt wird. Dies kann zu einer Zunahme der Geschwindigkeit führen, da der Treiber dann die Anweisung vorbereiten kann, die er für jeden Parametersatz einmal ausführen soll. Dies kann auch zu einfachem Anwendungscode führen.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Binden von Parameterarrays](../../../odbc/reference/develop-app/binding-arrays-of-parameters.md)  
  
-   [Verwenden von Parameterarrays](../../../odbc/reference/develop-app/using-arrays-of-parameters.md)
