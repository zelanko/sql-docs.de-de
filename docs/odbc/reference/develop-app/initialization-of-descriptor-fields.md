---
title: Initialisierung von Deskriptorfeldern | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c78162bcf0421fee609abe5fcacf9613e0f8020b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68138939"
---
# <a name="initialization-of-descriptor-fields"></a>Initialisierung der Deskriptorfelder
Wenn ein Anwendungs Zeilen Deskriptor zugeordnet wird, empfangen seine Felder Anfangswerte, wie in [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)angegeben. Der Anfangswert des SQL_DESC_TYPE Felds ist SQL_DEFAULT. Dies ermöglicht eine Standardbehandlung von Datenbankdaten zur Darstellung der Anwendung. Die Anwendung kann eine andere Behandlung der Daten angeben, indem Felder des deskriptordaten Satzes festgelegt werden.  
  
 Der Anfangswert von SQL_DESC_ARRAY_SIZE im deskriptorheader ist 1. Die Anwendung kann dieses Feld ändern, um das Abrufen mehrerer Zeilen zu aktivieren.  
  
 Das Konzept eines Standardwerts ist für die Felder eines IRD ungültig. Eine Anwendung kann nur dann auf die Felder eines IRD zugreifen, wenn eine vorbereitete oder ausgeführte-Anweisung zugeordnet ist.  
  
 Bestimmte Felder einer IPD werden nur definiert, nachdem die IPD vom Treiber automatisch aufgefüllt wurde. Wenn dies nicht der Fall ist, sind Sie nicht definiert. Diese Felder sind SQL_DESC_CASE_SENSITIVE, SQL_DESC_FIXED_PREC_SCALE, SQL_DESC_TYPE_NAME, SQL_DESC_UNSIGNED und SQL_DESC_LOCAL_TYPE_NAME.
