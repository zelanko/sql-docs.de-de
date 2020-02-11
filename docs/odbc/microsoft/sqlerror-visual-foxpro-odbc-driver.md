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
ms.openlocfilehash: d7e8a60030e9c5c7666ce3b25488cfc6adf00783
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68053866"
---
# <a name="sqlerror-visual-foxpro-odbc-driver"></a>SQLError (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro-ODBC-Treiber spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Unterstützung: vollständig  
  
 ODBC-API-Konformität: kernstufe  
  
 Gibt Fehler-oder Statusinformationen zum letzten Fehler zurück. Der Treiber verwaltet einen Stapel oder eine Liste von Fehlern, die für die Argumente *hstmt*, *hdbc*und *HENV* zurückgegeben werden können. Dies hängt davon ab, wie der **SQLError** -Befehl durchgeführt wird. Die Fehler Warteschlange wird nach jeder Anweisung geleert.  
  
 In der folgenden Tabelle werden die **SQLError** -Argumente und-Rückgabewerte beschrieben, die vom Treiber verwendet werden.  
  
|SQLError-Argument|Rückgabewert Beschreibung|  
|-----------------------|------------------------------|  
|*szsqlstate*|Der Wert für SQLSTATE, der durch den Fehler dargestellt wird.|  
|*pfnativeerror*|Ein Wert ungleich 0 (null) gibt eine [native Fehlermeldung für einen Visual FoxPro-ODBC-Treiber](../../odbc/microsoft/visual-foxpro-odbc-driver-native-error-messages.md)an Der Wert 0 (null) gibt an, dass der Fehler vom Treiber erkannt und dem entsprechenden [ODBC-Fehler Code](../../odbc/microsoft/odbc-error-codes-visual-foxpro-odbc-driver.md)zugeordnet wurde.|  
|*szErrorMsg*|Der Text für den nativen Fehler oder ODBC-Fehler.|  
|*pcberrormsg*|Die Länge des Nachrichten Texts zuzüglich der Länge der Bezeichner.|  
  
 Weitere Informationen zu Treiber Fehlermeldungen finden Sie unter [Übersicht über Fehlermeldungen](../../odbc/microsoft/error-messages-visual-foxpro-odbc-driver.md). Weitere Informationen zu dieser Funktion finden Sie unter [SQLError](../../odbc/reference/syntax/sqlerror-function.md) in der *ODBC Programmer es Reference*.
