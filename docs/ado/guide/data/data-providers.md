---
title: Datenanbieter | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data providers [ADO]
- OLE DB providers [ADO]
- ADO, OLE DB providers
ms.assetid: 877b9f25-60c4-4ab6-8052-2c28a3849e89
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 40506ec971782c5e9108a34fd240faabcc2756b2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67925655"
---
# <a name="data-providers"></a>Datenanbieter
Datenanbieter stellen unterschiedliche Datenquellen wie SQL-Datenbanken, indizierte sequenzielle Dateien, Kalkulations Tabellen, Dokument Speicher und e-Mail-Dateien dar. Anbieter machen Daten einheitlich verfügbar, indem eine gängige Abstraktion, die als Rowset bezeichnet wird.  
  
 ADO ist leistungsstark und flexibel, da es eine Verbindung mit einem von mehreren unterschiedlichen Datenanbietern herstellen kann und immer noch dasselbe Programmiermodell verfügbar macht, unabhängig von den spezifischen Features eines beliebigen Anbieters. Da jedoch jeder Datenanbieter eindeutig ist, variiert die Interaktion der Anwendung mit ADO je nach Datenanbieter.  
  
 Beispielsweise unterscheiden sich die Funktionen und Features des OLE DB Anbieters für SQL Server, der für den Zugriff auf Microsoft SQL Server-Datenbanken verwendet wird, erheblich von denen des Microsoft OLE DB-Anbieters für die Internet Veröffentlichung, der für den Zugriff auf Dateispeicher auf einem Webserver verwendet wird.
