---
title: Blockieren von Blockcursor, scrollbare Cursor und Abwärtskompatibilität | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 66b4cf0ce2b2ffc15a9e450461021a9b20b1f0c3
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2019
ms.locfileid: "67794132"
---
# <a name="block-cursors-scrollable-cursors-and-backward-compatibility"></a>Blockcursor, scrollbarer Cursor und Abwärtskompatibilität
Das Vorhandensein sowohl **SQLFetchScroll** und **SQLExtendedFetch** darstellt, die erste Klartext geteilt werden, in ODBC zwischen der Schnittstelle API (Application Programming), die den Satz von Funktionen ist die Anwendungsaufrufe und der Service Provider-Schnittstelle (SPI), wird der Satz von Funktionen der Treiber implementiert. Diese Auftrennung ist erforderlich, damit ODBC *3.x*, verwendet **SQLFetchScroll**, Bealigned mit den Standards und auch mit dem ODBC-kompatibel sein *2.x*, verwendet**SQLExtendedFetch**.  
  
 Die ODBC *3.x* -API, die ist der Satz von Funktionen, die Anwendung ruft, umfasst **SQLFetchScroll** und zugehörigen Anweisungsattribute. Die ODBC *3.x* SPI, den Satz von Funktionen der Treiber implementiert wird, enthält **SQLFetchScroll**, **SQLExtendedFetch**, und zugehörigen Anweisungsattribute. Da es sich bei ODBC diese Auftrennung zwischen der API und der SPI formal nicht erzwingt, ist es möglich, für ODBC *3.x* aufrufen, **SQLExtendedFetch** und zugehörigen Anweisungsattribute. Allerdings besteht kein Grund für ODBC *3.x* Anwendung dazu. Weitere Informationen zu APIs und SPIs, finden Sie unter der Einführung zur [ODBC-Architektur](../../../odbc/reference/odbc-architecture.md).  
  
 Für Informationen darüber, welche Funktionen und die Anweisung einen ODBC-Attribute *3.x* Anwendung sollte mit Blocks und bildlauffähigen Cursor verwenden, finden Sie unter [Blockcursor, scrollbare Cursor und Abwärtskompatibilität für ODBC 3.x Anwendungen](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md).  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [What the Driver Manager Does (Was der Treibermanager tut)](../../../odbc/reference/appendixes/what-the-driver-manager-does.md)  
  
-   [What the Driver Does (Was der Treiber tut)](../../../odbc/reference/appendixes/what-the-driver-does.md)
