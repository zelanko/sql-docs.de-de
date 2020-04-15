---
title: SQLError (Visual FoxPro ODBC-Treiber) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0d1247217905187cfb2dbaca6d7b7b562d0175bd
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298680"
---
# <a name="sqlerror-visual-foxpro-odbc-driver"></a>SQLError (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro ODBC-Treiberspezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Support: Voll  
  
 ODBC-API-Konformität: Kernebene  
  
 Gibt Fehler- oder Statusinformationen zum letzten Fehler zurück. Der Treiber verwaltet einen Stapel oder eine Liste von Fehlern, die für die Argumente *hstmt*, *hdbc*und *henv* zurückgegeben werden können, je nachdem, wie der Aufruf von **SQLError** erfolgt. Die Fehlerwarteschlange wird nach jeder Anweisung geleert.  
  
 In der folgenden Tabelle werden die **SQLError-Argumente** und Rückgabewerte beschrieben, die vom Treiber verwendet werden.  
  
|SQLError-Argument|Rückgabewertbeschreibung|  
|-----------------------|------------------------------|  
|*szSQLState*|Der Wert für SQLSTATE, der durch den Fehler dargestellt wird.|  
|*pfNativeError*|Ein Wert ungleich Null gibt eine native Fehlermeldung des [Visual FoxPro ODBC-Treibers](../../odbc/microsoft/visual-foxpro-odbc-driver-native-error-messages.md)an. Der Wert Null gibt an, dass der Fehler vom Treiber erkannt und dem entsprechenden [ODBC-Fehlercode](../../odbc/microsoft/odbc-error-codes-visual-foxpro-odbc-driver.md)zugeordnet wurde.|  
|*szErrorMsg*|Der Text für den systemeigenen Fehler oder ODBC-Fehler.|  
|*pcbErrorMsg*|Die Länge des Nachrichtentexts plus die Länge der Bezeichner.|  
  
 Weitere Informationen zu Treiberfehlermeldungen finden Sie unter [Übersicht über Fehlermeldungen](../../odbc/microsoft/error-messages-visual-foxpro-odbc-driver.md). Weitere Informationen zu dieser Funktion finden Sie unter [SQLError](../../odbc/reference/syntax/sqlerror-function.md) in der *ODBC-Programmiererreferenz*.
