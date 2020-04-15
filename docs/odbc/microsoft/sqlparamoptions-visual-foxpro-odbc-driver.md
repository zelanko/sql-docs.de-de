---
title: SQLParamOptions (Visual FoxPro ODBC-Treiber) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLParamOptions function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 7f94a6e2-9c34-405c-b2b0-304d94269715
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: dd714ce7774265a2afd00d42894d644a516bc402
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299470"
---
# <a name="sqlparamoptions-visual-foxpro-odbc-driver"></a>SQLParamOptions (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro ODBC-Treiberspezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Support: Voll  
  
 ODBC-API-Konformität: Ebene 1  
  
 Ermöglicht einer Anwendung, mehrere Werte für den Von [SQLBindParameter](../../odbc/microsoft/sqlbindparameter-visual-foxpro-odbc-driver.md)zugewiesenen Parametersatz anzugeben. Die Möglichkeit, mehrere Werte für einen Satz von Parametern anzugeben, ist nützlich für Masseneinfügungen und andere Arbeiten, bei denen die Datenquelle dieselbe SQL-Anweisung mehrmals mit verschiedenen Parameterwerten verarbeiten muss. Eine Anwendung kann z. B. drei Wertesätze für den Satz von Parametern angeben, die einer **INSERT-Anweisung** zugeordnet sind, und dann die **INSERT-Anweisung** einmal ausführen, um die drei Einfügevorgänge auszuführen.  
  
 Weitere Informationen finden Sie unter [SQLParamOptions](../../odbc/reference/syntax/sqlparamoptions-function.md) in der *ODBC-Programmiererreferenz*.
