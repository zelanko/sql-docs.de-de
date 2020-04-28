---
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
ms.openlocfilehash: 28c354fddb36b9e035361fa4ba03fbde34b7d399
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81296050"
---
# <a name="translator-setup-dlls"></a>Setup-DLLs für das Konvertierungsprogramm
> [!NOTE]  
>  Ab Windows XP und Windows Server 2003 ist ODBC im Windows-Betriebssystem enthalten. Sie sollten ODBC nur in früheren Versionen von Windows explizit installieren.  
  
 Die Konvertierungs-Setup-DLL enthält die **ConfigTranslator** -Funktion, die die Standardoption für einen Konvertierer zurückgibt. Bei Bedarf wird der Benutzer zur Eingabe dieser Informationen aufgefordert. Eine umfassende Beschreibung dieser Funktion finden Sie unter [dll-API-Referenz für Setup](../../../odbc/reference/syntax/setup-dll-api-reference.md).  
  
 Die Konvertierungs-Setup-DLL wird vom Entwickler des Konvertierers verfasst. Es kann Teil der Konvertierungs-DLL oder einer separaten DLL sein.
