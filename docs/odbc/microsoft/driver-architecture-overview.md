---
description: Übersicht über die Treiberarchitektur
title: Übersicht über die Treiberarchitektur | Microsoft-Dokumentation
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
ms.openlocfilehash: d71a2c28825ee8c7d4e12e047234f3e336b339e0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466442"
---
# <a name="driver-architecture-overview"></a>Übersicht über die Treiberarchitektur
Der Microsoft Visual FoxPro-ODBC-Treiber ist ein 32-Bit-Treiber, der es Ihnen ermöglicht, eine Microsoft Visual FoxPro-Datenbank oder FoxPro-Tabellen über die Open Database Connectivity (ODBC)-Schnittstelle zu öffnen und abzufragen. Sie können mit den folgenden Anwendungs Typen auf FoxPro-Daten zugreifen:  
  
-   Eine Microsoft Office Anwendung, z. b. Microsoft Excel oder Microsoft Word, die Microsoft Query für die Kommunikation mit ODBC verwendet.  
  
-   Eine in Microsoft Visual C++ oder C geschriebene Anwendung, die die ODBC SDK-API verwendet.  
  
-   Eine Anwendung, die in Microsoft Visual Basic oder Microsoft Visual Basic for Applications geschrieben wurde.  
  
 In jedem Fall wird für die Informationsanforderung die ODBC-API verwendet. Der ODBC-Treiber-Manager verwendet den Visual FoxPro-ODBC-Treiber, um Daten aus FoxPro-Tabellen und-Datenbanken zu öffnen und abzurufen.  
  
 Die Architektur wird im folgenden Diagramm dargestellt:  
  
 ![Zeigt die ODBC-Treiberarchitektur](../../odbc/microsoft/media/vfparch.gif "vfparser")  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Visual FoxPro-Terminologie](../../odbc/microsoft/visual-foxpro-terminology.md)  
  
-   [Installieren und Konfigurieren des Visual FoxPro-ODBC-Treibers](../../odbc/microsoft/installing-and-configuring.md)  
  
-   [Verwenden des Visual FoxPro-ODBC-Treibers](../../odbc/microsoft/using-the-visual-foxpro-odbc-driver.md)
