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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68071923"
---
# <a name="driver-architecture-overview"></a>Übersicht über die Treiberarchitektur
Die Microsoft Visual FoxPro-ODBC-Treiber ist eine 32-Bit-Treiber, der Sie öffnen und eine Microsoft Visual FoxPro-Datenbank oder FoxPro-Tabellen über die öffnen Database Connectivity (ODBC)-Schnittstelle Abfragen ermöglicht. Sie können mithilfe der folgenden Arten von Anwendungen FoxPro-Daten zugreifen:  
  
-   Microsoft Office-Anwendung, z. B. Microsoft Excel oder Microsoft Word, Microsoft Query für die Kommunikation mit ODBC verwendet.  
  
-   Eine Anwendung, geschrieben in Microsoft Visual C++ oder C#, die die ODBC-SDK-API verwendet.  
  
-   Eine Anwendung, die in Microsoft Visual Basic oder Microsoft Visual Basic for Applications geschrieben wird.  
  
 In jedem Fall verwendet die Anforderung von Informationen über die ODBC-API. Der ODBC-Treiber-Manager arbeitet mit der Visual FoxPro-ODBC-Treiber öffnen und das Abrufen von Daten aus Datenbanken und FoxPro-Tabellen.  
  
 Die Architektur wird in der folgenden Abbildung dargestellt:  
  
 ![Zeigt die ODBC-Treiberarchitektur](../../odbc/microsoft/media/vfparch.gif "Vfparch")  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Visual FoxPro-Terminologie](../../odbc/microsoft/visual-foxpro-terminology.md)  
  
-   [Installieren und Konfigurieren des Visual FoxPro-ODBC-Treibers](../../odbc/microsoft/installing-and-configuring.md)  
  
-   [Verwenden des Visual FoxPro-ODBC-Treibers](../../odbc/microsoft/using-the-visual-foxpro-odbc-driver.md)
