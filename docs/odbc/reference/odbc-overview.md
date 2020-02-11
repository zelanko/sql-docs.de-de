---
title: ODBC-Übersicht | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC]
- ODBC [ODBC], about ODBC
ms.assetid: 233315bd-2b7f-4b20-9978-e920e1ea9a07
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 945ebced0703c109ac64c374e31d2e76b556e7ab
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67944839"
---
# <a name="odbc-overview"></a>Übersicht über ODBC
Die Open Database Connectivity (ODBC) ist eine weit verbreitete Anwendungsprogrammierschnittstelle (API) für Datenbankzugriff. Es basiert auf den CLI-Spezifikationen (calllevel Interface) von Open Group und ISO/IEC für Datenbank-APIs und verwendet strukturierte Abfragesprache (SQL) als Datenbankzugriffs Sprache.  
  
 ODBC ist für maximale *Interoperabilität* konzipiert, d. h. die Fähigkeit einer einzelnen Anwendung, auf unterschiedliche Datenbankverwaltungssysteme (DBMSs) mit demselben Quellcode zuzugreifen. Datenbankanwendungen aufrufen Funktionen in der ODBC-Schnittstelle, die in datenbankspezifischen Modulen implementiert werden, die als *Treiber*bezeichnet werden. Die Verwendung von Treibern isoliert Anwendungen von datenbankspezifischen aufrufen auf die gleiche Weise, wie Druckertreiber Textverarbeitungsprogramme von druckerspezifischen Befehlen isolieren. Da Treiber zur Laufzeit geladen werden, muss ein Benutzer nur einen neuen Treiber hinzufügen, um auf ein neues DBMS zuzugreifen. die Anwendung muss nicht neu kompiliert oder neu verknüpft werden.  
  
 Dieser Abschnitt enthält die folgenden Themen:  
  
-   [Warum wurde ODBC erstellt?](../../odbc/reference/why-was-odbc-created.md)  
  
-   [Was ist ODBC?](../../odbc/reference/what-is-odbc.md)  
  
-   [ODBC und die Standard-CLI](../../odbc/reference/odbc-and-the-standard-cli.md)
