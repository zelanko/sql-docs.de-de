---
title: Block Cursor, scrollbare Cursor und Abwärtskompatibilität | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], backward compatibility
- compatibility [ODBC], cursors
- backward compatibility [ODBC], cursors
- block cursors [ODBC]
ms.assetid: d9d271f6-d2d9-49b9-a365-4909ca06caae
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 433647481b2b73c22e00657c430d98177d3d4524
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68125219"
---
# <a name="block-cursors-scrollable-cursors-and-backward-compatibility"></a>Blockcursor, scrollbarer Cursor und Abwärtskompatibilität
Das vorhanden sein von **SQLFetchScroll** und **SQLExtendedFetch** stellt die erste Clear-Teilung in ODBC zwischen der Anwendungsprogrammierschnittstelle (Application Programming Interface, API) dar. dabei handelt es sich um den Satz von Funktionen, den die Anwendung aufruft, und um die Service Provider Interface (SPI), die den Satz von Funktionen darstellt, den der Treiber implementiert. Diese Aufteilung ist erforderlich, damit ODBC *3. x*, das **SQLFetchScroll**verwendet, mit den Standards abgeglichen wird und auch mit ODBC *2. x*kompatibel ist, das **sqlextendecodfetch**verwendet.  
  
 Die ODBC *3. x* -API, d. h. der Satz von Funktionen, die die Anwendung aufruft, umfasst **SQLFetchScroll** und verwandte Anweisungs Attribute. Der ODBC *3. x* SPI, d. h. der Satz von Funktionen, den der Treiber implementiert, umfasst **SQLFetchScroll**, **SQLExtendedFetch**und verwandte Anweisungs Attribute. Da ODBC diese Aufteilung zwischen der API und der SPI nicht formal erzwingt, ist es möglich, dass ODBC *3. x* -Anwendungen **sqlextenentdfetch** und verwandte Anweisungs Attribute aufruft. Hierfür gibt es jedoch keinen Grund für die ODBC *3. x* -Anwendung. Weitere Informationen zu APIs und SPIs finden Sie unter Einführung in die [ODBC-Architektur](../../../odbc/reference/odbc-architecture.md).  
  
 Informationen zu den Funktionen und Anweisungs Attributen, die eine ODBC *3. x* -Anwendung mit Block-und Bild lauffähigen Cursorn verwenden soll, finden Sie unter [Blockcursor, scrollfähige Cursor und Abwärtskompatibilität für ODBC 3. x-Anwendungen](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md).  
  
 Dieser Abschnitt enthält die folgenden Themen:  
  
-   [Funktionen des Treiber-Managers](../../../odbc/reference/appendixes/what-the-driver-manager-does.md)  
  
-   [Funktionen des Treibers](../../../odbc/reference/appendixes/what-the-driver-does.md)
