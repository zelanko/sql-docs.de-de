---
title: Rolle des Treibers | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver error checking [ODBC]
- diagnostic information [ODBC], driver error checking
ms.assetid: cac64c24-a27d-4884-96c0-ea7988351711
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8c683d990aaa3fd6892369e734c06fd1c356bd0f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304282"
---
# <a name="role-of-the-driver"></a>Rolle des Treibers
Der Treiber überprüft alle Fehler und Warnungen, die nicht vom Treiber-Manager und den von ihm generierten Auftragsstatus Daten angezeigt werden. (ODBC 2. der *x* -Treiber sortiert keine Status Einträge.) Dies schließt Fehler und Warnungen beim Abschneiden von Daten, Datenkonvertierung, Syntax und einige Statusübergänge ein. Der Treiber kann auch Fehler und Warnungen überprüfen, die vom Treiber-Manager teilweise überprüft wurden. Wenn beispielsweise der Treiber-Manager überprüft, ob der Wert des *Vorgangs* in **SQLSetPos** zulässig ist, muss der Treiber überprüfen, ob er unterstützt wird.  
  
 Der Treiber ordnet auch systemeigene *Fehler* zu, d. h. Fehler, die von der Datenquelle zurückgegeben werden, in Sqlstates. Beispielsweise kann der Treiber eine Reihe von unterschiedlichen systemeigenen Fehlern für eine ungültige SQL-Syntax zu SQLSTATE 42000 zuordnen (Syntax Fehler oder Zugriffsverletzung). Der Treiber gibt die systemeigene Fehlernummer im Feld SQL_DIAG_NATIVE des Statusdaten Satzes zurück. Die Treiber Dokumentation sollte zeigen, wie Fehler und Warnungen aus der Datenquelle den Argumenten in **SQLGetDiagRec** und **SQLGetDiagField**zugeordnet werden.
