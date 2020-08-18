---
description: Erkennen einer Datenabschneidung bei aktiviertem ExtendedAnsiSQL
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
ms.openlocfilehash: 26965093caecbc11e94ef738ba6b8ff757b43258
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88412888"
---
# <a name="data-truncation-detection-enabled-using-extendedansisql"></a>Erkennen einer Datenabschneidung bei aktiviertem ExtendedAnsiSQL
Wenn das extendedansisql-Flag aktiviert ist und die Anwendung Daten in eine char-oder Binary-Spalte einfügt und die Daten abgeschnitten werden, wird das Abschneiden erkannt. Wenn das extendedansisql-Flag deaktiviert ist, werden die Daten ohne Warnung gekürzt, wie dies in früheren Versionen der ODBC Desktop-Datenbanktreiber der Fall war.
