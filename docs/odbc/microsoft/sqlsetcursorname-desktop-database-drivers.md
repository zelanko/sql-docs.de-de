---
title: SQLSetCursorName (Desktop-Datenbanktreiber) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetCursorName function [ODBC], Desktop Database Drivers
ms.assetid: 9bd7c87b-d99d-4e23-b2db-868d3b461c94
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5d618a7f845a87394c2fc3c7978a7aef5716e21f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301481"
---
# <a name="sqlsetcursorname-desktop-database-drivers"></a>SQLSetCursorName (Desktop-Datenbanktreiber)
Da der Treiber keine positionierte Aktualisierung oder Löschung durch die WHERE CURRENT OF *Cursorname-Syntax* unterstützt, **wird SQLSetCursorName** unterstützt, kann jedoch nicht für positionierte Aktualisierungen verwendet werden. Sie kann nur verwendet werden, wenn die Cursorbibliothek aktiviert ist und die Anwendung **SQLExtendedFetch**verwendet.
