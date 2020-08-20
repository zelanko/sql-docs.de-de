---
description: Die ODBC-Cursorbibliothek
title: Die ODBC-Cursor Bibliothek | Microsoft-Dokumentation
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
ms.openlocfilehash: 4e5e3a01633a19c4ae82596ba1e180c64bcce06c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487513"
---
# <a name="the-odbc-cursor-library"></a>Die ODBC-Cursorbibliothek
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Vermeiden Sie die Verwendung dieses Features bei der Entwicklung neuer Anwendungen, und planen Sie das Ändern von Anwendungen, in denen diese Funktion derzeit verwendet wird Microsoft empfiehlt die Verwendung der Cursor-Funktionalität des Treibers.  
  
 Block-und Bild lauffähigen Cursor sind sehr nützliche Ergänzungen für viele Anwendungen. Allerdings unterstützen nicht alle Treiber Block-und scrollfähige Cursor. Das gleiche gilt für positionierte UPDATE-und DELETE-Anweisungen und **SQLSetPos**, die unter Aktualisieren von Daten erläutert werden. Daher enthält die ODBC-Komponente der Windows SDK, die zuvor im Microsoft Data Access Components (MDAC) SDK enthalten war, eine Cursor Bibliothek. Die Cursor Bibliothek implementiert Block-, statische Cursor, positionierte UPDATE-und DELETE-Anweisungen und **SQLSetPos** für jeden Treiber, der den Standard mäßigen CLI-Konformitäts Grad der Open Group-CLI erfüllt. Die Cursor Bibliothek kann mit ODBC-Anwendungen neu verteilt werden. Weitere Informationen finden Sie im Lizenzvertrag im SDK.  
  
 Um die Cursor Bibliothek zu verwenden, legt eine Anwendung das SQL_ATTR_ODBC_CURSORS-Verbindungs Attribut fest, bevor eine Verbindung mit der Datenquelle hergestellt wird. Weitere Informationen zur Cursor Bibliothek finden Sie unter [Anhang F: ODBC-Cursor Bibliothek](../../../odbc/reference/appendixes/appendix-f-odbc-cursor-library.md).
