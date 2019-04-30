---
title: SQLInstallTranslator-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLInstallTranslator
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLInstallTranslator
helpviewer_keywords:
- SQLInstallTranslator function [ODBC]
ms.assetid: 453b21ff-3c2b-4069-8ff7-5c727f062d89
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: de493cc42980390fee94ca4d86efc8f5cd40646c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63242307"
---
# <a name="sqlinstalltranslator-function"></a>SQLInstallTranslator-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 2.5, als veraltet markiert  
  
 **Zusammenfassung**  
 In ODBC 3.0 **SQLInstallTranslator** wurde ersetzt durch [SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md). Aufrufe von **SQLInstallTranslator** zugeordnet **SQLInstallTranslatorEx**. Weitere Informationen finden Sie unter **SQLInstallTranslatorEx**.  
  
 **SQLInstallTranslator** gibt "false" zurück, wenn eine Anwendung in die ODBC 3. ruft *.x* Treiber-Manager mit der *LpszInfFile* -Argument auf einen anderen Wert als NULL festgelegt. Die Odbc.inf-Datei, die in ODBC 2. verwendet. *x* wird nicht mehr unterstützt, in ODBC 3.*.x*, dies gilt auch für die Abwärtskompatibilität.
