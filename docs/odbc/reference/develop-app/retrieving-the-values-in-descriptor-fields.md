---
description: Abrufen der Werte in Deskriptorfeldern
title: Abrufen der Werte in Deskriptorfeldern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], retrieving or setting field values
ms.assetid: c05b180f-c2b0-437b-8d1c-ce7f4da93287
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a2118efe58b076287dd75192de679bdb74299435
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494648"
---
# <a name="retrieving-the-values-in-descriptor-fields"></a>Abrufen der Werte in Deskriptorfeldern
Eine Anwendung kann **SQLGetDescField** aufrufen, um ein einzelnes Feld eines deskriptordaten Satzes abzurufen. **SQLGetDescField** ermöglicht der Anwendung den Zugriff auf alle Deskriptorfelder, die in ODBC definiert sind, sowie auf Treiber definierte Felder.  
  
 **SQLGetDescRec** kann aufgerufen werden, um die Einstellungen mehrerer Deskriptorfelder abzurufen, die sich auf den Datentyp und die Speicherung von Spalten-oder Parameterdaten auswirken.
