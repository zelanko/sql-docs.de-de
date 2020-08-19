---
description: Standardprogrammierschnittstelle
title: Standard Programmierschnittstelle | Microsoft-Dokumentation
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
ms.openlocfilehash: e8fd0e9e3901ea6b3dcf9a09366b13fe532f1198
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88448883"
---
# <a name="standard-programming-interface"></a>Standardprogrammierschnittstelle
Die Programmierschnittstelle ist vielleicht der offensichtlichste Kandidat für die Standardisierung. Tatsächlich wurden bei der Entwicklung von ODBC bereits-ANSI-und ISO-Standards für eingebettete SQL-und SQL-Module bereitgestellt. Obwohl für eine Datenbank-CLI keine Standards vorhanden waren, hat die SQL-Zugriffs Gruppe (ein Branchen Konsortium von Datenbankanbietern) in Erwägung gezogen, ob ein solches erstellt werden sollte. Teile von ODBC wurden später zur Grundlage ihrer Arbeit.  
  
 Eine der Voraussetzungen für ODBC war, dass eine einzelne Anwendungs Binärdatei mit mehreren DBMSs funktionieren musste. Der Grund hierfür ist, dass ODBC keine eingebetteten SQL-oder Modul Sprachen verwendet. Obwohl die Sprache in eingebetteten SQL-und Modul Sprachen standardisiert ist, ist jede an DBMS-spezifische präcompiler gebunden. Daher müssen Anwendungen für jedes DBMS neu kompiliert werden, und die resultierenden Binärdateien können nur mit einem einzelnen DBMS verwendet werden. Dies ist zwar für Anwendungen mit geringem Volumen in der Minicomputer-und Main Frame-Welt akzeptabel, aber in der Welt der persönlichen Computer nicht akzeptabel. Erstens ist es ein logistischer Alptraum, mehrere Versionen von Software mit umfangreichen Volumen und Verkleinerungs umschließenden Software für Kunden bereitzustellen. Zweitens müssen Anwendungen für persönliche Computer häufig gleichzeitig auf mehrere DBMSs zugreifen.  
  
 Auf der anderen Seite kann eine Schnittstelle auf callsebene durch Bibliotheken oder Datenbanktreiber implementiert werden, die sich auf jedem lokalen Computer befinden. für jedes DBMS ist ein anderer Treiber erforderlich. Da moderne Betriebssysteme solche Bibliotheken (z. b. Dynamic Link Libraries auf dem Betriebssystem Microsoft® Windows®) zur Laufzeit laden können, kann eine einzelne Anwendung ohne Neukompilierung auf Daten aus unterschiedlichen DBMSs zugreifen und auch gleichzeitig auf Daten aus mehreren Datenbanken zugreifen. Wenn neue Datenbanktreiber verfügbar werden, können Benutzer diese einfach auf ihren Computern installieren, ohne dass Sie Ihre Datenbankanwendungen ändern, neu kompilieren oder erneut verknüpfen müssen. Außerdem war eine Schnittstelle auf Callcenter-Ebene ein guter Kandidat für ODBC, da Windows-die Plattform, für die ODBC ursprünglich entwickelt wurde, diese Bibliotheken bereits umfassend genutzt hat.
