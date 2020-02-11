---
title: Sqlinstalltranslator-Zuordnung | Microsoft-Dokumentation
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
ms.openlocfilehash: 6433df796c88abd7873915266d1a2ca4041a5c62
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68125727"
---
# <a name="sqlinstalltranslator-mapping"></a>SQLInstallTranslator-Zuordnung
Wenn eine ODBC *2. x* -Anwendung **sqlinstalltranslator** über einen ODBC *3. x* -Treiber aufruft, ordnet der Treiber-Manager den Aufruf **sqlinstalltranslatorex**zu. Eine Anwendung sollte **sqlinstalltranslator** nicht im ODBC *3. x* -Treiber-Manager aufzurufen, wobei das *lpszinffile* -Argument auf einen anderen Wert als NULL festgelegt ist. Der ODBC. Die in ODBC *2. x* verwendete INF-Datei wird in ODBC *3. x*nicht mehr unterstützt, selbst aus Gründen der Abwärtskompatibilität.
