---
title: Initialisierung der Deskriptorfelder | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: d988099cad357254f04a79a8a6cccbbe4eb2768c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62446811"
---
# <a name="initialization-of-descriptor-fields"></a>Initialisierung der Deskriptorfelder
Wenn ein Anwendungsdienst-Deskriptor Zeile zugeordnet ist, erhalten ihre Felder Anfangswerte gemäß [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). Der anfängliche Wert das SQL_DESC_TYPE-Feld ist SQL_DEFAULT. Dies ist für eine standardmäßige Erläuterung von Daten für die Darstellung der Anwendung. Die Anwendung möglicherweise eine unterschiedliche Behandlung der Daten durch Festlegen der Felder der Deskriptordatensatz angeben.  
  
 Der Anfangswert der SQL_DESC_ARRAY_SIZE im Deskriptor-Header ist 1. Die Anwendung kann dieses Feld zum Aktivieren von mehrzeiligen Abrufvorgang ändern.  
  
 Das Konzept der Standardwert ist für die Felder einer IRD ungültig. Eine Anwendung Zugriff auf die Felder einer IRD nur, wenn eine vorbereitete oder ausgeführte Anweisung, die zugeordnet.  
  
 Erst nach IPD automatisch vom Treiber aufgefüllt wurde, werden bestimmte Felder von einem IPD definiert. Falls nicht, sind sie nicht definiert. Diese Felder sind SQL_DESC_CASE_SENSITIVE, SQL_DESC_FIXED_PREC_SCALE, sql_desc_type_name verwendet wird, SQL_DESC_UNSIGNED und SQL_DESC_LOCAL_TYPE_NAME.
