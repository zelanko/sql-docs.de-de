---
title: SQLExecDirect (Visual FoxPro-ODBC-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLExecDirect function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5004060f-8510-4018-87a4-d41789e69d3e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 40c0a3404a3e7a9a67b6f71d197343eddb417955
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298670"
---
# <a name="sqlexecdirect-visual-foxpro-odbc-driver"></a>SQLExecDirect (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro-ODBC-Treiber spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Unterstützung: vollständig  
  
 ODBC-API-Konformität: kernstufe  
  
 Führt eine neue, vorbereit [Bare SQL-Anweisung](../../odbc/microsoft/visual-foxpro-terminology.md)aus. Der Visual FoxPro-ODBC-Treiber verwendet die aktuellen Werte der Parametermarker-Variablen, wenn in der Anweisung Parameter vorhanden sind.  
  
 Um einen Batch-Befehl zu erstellen, um mehrere SQL-Anweisungen gleichzeitig zu übermitteln, verwenden Sie ein Semikolon (;) zum Trennen der einzelnen SQL-Anweisungen im Batch.  
  
 Wenn Ihre Tabellen-, Ansichts-oder Feldnamen Leerzeichen enthalten, schließen Sie die Namen in die rückanführungs Zeichen ein. Wenn Ihre Datenbank z. b. eine Tabelle mit dem Namen "My Table" und das Feld "My" enthält, schließen Sie jedes Element des Bezeichners wie folgt ein:  
  
```  
SELECT `My Table`.`Field1`, `My Table`.`Field2` FROM `My Table`  
```  
  
 Weitere Informationen finden Sie unter [SQLExecDirect](../../odbc/reference/syntax/sqlexecdirect-function.md) in der *ODBC Programmer es Reference*.
