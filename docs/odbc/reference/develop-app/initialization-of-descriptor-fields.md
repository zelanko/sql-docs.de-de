---
title: Initialisierung von Deskriptorfeldern | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], allocating and freeing
- initializing descriptor fields [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 1da157cb-8ea9-4a56-983b-1c45650217c5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e4ed6479a60f1d0695107c216b2f0c94a55f68ff
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300120"
---
# <a name="initialization-of-descriptor-fields"></a>Initialisierung der Deskriptorfelder
Wenn ein Anwendungszeilendeskriptor zugewiesen wird, erhalten seine Felder Anfangswerte, wie in [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)angegeben. Der Anfangswert des Feldes SQL_DESC_TYPE ist SQL_DEFAULT. Dies sieht eine Standardbehandlung der Datenbankdaten für die Darstellung der Anwendung vor. Die Anwendung kann eine unterschiedliche Behandlung der Daten angeben, indem Sie Felder des Deskriptordatensatzes festlegen.  
  
 Der Anfangswert von SQL_DESC_ARRAY_SIZE im Deskriptorheader ist 1. Die Anwendung kann dieses Feld ändern, um den Mehrzeilenabruf zu aktivieren.  
  
 Das Konzept eines Standardwerts ist für die Felder eines IRD ungültig. Eine Anwendung kann nur dann auf die Felder einer IRD zugreifen, wenn ihr eine vorbereitete oder ausgeführte Anweisung zugeordnet ist.  
  
 Bestimmte Felder einer IPD werden erst definiert, nachdem die IPD automatisch vom Treiber aufgefüllt wurde. Wenn nicht, sind sie nicht definiert. Diese Felder sind SQL_DESC_CASE_SENSITIVE, SQL_DESC_FIXED_PREC_SCALE, SQL_DESC_TYPE_NAME, SQL_DESC_UNSIGNED und SQL_DESC_LOCAL_TYPE_NAME.
