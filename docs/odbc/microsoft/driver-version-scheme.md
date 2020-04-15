---
title: Treiberversionsschema | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], versions
ms.assetid: e4a8d9d7-8aba-48ab-8be6-1a6129adfb8f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 864a8bd892315b060fc6fcf42dbe69dfea61ae59
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303451"
---
# <a name="driver-version-scheme"></a>Treiberversionsschema
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 In der folgenden Tabelle sind alle veröffentlichten Versionen des Microsoft ODBC-Treibers für Oracle aufgeführt.  
  
|Treiberversion|Buildnummer|Verfügbarkeitsverlauf|  
|--------------------|------------------|--------------------------|  
|1.0|2.00.6235|Visual C++ 4.2 und Visual Basic 5.0, Enterprise Edition|  
|2.0|2.73.7269|Visual Studio 97 und MDAC 1.5a|  
|2.0 aktualisiert|2.73.7283.01|IIS 4.0|  
|2.0 aktualisiert|2.73.7283.03|MDAC 1.5b und 1.5c|  
|2.0 aktualisiert|2.73.7356|ODBC 3.5 SDK|  
|2.5|2.573.2927|Visual Studio 6.0 und MDAC 2.0|  
|2.5 aktualisiert|2.573.3513|SQL Server 7.0<br /><br /> SQL Server 6.5 SP5|  
  
 Build 2.00.6235 (Version 1) war die erste Version des Microsoft ODBC-Treibers für Oracle. Nach der Veröffentlichung der ersten Version wurde eine neue Namenskonvention angenommen.  
  
 Beispielsweise kann 2.73.7283.03 in die folgenden verschiedenen Komponenten unterteilt werden:  
  
-   2 = Die Versionsnummer.  
  
-   73 = Die Version von Oracle Server, für die der Treiber entwickelt wurde.  
  
-   7283.03 = Die Buildnummer des Treibers.  
  
> [!NOTE]  
>  Mit Release 2.573.2973 hat die Namenskonvention zu einigen Verwirrungen geführt, dass 2.573 eine frühere Version als 2.73 ist, aber jeder Abschnitt der Buildnummer sollte einzeln betrachtet werden. Die Zahl 573 ist größer als 73, also ist es eine neuere Version. Außerdem gibt "2.5" die Versionsnummer des Treibers an.
