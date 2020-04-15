---
title: Übersicht über die Treiberarchitektur | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], architecture
- FoxPro ODBC driver [ODBC], architecture
ms.assetid: ef5a91cd-158e-40bf-b5a8-8ba535c4705e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cd55290e09fbd35f5a1559ce4209693ef8eaaf73
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303461"
---
# <a name="driver-architecture-overview"></a>Übersicht über die Treiberarchitektur
Der Microsoft Visual FoxPro ODBC-Treiber ist ein 32-Bit-Treiber, mit dem Sie eine Microsoft Visual FoxPro-Datenbank oder FoxPro-Tabellen über die ODBC-Schnittstelle (Open Database Connectivity) öffnen und abfragen können. Sie können auf FoxPro-Daten mit den folgenden Anwendungstypen zugreifen:  
  
-   Eine Microsoft Office-Anwendung, z. B. Microsoft Excel oder Microsoft Word, die Microsoft Query verwendet, um mit ODBC zu kommunizieren.  
  
-   Eine in Microsoft Visual C++ oder C geschriebene Anwendung, die die ODBC SDK-API verwendet.  
  
-   Eine Anwendung, die in Microsoft Visual Basic oder Microsoft Visual Basic for Applications geschrieben wurde.  
  
 In jedem Fall verwendet die Informationsanforderung die ODBC-API. Der ODBC-Treiber-Manager arbeitet mit dem Visual FoxPro ODBC-Treiber zusammen, um Daten aus FoxPro-Tabellen und -Datenbanken zu öffnen und abzurufen.  
  
 Die Architektur wird im folgenden Diagramm dargestellt:  
  
 ![Zeigt die ODBC-Treiberarchitektur an](../../odbc/microsoft/media/vfparch.gif "vfparch")  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Visual FoxPro-Terminologie](../../odbc/microsoft/visual-foxpro-terminology.md)  
  
-   [Installieren und Konfigurieren des Visual FoxPro ODBC-Treibers](../../odbc/microsoft/installing-and-configuring.md)  
  
-   [Verwenden des Visual FoxPro-ODBC-Treibers](../../odbc/microsoft/using-the-visual-foxpro-odbc-driver.md)
