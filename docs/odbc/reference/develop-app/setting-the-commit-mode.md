---
description: Festlegen des Commitmodus
title: Festlegen des Commitmodus | Microsoft-Dokumentation
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
ms.openlocfilehash: 6a71d6f97f4683f9177c940be7d6ca1cc4a27c01
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494624"
---
# <a name="setting-the-commit-mode"></a>Festlegen des Commitmodus
Anwendungen geben den Transaktionsmodus mit dem SQL_ATTR_AUTOCOMMIT Verbindungs Attribut an. Standardmäßig befinden sich ODBC-Transaktionen im Autocommit-Modus (es sei denn, **SQLSetConnectAttr** und **SQLSetConnectOption** werden nicht unterstützt, was unwahrscheinlich ist). Wenn Sie vom manuellen Commitmodus in den Autocommit-Modus wechseln, wird für alle geöffneten Transaktionen der Verbindung automatisch ein Commit ausgeführt.
