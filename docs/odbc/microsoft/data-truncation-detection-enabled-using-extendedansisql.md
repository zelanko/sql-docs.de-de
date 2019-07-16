---
title: Daten abschneiden Erkennung aktiviert mit ExtendedAnsiSQL | Microsoft-Dokumentation
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68096511"
---
# <a name="data-truncation-detection-enabled-using-extendedansisql"></a>Erkennen einer Datenabschneidung bei aktiviertem ExtendedAnsiSQL
Wenn das Flag ExtendedAnsiSQL eingeschaltet ist und die Anwendung Daten in einer char- oder binary-Spalte einfügen und Daten werden abgeschnitten, wird das Abschneiden erkannt werden. Wenn das Flag ExtendedAnsiSQL deaktiviert ist, werden ohne Warnung, die Daten abgeschnitten, wie in früheren Versionen von der ODBC-Desktop-Datenbanktreiber.
