---
title: Abrufen von Deskriptorhandles | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], retrieving or setting field values
ms.assetid: 936f983f-c7e9-43f3-97ea-dd4b1bbf4654
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8bfa0b36ecca3af655efde84c3ce3f22ab0c1f88
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68086307"
---
# <a name="obtaining-descriptor-handles"></a>Abrufen von Deskriptorhandles
Eine Anwendung erhält das Handle des beliebige explizit zugewiesene Deskriptoren als ausgabeargument des Aufrufs von **SQLAllocHandle**. Das Handle für einen implizit zugewiesene Deskriptor wird abgerufen, durch den Aufruf **SQLGetStmtAttr**.
