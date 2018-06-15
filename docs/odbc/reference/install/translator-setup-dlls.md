---
title: Konvertierer Setup DLLs | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- translator setup DLL [ODBC]
ms.assetid: b3ca79e9-01b9-4541-81de-bbbad24ca736
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 65eca03533940a50a169a948021342f71a032153
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "32915645"
---
# <a name="translator-setup-dlls"></a>Konvertierer-Setup-DLLs
> [!NOTE]  
>  Ab Windows XP und Windows Server 2003, ist ODBC in der Windows-Betriebssystem enthalten. Sie sollten nur explizit ODBC in früheren Versionen von Windows installieren.  
  
 Das Konvertierungsprogramm-Setup-DLL enthält die **ConfigTranslator** Funktion, die die Standardoption für ein Konvertierungsprogramm zurückgibt. Falls erforderlich, wird diese Informationen vom Benutzer zur Eingabe aufgefordert. Eine vollständige Beschreibung dieser Funktion, finden Sie unter [Setup DLL-API-Referenz](../../../odbc/reference/syntax/setup-dll-api-reference.md).  
  
 Das Konvertierungsprogramm-Setup wird vom Entwickler Konvertierer DLL geschrieben. Teil des Konvertierungsprogramms möglich DLL oder eine separate DLL.
