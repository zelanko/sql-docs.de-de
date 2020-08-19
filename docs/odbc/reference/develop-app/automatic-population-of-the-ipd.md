---
description: Automatische Auffüllung des IPD
title: Automatische Auffüllung der IPD | Microsoft-Dokumentation
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
ms.openlocfilehash: 73c0456f1c78ccc19f1ff55a1ab288baedae2e14
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476882"
---
# <a name="automatic-population-of-the-ipd"></a>Automatische Auffüllung des IPD
Einige Treiber können die Felder der IPD festlegen, nachdem eine parametrisierte Abfrage vorbereitet wurde. Die Deskriptorfelder werden automatisch mit Informationen über den-Parameter aufgefüllt, einschließlich des Datentyps, der Genauigkeit, der Skala und anderer Merkmale. Dies entspricht der Unterstützung von **SQLDescribeParam**. Diese Informationen können für eine Anwendung besonders wertvoll sein, wenn Sie keine andere Möglichkeit hat, Sie zu ermitteln, z. b. Wenn eine Ad-hoc-Abfrage mit Parametern ausgeführt wird, von denen die Anwendung nicht weiß.  
  
 Eine Anwendung bestimmt, ob der Treiber die automatische Auffüllung durch Aufrufen von **SQLGetConnectAttr** mit dem *Attribut* SQL_ATTR_AUTO_IPD unterstützt. Wenn SQL_TRUE zurückgegeben wird, unterstützt der Treiber dies, und die Anwendung kann Sie aktivieren, indem das SQL_ATTR_ENABLE_AUTO_IPD Statement-Attribut auf SQL_TRUE festgelegt wird.  
  
 Wenn die automatische Auffüllung unterstützt und aktiviert wird, füllt der Treiber die Felder der IPD auf, nachdem eine SQL-Anweisung mit Parameter Markierungen durch einen **SQLPrepare**-aufrufungstyp vorbereitet wurde. Eine Anwendung kann diese Informationen durch Aufrufen von **SQLGetDescField** oder **SQLGetDescRec**oder **SQLDescribeParam**abrufen. Die Anwendung kann die Informationen verwenden, um den am besten geeigneten Anwendungs Puffer für einen Parameter zu binden oder eine Datenkonvertierung dafür anzugeben.  
  
 Die automatische Auffüllung der IPD kann zu einer Leistungs Einbuße führen. Eine Anwendung kann Sie ausschalten, indem Sie das SQL_ATTR_ENABLE_AUTO_IPD-Anweisungs Attribut auf SQL_FALSE (den Standardwert) zurücksetzt.
