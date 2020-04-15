---
title: Festlegen des Commit-Modus | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- transactions [ODBC], commit modes
- committing transactions [ODBC]
- commit modes [ODBC]
ms.assetid: b60d0d74-0655-4013-8d5a-bc1866eaa166
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f05aaca2349a612cda7c5b6b257e7a1d5a5ea9c5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299820"
---
# <a name="setting-the-commit-mode"></a>Festlegen des Commitmodus
Anwendungen geben den Transaktionsmodus mit dem SQL_ATTR_AUTOCOMMIT Verbindungsattribut an. Standardmäßig befinden sich ODBC-Transaktionen im Autocommit-Modus (es sei denn, **SQLSetConnectAttr** und **SQLSetConnectOption** werden nicht unterstützt, was unwahrscheinlich ist). Der Wechsel vom manuellen Commit-Modus in den Auto-Commit-Modus überträgt automatisch jede offene Transaktion auf der Verbindung.
