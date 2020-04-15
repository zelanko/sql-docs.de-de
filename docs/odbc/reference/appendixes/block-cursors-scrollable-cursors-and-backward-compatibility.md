---
title: Blockieren von Cursorn, scrollbaren Cursorn und Abwärtskompatibilität | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fe24362f1a49577a7fb494f768947080d0ab6e9e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292310"
---
# <a name="block-cursors-scrollable-cursors-and-backward-compatibility"></a>Blockcursor, scrollbarer Cursor und Abwärtskompatibilität
Das Vorhandensein von **SQLFetchScroll** und **SQLExtendedFetch** stellt die erste klare Aufteilung in ODBC zwischen der APPLICATION Programming Interface (API), dem Satz von Funktionen, die die Anwendung aufruft, und der Dienstanbieterschnittstelle (Service Provider Interface, SPI), dem Satz von Funktionen, die der Treiber implementiert, dar. Diese Aufteilung ist notwendig, damit ODBC *3.x*, das **SQLFetchScroll**verwendet, mit den Standards ausgerichtet ist und auch mit ODBC *2.x*kompatibel ist, das **SQLExtendedFetch**verwendet.  
  
 Die ODBC *3.x-API,* die den Satz von Funktionen ist, die die Anwendung aufruft, enthält **SQLFetchScroll** und zugehörige Anweisungsattribute. Der ODBC *3.x* SPI, der Satz von Funktionen, die der Treiber implementiert, enthält **SQLFetchScroll**, **SQLExtendedFetch**und zugehörige Anweisungsattribute. Da ODBC diese Aufteilung zwischen api und SPI formal nicht erzwingt, ist es für ODBC *3.x-Anwendungen* möglich, **SQLExtendedFetch** und zugehörige Anweisungsattribute aufzurufen. Es gibt jedoch keinen Grund für ODBC *3.x-Anwendung,* dies zu tun. Weitere Informationen zu APIs und SPIs finden Sie in der Einführung in [ODBC Architecture](../../../odbc/reference/odbc-architecture.md).  
  
 Informationen darüber, welche Funktionen und Anweisungsattribute eine ODBC *3.x-Anwendung* mit Block- und Scrollable-Cursor verwenden sollte, finden Sie unter [Blockcursor, Scrollable Cursors und Backward Compatibility for ODBC 3.x Applications](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md).  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [What the Driver Manager Does (Was der Treibermanager tut)](../../../odbc/reference/appendixes/what-the-driver-manager-does.md)  
  
-   [What the Driver Does (Was der Treiber tut)](../../../odbc/reference/appendixes/what-the-driver-does.md)
