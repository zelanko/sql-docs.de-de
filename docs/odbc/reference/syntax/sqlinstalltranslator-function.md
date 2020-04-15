---
title: SQLInstallTranslator-Funktion | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300320"
---
# <a name="sqlinstalltranslator-function"></a>SQLInstallTranslator-Funktion
**Konformität**  
 Eingeführte Version: ODBC 2.5, Veraltet  
  
 **Zusammenfassung**  
 In ODBC 3.0 wurde **SQLInstallTranslator** durch [SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)ersetzt. Aufrufe von **SQLInstallTranslator** werden **SQLInstallTranslatorEx**zugeordnet. Weitere Informationen finden Sie unter **SQLInstallTranslatorEx**.  
  
 **SQLInstallTranslator** gibt FALSE zurück, wenn eine Anwendung sie im ODBC *3.x-Treiber-Manager* aufruft, wobei das Argument *lpszInfFile* auf einen anderen Wert als NULL festgelegt ist. Die odbc.inf-Datei, die in ODBC *2.x* verwendet wird, wird in ODBC *3.x*nicht mehr unterstützt, auch aus Gründen der Abwärtskompatibilität.
