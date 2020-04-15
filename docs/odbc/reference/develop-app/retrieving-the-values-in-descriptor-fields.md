---
title: Abrufen der Werte in Deskriptorfeldern | Microsoft Docs
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
ms.openlocfilehash: 43467d19f3f2e576efa0402c4ba513e23da59390
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304321"
---
# <a name="retrieving-the-values-in-descriptor-fields"></a>Abrufen der Werte in Deskriptorfeldern
Eine Anwendung kann **SQLGetDescField** aufrufen, um ein einzelnes Feld eines Deskriptordatensatzes abzurufen. **SQLGetDescField** gewährt der Anwendung Zugriff auf alle in ODBC definierten Deskriptorfelder und auch auf treiberdefinierte Felder.  
  
 **SQLGetDescRec** kann aufgerufen werden, um die Einstellungen mehrerer Deskriptorfelder abzurufen, die sich auf den Datentyp und die Speicherung von Spalten- oder Parameterdaten auswirken.
