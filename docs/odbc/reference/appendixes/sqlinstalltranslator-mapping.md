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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8ab5ebccaac7ccf6374971c1d21040ad15fb3e55
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300582"
---
# <a name="sqlinstalltranslator-mapping"></a>SQLInstallTranslator-Zuordnung
Wenn eine ODBC *2. x* -Anwendung **sqlinstalltranslator** über einen ODBC *3. x* -Treiber aufruft, ordnet der Treiber-Manager den Aufruf **sqlinstalltranslatorex**zu. Eine Anwendung sollte **sqlinstalltranslator** nicht im ODBC *3. x* -Treiber-Manager aufzurufen, wobei das *lpszinffile* -Argument auf einen anderen Wert als NULL festgelegt ist. Der ODBC. Die in ODBC *2. x* verwendete INF-Datei wird in ODBC *3. x*nicht mehr unterstützt, selbst aus Gründen der Abwärtskompatibilität.
