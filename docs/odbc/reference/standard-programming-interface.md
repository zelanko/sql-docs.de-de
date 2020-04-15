---
title: Standard-Programmierschnittstelle | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC], database access
- SQL [ODBC], database access
- database access [ODBC]
- standardizing database access [ODBC], programming interface
- programming interface standardization [ODBC]
ms.assetid: a2fa727e-51f2-4123-ae25-0ee28e611231
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c7767f113d0f70569ce253f0200cd35cb83915a4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81279996"
---
# <a name="standard-programming-interface"></a>Standardprogrammierschnittstelle
Die Programmierschnittstelle ist vielleicht der offensichtlichste Kandidat für die Standardisierung. Tatsächlich haben ANSI und ISO bereits bei der Entwicklung von ODBC Standards für eingebettete SQL- und SQL-Module bereitgestellt. Obwohl es keine Standards für eine Datenbank-CLI gab, überlegte die SQL Access Group - ein Branchenkonsortium von Datenbankanbietern - ob eine datenbankbasierte Gruppe erstellt werden sollte. Teile von ODBC wurden später die Grundlage für ihre Arbeit.  
  
 Eine der Anforderungen für ODBC war, dass eine einzelne Anwendungsbinärdatei mit mehreren DBMS arbeiten musste. Aus diesem Grund verwendet ODBC keine eingebetteten SQL- oder Modulsprachen. Obwohl die Sprache in eingebetteten SQL- und Modulsprachen standardisiert ist, ist jede Sprache an DBMS-spezifische Vorkompilierer gebunden. Daher müssen Anwendungen für jedes DBMS neu kompiliert werden, und die resultierenden Binärdateien funktionieren nur mit einem einzigen DBMS. Während dies für die Low-Volume-Anwendungen in der Minicomputer- und Mainframe-Welt akzeptabel ist, ist es in der PC-Welt inakzeptabel. Erstens ist es ein logistischer Alptraum, mehrere Versionen von hochvolumiger, schrumpfverpackter Software an Kunden zu liefern; zweitens müssen PC-Anwendungen häufig gleichzeitig auf mehrere DBMS zugreifen.  
  
 Andererseits kann eine Schnittstelle auf Aufrufebene über Bibliotheken oder Datenbanktreiber implementiert werden, die sich auf jedem lokalen Computer befinden. Für jedes DBMS ist ein anderer Treiber erforderlich. Da moderne Betriebssysteme solche Bibliotheken (z. B. Dynamic-Link-Bibliotheken auf dem Microsoft® Windows® Betriebssystem) zur Laufzeit laden können, kann eine einzelne Anwendung ohne Neukompilierung auf Daten aus verschiedenen DBMS und auch auf Daten aus mehreren Datenbanken gleichzeitig zugreifen. Wenn neue Datenbanktreiber verfügbar werden, können Benutzer diese einfach auf ihren Computern installieren, ohne ihre Datenbankanwendungen ändern, neu kompilieren oder neu verknüpfen zu müssen. Darüber hinaus war eine Schnittstelle auf Call-Ebene ein guter Kandidat für ODBC, da Windows - die Plattform, für die ODBC ursprünglich entwickelt wurde - bereits umfangreiche Nutzung solcher Bibliotheken machte.
