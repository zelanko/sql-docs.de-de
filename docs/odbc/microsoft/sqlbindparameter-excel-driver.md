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
manager: craigg
ms.openlocfilehash: 84f6e44f4849db81c591a791674878190f21e486
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47709318"
---
# <a name="sqlbindparameter-excel-driver"></a>SQLBindParameter (Excel-Treiber)
> [!NOTE]  
>  Dieses Thema enthält die Excel-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Wenn der Microsoft Excel-Treiber verwendet wird, zurück Ausführen einer INSERT-Anweisung, die einen Parameter verwendet wird, ein NULL-Wert in eine SQL_CHAR-Spalte einzufügenden SQL_SUCCESS_WITH_INFO mit SQLSTATE 01004, "Daten abgeschnitten."
