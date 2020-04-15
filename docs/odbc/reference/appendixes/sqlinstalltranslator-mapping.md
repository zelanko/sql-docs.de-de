---
title: SQLInstallTranslator-Zuordnung | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300582"
---
# <a name="sqlinstalltranslator-mapping"></a>SQLInstallTranslator-Zuordnung
Wenn eine ODBC *2.x-Anwendung* **SQLInstallTranslator** über einen ODBC *3.x-Treiber* aufruft, ordnet der Treiber-Manager den Aufruf **SQLInstallTranslatorEx**zu. Eine Anwendung sollte **SQLInstallTranslator** im ODBC *3.x-Treiber-Manager* nicht aufrufen, wobei das Argument *lpszInfFile* auf einen anderen Wert als NULL festgelegt ist. Die ODBC. InF-Datei in ODBC *2.x* verwendet wird nicht mehr in ODBC *3.x*unterstützt, auch aus Gründen der Abwärtskompatibilität.
