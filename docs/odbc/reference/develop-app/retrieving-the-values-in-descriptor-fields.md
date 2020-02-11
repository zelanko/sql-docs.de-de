---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 55d7017c659ca4d0b8094ed4a665d27c10b355f7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68020451"
---
# <a name="retrieving-the-values-in-descriptor-fields"></a>Abrufen der Werte in Deskriptorfeldern
Eine Anwendung kann **SQLGetDescField** aufrufen, um ein einzelnes Feld eines deskriptordaten Satzes abzurufen. **SQLGetDescField** ermöglicht der Anwendung den Zugriff auf alle Deskriptorfelder, die in ODBC definiert sind, sowie auf Treiber definierte Felder.  
  
 **SQLGetDescRec** kann aufgerufen werden, um die Einstellungen mehrerer Deskriptorfelder abzurufen, die sich auf den Datentyp und die Speicherung von Spalten-oder Parameterdaten auswirken.
