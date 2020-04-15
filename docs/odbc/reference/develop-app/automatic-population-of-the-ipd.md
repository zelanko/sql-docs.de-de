---
title: Automatische Besiedlung der IPD | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- automatically populating ipd [ODBC]
- descriptors [ODBC], automatically populating ipd
- descriptors [ODBC], allocating and freeing
- ipd [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 1184a7d8-d557-4140-843b-6633ae6deacc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1998ea1992ee7f14d87d01e348d955b017166088
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285070"
---
# <a name="automatic-population-of-the-ipd"></a>Automatische Auffüllung des IPD
Einige Treiber können die Felder der IPD festlegen, nachdem eine parametrisierte Abfrage vorbereitet wurde. Die Deskriptorfelder werden automatisch mit Informationen über den Parameter aufgefüllt, einschließlich Datentyp, Genauigkeit, Skalierung und anderen Merkmalen. Dies entspricht der Unterstützung von **SQLDescribeParam**. Diese Informationen können für eine Anwendung besonders nützlich sein, wenn sie keine andere Möglichkeit hat, sie zu ermitteln, z. B. wenn eine Ad-hoc-Abfrage mit Parametern ausgeführt wird, von denen die Anwendung nichts weiß.  
  
 Eine Anwendung bestimmt, ob der Treiber die automatische Auffüllung unterstützt, indem **SQLGetConnectAttr** mit einem *Attribut* von SQL_ATTR_AUTO_IPD aufgerufen wird. Wenn SQL_TRUE zurückgegeben wird, unterstützt der Treiber ihn, und die Anwendung kann es aktivieren, indem das Attribut SQL_ATTR_ENABLE_AUTO_IPD-Anweisung auf SQL_TRUE.  
  
 Wenn die automatische Auffüllung unterstützt und aktiviert wird, füllt der Treiber die Felder der IPD auf, nachdem eine SQL-Anweisung mit Parametermarkierungen durch einen Aufruf von **SQLPrepare**vorbereitet wurde. Eine Anwendung kann diese Informationen abrufen, indem sie **SQLGetDescField** oder **SQLGetDescRec**oder **SQLDescribeParam**aufruft. Die Anwendung kann die Informationen verwenden, um den am besten geeigneten Anwendungspuffer für einen Parameter zu binden oder eine Datenkonvertierung für sie anzugeben.  
  
 Die automatische Auffüllung der IPD kann zu einer Leistungseinbußen führen. Eine Anwendung kann sie deaktivieren, indem sie das Attribut SQL_ATTR_ENABLE_AUTO_IPD Anweisung auf SQL_FALSE (Standardwert) zurücksetzt.
