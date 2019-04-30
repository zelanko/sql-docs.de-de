---
title: SQLError (Visual FoxPro-ODBC-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLError function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 8315ec16-1c22-447a-a577-39bd94f61070
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3014c5c2af1a0ef8e5f485c790089e4807834446
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63313281"
---
# <a name="sqlerror-visual-foxpro-odbc-driver"></a>SQLError (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro-ODBC-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Support: Vollständig  
  
 ODBC-API-Übereinstimmung: Kern-Ebene  
  
 Fehler oder Status Informationen zu den letzten Fehler zurückgegeben. Der Treiber verwaltet einen Stapel oder eine Liste von Fehlern, die für die zurückgegeben werden, können die *Befehls beschäftigt*, *Hdbc*, und *Henv* Argumente, je nachdem, wie der Aufruf von **SQLError**  erfolgt. Die Fehlerwarteschlange wird nach jeder Anweisung geleert.  
  
 Die folgende Tabelle beschreibt die **SQLError** Argumente und Rückgabewerte, die vom Treiber verwendet.  
  
|SQLError-argument|Beschreibung des Rückgabewerts|  
|-----------------------|------------------------------|  
|*szSQLState*|Der Wert für den SQLSTATE, dargestellt durch den Fehler.|  
|*pfNativeError*|Gibt ein Wert ungleich NULL eine [Visual FoxPro-ODBC-Treiber systemeigene Fehlermeldung](../../odbc/microsoft/visual-foxpro-odbc-driver-native-error-messages.md). Der Wert 0 (null) gibt an, der Fehler wurde vom Treiber erkannt wurden und an die entsprechende zugeordnet [ODBC-Fehlercode](../../odbc/microsoft/odbc-error-codes-visual-foxpro-odbc-driver.md).|  
|*szErrorMsg*|Der Text für den systemeigenen Fehler oder die ODBC-Fehler.|  
|*pcbErrorMsg*|Die Länge der den Meldungstext plus die Länge der Bezeichner.|  
  
 Weitere Informationen zu Treiber-Fehlermeldungen finden Sie unter [Übersicht über Fehler](../../odbc/microsoft/error-messages-visual-foxpro-odbc-driver.md). Weitere Informationen zu dieser Funktion finden Sie unter [SQLError](../../odbc/reference/syntax/sqlerror-function.md) in die *ODBC Programmer's Reference*.
