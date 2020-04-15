---
title: Übersetzer-Setup-DLLs | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296050"
---
# <a name="translator-setup-dlls"></a>Setup-DLLs für das Konvertierungsprogramm
> [!NOTE]  
>  Ab Windows XP und Windows Server 2003 ist ODBC im Windows-Betriebssystem enthalten. Sie sollten ODBC nur explizit auf früheren Windows-Versionen installieren.  
  
 Die Translator-Setup-DLL enthält die **ConfigTranslator-Funktion,** die die Standardoption für einen Übersetzer zurückgibt. Bei Bedarf wird der Benutzer aufgefordert, diese Informationen einzugeben. Eine vollständige Beschreibung dieser Funktion finden Sie unter [Setup-DLL-API-Referenz](../../../odbc/reference/syntax/setup-dll-api-reference.md).  
  
 Die Übersetzer-Setup-DLL wird vom Übersetzer-Entwickler geschrieben. Es kann Teil der Übersetzer-DLL oder einer separaten DLL sein.
