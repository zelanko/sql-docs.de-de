---
description: Versionsnummer
title: Versionsnummer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- version number supported [ODBC]
- interoperability [ODBC], version number supported
ms.assetid: 6eccacdf-b837-4b66-bd48-ba31771acecb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 86da481ef7854bb9878c2bac565ef2797b61f5ab
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421424"
---
# <a name="version-number"></a>Versionsnummer
Es gibt mehrere Versionen von ODBC, die jeweils über unterschiedliche Features verfügen. Eine Anwendung bestimmt, welche ODBC-Version der Treiber-Manager und ein bestimmter Treiber durch Aufrufen von **SQLGetInfo** mit den Optionen SQL_ODBC_VER und SQL_DRIVER_ODBC_VER unterstützen.
