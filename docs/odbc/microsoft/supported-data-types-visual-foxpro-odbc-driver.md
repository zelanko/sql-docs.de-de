---
title: Unterstützte Datentypen (Visual FoxPro-ODBC-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], data types
- FoxPro ODBC driver [ODBC], data types
- data types [ODBC], Visual FoxPro ODBC driver
ms.assetid: ab529cc6-d157-4b35-b6f9-6ffd09af098c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3fc28464a7c14f9801473cc125b0e90c50247d68
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301100"
---
# <a name="supported-data-types-visual-foxpro-odbc-driver"></a>Unterstützte Datentypen (Visual FoxPro-ODBC-Treiber)
Die Liste der Datentypen, die vom Treiber unterstützt werden, wird über die ODBC-API und die Microsoft-Abfrage angezeigt.  
  
## <a name="data-types-in-c-applications"></a>Datentypen in C-Anwendungen  
 Sie können eine Liste der vom Visual FoxPro-ODBC-Treiber unterstützten Datentypen abrufen, indem Sie die [SQLGetTypeInfo](../../odbc/microsoft/sqlgettypeinfo-visual-foxpro-odbc-driver.md) -Funktion in C-oder C++-Anwendungen verwenden.  
  
## <a name="data-types-in-applications-using-microsoft-query"></a>Datentypen in Anwendungen, die Microsoft Query verwenden  
 Wenn Ihre Anwendung Microsoft Query verwendet, um eine neue Tabelle für eine Visual FoxPro-Datenquelle zu erstellen, zeigt Microsoft Query das Dialogfeld **neue Tabellen Definition** an. Unter **Feld Beschreibung**listet das Feld **Typ** die von einzelnen Zeichen dargestellten [Visual FoxPro-Feld Datentypen](../../odbc/microsoft/visual-foxpro-field-data-types.md)auf.
