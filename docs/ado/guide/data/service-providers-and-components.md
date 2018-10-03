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
manager: craigg
ms.openlocfilehash: e4ae286264f4f896fe1b8a36d9c400367bd818dd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47662428"
---
# <a name="service-providers-and-components"></a>Dienstanbieter und -komponenten
Dienstanbieter sind Komponenten, die die Funktionalität von Datenanbieter erweitern, durch die Implementierung von erweiterter Schnittstellen, die nicht nativ vom Datenspeicher unterstützt werden.  
  
 Universal Data Access ermöglicht einen *Komponentenarchitektur* , einzelne, spezielle Komponenten zum Implementieren von diskreter Gruppen von Funktionen für Datenbanken oder "Dienste", auf weniger leistungsstarken Speicher ermöglicht. Daher geben Sie Dienstkomponenten anstatt jeden Datenspeicher, eine eigene Implementierung der erweiterten Funktionen erzwingen, oder erzwingen allgemeine Anwendungen, Datenbankfunktionalität intern zu implementieren, eine gängige Implementierung, die eine Anwendung kann Verwenden Sie Wenn Sie einen beliebigen Datenspeicher zugreifen. Die Tatsache, dass einige Funktionen systemintern von Datenspeicher und durch allgemeine Komponenten implementiert wird, ist für die Anwendung transparent.  
  
 Z. B. ein Cursor-engine, wie z. B. [der Cursor Service für OLE DB](http://msdn.microsoft.com/57638feb-4ecd-4051-becb-8f828d21cf44), ist eine Dienstkomponente, die Daten aus einem sequenziellen, nur vorwärts gerichteten Datenspeicher bildlauffähigen Daten verwenden. Andere Dienstanbieter, die häufig für ADO verwendeten umfassen die [Microsoft OLE DB-Persistenz-Anbieter (ADO-Dienstanbieter)](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md) (zum Speichern von Daten in eine Datei), die [Microsoft Data Shaping Service für OLE DB (ADO-Dienstanbieter) ](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) (für hierarchische **Recordsets**), und die [Microsoft OLE DB Remoting-Anbieter (ADO-Dienstanbieter)](../../../ado/guide/appendixes/microsoft-ole-db-remoting-provider-ado-service-provider.md) (zum Aufrufen von Datenanbieter auf einem Remotecomputer).  
  
 Weitere Informationen zu Dienst- und Anbietern finden Sie unter [Anhang A: Anbieter](../../../ado/guide/appendixes/appendix-a-providers.md).
