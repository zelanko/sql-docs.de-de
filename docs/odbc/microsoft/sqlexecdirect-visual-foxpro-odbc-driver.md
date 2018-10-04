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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 808d7890c18839c0e9059cdc3181a4579eb2ec4f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47716038"
---
# <a name="sqlexecdirect-visual-foxpro-odbc-driver"></a>SQLExecDirect (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro-ODBC-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Support: vollständige  
  
 ODBC-API-Übereinstimmung: Kernebene  
  
 Führt eine neue [vorbereitbaren SQL-Anweisung](../../odbc/microsoft/visual-foxpro-terminology.md). Der Visual FoxPro-ODBC-Treiber verwendet die aktuellen Werte der Variablen Marker Parameter auf, wenn alle Parameter in der Anweisung vorhanden.  
  
 Verwenden Sie zum Erstellen eines Batch-Befehls zum Übermitteln von mehr als eine SQL-Anweisung zu einem Zeitpunkt ein Semikolon (;), um jede SQL-Anweisung im Batch zu trennen.  
  
 Wenn Ihre Tabelle, Sicht oder Feldnamen Leerzeichen enthalten, schließen Sie die Namen wieder in Anführungszeichen ein. Z. B. wenn die Datenbank eine Tabelle namens "Meine Tabelle" und "das Feld mein Feld enthält, müssen Sie jedes Element des Bezeichners wie folgt:  
  
```  
SELECT `My Table`.`Field1`, `My Table`.`Field2` FROM `My Table`  
```  
  
 Weitere Informationen finden Sie unter [SQLExecDirect](../../odbc/reference/syntax/sqlexecdirect-function.md) in die *ODBC Programmer's Reference*.
