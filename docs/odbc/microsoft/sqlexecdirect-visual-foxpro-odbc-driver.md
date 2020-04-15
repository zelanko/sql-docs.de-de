---
title: SQLExecDirect (Visual FoxPro ODBC-Treiber) | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298670"
---
# <a name="sqlexecdirect-visual-foxpro-odbc-driver"></a>SQLExecDirect (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro ODBC-Treiberspezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Support: Voll  
  
 ODBC-API-Konformität: Kernebene  
  
 Führt eine neue, [präparierbare SQL-Anweisung](../../odbc/microsoft/visual-foxpro-terminology.md)aus. Der Visual FoxPro ODBC-Treiber verwendet die aktuellen Werte der Parametermarkervariablen, wenn Parameter in der Anweisung vorhanden sind.  
  
 Um einen Batchbefehl zu erstellen, um mehr als eine SQL-Anweisung gleichzeitig zu senden, verwenden Sie ein Semikolon (;) , um jede SQL-Anweisung im Batch zu trennen.  
  
 Wenn Ihre Tabellen-, Ansichts- oder Feldnamen Leerzeichen enthalten, schließen Sie die Namen in hintere Anführungszeichen ein. Wenn Ihre Datenbank beispielsweise eine Tabelle mit dem Namen "Meine Tabelle" und das Feld "Mein Feld" enthält, schließen Sie jedes Element des Bezeichners wie folgt ein:  
  
```  
SELECT `My Table`.`Field1`, `My Table`.`Field2` FROM `My Table`  
```  
  
 Weitere Informationen finden Sie unter [SQLExecDirect](../../odbc/reference/syntax/sqlexecdirect-function.md) in der *ODBC-Programmiererreferenz*.
