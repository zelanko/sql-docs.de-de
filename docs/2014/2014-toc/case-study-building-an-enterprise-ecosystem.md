---
title: 'Fallstudie: aufbauen eines Unternehmens Ökosystems mit Microsoft Dynamics ERP und SQL Server 2014-Replikation für Skalierbarkeit und Leistung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 2b0b5ab7-4e08-431a-bd59-360177c4565c
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a6cc9530b636409864e7e1b72f7417619a0fc8af
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67792470"
---
# <a name="case-study-building-an-enterprise-ecosystem-with-microsoft-dynamics-erp-and-sql-server-2014-replication-for-scalability-and-performance"></a>Fallstudie: Aufbau eines skalierbaren und leistungsfähigen Ökosystems in einem Unternehmen mithilfe von Microsoft Dynamics ERP und SQL Server 2014-Replikation

  **Zusammenfassung:** In diesem Dokument werden die folgenden Szenarien behandelt:  
Verwenden der Transaktions Replikation in SQL Server 2014, um die Transaktionen von Dynamics AX-Clients auf mehrere Knoten zu verteilen. Da die Daten über die Knoten hinweg in Echtzeit verwaltet werden, sorgt die Transaktionsreplikation für Datenredundanz. Dies steigert die Verfügbarkeit unter anderem bei Daten, die für eine effizientere Leistungsanalyse verwendet werden.  
Kennenlernen der Besonderheiten bei der Nutzung der Transaktionsreplikation für die Erstellung hochgradig skalierbarer Ökosysteme für Unternehmen in Microsoft Dynamics ERP. Erzielen Sie hohe Leistung und Skalierbarkeit, ohne die mit AX mitgelieferten Funktionen anpassen zu müssen.  
  
 Die Transaktionsreplikation wird üblicherweise bei Workflows zwischen Servern verwendet, die hohe Durchsätze erfordern. Beispiele hierfür sind: Verbessern der Skalierbarkeit und Verfügbarkeit, Data Warehousing und Berichterstellung, Integrieren von Daten aus mehreren Standorten, Integrieren heterogener Daten und Auslagern der Batchverarbeitung. Dieses Whitepaper beschreibt ein bestimmtes Szenario und zugeordnete Muster, in dem in Microsoft Dynamics ERP die Transaktionsreplikation genutzt wird. Zusätzlich deckt es die Herausforderungen ab, die sich ergeben, wenn die Transaktionsreplikation für den Aufbau unternehmensspezifischer ERP-Lösungen (Enterprise Resource Planning) verwendet werden soll, zeigt bewährte Lösungsmethoden auf und enthält Leistungsanalysen zu verschiedenen Zeitpunkten.  
  
 Die Zielgruppe dieses Whitepapers sind Entwickler, Architekten und Datenbankadministratoren. Es richtet sich an Leser mit grundlegenden Kenntnissen in SQL Server 2008, 2012 oder 2014 sowie Erfahrung als SQL Server-Administrator.  
  
 **Writer:** Prabhakaran "sthuraman" (Prab), Microsoft  
  
 **Technische Reviewer:** Prabhakaran "tenthuraman" (Prab), Microsoft; Santosh padhy, Microsoft; Pavel majstrov, Microsoft; Karthik Sankaranarayanan, Microsoft; Jon Acone, Microsoft; David Stahlkopf, Microsoft; Kent Oldenburger, Microsoft; Mandi Ohlinger, Microsoft; Jason Roth, Microsoft  
  
 **Veröffentlicht:** Oktober 2015  
  
 **Gilt für:** SQL Server 2008, SQL Server 2012 und SQL Server 2014  
  
 Um das Dokument zu lesen, laden Sie das  
        [Fallstudie: aufbauen eines Unternehmens Ökosystems mit Microsoft Dynamics ERP und SQL Server 2014-Replikation für Skalierbarkeit und Leistung](https://download.microsoft.com/download/D/2/0/D20E1C5F-72EA-4505-9F26-FEF9550EFD44/A%20Case%20Study%20Using%20Replication%20to%20Build%20an%20Enterprise%20Ecosystem%20in%20Microsoft%20Dynamics%20ERP%20for%20Scalability%20and%20Performance.docx) Word-Dokument.  
  
  
