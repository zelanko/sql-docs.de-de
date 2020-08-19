---
description: SQLBindParameter (Excel-Treiber)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2f18d34bb17f6f6b039bac5f6842ff837c22f362
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483373"
---
# <a name="sqlbindparameter-excel-driver"></a>SQLBindParameter (Excel-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Informationen zu Excel-Treibern. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Wenn der Microsoft Excel-Treiber verwendet wird, wird beim Ausführen einer INSERT-Anweisung, die einen-Parameter verwendet, um einen NULL-Wert in eine SQL_CHAR Spalte einzufügen, SQL_SUCCESS_WITH_INFO mit SQLSTATE 01004 zurückgegeben, "Data truncated".
