---
title: Datentrunkerkennung mit ExtendedAnsiSQL aktiviert | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- truncating data [ODBC]
- extendedANSISQL [ODBC], data truncation detection
ms.assetid: cec2359b-917d-4e1d-9625-5cd678b62f10
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ae1aa7a8a8b9ea2c3f3054717546506e660d5270
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280697"
---
# <a name="data-truncation-detection-enabled-using-extendedansisql"></a>Erkennen einer Datenabschneidung bei aktiviertem ExtendedAnsiSQL
Wenn das ExtendedAnsiSQL-Flag aktiviert ist und die Anwendung Daten in eine Zeichen- oder Binärspalte einfügt und Daten abgeschnitten werden, wird die Kürzung erkannt. Wenn das ExtendedAnsiSQL-Flag deaktiviert ist, werden die Daten ohne Warnung abgeschnitten, wie es in früheren Versionen der ODBC Desktop-Datenbanktreiber der Fall war.
