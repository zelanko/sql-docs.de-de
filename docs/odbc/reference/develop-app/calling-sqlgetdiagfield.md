---
description: Aufrufen von SQLGetDiagField
title: Aufrufen von SQLGetDiagField | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application upgrades [ODBC], SQLGetDiagField
- backward compatibility [ODBC], SqlGetDiagField
- upgrading applications [ODBC], SQLGetDiagField
- SQLGetDiagField function [ODBC], calling
- compatibility [ODBC], SQLGetDiagField
ms.assetid: 3c4fb606-b81c-4f11-9820-f0a54e3bc401
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0f579da3c05b541afda21d98c7e9dd72ce5f64e5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494701"
---
# <a name="calling-sqlgetdiagfield"></a>Aufrufen von SQLGetDiagField
Wenn eine ODBC *3. x* -Anwendung **SQLGetDiagField** in einem ODBC *2. x* -Treiber aufruft, gibt der Treiber SQL_SUCCESS und die entsprechenden Informationen in * \* diaginfoptr* zurück, wenn das *DiagIdentifier* -Argument SQL_DIAG_CLASS_ORIGIN, SQL_DIAG_CLASS_SUBCLASS_ORIGIN, SQL_DIAG_CONNECTION_NAME, SQL_DIAG_MESSAGE_TEXT, SQL_DIAG_NATIVE, SQL_DIAG_NUMBER, SQL_DIAG_RETURNCODE, SQL_DIAG_SERVER_NAME oder SQL_DIAG_SQLSTATE ist. Alle anderen Diagnose Felder geben SQL_ERROR zurück.
