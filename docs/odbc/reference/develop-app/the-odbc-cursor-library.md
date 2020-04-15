---
title: Die ODBC-Cursorbibliothek | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], about cursor library
- ODBC cursor library [ODBC]
- cursor library [ODBC], about cursor library
- scrollable cursors [ODBC]
- cursors [ODBC], cursor library
- block cursors [ODBC]
ms.assetid: 32fb7df0-953a-4f68-b041-7d2852e45d0f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b243e8ae2dc931830a249d4392da308e68722cdf
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300050"
---
# <a name="the-odbc-cursor-library"></a>Die ODBC-Cursorbibliothek
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Vermeiden Sie es, diese Funktion in neuen Entwicklungsarbeiten zu verwenden, und planen Sie, Anwendungen zu ändern, die diese Funktion derzeit verwenden. Microsoft empfiehlt die Verwendung der Cursorfunktionalität des Treibers.  
  
 Block- und Scrollable-Cursor sind sehr nützliche Ergänzungen zu vielen Anwendungen. Allerdings unterstützen nicht alle Treiber Block- und Scroll-Cursor. Dasselbe gilt für positionierte Aktualisierungs- und Löschanweisungen und **SQLSetPos**, die unter Aktualisieren von Daten erläutert werden. Daher enthält die ODBC-Komponente des Windows SDK, die zuvor im Microsoft Data Access Components (MDAC) SDK enthalten war, eine Cursorbibliothek. Die Cursorbibliothek implementiert Block, statische Cursor, positionierte Aktualisierungs- und Löschanweisungen und **SQLSetPos** für alle Treiber, die die Open Group Standard CLI-Konformitätsstufe erfüllen. Die Cursorbibliothek kann mit ODBC-Anwendungen neu verteilt werden. Weitere Informationen finden Sie in der Lizenzvereinbarung im SDK.  
  
 Um die Cursorbibliothek zu verwenden, legt eine Anwendung das SQL_ATTR_ODBC_CURSORS Verbindungsattribut fest, bevor eine Verbindung mit der Datenquelle hergestellt wird. Weitere Informationen zur Cursorbibliothek finden Sie in [Anhang F: ODBC Cursor Library](../../../odbc/reference/appendixes/appendix-f-odbc-cursor-library.md).
