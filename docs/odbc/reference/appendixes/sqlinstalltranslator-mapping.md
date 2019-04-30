---
title: SQLInstallTranslator-Zuordnung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLInstallTranslator function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLInstallTranslator
ms.assetid: bcd9ba4f-7834-4bc4-876e-c7478998e524
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9760bfad769e9508d58d1cd00f98376dbd13d877
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63298510"
---
# <a name="sqlinstalltranslator-mapping"></a>SQLInstallTranslator-Zuordnung
Wenn eine ODBC-2. *x* Anwendungsaufrufe **SQLInstallTranslator** über einen ODBC 3.*.x* Treiber, der Treiber-Manager ordnet den Aufruf von **SQLInstallTranslatorEx**. Eine Anwendung sollte nicht aufrufen **SQLInstallTranslator** in die ODBC 3.*.x* Treiber-Manager mit der *LpszInfFile* -Argument auf einen anderen Wert als NULL festgelegt. Die ODBC. In ODBC 2. verwendeten INF-Datei. *x* wird nicht mehr unterstützt, in ODBC 3.*.x*, dies gilt auch für die Abwärtskompatibilität.
