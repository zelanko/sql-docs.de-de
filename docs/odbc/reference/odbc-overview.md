---
title: ODBC Übersicht | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0a0515a882cd7d1c97a60e9262942bd7c397b0b2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298290"
---
# <a name="odbc-overview"></a>Übersicht über ODBC
Die Open Database Connectivity (ODBC) ist eine weit verbreitete Anwendungsprogrammierschnittstelle (API) für Datenbankzugriff. Es basiert auf den CLI-Spezifikationen (Call-Level Interface) von Open Group und ISO/IEC für Datenbank-APIs und verwendet Structured Query Language (SQL) als Datenbankzugriffssprache.  
  
 ODBC ist für maximale *Interoperabilität* ausgelegt, d. h. die Fähigkeit einer einzelnen Anwendung, auf verschiedene Datenbankverwaltungssysteme (DbMS) mit demselben Quellcode zuzugreifen. Datenbankanwendungen rufen Funktionen in der ODBC-Schnittstelle auf, die in datenbankspezifischen Modulen implementiert sind, die als *Treiber*bezeichnet werden. Die Verwendung von Treibern isoliert Anwendungen von datenbankspezifischen Aufrufen auf die gleiche Weise wie Druckertreiber Textverarbeitungsprogramme von druckerspezifischen Befehlen isolieren. Da Treiber zur Laufzeit geladen werden, muss ein Benutzer nur einen neuen Treiber hinzufügen, um auf ein neues DBMS zuzugreifen. Es ist nicht erforderlich, die Anwendung neu zu kompilieren oder neu zu verknüpfen.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Warum wurde ODBC erstellt?](../../odbc/reference/why-was-odbc-created.md)  
  
-   [Was ist ODBC?](../../odbc/reference/what-is-odbc.md)  
  
-   [ODBC und die Standard-CLI](../../odbc/reference/odbc-and-the-standard-cli.md)
