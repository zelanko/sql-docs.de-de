---
title: Daten abschneide Erkennung mithilfe von extendedansisql aktiviert | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81280697"
---
# <a name="data-truncation-detection-enabled-using-extendedansisql"></a>Erkennen einer Datenabschneidung bei aktiviertem ExtendedAnsiSQL
Wenn das extendedansisql-Flag aktiviert ist und die Anwendung Daten in eine char-oder Binary-Spalte einfügt und die Daten abgeschnitten werden, wird das Abschneiden erkannt. Wenn das extendedansisql-Flag deaktiviert ist, werden die Daten ohne Warnung gekürzt, wie dies in früheren Versionen der ODBC Desktop-Datenbanktreiber der Fall war.
