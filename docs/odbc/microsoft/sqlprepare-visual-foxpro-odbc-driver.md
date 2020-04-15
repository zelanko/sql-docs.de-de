---
title: SQLPrepare (Visual FoxPro ODBC-Treiber) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLPrepare function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 0c4cb5a4-9729-4b2e-a0c6-52027b92e8fc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 14c9358d04e539eb2c77a00e195e8216cd0f5496
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301556"
---
# <a name="sqlprepare-visual-foxpro-odbc-driver"></a>SQLPrepare (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro ODBC-Treiberspezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Support: Voll  
  
 ODBC-API-Konformität: Kernebene  
  
 Bereitet eine SQL-Anweisung vor, indem geplant wird, wie die Anweisung optimiert und ausgeführt wird. Die SQL-Anweisung wird für die Ausführung durch [SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md)kompiliert.  
  
 Wenn Ihre Tabellen-, Ansichts- oder Feldnamen Leerzeichen enthalten, schließen Sie die Namen in Hinterzeichen (') ein. Wenn Ihre Datenbank beispielsweise eine Tabelle mit dem Namen "Meine Tabelle" und das Feld "Mein Feld" enthält, schließen Sie jedes Element des Bezeichners wie folgt ein:  
  
```  
SELECT * FROM `My Table`.`My Field`  
```  
  
 Weitere Informationen finden Sie unter [SQLPrepare](../../odbc/reference/syntax/sqlprepare-function.md) in der *ODBC-Programmiererreferenz*.
