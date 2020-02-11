---
title: Allgemeine Fehlerüberprüfungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], driver manager error checking
- general error checks [ODBC]
- driver manager [ODBC], error checking
ms.assetid: 0c9a3425-0a7c-48de-9ff6-73601c26283e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f6b7c37febee411571b8ac8316d3800912e35758
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68069922"
---
# <a name="general-error-checks"></a>Überprüfungen auf allgemeine Fehler
Der Treiber-Manager überprüft einen allgemeinen Fehler. Es wird immer SQL_ERROR zurückgegeben, wenn der folgende Fehler auftritt: die Funktion muss vom Treiber unterstützt werden.
