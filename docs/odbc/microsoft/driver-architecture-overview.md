---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 833c953df3502eb7e5d5676da8df057734174619
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68071923"
---
# <a name="driver-architecture-overview"></a>Übersicht über die Treiberarchitektur
Der Microsoft Visual FoxPro-ODBC-Treiber ist ein 32-Bit-Treiber, der es Ihnen ermöglicht, eine Microsoft Visual FoxPro-Datenbank oder FoxPro-Tabellen über die Open Database Connectivity (ODBC)-Schnittstelle zu öffnen und abzufragen. Sie können mit den folgenden Anwendungs Typen auf FoxPro-Daten zugreifen:  
  
-   Eine Microsoft Office Anwendung, z. b. Microsoft Excel oder Microsoft Word, die Microsoft Query für die Kommunikation mit ODBC verwendet.  
  
-   Eine in Microsoft Visual C++ oder C geschriebene Anwendung, die die ODBC SDK-API verwendet.  
  
-   Eine Anwendung, die in Microsoft Visual Basic oder Microsoft Visual Basic for Applications geschrieben wurde.  
  
 In jedem Fall wird für die Informationsanforderung die ODBC-API verwendet. Der ODBC-Treiber-Manager verwendet den Visual FoxPro-ODBC-Treiber, um Daten aus FoxPro-Tabellen und-Datenbanken zu öffnen und abzurufen.  
  
 Die Architektur wird im folgenden Diagramm dargestellt:  
  
 ![Zeigt die ODBC-Treiberarchitektur](../../odbc/microsoft/media/vfparch.gif "vfparser")  
  
 Dieser Abschnitt enthält die folgenden Themen:  
  
-   [Visual FoxPro-Terminologie](../../odbc/microsoft/visual-foxpro-terminology.md)  
  
-   [Installieren und Konfigurieren des Visual FoxPro-ODBC-Treibers](../../odbc/microsoft/installing-and-configuring.md)  
  
-   [Verwenden des Visual FoxPro-ODBC-Treibers](../../odbc/microsoft/using-the-visual-foxpro-odbc-driver.md)
