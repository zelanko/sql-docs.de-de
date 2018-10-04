---
title: Die ODBC-Cursorbibliothek | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a85868cf22fa6d385c3bf75261e0f1cd54e4e1d0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47727374"
---
# <a name="the-odbc-cursor-library"></a>Die ODBC-Cursorbibliothek
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen und Änderung von Anwendungen, die derzeit auf dieses Feature verwenden möchten. Microsoft empfiehlt die Verwendung von Cursor-Funktionalität des Treibers.  
  
 Blocks und bildlauffähigen Cursorn sind sehr nützliche Ergänzungen für viele Anwendungen. Allerdings unterstützen nicht alle Treiber Blocks und bildlauffähigen Cursorn. Dasselbe gilt für positioniertes Update und delete-Anweisungen und **SQLSetPos**, werden die in das Aktualisieren von Daten erläutert. Aus diesem Grund enthält die ODBC-Komponente des Windows SDK, war früher in der Microsoft Data Access Components (MDAC)-SDK, enthalten eine Cursorbibliothek. Die Cursorbibliothek implementiert werden, blockieren, statische Cursor, positioniertes Update und Delete-Anweisungen und **SQLSetPos** für alle Treiber, die die Open Group-Standard-CLI-Standards erfüllt. Die Cursorbibliothek kann ODBC-Anwendungen verteilt werden. sehen Sie den Lizenzvertrag im SDK für Weitere Informationen.  
  
 Um die Cursorbibliothek verwenden, setzt eine Anwendung das SQL_ATTR_ODBC_CURSORS-Verbindungsattribut, bevor er eine Verbindung mit der Datenquelle herstellt. Weitere Informationen über die Cursorbibliothek finden Sie unter [Anhang F: ODBC-Cursorbibliothek](../../../odbc/reference/appendixes/appendix-f-odbc-cursor-library.md).
