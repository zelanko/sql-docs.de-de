---
title: Automatische Auffüllung des IPD | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3d127e2da3397e96059c7d04305a983766ca1db6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63198337"
---
# <a name="automatic-population-of-the-ipd"></a>Automatische Auffüllung des IPD
Einige Treiber können mit der die Felder des IPD festlegen, nachdem eine parametrisierte Abfrage vorbereitet wurde. Die deskriptorfelder sind automatisch mit Informationen über den Parameter, einschließlich der Datentyp, Genauigkeit, Dezimalstellen und andere Eigenschaften aufgefüllt. Dies ist gleichbedeutend mit Unterstützung von **SQLDescribeParam**. Diese Informationen können besonders nützlich, um eine Anwendung sein, wenn es keine andere Möglichkeit zum Ermitteln besitzt, wie z. B. wenn eine ad-hoc-Abfrage mit Parametern ausgeführt wird, die die Anwendung nicht kennt.  
  
 Eine Anwendung bestimmt, ob der Treiber unterstützt die automatischen Auffüllung durch Aufrufen von **SQLGetConnectAttr** mit einer *Attribut* von SQL_ATTR_AUTO_IPD. SQL_TRUE zurückgegeben wird, wird der Treiber unterstützt, und die Anwendung kann durch Festlegen der SQL_ATTR_ENABLE_AUTO_IPD-Anweisungsattribut auf SQL_TRUE aktivieren.  
  
 Wenn automatischer Auffüllung unterstützt und aktiviert ist, füllt der Treiber die Felder des IPD, nachdem eine SQL-Anweisung, die parametermarkierungen, durch einen Aufruf von vorbereitet wurde **SQLPrepare**. Eine Anwendung kann diese Informationen abrufen, durch den Aufruf **SQLGetDescField** oder **SQLGetDescRec**, oder **SQLDescribeParam**. Die Anwendung können die Informationen zu den am besten geeigneten Anwendungspuffer für einen Parameter zu binden oder eine Datenkonvertierung angeben.  
  
 Automatischer Auffüllung des IPD kann es sich um eine Leistungseinbuße führen. Eine Anwendung kann diese Eigenschaft deaktivieren, wenn Sie das SQL_ATTR_ENABLE_AUTO_IPD-Anweisungsattribut auf SQL_FALSE (Standardwert) zurücksetzen.
