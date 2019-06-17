---
title: -Dienstanbieter und Komponenten | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- OLE DB providers [ADO]
- ADO, OLE DB providers
- service providers [ADO]
ms.assetid: 1fd7a374-587b-4ca9-9204-3a4019b67a71
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 9bebbf4c89a04474cbf2d0c88704603cb4c3fef3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66700387"
---
# <a name="service-providers-and-components"></a>Dienstanbieter und -komponenten
Dienstanbieter sind Komponenten, die die Funktionalität von Datenanbieter erweitern, durch die Implementierung von erweiterter Schnittstellen, die nicht nativ vom Datenspeicher unterstützt werden.  
  
 Universal Data Access ermöglicht einen *Komponentenarchitektur* , einzelne, spezielle Komponenten zum Implementieren von diskreter Gruppen von Funktionen für Datenbanken oder "Dienste", auf weniger leistungsstarken Speicher ermöglicht. Daher geben Sie Dienstkomponenten anstatt jeden Datenspeicher, eine eigene Implementierung der erweiterten Funktionen erzwingen, oder erzwingen allgemeine Anwendungen, Datenbankfunktionalität intern zu implementieren, eine gängige Implementierung, die eine Anwendung kann Verwenden Sie Wenn Sie einen beliebigen Datenspeicher zugreifen. Die Tatsache, dass einige Funktionen systemintern von Datenspeicher und durch allgemeine Komponenten implementiert wird, ist für die Anwendung transparent.  
  
 Z. B. ein Cursor-engine, wie z. B. [der Cursor Service für OLE DB](https://msdn.microsoft.com/57638feb-4ecd-4051-becb-8f828d21cf44), ist eine Dienstkomponente, die Daten aus einem sequenziellen, nur vorwärts gerichteten Datenspeicher bildlauffähigen Daten verwenden. Andere Dienstanbieter, die häufig für ADO verwendeten umfassen die [Microsoft OLE DB-Persistenz-Anbieter (ADO-Dienstanbieter)](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md) (zum Speichern von Daten in eine Datei), die [Microsoft Data Shaping Service für OLE DB (ADO-Dienstanbieter) ](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) (für hierarchische **Recordsets**), und die [Microsoft OLE DB Remoting-Anbieter (ADO-Dienstanbieter)](../../../ado/guide/appendixes/microsoft-ole-db-remoting-provider-ado-service-provider.md) (zum Aufrufen von Datenanbieter auf einem Remotecomputer).  
  
 Weitere Informationen zu Dienst- und Anbietern finden Sie unter [Anhang A: Anbieter](../../../ado/guide/appendixes/appendix-a-providers.md).
