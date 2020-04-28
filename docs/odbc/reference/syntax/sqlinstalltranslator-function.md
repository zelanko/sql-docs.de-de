---
title: Sqlinstalltranslator-Funktion | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b094aa730fff6db80b9addb63a92bee0f5f85b2a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300320"
---
# <a name="sqlinstalltranslator-function"></a>SQLInstallTranslator-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 2,5, veraltet  
  
 **Zusammenfassung**  
 In ODBC 3,0 wurde **sqlinstalltranslator** durch [sqlinstalltranslatorex](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)ersetzt. **Sqlinstalltranslator** -Aufrufe werden **sqlinstalltranslatorex**zugeordnet. Weitere Informationen finden Sie unter **sqlinstalltranslatorex**.  
  
 **Sqlinstalltranslator** gibt false zurück, wenn eine Anwendung Sie im ODBC *3. x* -Treiber-Manager aufruft, wobei das *lpszinffile* -Argument auf einen anderen Wert als NULL festgelegt ist. Die in ODBC *2. x* verwendete ODBC-INF-Datei wird in ODBC *3. x*nicht mehr unterstützt, selbst aus Gründen der Abwärtskompatibilität.
