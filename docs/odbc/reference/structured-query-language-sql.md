---
description: Structured Query Language (SQL) (Structured Query Language, SQL)
title: Strukturierte Abfragesprache (SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL [ODBC]
- SQL [ODBC], about SQL
- ODBC [ODBC], SQL
ms.assetid: bebfd93e-0dc0-46b3-a531-518beb7ea976
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c68f14bd3e1ae5df29f52332d29393bf15c3b665
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88428972"
---
# <a name="structured-query-language-sql"></a>Structured Query Language (SQL) (Structured Query Language, SQL)
Ein typisches DBMS ermöglicht Benutzern das Speichern, zugreifen auf und Ändern von Daten auf eine strukturierte und effiziente Weise. Ursprünglich waren die Benutzer von DBMSs Programmierer. Der Zugriff auf die gespeicherten Daten erforderte das Schreiben eines Programms in eine Programmiersprache wie z. b. COBOL. Obwohl diese Programme oft so geschrieben wurden, dass Sie eine benutzerfreundliche Oberfläche für einen nichttechnischen Benutzer darstellen, erforderte der Zugriff auf die Daten selbst die Dienste eines erfahrenen Programmierers. Der ungezwungene Zugriff auf die Daten war nicht praktikabel.  
  
 Die Benutzer waren in dieser Situation nicht ganz glücklich. Obwohl Sie auf Daten zugreifen konnten, war es oft erforderlich, dass ein DBMS-Programmierer eine spezielle Software schreiben konnte. Wenn z. b. eine Vertriebsabteilung den Gesamtumsatz im vorhergehenden Monat von den einzelnen Vertriebsmitarbeitern anzeigen soll und diese Informationen in der Reihenfolge nach der Dienst Länge der Vertriebsmitarbeiter im Unternehmen anordnen wollte, gab es zwei Möglichkeiten: entweder war bereits ein Programm vorhanden, das auf genau diese Weise auf die Informationen zugreifen konnte, oder die Abteilung musste einen Programmierer bitten, ein solches Programm zu schreiben In vielen Fällen war dies mehr Aufwand als ein Wert, und es war immer eine teure Lösung für einmalige oder Ad-hoc-Abfragen. Da immer mehr Benutzer einen einfachen Zugriff wollten, wurde dieses Problem größer und größer.  
  
 Benutzern den Zugriff auf Daten auf Ad-hoc-Basis zu ermöglichen, müssen Sie eine Sprache angeben, in der Ihre Anforderungen ausgedrückt werden. Eine einzelne Anforderung an eine Datenbank wird als Abfrage definiert. eine solche Sprache wird als Abfragesprache bezeichnet. Zu diesem Zweck wurden viele Abfrage Sprachen entwickelt, aber eine dieser Sprachen wurde zu den beliebtesten: strukturierte Abfragesprache, in den 70er Jahren in IBM erfunden. Dies ist üblicherweise durch das Akronym, SQL, und wird sowohl als "ESS-Hinweis-ell" als auch als "Fortsetzung" bezeichnet. SQL wurde ein ANSI-Standard in 1986 und ein ISO-Standard in 1987. Sie wird heute in vielen Datenbankverwaltungssystemen verwendet.  
  
 Obwohl SQL die Ad-hoc-Anforderungen von Benutzern gelöst hat, wurde die Notwendigkeit des Datenzugriffs durch Computerprogramme nicht entfernt. Tatsächlich war der größte Datenbankzugriff immer noch (und ist) Programm gesteuert, in Form von regelmäßig geplanten Berichten und statistischen Analysen, von Dateneingabe Programmen wie z. b. denen, die für den Bestell Eintrag verwendet werden, und von Daten Bearbeitungsprogrammen, wie z  
  
 Diese Programme verwenden auch SQL mit einer der folgenden drei Verfahren:  
  
-   **Eingebettetes SQL**, in dem SQL-Anweisungen in eine Host Sprache wie C oder COBOL eingebettet sind.  
  
-   **SQL-Module**, in denen SQL-Anweisungen auf dem DBMS kompiliert und von einer Host Sprache aufgerufen werden.  
  
-   **Schnittstelle auf Aufruf Ebene**oder CLI, die aus Funktionen besteht, die zum Übergeben von SQL-Anweisungen an das DBMS und zum Abrufen von Ergebnissen aus dem DBMS aufgerufen werden.  
  
> [!NOTE]  
>  Es ist ein Verlaufs Zufall, dass anstelle der Anwendungsprogrammierschnittstelle (Application Programming Interface, API) der Begriff "callsebenenschnittstelle" verwendet wird. In der Welt der Datenbanken wird die API verwendet, um SQL selbst zu beschreiben: SQL ist die API für ein DBMS.  
  
 Von diesen Optionen wird eingebettetes SQL am häufigsten verwendet, obwohl die meisten wichtigen DBMSs proprietäre Clis unterstützen.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Verarbeiten einer SQL-Anweisung](../../odbc/reference/processing-a-sql-statement.md)  
  
-   [Embedded SQL](../../odbc/reference/embedded-sql.md)  
  
-   [SQL-Module](../../odbc/reference/sql-modules.md)  
  
-   [Call-Level-Interface](../../odbc/reference/call-level-interfaces.md)
