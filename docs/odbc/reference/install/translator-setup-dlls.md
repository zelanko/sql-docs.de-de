---
description: Setup-DLLs für das Konvertierungsprogramm
title: Setup-DLLs für Übersetzer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- translator setup DLL [ODBC]
ms.assetid: b3ca79e9-01b9-4541-81de-bbbad24ca736
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2fe4d514f098773024392666d8f528592d362da4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487393"
---
# <a name="translator-setup-dlls"></a>Setup-DLLs für das Konvertierungsprogramm
> [!NOTE]  
>  Ab Windows XP und Windows Server 2003 ist ODBC im Windows-Betriebssystem enthalten. Sie sollten ODBC nur in früheren Versionen von Windows explizit installieren.  
  
 Die Konvertierungs-Setup-DLL enthält die **ConfigTranslator** -Funktion, die die Standardoption für einen Konvertierer zurückgibt. Bei Bedarf wird der Benutzer zur Eingabe dieser Informationen aufgefordert. Eine umfassende Beschreibung dieser Funktion finden Sie unter [dll-API-Referenz für Setup](../../../odbc/reference/syntax/setup-dll-api-reference.md).  
  
 Die Konvertierungs-Setup-DLL wird vom Entwickler des Konvertierers verfasst. Es kann Teil der Konvertierungs-DLL oder einer separaten DLL sein.
