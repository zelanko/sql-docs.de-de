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
manager: craigg
ms.openlocfilehash: 95b7d538c2ace45b42c947b56ca5a5bd5f981ec5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47793648"
---
# <a name="data-truncation-detection-enabled-using-extendedansisql"></a>Erkennen einer Datenabschneidung bei aktiviertem ExtendedAnsiSQL
Wenn das Flag ExtendedAnsiSQL eingeschaltet ist und die Anwendung Daten in einer char- oder binary-Spalte einfügen und Daten werden abgeschnitten, wird das Abschneiden erkannt werden. Wenn das Flag ExtendedAnsiSQL deaktiviert ist, werden ohne Warnung, die Daten abgeschnitten, wie in früheren Versionen von der ODBC-Desktop-Datenbanktreiber.
