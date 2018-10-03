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
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47831384"
---
# <a name="sqlinstalltranslator-mapping"></a>SQLInstallTranslator-Zuordnung
Wenn eine ODBC-2. *x* Anwendungsaufrufe **SQLInstallTranslator** über einen ODBC 3.*.x* Treiber, der Treiber-Manager ordnet den Aufruf von **SQLInstallTranslatorEx**. Eine Anwendung sollte nicht aufrufen **SQLInstallTranslator** in die ODBC 3.*.x* Treiber-Manager mit der *LpszInfFile* -Argument auf einen anderen Wert als NULL festgelegt. Die ODBC. In ODBC 2. verwendeten INF-Datei. *x* wird nicht mehr unterstützt, in ODBC 3.*.x*, dies gilt auch für die Abwärtskompatibilität.
