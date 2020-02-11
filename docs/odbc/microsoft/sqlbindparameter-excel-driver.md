---
title: SQLBindParameter (Excel-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Excel driver [ODBC], SQLBindParameter
- SQLBindParameter function [ODBC], Excel Driver
ms.assetid: 40489bc5-3e2a-425e-892d-e0dc037f4d7a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8b33200e0628566bc88f770ca1fe8fd895ecbf2a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68063256"
---
# <a name="sqlbindparameter-excel-driver"></a>SQLBindParameter (Excel-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Informationen zu Excel-Treibern. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Wenn der Microsoft Excel-Treiber verwendet wird, wird beim Ausführen einer INSERT-Anweisung, die einen-Parameter verwendet, um einen NULL-Wert in eine SQL_CHAR Spalte einzufügen, SQL_SUCCESS_WITH_INFO mit SQLSTATE 01004 zurückgegeben, "Data truncated".
