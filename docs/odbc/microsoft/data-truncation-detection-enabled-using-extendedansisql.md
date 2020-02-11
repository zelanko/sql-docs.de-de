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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d7fb67171a796755bf8d6229b9d562f69bd588ed
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68096511"
---
# <a name="data-truncation-detection-enabled-using-extendedansisql"></a>Erkennen einer Datenabschneidung bei aktiviertem ExtendedAnsiSQL
Wenn das extendedansisql-Flag aktiviert ist und die Anwendung Daten in eine char-oder Binary-Spalte einfügt und die Daten abgeschnitten werden, wird das Abschneiden erkannt. Wenn das extendedansisql-Flag deaktiviert ist, werden die Daten ohne Warnung gekürzt, wie dies in früheren Versionen der ODBC Desktop-Datenbanktreiber der Fall war.
