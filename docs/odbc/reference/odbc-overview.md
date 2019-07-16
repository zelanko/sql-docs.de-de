---
title: Übersicht über die ODBC | Microsoft-Dokumentation
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67944839"
---
# <a name="odbc-overview"></a>Übersicht über ODBC
Open Database Connectivity (ODBC) ist eine weit verbreitete Anwendungsprogrammierschnittstelle (API) für den Datenbankzugriff. Es basiert auf die Call-Level-Interface (CLI)-Spezifikationen von Open Group und ISO/IEC für Datenbank-APIs und verwendet als Sprache für den Zugriff Datenbank (SQL = Structured Query Language).  
  
 ODBC dient für die maximale *Interoperabilität* – d. h. die Möglichkeit einer einzelnen Anwendung auf andere Datenbank-Managementsystemen (DBMS) mit der gleiche Quellcode zugreifen. Datenbankanwendungen Aufrufen von Funktionen in der ODBC-Schnittstelle, die in der Datenbank-smartcardspezifische Module, implementiert werden *Treiber*. Die Verwendung von Treibern isoliert Anwendungen datenbankspezifischen Aufrufe auf die gleiche Weise, Druckertreiber Textverarbeitungsprogramme druckerspezifische Befehle isolieren. Da Treiber zur Laufzeit geladen werden, muss ein Benutzer nur einen neuen Treiber für den Zugriff auf eine neue DBMS hinzufügen; Es ist nicht erforderlich, neu kompilieren oder verknüpfen Sie die Anwendung erneut.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Warum wurde ODBC erstellt?](../../odbc/reference/why-was-odbc-created.md)  
  
-   [Was ist ODBC?](../../odbc/reference/what-is-odbc.md)  
  
-   [ODBC und die Standard-CLI](../../odbc/reference/odbc-and-the-standard-cli.md)
