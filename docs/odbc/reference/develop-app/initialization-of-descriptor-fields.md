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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e4ed6479a60f1d0695107c216b2f0c94a55f68ff
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300120"
---
# <a name="initialization-of-descriptor-fields"></a>Initialisierung der Deskriptorfelder
Wenn ein Anwendungs Zeilen Deskriptor zugeordnet wird, empfangen seine Felder Anfangswerte, wie in [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)angegeben. Der Anfangswert des SQL_DESC_TYPE Felds ist SQL_DEFAULT. Dies ermöglicht eine Standardbehandlung von Datenbankdaten zur Darstellung der Anwendung. Die Anwendung kann eine andere Behandlung der Daten angeben, indem Felder des deskriptordaten Satzes festgelegt werden.  
  
 Der Anfangswert von SQL_DESC_ARRAY_SIZE im deskriptorheader ist 1. Die Anwendung kann dieses Feld ändern, um das Abrufen mehrerer Zeilen zu aktivieren.  
  
 Das Konzept eines Standardwerts ist für die Felder eines IRD ungültig. Eine Anwendung kann nur dann auf die Felder eines IRD zugreifen, wenn eine vorbereitete oder ausgeführte-Anweisung zugeordnet ist.  
  
 Bestimmte Felder einer IPD werden nur definiert, nachdem die IPD vom Treiber automatisch aufgefüllt wurde. Wenn dies nicht der Fall ist, sind Sie nicht definiert. Diese Felder sind SQL_DESC_CASE_SENSITIVE, SQL_DESC_FIXED_PREC_SCALE, SQL_DESC_TYPE_NAME, SQL_DESC_UNSIGNED und SQL_DESC_LOCAL_TYPE_NAME.
